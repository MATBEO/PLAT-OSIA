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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath 0.7 installé.
- Au 3 mars 2026, la version officielle vérifiée est `v0.7.0-rc1`.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Évaluer les deux modèles sur les mêmes ROI.
2. Mesurer temps de traitement et stabilité des contours.
3. Comparer faux positifs/faux négatifs sur 3 cas difficiles.
4. Choisir un modèle unique par cohorte pour éviter les biais.
5. Documenter le choix final et la raison.

## À copier-coller
```text
Décision rapide:
- StarDist: souvent plus simple pour noyaux H&E
- InstanSeg: flexible nuclei+cell, bon en multiplex
- Choix final: meilleur compromis précision/temps sur ton jeu de données
```

## Vérifier que ça marche
- Des objets sont bien détectés dans la ROI test.
- Pas de sur-segmentation massive en bordure.
- Les mesures exportées sont non vides.

## En cas de problème
- Tester d'abord en CPU puis passer en GPU/MPS.
- Réduire la taille de tuile si erreur mémoire.

## Documentation officielle
- [QuPath `v0.7.0-rc1`](https://github.com/qupath/qupath/releases/tag/v0.7.0-rc1)
- [StarDist extension](https://github.com/qupath/qupath-extension-stardist)
- [InstanSeg extension](https://github.com/qupath/qupath-extension-instanseg)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
