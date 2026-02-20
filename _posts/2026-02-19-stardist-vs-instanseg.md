---
title: "StarDist vs InstanSeg : quand utiliser quoi"
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

# StarDist vs InstanSeg : quand utiliser quoi

## Étapes
1. Évaluer les deux modèles sur les mêmes ROI.
2. Mesurer temps de traitement et stabilité des contours.
3. Comparer faux positifs/faux négatifs sur 3 cas difficiles.
4. Choisir un modèle unique par cohorte pour éviter les biais.
5. Documenter le choix final et la raison.

## Exemple
```text
Décision rapide:
- StarDist: souvent plus simple pour noyaux H&E
- InstanSeg: flexible nuclei+cell, bon en multiplex
- Choix final: meilleur compromis précision/temps sur ton jeu de données
```

## Documentation
- [StarDist extension](https://github.com/qupath/qupath-extension-stardist)
- [InstanSeg extension](https://github.com/qupath/qupath-extension-instanseg)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
