---
title: "Publication : figure QuPath nette et lisible"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Publication
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Publication : figure QuPath nette et lisible

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Figure source générée dans QuPath.
- Format cible demandé par le journal.
- Nommage de fichiers standardisé.

## Pas à pas
1. Fixer la zone d'intérêt exacte avant export.
2. Activer barre d'échelle et annotations utiles uniquement.
3. Exporter en PNG/TIFF sans compression destructive.
4. Conserver une version avec et sans labels.
5. Archiver paramètres d'export (magnification, taille, format).

## À copier-coller
```text
Paramètres recommandés:
- format: PNG ou TIFF
- largeur: >= 2000 px
- barre d'échelle: visible
- pas de zoom numérique post-export
```

## Vérifier que ça marche
- La figure est lisible à la taille finale.
- Le format exporté correspond aux exigences.
- La version finale est archivée sans perte.

## En cas de problème
- Exporter une version intermédiaire et vérifier la lisibilité.
- Comparer avec les consignes officielles du journal.

## Documentation officielle
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)
- [Nature figure guide](https://www.nature.com/nature/for-authors/formatting-guide)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Publication : export haute résolution]({{ site.baseurl }}{% post_url 2026-02-19-publication-export-haute-resolution %})
- [Publication : légendes cohérentes et utiles]({{ site.baseurl }}{% post_url 2026-02-19-publication-legendes-coherentes %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
