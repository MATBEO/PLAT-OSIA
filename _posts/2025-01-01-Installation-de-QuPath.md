---
title: "Installation de QuPath 0.7"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
---

# Installation de QuPath 0.7

Au **3 mars 2026**, la source officielle que j'ai pu vérifier pour QuPath 0.7 est la **pré-release `v0.7.0-rc1` publiée le 17 février 2026** sur le GitHub officiel de QuPath.

## Téléchargements officiels

- Release GitHub: [QuPath `v0.7.0-rc1`](https://github.com/qupath/qupath/releases/tag/v0.7.0-rc1)
- Documentation d'installation: [Installation QuPath](https://qupath.readthedocs.io/en/latest/docs/intro/installation.html)
- Documentation générale: [Documentation QuPath](https://qupath.readthedocs.io/en/latest/)

### Liens directs

- Windows: [QuPath-v0.7.0-rc1-Windows.zip](https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Windows.zip)
- macOS Intel: [QuPath-v0.7.0-rc1-Mac-x64.pkg](https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Mac-x64.pkg)
- macOS Apple Silicon: [QuPath-v0.7.0-rc1-Mac-arm64.pkg](https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Mac-arm64.pkg)
- Linux: [QuPath-v0.7.0-rc1-Linux.tar.xz](https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Linux.tar.xz)

## Installation Windows

1. Téléchargez `QuPath-v0.7.0-rc1-Windows.zip`.
2. Décompressez l'archive dans un dossier simple, par exemple `C:\QuPath`.
3. Ouvrez le dossier extrait.
4. Lancez `QuPath-v0.7.0-rc1.exe`.

## Installation macOS

1. Téléchargez le `.pkg` correspondant à votre machine:
   - `Mac-x64.pkg` pour Intel
   - `Mac-arm64.pkg` pour Apple Silicon
2. Lancez l'installateur.
3. Si macOS bloque l'ouverture:
   - faites clic droit sur l'application
   - choisissez `Ouvrir`
   - confirmez l'ouverture

## Installation Linux

1. Téléchargez `QuPath-v0.7.0-rc1-Linux.tar.xz`.
2. Décompressez l'archive.
3. Ouvrez un terminal dans le dossier extrait.
4. Rendez exécutable le lanceur puis lancez QuPath:

```bash
tar -xf QuPath-v0.7.0-rc1-Linux.tar.xz
cd QuPath-*/bin
chmod u+x QuPath
./QuPath
```

## Vérifier l'installation

Dans QuPath:

1. Ouvrez `Help > About`.
2. Vérifiez que la version affichée est bien `0.7.0-rc1`.
3. Ouvrez une image test.
4. Créez une annotation simple.
5. Sauvegardez un projet.

## Important

- `0.7.0-rc1` est une **pré-release**.
- Sauvegardez vos projets avant de les ouvrir avec cette version.
- Vérifiez la compatibilité de vos extensions QuPath avant migration.

## Voir aussi

- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Liste des extensions QuPath]({{ site.baseurl }}{% post_url 2025-01-01-Liste_extension_QuPath %})
- [Comment détecter des cellules dans QuPath]({{ site.baseurl }}{% post_url 2025-01-01-InstaSeg %})
