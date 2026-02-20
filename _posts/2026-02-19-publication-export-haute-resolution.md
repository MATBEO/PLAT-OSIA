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

## Étapes
1. Exporter l'image source en résolution maximale utile.
2. Préférer TIFF/PNG pour éviter les artefacts JPEG.
3. Utiliser 300 dpi (print) ou plus si demandé par journal.
4. Vérifier taille fichier et lisibilité des détails.
5. Conserver une copie non retouchée.

## Exemple
```bash
# Vérifier dimensions d'une image exportée (ImageMagick)
identify figure_export.tif
# Exemple conversion sans perte
magick figure_export.tif -compress none figure_export_uncompressed.tif
```

## Documentation
- [ImageMagick identify](https://imagemagick.org/script/identify.php)
- [Nature formatting guide](https://www.nature.com/nature/for-authors/formatting-guide)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Publication : figure QuPath nette et lisible]({{ site.baseurl }}{% post_url 2026-02-19-publication-figure-qupath %})
- [Publication : légendes cohérentes et utiles]({{ site.baseurl }}{% post_url 2026-02-19-publication-legendes-coherentes %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
