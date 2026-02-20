---
title: "Multiplex : définir les seuils de marqueurs"
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

# Multiplex : définir les seuils de marqueurs

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Images multiplex avec canaux identifiés.
- Liste des marqueurs et contrôles disponible.
- Projet QuPath dédié au multiplex.

## Pas à pas
1. Calculer les seuils à partir des contrôles négatifs.
2. Vérifier les distributions de signal par marqueur.
3. Fixer un seuil stable (ex: percentile 99 des négatifs).
4. Ne pas ajuster les seuils lame par lame sans justification.
5. Documenter tous les seuils dans un fichier versionné.

## À copier-coller
```python
import pandas as pd

df = pd.read_csv('controls_negative.csv')
for marker in ['CD3_mean', 'CD8_mean', 'PDL1_mean']:
    thr = df[marker].quantile(0.99)
    print(marker, 'threshold=', round(thr, 2))
```

## Vérifier que ça marche
- Les canaux sont correctement nommés.
- Les seuils/phénotypes produisent des classes cohérentes.
- Les exports sont complets pour le lot test.

## En cas de problème
- Vérifier l'ordre des canaux et les seuils de base.
- Contrôler une lame témoin avant lot complet.

## Documentation officielle
- [Pandas quantile](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.quantile.html)
- [QuPath classification docs](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
