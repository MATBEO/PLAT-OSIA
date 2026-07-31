---
title: "Installer CUDA pour les extensions QuPath"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - GPU
toc: true
toc_label: "Sommaire"
toc_sticky: true
layout: single
---

CUDA concerne uniquement les cartes **NVIDIA**. QuPath fonctionne sans CUDA; installez-le seulement si une extension de deep learning, comme InstanSeg, doit utiliser votre GPU. Les Mac Apple Silicon utilisent MPS, pas CUDA.

La procédure ci-dessous vise CUDA 13.3. Vérifiez d'abord que votre carte est [compatible CUDA](https://developer.nvidia.com/cuda-gpus).

## 1. Installer et tester le pilote NVIDIA

1. Téléchargez le pilote adapté à votre carte depuis [NVIDIA Driver Downloads](https://www.nvidia.com/download/index.aspx).
2. Installez-le, puis redémarrez l'ordinateur.
3. Ouvrez un terminal (ou PowerShell sous Windows) et lancez:

```bash
nvidia-smi
```

La commande doit afficher le modèle de la carte et une version de pilote. Si elle échoue, n'installez pas encore CUDA Toolkit: corrigez d'abord le pilote.

## 2. Windows

1. Ouvrez [CUDA Downloads](https://developer.nvidia.com/cuda-downloads), puis choisissez **Windows > x86_64 > version de Windows > exe (local)**.
2. Téléchargez CUDA 13.3 et lancez l'installateur en tant qu'administrateur.
3. Gardez les composants Toolkit proposés. Le pilote NVIDIA est déjà installé à l'étape précédente.
4. Fermez puis rouvrez PowerShell et vérifiez:

```powershell
nvidia-smi
nvcc --version
where.exe nvcc
```

`nvcc --version` doit afficher `release 13.3`. Si `where.exe nvcc` ne retourne rien, rouvrez une session Windows avant de modifier manuellement la variable `PATH`.

## 3. Ubuntu 24.04

Ces commandes installent le Toolkit 13.3 sans remplacer votre environnement par une installation générique. Elles supposent qu'un pilote NVIDIA fonctionnel est déjà présent.

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update
sudo apt install -y cuda-toolkit-13-3
echo 'export PATH=/usr/local/cuda-13.3/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
nvidia-smi
nvcc --version
```

Sur une autre distribution Linux, sélectionnez la distribution exacte sur [CUDA Downloads](https://developer.nvidia.com/cuda-downloads). N'utilisez pas les commandes Ubuntu sur Debian, Fedora ou WSL sans adapter le dépôt.

## 4. Vérifier dans QuPath

Dans **Extensions > Manage extensions**, vérifiez que **Deep Java Library** et **InstanSeg** sont installés. Lancez d'abord InstanSeg sur une petite annotation avec `cpu`, puis choisissez le périphérique GPU dans l'interface si l'extension le propose. Un `nvidia-smi` valide prouve que le système voit le GPU; il ne prouve pas à lui seul que l'extension utilise CUDA.

## En cas de problème

- `nvidia-smi` introuvable: pilote NVIDIA absent ou non chargé.
- `nvcc` introuvable: Toolkit absent ou terminal ouvert avant l'installation.
- mémoire insuffisante pendant une segmentation: réduisez la taille de tuile ou testez une annotation plus petite.
- Mac Apple Silicon: utilisez `mps` ou `cpu`, sans installer CUDA.

## Continuer

- [Segmenter des cellules avec InstanSeg]({{ site.baseurl }}{% post_url 2025-01-01-InstaSeg %})
- [Documentation CUDA 13.3 pour Linux](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/)
- [Documentation CUDA pour Windows](https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/)
