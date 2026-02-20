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

## Téléchargements
- Pilotes NVIDIA (officiel): [https://www.nvidia.com/download/index.aspx](https://www.nvidia.com/download/index.aspx)
- CUDA Toolkit (officiel): [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)
- Archive CUDA (versions): [https://developer.nvidia.com/cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive)

Version actuelle repérée dans l'archive au 20 février 2026: **CUDA Toolkit 13.1.1 (janvier 2026)**.

## Installation Windows 10/11
1. Installer le pilote NVIDIA depuis la page officielle.
2. Aller sur `cuda-downloads`, choisir `Windows` puis télécharger l'installateur `exe (local)`.
3. Lancer l'installateur CUDA en administrateur.
4. Redémarrer le PC.
5. Vérifier dans PowerShell:

```powershell
nvidia-smi
nvcc --version
where nvcc
```

Si `nvcc` n'est pas trouvé, vérifier ce dossier dans le `PATH`:
`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v13.1\bin`

## Installation Ubuntu 24.04 (APT)
```bash
# 1) Pilote NVIDIA
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
sudo reboot

# 2) Dépôt CUDA
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update

# 3) Toolkit
sudo apt install -y cuda-toolkit-13-1
sudo reboot
```

Liens utiles Ubuntu 24.04:
- [Index dépôt NVIDIA CUDA Ubuntu 24.04 x86_64](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/)
- [Pin de repo](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-ubuntu2404.pin)
- [Meta-paquet CUDA 13.1.1](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-toolkit-13-1_13.1.1-1_amd64.deb)

## Installation Ubuntu 22.04 (APT)
```bash
# 1) Pilote NVIDIA
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
sudo reboot

# 2) Dépôt CUDA
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update

# 3) Toolkit
sudo apt install -y cuda-toolkit-13-1
sudo reboot
```

Liens utiles Ubuntu 22.04:
- [Index dépôt NVIDIA CUDA Ubuntu 22.04 x86_64](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/)
- [Pin de repo](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin)
- [Meta-paquet CUDA 13.1.1](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-toolkit-13-1_13.1.1-1_amd64.deb)

## Vérification rapide
```bash
nvidia-smi
nvcc --version
```

## Documentation
- [Guide d'installation CUDA Linux 13.1](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)
- [Guide d'installation CUDA Windows 13.1](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html)
- [Documentation CUDA](https://docs.nvidia.com/cuda/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : vérifier CUDA côté système]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-verification %})
- [Performance : choisir CPU/GPU selon la tâche]({{ site.baseurl }}{% post_url 2026-02-19-perf-qupath-gpu-choix %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
