---
title: "Python : exporter des ROI en images publication"
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

# Python : exporter des ROI en images publication

## Étapes
1. Lire la ROI (polygone) depuis un GeoJSON.
2. Extraire la bounding box dans la lame WSI.
3. Appliquer un masque polygone pour ne garder que la ROI.
4. Exporter en PNG/TIFF haute qualité.
5. Conserver nommage incluant ID ROI.

## Exemple
```python
import json
import openslide
import numpy as np
from PIL import Image, ImageDraw

slide = openslide.OpenSlide('sample.svs')
with open('roi.geojson', 'r', encoding='utf-8') as f:
    poly = json.load(f)['features'][0]['geometry']['coordinates'][0]

xs = [p[0] for p in poly]; ys = [p[1] for p in poly]
minx, miny, maxx, maxy = map(int, (min(xs), min(ys), max(xs), max(ys)))
img = slide.read_region((minx, miny), 0, (maxx-minx, maxy-miny)).convert('RGB')
mask = Image.new('L', img.size, 0)
pts = [(x-minx, y-miny) for x, y in poly]
ImageDraw.Draw(mask).polygon(pts, fill=255)
out = Image.new('RGB', img.size)
out.paste(img, mask=mask)
out.save('roi_export.png')
```

## Documentation
- [OpenSlide Python API](https://openslide.org/api/python/)
- [Pillow ImageDraw](https://pillow.readthedocs.io/en/stable/reference/ImageDraw.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
