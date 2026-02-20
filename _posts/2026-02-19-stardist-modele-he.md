---
title: "StarDist : utiliser un modèle H&E pré-entraîné"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cell
tags:
  - Segmentation
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# StarDist : utiliser un modèle H&E pré-entraîné

## Étapes
1. Installer/activer l'extension StarDist dans QuPath.
2. Tester 2 à 3 paramètres de seuil sur une ROI de référence.
3. Valider la morphologie des noyaux détectés.
4. Exécuter le lot avec le même preset.
5. Exporter les mesures pour audit QC.

## Exemple
```groovy
// Contrôle simple avant StarDist
println "Image: " + getCurrentImageName()
println "Pixel size (µm): " + getCurrentServer().getPixelCalibration().getAveragedPixelSizeMicrons()
```

## Documentation
- Documentation technique: [Documentation StarDist (QuPath)](https://github.com/qupath/qupath-extension-stardist)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
