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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Résultats intermédiaires déjà exportés.
- Checklist projet disponible.
- Critères de validation définis en amont.

## Pas à pas
1. Exporter les mesures d'objets segmentés.
2. Détecter les outliers de taille et circularité.
3. Revenir sur image pour confirmer les erreurs.
4. Ajuster paramètres et relancer uniquement les lames touchées.
5. Comparer avant/après avec métriques.

## À copier-coller
```python
import pandas as pd

df = pd.read_csv('detections.csv')
a = df['Cell: Area']
lo, hi = a.quantile([0.01, 0.99])
outliers = df[(a < lo) | (a > hi)]
print('outliers:', len(outliers), '/', len(df))
```

## Vérifier que ça marche
- Chaque point de checklist est renseigné.
- Les anomalies bloquantes sont isolées.
- La décision Go/No-Go est explicite.

## En cas de problème
- Revenir à l'étape précédente avec un lot plus petit.
- Comparer avec un cas validé de référence.

## Documentation officielle
- [QuPath tutorials](https://qupath.readthedocs.io/en/latest/docs/tutorials/index.html)
- [Pandas quantile](https://pandas.pydata.org/docs/reference/api/pandas.Series.quantile.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QC : check-list avant lancement d'analyse]({{ site.baseurl }}{% post_url 2026-02-19-qc-checklist-avant-analyse %})
- [QC : qualité d'image à l'entrée du pipeline]({{ site.baseurl }}{% post_url 2026-02-19-qc-qualite-image-entree %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
