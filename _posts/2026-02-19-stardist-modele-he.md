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
1. Charger une lame H&E correctement calibrée.
2. Sélectionner un modèle StarDist entraîné pour H&E.
3. Lancer sur petite ROI pour ajuster les paramètres.
4. Étendre au lot si le résultat visuel est acceptable.
5. Exporter les objets et mesures pour revue.

## Exemple
```yaml
model: he_pretrained
probability_threshold: 0.5
nms_threshold: 0.4
pixel_size_um: 0.5
output: nuclei
```

## Documentation
- [StarDist extension QuPath](https://github.com/qupath/qupath-extension-stardist)
- [QuPath tutorials](https://qupath.readthedocs.io/en/latest/docs/tutorials/index.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
