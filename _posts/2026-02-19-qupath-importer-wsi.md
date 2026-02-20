---
title: "QuPath : importer des lames entières (WSI) correctement"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QuPath : importer des lames entières (WSI) correctement

## Étapes
1. Vérifier que la lame est bien pyramidale (`.svs`, `.ndpi`, `.mrxs`, `.tif` pyramidal).
2. Importer via `Project > Add images...` et ne pas dupliquer les fichiers.
3. Contrôler la calibration pixel (`Image > Properties`).
4. Vérifier orientation/couches de la lame avant annotation.
5. Bloquer toute analyse si `pixel size` est absent ou incohérent.

## Exemple
```groovy
def md = getCurrentServer().getMetadata()
println "Width x Height: ${md.getWidth()} x ${md.getHeight()}"
println "Pixel size (um): " + md.getPixelCalibration().getAveragedPixelSizeMicrons()
println "Magnification: " + md.getMagnification()
```

## Documentation
- [Formats supportés par QuPath](https://qupath.readthedocs.io/en/latest/docs/intro/formats.html)
- [OpenSlide (formats WSI)](https://openslide.org/formats/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : fondamentaux des annotations]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
