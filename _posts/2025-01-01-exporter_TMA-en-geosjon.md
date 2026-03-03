---
title: "Exporter des TMA de QuPath en GeoJSON puis les réimporter"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
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

Au **3 mars 2026**, la version QuPath 0.7 que j'ai pu vérifier est **`v0.7.0-rc1`**.
Pour QuPath 0.7, gardez ce script dans **Automate → Show script editor**. N'utilisez pas d'ancien workflow enregistré.

# Lancer le script en Groovy

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

# Sauvegarder le GeoJSON

Sauvegardez votre objet GeoJSON.
Dans QuPath 0.7, utilisez **File → Export objects as GeoJSON...**
Si ce menu n'apparaît pas, sélectionnez les annotations dans la liste des objets puis exportez-les en GeoJSON.
Sélectionnez : **All objects**.
