---
title: "QuPath : installation propre et vérification initiale"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QuPath : installation propre et vérification initiale

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Télécharger QuPath 0.7 depuis la release officielle.
- Au 3 mars 2026, la version officielle vérifiée est `v0.7.0-rc1`.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Télécharger QuPath depuis la page Release officielle.
2. Installer `v0.7.0-rc1` avec le paquet adapté à votre système.
3. Ouvrir QuPath une première fois pour créer le dossier de configuration.
4. Ajuster la mémoire JVM (`Preferences > Memory`) selon la RAM machine.
5. Valider l'installation sur une lame test (ouverture + annotation + export).

## À copier-coller
```text
Téléchargements officiels QuPath 0.7:
- Release: https://github.com/qupath/qupath/releases/tag/v0.7.0-rc1
- Windows: https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Windows.zip
- macOS Intel: https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Mac-x64.pkg
- macOS Apple Silicon: https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Mac-arm64.pkg
- Linux: https://github.com/qupath/qupath/releases/download/v0.7.0-rc1/QuPath-v0.7.0-rc1-Linux.tar.xz
```

## Vérifier que ça marche
- `Help > About` affiche bien `0.7.0-rc1`.
- La manipulation se lance sans erreur dans QuPath.
- Le résultat attendu est visible sur l'image test.
- Le projet se sauvegarde correctement.

## En cas de problème
- Redémarrer QuPath puis relancer sur une image plus petite.
- Vérifier que vos extensions sont compatibles avec QuPath 0.7.
- Sauvegarder les anciens projets avant migration depuis QuPath 0.6.

## Documentation officielle
- [QuPath `v0.7.0-rc1`](https://github.com/qupath/qupath/releases/tag/v0.7.0-rc1)
- [QuPath Releases](https://github.com/qupath/qupath/releases)
- [Installation QuPath](https://qupath.readthedocs.io/en/latest/docs/intro/installation.html)
- [Documentation QuPath](https://qupath.readthedocs.io/en/latest/)
- [QuPath Scripting](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)

## Articles liés
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [QuPath : fondamentaux des annotations]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
