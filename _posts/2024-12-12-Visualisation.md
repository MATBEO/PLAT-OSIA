---
title: "Comment regarder les data sur Qupath."
date: 2024-04-18T15:34:30-04:00
categories:
  - Visualisation
tags:
  - Qupath
  - Groovy
  - Python
  - Geojson
---

<img src="/assets/images/visualisation.svg" width="50">

## geojson extraction

    // Define output where to save annotations
    def pathOutput = buildFilePath('PATH', 'Annotations')
    print pathOutput
    mkdirs(pathOutput)

    // To get all image of the project -> in order to run the scripts on all function (if no project: just getCurrentImageData() and remove the loop)
    def project = getProject()

    for (img in project.getImageList()){
    // Get image data, hierarchy and annotations for given image
    def imageData = img.readImageData()
    def hierarchy=imageData.getHierarchy()
    def annotations=hierarchy.getAnnotationObjects()


    // name of the output file to save
    def name = GeneralTools.getNameWithoutExtension(imageData.getServer().getMetadata().getName())
    def fileOutput = buildFilePath(pathOutput, name)
    println "save annotation: "+fileOutput+".geojson"
    tt=fileOutput+".geojson"

    // write (save) the json file
    try (Writer writer = new FileWriter(fileOutput+".geojson")) {
    exportObjectsToGeoJson(annotations,tt, "FEATURE_COLLECTION")
     }
    }
    print("done")

## annotation to detection
    def detections = getDetectionObjects()
    def newAnnotations = detections.collect {
    return PathObjects.createAnnotationObject(it.getROI(), it.getPathClass())
    }
    removeObjects(detections, true)
    addObjects(newAnnotations)

## tissu detection and tiles extraction

    import timm
    import os
    import torch
    from torchvision import transforms
    from PIL import Image
    import openslide
    import numpy as np
    from skimage.color import rgb2gray
    import json

    #### definition of the model
    model = timm.create_model("vit_large_patch16_224", img_size=224, patch_size=16, init_values=1e-5, num_classes=0, dynamic_img_size=True)
    model.load_state_dict(torch.load("PATH.bin", map_location="mps",weights_only=True), strict=True)
    transform = transforms.Compose(
        [
            transforms.Resize(224),
            transforms.ToTensor(),
            transforms.Normalize(mean=(0.485, 0.456, 0.406), std=(0.229, 0.224, 0.225)),
        ]
    )


    def is_tissue(tile, extrem_val = 0.1,tissue_threshold=0.02, homogeneity_threshold=0.005):
        """
        Extract tiles with tissue from a whole-slide image.
        :param tile: tile to analyse ([:,:,1])
        :param extrem_val: extrem grey value to exclude (default: 0.1)
        :param tissue_threshold: ratio of pixels to consider as tissu in the tile (default: 0.02)
        :param homogeneity_threshold : homogeneity in the tile (default: 5x)
        """
        return (np.sum((tile < (1-extrem_val)) & (tile > extrem_val))/ tile.size) > tissue_threshold and (np.var(tile)) > homogeneity_threshold

    def extract_tiles_with_tissue(slide_path,geojson_path, magnification=20, tile_size=224, low_mag=5, extract_features=False):
        """
        Extract tiles with tissue from a whole-slide image.
        :param slide_path: Path to the whole-slide image (.mrxs, .svs, .ndpi)
        :param geojson_path: Path to the geojson (.geojson)
        :param magnification: Desired magnification for tile extraction (e.g., 20x)
        :param tile_size: Size of the square tile in pixels (default: 224x224)
        :param low_mag: Low magnification level for tissue detection (default: 5x)
        :param extract_features: do you want to extract features ? (default: false)   
        """
        # Open the whole-slide image
        slide = openslide.OpenSlide(slide_path)
        
        # Get the best level to use for tissue detection (closest to low_mag)
        low_mag_level = slide.get_best_level_for_downsample(float(slide.properties[openslide.PROPERTY_NAME_OBJECTIVE_POWER]) / low_mag)
        low_mag_downsample_factor = slide.level_downsamples[low_mag_level]
        
        # Get dimensions of the slide at this low magnification level
        low_mag_width, low_mag_height = slide.level_dimensions[low_mag_level]
        
        # Calculate the scaled tile size for tissue detection (in low magnification level)
        scaled_tile_size = int(tile_size * low_mag_downsample_factor)
        
        tile_id = 0
        features=[]
        feat=[]

        # Iterate over the slide at low magnification level and detect tissue
        for y in range(0, low_mag_height, scaled_tile_size):
            for x in range(0, low_mag_width, scaled_tile_size):
                # Corrected: Scale back to full-resolution coordinates for reading the tile
                region_x = int(x * low_mag_downsample_factor)
                region_y = int(y * low_mag_downsample_factor)
                region_size = int(scaled_tile_size / low_mag_downsample_factor)
                # Extract the tile at low magnification level for tissue detection
                low_mag_tile = rgb2gray(np.array(slide.read_region((region_x, region_y), low_mag_level, (scaled_tile_size, scaled_tile_size)))[:,:,0:3])
                # Check if the tile contains tissue
                if is_tissue(low_mag_tile):
                    for high_y in range(0, scaled_tile_size*int(low_mag_downsample_factor), tile_size):
                        for high_x in range(0, scaled_tile_size*int(low_mag_downsample_factor), tile_size):
                            global_x = int(region_x + high_x)
                            global_y = int(region_y + high_y)
                            # Read the corresponding tile at the desired magnification (e.g., 20x)
                            high_mag_tile = slide.read_region(
                                (global_x, global_y),
                                0,  # Full-resolution level (20x)
                                (tile_size, tile_size)
                            )
                            if is_tissue(rgb2gray(np.array(high_mag_tile)[:,:,0:3])):
                                high_mag_tile = high_mag_tile.convert("RGB")
                                image = transform(high_mag_tile).unsqueeze(dim=0) # Image (torch.Tensor) with shape [1, 3, 224, 224] following image resizing and normalization (ImageNet parameters)
                                if extract_features :
                                    with torch.inference_mode():
                                        feature_emb = model(image) # Extracted features (torch.Tensor) with shape [1,1024]
                                        feat.append(feature_emb)
    
                                # Create GeoJSON feature for this tile
                                feature = {
                                        "type": "Feature",
                                        "geometry": {
                                            "type": "Polygon",
                                            "coordinates": [[
                                                [global_x, global_y],  # Top-left corner
                                                [global_x + tile_size, global_y],  # Top-right corner
                                                [global_x + tile_size, global_y + tile_size],  # Bottom-right corner
                                                [global_x, global_y + tile_size],  # Bottom-left corner
                                                [global_x, global_y]  # Closing the polygon
                                            ]]
                                        },
                                        "properties": {
                                            "tile_id": tile_id,
                                            "tile_path": slide_path,
                                            "width": tile_size,
                                            "height": tile_size
                                        }
                                    }
                                features.append(feature)
                            tile_id += 1
        # Save GeoJSON
        geojson_data = {
                "type": "FeatureCollection",
                "features": features
                }
        with open(geojson_path, 'w') as geojson_file:
                    json.dump(geojson_data, geojson_file, indent=4)
                            
        print(f"Tiles extraction complete! Extracted {tile_id} tiles with tissue.")
        return feat,features
        
    # Path to your whole-slide image (.mrxs, .svs, or .ndpi)
    slide_path = 'PATH.ndpi'
        
    # Output directory where geojson will be saved
    geojson_path = 'PATH.geojson' 
    # Extract tiles with tissue at 20x magnification and save
    tt=extract_tiles_with_tissue(slide_path, 
                                 geojson_path, 
                                 magnification=20, 
                                 tile_size=224, 
                                 low_mag=10, 
                                 extract_features=False)`

