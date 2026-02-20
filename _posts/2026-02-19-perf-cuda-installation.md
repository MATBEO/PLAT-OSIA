---
title: "Performance : installer CUDA proprement"
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

# Performance : installer CUDA proprement

## Étapes
1. Installer le pilote NVIDIA depuis la page officielle des pilotes.
2. Télécharger CUDA Toolkit depuis la page NVIDIA officielle.
3. Installer CUDA puis redémarrer la machine.
4. Vérifier `nvidia-smi` et `nvcc --version`.
5. Tester l'accès CUDA depuis Python (si pipeline Python).

## Exemple
```bash
# Téléchargements officiels
# Driver: https://www.nvidia.com/download/index.aspx
# CUDA:   https://developer.nvidia.com/cuda-downloads
# Archive: https://developer.nvidia.com/cuda-toolkit-archive

# Windows (PowerShell)
# 1) Télécharger le .exe local depuis cuda-downloads
# 2) Lancer l'installateur en administrateur
# 3) Vérifier:
# nvidia-smi
# nvcc --version
# where nvcc

# Ubuntu 24.04 (APT)
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update
sudo apt install -y cuda-toolkit-13-1
sudo reboot

# Vérification
nvidia-smi
nvcc --version

# Vérification Python (optionnel)
python - <<'PY'
import torch
print('torch:', torch.__version__)
print('cuda available:', torch.cuda.is_available())
if torch.cuda.is_available():
    print('device:', torch.cuda.get_device_name(0))
PY
```

## Documentation
- [CUDA downloads](https://developer.nvidia.com/cuda-downloads)
- [CUDA toolkit archive](https://developer.nvidia.com/cuda-toolkit-archive)
- [NVIDIA driver downloads](https://www.nvidia.com/download/index.aspx)
- [Guide installation CUDA Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)
- [Guide installation CUDA Windows](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : vérifier CUDA côté système]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-verification %})
- [Performance : choisir CPU/GPU selon la tâche]({{ site.baseurl }}{% post_url 2026-02-19-perf-qupath-gpu-choix %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
