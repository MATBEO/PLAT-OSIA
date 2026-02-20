---
title: "InstanSeg : comparaison CPU, GPU et MPS"
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

# InstanSeg : comparaison CPU, GPU et MPS

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Tester d'abord le pipeline en CPU (robustesse).
2. Activer GPU NVIDIA si disponible pour la production.
3. Sur Apple Silicon, utiliser MPS si l'extension le supporte.
4. Comparer le temps sur la même image et mêmes paramètres.
5. Conserver le mode le plus stable, pas seulement le plus rapide.

## À copier-coller
```bash
# Linux/Windows (NVIDIA)
nvidia-smi
nvcc --version

# macOS Apple Silicon
system_profiler SPHardwareDataType | grep 'Chip' 
```

## Vérifier que ça marche
- Des objets sont bien détectés dans la ROI test.
- Pas de sur-segmentation massive en bordure.
- Les mesures exportées sont non vides.

## En cas de problème
- Tester d'abord en CPU puis passer en GPU/MPS.
- Réduire la taille de tuile si erreur mémoire.

## Documentation officielle
- [CUDA downloads](https://developer.nvidia.com/cuda-downloads)
- [PyTorch MPS backend](https://pytorch.org/docs/stable/notes/mps.html)
- [InstanSeg extension](https://github.com/qupath/qupath-extension-instanseg)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
