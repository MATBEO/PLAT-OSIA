---
title: "Scripts QuPath"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
layout: single
toc: true
toc_label: "Table des matières"
classes: wide
---

# Extraction GeoJSON

Scripts relus pour **QuPath 0.7**.
Point important : les anciens workflows enregistrés ne sont plus supportés en 0.7. Gardez vos scripts dans **Automate > Show script editor** puis sauvegardez-les dans votre dépôt.

```groovy
import qupath.lib.common.GeneralTools

// Define output where to save annotations
def pathOutput = buildFilePath(PROJECT_BASE_DIR, 'exports', 'annotations')
print pathOutput
mkdirs(pathOutput)

// To get all image of the project -> in order to run the scripts on all function (if no project: just getCurrentImageData() and remove the loop)
def project = getProject()
assert project != null : 'Ouvrez un projet QuPath avant de lancer ce script.'

for (img in project.getImageList()) {
// Get image data, hierarchy and annotations for given image
def imageData = img.readImageData()
def hierarchy = imageData.getHierarchy()
def annotations = hierarchy.getAnnotationObjects()


// name of the output file to save
def name = GeneralTools.getNameWithoutExtension(imageData.getServer().getMetadata().getName())
def fileOutput = buildFilePath(pathOutput, name + '.geojson')
println "save annotation: " + fileOutput
exportObjectsToGeoJson(annotations, fileOutput, 'FEATURE_COLLECTION')
}
println 'done'
```

# Détection vers annotation
```groovy
import qupath.lib.objects.PathObjects

def detections = getDetectionObjects()
def newAnnotations = detections.collect {
    PathObjects.createAnnotationObject(it.getROI(), it.getPathClass())
}
removeObjects(detections, true)
addObjects(newAnnotations)
```

# Annotation vers détection
```groovy
import qupath.lib.objects.PathObjects

def annotations = getAnnotationObjects()
def newDetections = annotations.collect {
    PathObjects.createDetectionObject(it.getROI(), it.getPathClass())
}
// removeObjects(annotations, true) // uncomment to remove original annotations
addObjects(newDetections)
```

# TMA To Annotation
```groovy
import qupath.lib.objects.PathObjects

// Récupérer tous les TMA cores
def tmaCores = getTMACoreList()

def newAnnotations = []

tmaCores.each { core ->
    def roi = core.getROI()
    def cls

    // Si le core est marqué comme manquant
    if (core.isMissing()) {
        cls = getPathClass('no Tumor')
    } else {
        cls = getPathClass('Tumor')
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

# Définir le type d'image et l'échelle
```groovy
setImageType('BRIGHTFIELD_H_E');
setColorDeconvolutionStains('{"Name" : "H&E default", "Stain 1" : "Hematoxylin", "Values 1" : "0.65111 0.70119 0.29049", "Stain 2" : "Eosin", "Values 2" : "0.2159 0.8012 0.5581", "Background" : " 255 255 255"}');
setPixelSizeMicrons(0.262100, 0.262100)
```
