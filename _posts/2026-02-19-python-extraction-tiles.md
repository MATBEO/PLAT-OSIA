---
title: "Python : extraction de tuiles depuis WSI"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Python
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Python : extraction de tuiles depuis WSI

## Étapes
1. Définir niveau pyramidale, taille de tuile et stride.
2. Ignorer les tuiles hors tissu ou trop blanches.
3. Sauvegarder les tuiles avec coordonnées dans le nom.
4. Conserver un CSV index des tuiles exportées.
5. Vérifier un échantillon visuel de tuiles.

## Exemple
```python
import openslide
from pathlib import Path

slide = openslide.OpenSlide('sample.svs')
out = Path('tiles'); out.mkdir(exist_ok=True)
size, stride = 512, 512
W, H = slide.level_dimensions[0]
for y in range(0, H - size + 1, stride):
    for x in range(0, W - size + 1, stride):
        tile = slide.read_region((x, y), 0, (size, size)).convert('RGB')
        tile.save(out / f'tile_x{x}_y{y}.jpg', quality=90)
```

## Documentation
- [OpenSlide Python API](https://openslide.org/api/python/)
- [Pillow docs](https://pillow.readthedocs.io/en/stable/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : filtrer les tuiles sans tissu]({{ site.baseurl }}{% post_url 2026-02-19-python-filtre-tiles-vide %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
