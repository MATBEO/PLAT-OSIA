---
title: "Exporter des TMA de QuPath en GeoJSON puis les réimporter"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
  - Python
  - GeoJSON
  - TMA
toc: true
toc_sticky : true
layout: single
---

# Définir la zone d'intérêt sur QuPath

Ouvrez QuPath et créez les TMA.
Pour cela :
Allez dans **TMA → TMA dearray**
Précisez le nombre de lignes et de colonnes, ainsi que la taille des cores.

Déplacez les cores si nécessaire.

# Lancer le script en Groovy

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

# Sauvegarder le GeoJSON

Sauvegardez votre objet GeoJSON.
Allez dans **File → Export objects as GeoJSON**
Sélectionnez : "All objects"
