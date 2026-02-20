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
1. Définir 3 ROI tests (faible, moyenne, forte densité cellulaire).
2. Lancer InstanSeg sur ces ROI avec paramètres constants.
3. Comparer visuellement le contour cellule/noyau sur chaque ROI.
4. Ajuster `tile size` et padding si artefacts de bord.
5. Appliquer au lot complet et exporter les mesures.

## Exemple
```groovy
// QuPath - exemple minimal InstanSeg (adapter selon votre installation)
def rois = getAnnotationObjects()
if (rois.isEmpty()) throw new Exception('Aucune ROI sélectionnée')
println "InstanSeg sur ${rois.size()} ROI"
// Lancer ensuite via Extensions > InstanSeg > Run InstanSeg avec paramètres notés
```

## Documentation
- Documentation technique: [Documentation InstanSeg (QuPath)](https://github.com/qupath/qupath-extension-instanseg)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
