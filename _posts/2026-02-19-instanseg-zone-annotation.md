---
title: "InstanSeg : segmentation sur zones annotées"
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

# InstanSeg : segmentation sur zones annotées

## Étapes
1. Créer les annotations ROI avant la segmentation.
2. Ne sélectionner que les annotations cibles (éviter `Whole slide`).
3. Lancer InstanSeg en mode `selected annotations only`.
4. Vérifier le nombre de cellules détectées par ROI.
5. Exporter les mesures par annotation.

## Exemple
```groovy
def rois = getAnnotationObjects().findAll { it.getPathClass() != null }
selectObjects(rois)
println 'ROI sélectionnées: ' + rois.size()
```

## Documentation
- [Annotations in QuPath](https://qupath.readthedocs.io/en/latest/docs/starting/annotating.html)
- [InstanSeg extension](https://github.com/qupath/qupath-extension-instanseg)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
