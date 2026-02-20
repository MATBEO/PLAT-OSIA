---
title: "CytoMAP : importer un CSV cellulaire propre"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cluster
tags:
  - Cluster
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# CytoMAP : importer un CSV cellulaire propre

## Étapes
1. Préparer un CSV avec une ligne par cellule.
2. Inclure au minimum: `CellID`, `X`, `Y`, `Phenotype`.
3. Vérifier les valeurs manquantes avant import.
4. Importer dans CytoMAP via l'assistant d'import.
5. Contrôler le nuage spatial pour valider les coordonnées.

## Exemple
```python
import pandas as pd
req = {'CellID', 'X', 'Y', 'Phenotype'}
df = pd.read_csv('cells.csv')
missing = req - set(df.columns)
print('missing_columns:', missing)
print('na_counts:', df[list(req)].isna().sum().to_dict())
```

## Documentation
- [CytoMAP wiki](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
- [Pandas read_csv](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : phénotypage cellulaire de base]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-phenotypage %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
