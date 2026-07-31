---
title: "Créer un projet QuPath reproductible"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Sommaire"
layout: single
---

Un projet QuPath contient les chemins vers les lames, les annotations et les mesures. Il ne remplace pas les fichiers originaux. Préparez son dossier avant d'importer la première lame.

## Préparer les dossiers

Créez cette structure, de préférence sur un disque local ou un partage réseau stable:

```text
analyse-cohorte/
  lames/        # fichiers .svs, .ndpi, .mrxs, .ome.tif...
  qupath/       # fichier .qpproj et données du projet
  exports/      # CSV, GeoJSON et images produites
  scripts/      # scripts Groovy versionnés
  README.md     # objectifs, versions, classes et paramètres
```

Ne déplacez pas les lames après leur import dans QuPath. Sinon les chemins du projet deviennent invalides.

## Créer le projet

1. Installez [QuPath 0.7]({{ site.baseurl }}{% post_url 2025-01-01-Installation-de-QuPath %}).
2. Dans QuPath, sélectionnez **File > Project > Create project...**.
3. Choisissez le dossier `qupath/`, puis donnez un nom explicite, par exemple `cohorte_2026.qpproj`.
4. Ajoutez une seule lame pilote avec **Project > Add images...**.
5. Ouvrez-la, créez une annotation, enregistrez et fermez le projet.
6. Rouvrez le projet: la lame, l'annotation et l'échelle doivent être intactes.

## Fixer les conventions dès le départ

- Donnez un identifiant unique à chaque lame, par exemple `COH01_P012_HE`.
- Employez une seule langue pour les classes: `Tumor`, `Stroma`, `Immune`, `Artefact` est un exemple cohérent.
- Écrivez dans `README.md` la version de QuPath, les extensions, le modèle de segmentation et les réglages validés.
- Placez les scripts dans `scripts/`; un script est plus traçable qu'un enchaînement manuel non documenté.

## Vérification minimale

Avant d'ajouter toutes les lames, testez un export CSV et un export GeoJSON sur la lame pilote. Si vous pouvez les relier à l'identifiant de la lame, la structure est prête.

## Continuer

- [Importer une lame entière et contrôler son échelle]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Créer des annotations utiles]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Scripts QuPath utiles]({{ site.baseurl }}{% post_url 2025-01-01-Liste-Script_Qupath %})
