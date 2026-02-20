---
title: "Performance : vérifier CUDA côté système"
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

# Performance : vérifier CUDA côté système

## Étapes
1. Installer/mettre à jour le pilote NVIDIA.
2. Installer CUDA Toolkit correspondant.
3. Vérifier la version de `nvcc`.
4. Tester l'utilisation GPU dans l'outil cible.
5. Archiver versions exactes dans le runbook.

## Exemple
```bash
nvidia-smi
nvcc --version
# Linux/macOS
echo $PATH | tr ':' '
' | grep -i cuda || true
```

## Documentation
- Documentation technique: [Documentation CUDA](https://docs.nvidia.com/cuda/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : installer CUDA proprement]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %})
- [Performance : choisir CPU/GPU selon la tâche]({{ site.baseurl }}{% post_url 2026-02-19-perf-qupath-gpu-choix %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
