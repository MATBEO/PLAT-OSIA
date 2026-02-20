---
title: "Performance : choisir CPU/GPU selon la tâche"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Performance
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Performance : choisir CPU/GPU selon la tâche

## Étapes
1. Mesurer un baseline CPU sur échantillon fixe.
2. Activer GPU et relancer à paramètres constants.
3. Comparer temps, mémoire et qualité de sortie.
4. Ajuster batch/tile size si saturation mémoire.
5. Conserver le tableau comparatif final.

## Exemple
```bash
# Mesure rapide
/usr/bin/time -l python run_pipeline.py --device cpu
/usr/bin/time -l python run_pipeline.py --device gpu
nvidia-smi --query-gpu=utilization.gpu,memory.used --format=csv
```

## Documentation
- Documentation technique: [Documentation NVIDIA SMI](https://developer.nvidia.com/system-management-interface)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : installer CUDA proprement]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %})
- [Performance : vérifier CUDA côté système]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-verification %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
