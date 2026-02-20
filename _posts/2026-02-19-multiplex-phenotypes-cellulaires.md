---
title: "Multiplex : construire des phénotypes cellulaires"
date: 2026-02-19T00:00:00-01:00
categories:
  - Multiplex
tags:
  - Multiplex
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Multiplex : construire des phénotypes cellulaires

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Images multiplex avec canaux identifiés.
- Liste des marqueurs et contrôles disponible.
- Projet QuPath dédié au multiplex.

## Pas à pas
1. Définir des règles explicites de phénotypes (logique booléenne).
2. Appliquer les règles de manière identique à tout le lot.
3. Mesurer la proportion des classes rares.
4. Revoir les classes incohérentes avec un expert.
5. Exporter la table finale par cellule.

## À copier-coller
```python
import pandas as pd

df = pd.read_csv('cells_multiplex.csv')
df['phenotype'] = 'Other'
df.loc[(df['CD3_mean']>200) & (df['CD8_mean']>180), 'phenotype'] = 'T_CD8'
df.loc[(df['CD3_mean']>200) & (df['CD4_mean']>180), 'phenotype'] = 'T_CD4'
print(df['phenotype'].value_counts())
```

## Vérifier que ça marche
- Les canaux sont correctement nommés.
- Les seuils/phénotypes produisent des classes cohérentes.
- Les exports sont complets pour le lot test.

## En cas de problème
- Vérifier l'ordre des canaux et les seuils de base.
- Contrôler une lame témoin avant lot complet.

## Documentation officielle
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)
- [Pandas guide](https://pandas.pydata.org/docs/user_guide/index.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
