---
title: "Comment sauvegarder une image pour une publication"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Qupath
  - Groovy
  - Python
  - Geojson
toc: true
toc_label: "Table des Matieres"
toc_sticky : true
layout: single
---

# définir la zone d'interet sur qupath

Ouvrir Qupath et selectionnez votre zone d'interet


# sauver le geojson

Sauver votre objet geojson dans le meme dossier que votre lame et avec le meme nom

# lancer le script

```
import cv2
import openslide
import math
import json
import numpy as np
from shapely.geometry import Polygon
from PIL import Image
from skimage import transform,util
import os

def extract_and_plot_lowest_mag_roi_svs(fpath: str, rotation=False)
    print(fpath)
    """
    Extrait une région définie par un GeoJSON d'un fichier SVS au niveau de grandissement le plus faible,
    l'exporte en OME-TIFF et affiche les étapes intermédiaires.

    Args:
        svs_path (str): Chemin du fichier SVS.
        geojson_path (str): Chemin du fichier GeoJSON contenant la région à extraire.
        output_path (str): Chemin de sortie pour l'image OME-TIFF.
    """
    svs_path=fpath+".svs"
    geojson_path=fpath+".geojson"
    i=0
    # Charger l'image SVS
    slide = openslide.OpenSlide(svs_path)

    # Charger le GeoJSON
    with open(geojson_path, 'r') as f:
        geojson_data = json.load(f)

    # Extraire les coordonnées du polygone du GeoJSON
    for feature in geojson_data["features"]:
        i=i+1
        output_path=fpath+"."+str(i)+".jpg"
        polygon_coords = feature["geometry"]["coordinates"][0]
        #  mettre le polygone à l'echelle
        polygon_coords= [(int(xi ), int(yi )) for xi, yi in polygon_coords]
        # Convertir en tableau NumPy pour utiliser min et max
        polygon_coords_np = np.array(polygon_coords)
        min_x, min_y, max_x, max_y = map(int, Polygon(polygon_coords).bounds)
        # Déterminer les min et max des coordonnées
        Min_x, Min_y = polygon_coords_np.min(axis=0)
        # Normalisation et mise à l’échelle
        scaled_coords = [(int((x - Min_x)),int((y - Min_y)))for x, y in polygon_coords]

        # Lire la région d'intérêt (ROI) depuis le niveau de faible grandissement
        roi = slide.read_region((int(min_x), int(min_y)), 0, (max_x - min_x, max_y - min_y))
        roi = roi.convert("RGB")
        roi_np = np.array(roi)
        # Créer un masque pour ne garder que la zone définie par le polygone
        mask = np.zeros((roi_np.shape[0], roi_np.shape[1]), dtype=np.uint8)

        cv2.fillPoly(mask, [np.array(scaled_coords, np.int32)], 255)

        # Convertir en BGR pour OpenCV
        #roi_np_bgr = cv2.cvtColor(roi_np, cv2.COLOR_RGB2BGR)
        roi_np_bgr = roi_np
        roi_np_masked = cv2.bitwise_and(roi_np_bgr, roi_np_bgr, mask=mask)

        # Appliquer le masque sur l'image
        if rotation:
            X=int(np.min((np.where(roi_np_masked[0,:,0]>0))[0]))
            Y=int(np.min((np.where(roi_np_masked[:,0,0]>0))[0]))
            roi_np_masked = cv2.resize(roi_np_masked, (0, 0), fx=0.8, fy=0.8)
            if X!=0:
                roi_np_masked=transform.rotate(roi_np_masked, 180-math.atan(Y/X)*180/np.pi, resize=True)
            x,y=np.where(roi_np_masked[:,:,0]>0)
            roi_np_masked=roi_np_masked[min(x):max(x),min(y):max(y),:]
            if roi_np_masked.shape[1]<roi_np_masked.shape[0]:
                print("haut")
                roi_np_masked=transform.rotate(roi_np_masked, 90, resize=True)
        
        x,y=np.where(roi_np_masked[:,:,0]>0)
        roi_np_masked=roi_np_masked[min(x):max(x),min(y):max(y),:]

        Image.fromarray(util.img_as_ubyte(roi_np_masked)).save(output_path, quality=95)
```