---
title: "Scripts QuPath"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
  - Groovy
  - GeoJSON
layout: single
toc: true
toc_label: "Table des matières"
classes: wide
---

# Extraction GeoJSON

```
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
```

# Détection vers annotation
```   
def detections = getDetectionObjects()
def newAnnotations = detections.collect {
return PathObjects.createAnnotationObject(it.getROI(), it.getPathClass())
}
removeObjects(detections, true)
addObjects(newAnnotations)
```

# Annotation vers détection
```   
def annotations = getAnnotationObjects()
def newDetections = annotations.collect{
    return PathObjects.createDetectionObject(it.getROI(), it.getPathClass())
}
// removeObjects(annotations, true) // uncomment to remove original annotations
addObjects(newDetections)
```

# TMA To Annotation
```
import qupath.lib.objects.PathObjects
import qupath.lib.objects.classes.PathClassFactory

// Récupérer tous les TMA cores
def tmaCores = getTMACoreList()

def newAnnotations = []

tmaCores.each { core ->
    def roi = core.getROI()
    def cls

    // Si le core est marqué comme manquant
    if (core.isMissing()) {
        cls = PathClassFactory.getPathClass("no Tumor")
    } else {
        cls = PathClassFactory.getPathClass("Tumor")
    }

    def ann = PathObjects.createAnnotationObject(roi, cls)
    newAnnotations << ann
}

// Supprimer les TMA cores originaux
removeTMAGrid()

// Ajouter les nouvelles annotations
addObjects(newAnnotations)

print "Transformé ${tmaCores.size()} TMA cores en annotations avec classification Tumor / no Tumor."
```

# Préciser automatiquement l'échelle
```
setImageType('BRIGHTFIELD_H_E');
setColorDeconvolutionStains('{"Name" : "H&E default", "Stain 1" : "Hematoxylin", "Values 1" : "0.65111 0.70119 0.29049", "Stain 2" : "Eosin", "Values 2" : "0.2159 0.8012 0.5581", "Background" : " 255 255 255"}');
setPixelSizeMicrons(0.262100, 0.262100)
```
