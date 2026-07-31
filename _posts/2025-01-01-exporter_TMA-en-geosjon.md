---
title: "Exporter un TMA QuPath en GeoJSON"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Export
toc: true
toc_label: "Sommaire"
layout: single
---

Cette procédure convertit les cores d'une grille TMA en annotations, puis exporte ces annotations en GeoJSON. Faites une copie du projet: le script supprime la grille TMA après la conversion.

## Créer ou vérifier la grille TMA

1. Ouvrez une lame dans un projet QuPath 0.7.
2. Lancez **TMA > TMA dearray**.
3. Indiquez le nombre de lignes, de colonnes et le diamètre des cores.
4. Ajustez chaque core et marquez les cores absents dans la grille.
5. Enregistrez le projet avant la conversion.

## Convertir les cores en annotations

Ouvrez **Automate > Show script editor**, puis lancez ce script. Les cores présents reçoivent la classe `Tumor`; les cores marqués absents reçoivent `no Tumor`. Adaptez ces deux noms à votre nomenclature avant l'exécution.

```groovy
import qupath.lib.objects.PathObjects

def cores = getTMACoreList()
assert !cores.isEmpty() : 'Aucune grille TMA trouvée dans cette lame.'

def annotations = cores.collect { core ->
    def pathClass = core.isMissing() ? getPathClass('no Tumor') : getPathClass('Tumor')
    PathObjects.createAnnotationObject(core.getROI(), pathClass)
}

removeTMAGrid()
addObjects(annotations)
fireHierarchyUpdate()
println "${annotations.size()} cores convertis en annotations."
```

## Exporter le GeoJSON

1. Enregistrez le projet.
2. Choisissez **File > Export objects as GeoJSON...**.
3. Sélectionnez **All objects** et enregistrez, par exemple, `TMA_001.geojson` dans `exports/`.
4. Ouvrez le fichier dans un éditeur de texte: il doit contenir un tableau `features` avec un objet par core.

Pour automatiser cet export sur tout le projet, utilisez le [script d'export GeoJSON]({{ site.baseurl }}{% post_url 2025-01-01-Liste-Script_Qupath %}).
