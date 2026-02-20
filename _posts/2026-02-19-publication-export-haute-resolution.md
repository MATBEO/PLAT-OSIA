---
title: "Publication : export haute résolution"
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

# Publication : export haute résolution

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Figure source générée dans QuPath.
- Format cible demandé par le journal.
- Nommage de fichiers standardisé.

## Pas à pas
1. Exporter l'image source en résolution maximale utile.
2. Préférer TIFF/PNG pour éviter les artefacts JPEG.
3. Utiliser 300 dpi (print) ou plus si demandé par journal.
4. Vérifier taille fichier et lisibilité des détails.
5. Conserver une copie non retouchée.

## À copier-coller
```bash
# Vérifier dimensions d'une image exportée (ImageMagick)
identify figure_export.tif
# Exemple conversion sans perte
magick figure_export.tif -compress none figure_export_uncompressed.tif
```

## Vérifier que ça marche
- La figure est lisible à la taille finale.
- Le format exporté correspond aux exigences.
- La version finale est archivée sans perte.

## En cas de problème
- Exporter une version intermédiaire et vérifier la lisibilité.
- Comparer avec les consignes officielles du journal.

## Documentation officielle
- [ImageMagick identify](https://imagemagick.org/script/identify.php)
- [Nature formatting guide](https://www.nature.com/nature/for-authors/formatting-guide)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Publication : figure QuPath nette et lisible]({{ site.baseurl }}{% post_url 2026-02-19-publication-figure-qupath %})
- [Publication : légendes cohérentes et utiles]({{ site.baseurl }}{% post_url 2026-02-19-publication-legendes-coherentes %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
