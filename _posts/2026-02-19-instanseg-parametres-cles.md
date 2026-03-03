---
title: "InstanSeg : paramètres clés à connaître"
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

# InstanSeg : paramètres clés à connaître

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath 0.7 installé.
- Au 3 mars 2026, la version officielle vérifiée est `v0.7.0-rc1`.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Fixer `tile_size` selon la RAM GPU (512, 1024, 1536).
2. Augmenter `tile_padding` si les objets sont coupés en bordure.
3. Adapter le device (`cpu`, `gpu`, `mps`) selon la machine.
4. Conserver les mêmes paramètres sur toute la cohorte.
5. Journaliser les paramètres dans un fichier `run_params.yaml`.

## À copier-coller
```yaml
device: gpu
tile_size: 1024
tile_padding: 64
batch_size: 1
save_measurements: true
model: instanseg_general
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
- [InstanSeg README](https://github.com/qupath/qupath-extension-instanseg)
- [CUDA compatibility guide](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
