---
title: "QC : détecter les erreurs de segmentation"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cell
tags:
  - Qualite
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QC : détecter les erreurs de segmentation

## Étapes
1. Exporter les mesures d'objets segmentés.
2. Détecter les outliers de taille et circularité.
3. Revenir sur image pour confirmer les erreurs.
4. Ajuster paramètres et relancer uniquement les lames touchées.
5. Comparer avant/après avec métriques.

## Exemple
```python
import pandas as pd

df = pd.read_csv('detections.csv')
a = df['Cell: Area']
lo, hi = a.quantile([0.01, 0.99])
outliers = df[(a < lo) | (a > hi)]
print('outliers:', len(outliers), '/', len(df))
```

## Documentation
- [QuPath tutorials](https://qupath.readthedocs.io/en/latest/docs/tutorials/index.html)
- [Pandas quantile](https://pandas.pydata.org/docs/reference/api/pandas.Series.quantile.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QC : check-list avant lancement d'analyse]({{ site.baseurl }}{% post_url 2026-02-19-qc-checklist-avant-analyse %})
- [QC : qualité d'image à l'entrée du pipeline]({{ site.baseurl }}{% post_url 2026-02-19-qc-qualite-image-entree %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
