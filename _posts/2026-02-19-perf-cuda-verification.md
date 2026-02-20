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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Machine compatible avec la procédure.
- Droits administrateur si installation système.
- Un cas test pour valider avant production.

## Pas à pas
1. Vérifier pilote GPU visible (`nvidia-smi`).
2. Vérifier compilateur CUDA (`nvcc --version`).
3. Vérifier runtime CUDA côté Python.
4. Tester une opération GPU simple.
5. Archiver la sortie des commandes dans `logs/gpu_check.txt`.

## À copier-coller
```bash
# 1) Pilote et carte
nvidia-smi

# 2) Toolkit CUDA
nvcc --version

# 3) Vérification Python (PyTorch)
python - <<'PY'
import torch
print('torch:', torch.__version__)
print('cuda available:', torch.cuda.is_available())
print('device count:', torch.cuda.device_count())
if torch.cuda.is_available():
    print('device 0:', torch.cuda.get_device_name(0))
PY
```

## Vérifier que ça marche
- Les commandes de contrôle répondent correctement.
- Le gain (ou la stabilité) est mesuré sur cas test.
- Les versions logicielles sont tracées.

## En cas de problème
- Vérifier compatibilité driver/toolkit.
- Tester les commandes de diagnostic système.

## Documentation officielle
- [CUDA docs](https://docs.nvidia.com/cuda/)
- [NVIDIA SMI](https://developer.nvidia.com/system-management-interface)
- [PyTorch CUDA notes](https://pytorch.org/docs/stable/notes/cuda.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : installer CUDA proprement]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %})
- [Performance : choisir CPU/GPU selon la tâche]({{ site.baseurl }}{% post_url 2026-02-19-perf-qupath-gpu-choix %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
