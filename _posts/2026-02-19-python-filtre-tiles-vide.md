---
title: "Python : filtrer les tuiles sans tissu"
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

# Python : filtrer les tuiles sans tissu

## Étapes
1. Charger chaque tuile en niveaux de gris.
2. Calculer un masque tissu par seuillage Otsu.
3. Mesurer le pourcentage de tissu.
4. Supprimer les tuiles sous le seuil (ex: <10%).
5. Garder un log des tuiles rejetées.

## Exemple
```python
import cv2
import numpy as np
from pathlib import Path

for fp in Path('tiles').glob('*.jpg'):
    img = cv2.imread(str(fp), cv2.IMREAD_GRAYSCALE)
    _, mask = cv2.threshold(img, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
    tissue_ratio = float((mask > 0).mean())
    if tissue_ratio < 0.10:
        fp.unlink()
```

## Documentation
- [OpenCV thresholding](https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html)
- [NumPy docs](https://numpy.org/doc/stable/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
