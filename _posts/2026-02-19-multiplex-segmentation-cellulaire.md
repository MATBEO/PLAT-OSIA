---
title: "Multiplex : segmentation cellulaire adaptée"
date: 2026-02-19T00:00:00-01:00
categories:
  - Multiplex
tags:
  - Multiplex
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Multiplex : segmentation cellulaire adaptée

## Étapes
1. Sélectionner une méthode de segmentation compatible fluorescence.
2. Tester les paramètres sur 2 zones contrastées.
3. Ajuster `cell expansion` et taille minimale des objets.
4. Vérifier qu'il n'y a pas de sur-segmentation massive.
5. Geler les paramètres pour le lot complet.

## Exemple
```yaml
nucleus_detection:
  sigma: 1.5
  min_area_um2: 20
cell_expansion_um: 5
watershed_postprocess: true
```

## Documentation
- [QuPath cell detection tutorials](https://qupath.readthedocs.io/en/latest/docs/tutorials/cell_detection.html)
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
