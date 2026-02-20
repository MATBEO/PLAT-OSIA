---
title: "QC : qualité d'image à l'entrée du pipeline"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Qualite
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QC : qualité d'image à l'entrée du pipeline

## Étapes
1. Évaluer netteté, saturation et artefacts avant segmentation.
2. Mesurer automatiquement un score de focus.
3. Définir un seuil de rejet objectif.
4. Mettre de côté les lames non conformes.
5. Documenter les exclusions.

## Exemple
```python
import cv2
from pathlib import Path

THRESH_FOCUS = 120.0
for fp in Path('tiles_qc').glob('*.jpg'):
    img = cv2.imread(str(fp), cv2.IMREAD_GRAYSCALE)
    focus = cv2.Laplacian(img, cv2.CV_64F).var()
    if focus < THRESH_FOCUS:
        print('REJECT', fp.name, 'focus=', round(focus, 2))
```

## Documentation
- [OpenCV Laplacian](https://docs.opencv.org/4.x/d5/db5/tutorial_laplace_operator.html)
- [Quality control principles](https://www.iso.org/standard/62085.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QC : check-list avant lancement d'analyse]({{ site.baseurl }}{% post_url 2026-02-19-qc-checklist-avant-analyse %})
- [QC : détecter les erreurs de segmentation]({{ site.baseurl }}{% post_url 2026-02-19-qc-detection-erreurs-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
