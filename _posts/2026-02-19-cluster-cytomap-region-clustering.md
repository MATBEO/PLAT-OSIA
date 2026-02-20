---
title: "CytoMAP : clustering des régions tissulaires"
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

# CytoMAP : clustering des régions tissulaires

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Un CSV cellules propre (X, Y, phénotype).
- CytoMAP installé.
- Un échantillon test pour valider le workflow.

## Pas à pas
1. Construire des vecteurs de composition cellulaire par région.
2. Normaliser les variables avant clustering.
3. Tester plusieurs `k` et comparer la séparation.
4. Vérifier la cohérence biologique de chaque cluster.
5. Exporter l'assignation région -> cluster.

## À copier-coller
```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

X = pd.read_csv('region_features.csv')
Xs = StandardScaler().fit_transform(X)
labels = KMeans(n_clusters=4, random_state=0, n_init='auto').fit_predict(Xs)
print('cluster_counts:', pd.Series(labels).value_counts().to_dict())
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
- [scikit-learn KMeans](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
