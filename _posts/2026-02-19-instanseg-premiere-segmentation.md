---
title: "InstanSeg : première segmentation cellule + noyau"
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

# InstanSeg : première segmentation cellule + noyau

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Installer l'extension InstanSeg compatible avec ta version de QuPath.
2. Charger une image test avec une annotation de taille moyenne.
3. Lancer InstanSeg sur CPU d'abord pour valider le flux.
4. Passer en GPU/MPS ensuite pour accélérer.
5. Comparer visuellement 2 zones (dense vs peu cellulaire).

## À copier-coller
```text
Paramètres de départ recommandés:
- device: cpu (premier test), puis gpu/mps
- tile_size: 1024
- tile_padding: 64
- outputs: nuclei + cells
```

## Vérifier que ça marche
- Des objets sont bien détectés dans la ROI test.
- Pas de sur-segmentation massive en bordure.
- Les mesures exportées sont non vides.

## En cas de problème
- Tester d'abord en CPU puis passer en GPU/MPS.
- Réduire la taille de tuile si erreur mémoire.

## Documentation officielle
- [InstanSeg extension QuPath](https://github.com/qupath/qupath-extension-instanseg)
- [QuPath extension management](https://qupath.readthedocs.io/en/latest/docs/intro/extensions.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : paramètres clés à connaître]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-parametres-cles %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
