---
title: "exporter des TMA de Qupath en GeoJson puis pouvoir les réimporter"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Qupath
  - Python
  - Geojson
  - TMA
toc: true
toc_sticky : true
layout: single
---

# définir la zone d'interet sur qupath

Ouvrir Qupath et creer les TMAs
pour cela, 
Allez dans **TMA → TMA dearray**
Préciser le nombre de lignes et colonnes et la tailles des cores

Déplacer les cores si nécessaire

# lancer le script en groovy

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

# sauver le geojson

Sauver votre objet geojson 
Allez dans **File → Export objects as GeoJson**
selectionner : "All objects"

