---
title: "Installer QuPath 0.7"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
  - Installation
toc: true
toc_label: "Sommaire"
---

Cette procédure installe la version stable **QuPath 0.7.0**, publiée le 2 mars 2026. Téléchargez toujours QuPath depuis la [publication officielle](https://github.com/qupath/qupath/releases/tag/v0.7.0).

## Télécharger le bon fichier

- Windows: [installateur `.msi`](https://github.com/qupath/qupath/releases/download/v0.7.0/QuPath-v0.7.0-Windows.msi). La [version portable `.zip`](https://github.com/qupath/qupath/releases/download/v0.7.0/QuPath-v0.7.0-Windows.zip) ne nécessite pas d'installation.
- Mac Apple Silicon (M1, M2, M3, M4): [`.pkg` arm64](https://github.com/qupath/qupath/releases/download/v0.7.0/QuPath-v0.7.0-Mac-arm64.pkg).
- Mac Intel: [`.pkg` x64](https://github.com/qupath/qupath/releases/download/v0.7.0/QuPath-v0.7.0-Mac-x64.pkg).
- Linux 64 bits: [archive `.tar.xz`](https://github.com/qupath/qupath/releases/download/v0.7.0/QuPath-v0.7.0-Linux.tar.xz).

Pour connaître le processeur d'un Mac: menu Apple, puis **A propos de ce Mac**. La ligne `Puce` indique Apple Silicon; la ligne `Processeur` indique Intel.

## Windows

1. Téléchargez `QuPath-v0.7.0-Windows.msi` et ouvrez-le.
2. Conservez le dossier proposé, puis terminez l'installation.
3. Lancez **QuPath** depuis le menu Démarrer.

Pour la version portable, décompressez le `.zip` dans un dossier où vous avez les droits d'écriture, par exemple `C:\Applications\QuPath`, puis lancez `QuPath.exe`. Ne lancez pas QuPath directement depuis le dossier Téléchargements.

## macOS

1. Téléchargez le paquet adapté à votre processeur.
2. Ouvrez le fichier `.pkg` et suivez l'installateur.
3. Lancez QuPath depuis **Applications**.

Si macOS refuse l'ouverture, allez dans **Réglages Système > Confidentialité et sécurité**, puis choisissez **Ouvrir quand même**. Ne téléchargez pas une application depuis un site tiers pour contourner ce blocage.

## Linux

Dans un terminal, exécutez les commandes suivantes dans le dossier où l'archive a été téléchargée:

```bash
tar -xf QuPath-v0.7.0-Linux.tar.xz
cd QuPath-v0.7.0/bin
chmod u+x QuPath
./QuPath
```

## Vérifier avant de commencer une analyse

1. Dans QuPath, ouvrez **Help > About QuPath**: la version doit être `0.7.0`.
2. Créez un projet avec **File > Project > Create project...**.
3. Ajoutez une image test, dessinez une annotation, puis fermez et rouvrez le projet.

Si vous aviez une ancienne installation, mettez aussi les extensions à jour avec **Extensions > Manage extensions**. Gardez une copie du projet avant de l'ouvrir avec une nouvelle version.

## Continuer

- [Créer un projet QuPath reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [Importer une lame entière et contrôler son échelle]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Segmenter des cellules avec InstanSeg]({{ site.baseurl }}{% post_url 2025-01-01-InstaSeg %})
