---
title: "CytoMAP : phénotypage cellulaire de base"
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

# CytoMAP : phénotypage cellulaire de base

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Un CSV cellules propre (X, Y, phénotype).
- CytoMAP installé.
- Un échantillon test pour valider le workflow.

## Pas à pas
1. Définir des règles de phénotypage basées sur marqueurs et seuils.
2. Appliquer les règles sur un sous-ensemble de contrôle.
3. Comparer avec annotation experte si disponible.
4. Geler les règles avant l'analyse de cohorte complète.
5. Exporter la table finale `CellID -> Phenotype`.

## À copier-coller
```python
import pandas as pd

df = pd.read_csv('cells_markers.csv')
df['Phenotype'] = 'Other'
df.loc[(df['CD3'] > 200) & (df['CD8'] > 180), 'Phenotype'] = 'T_CD8'
df.loc[(df['CD20'] > 220), 'Phenotype'] = 'B_cell'
df.to_csv('cells_phenotyped.csv', index=False)
```

## Vérifier que ça marche
- Le CSV est importé sans erreur.
- Les neighborhoods/clusters sont calculés.
- Les résultats exportés sont exploitables.

## En cas de problème
- Valider les colonnes du CSV avant import.
- Commencer avec un sous-ensemble de cellules.

## Documentation officielle
- [CytoMAP wiki](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
- [Pandas indexing](https://pandas.pydata.org/docs/user_guide/indexing.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
