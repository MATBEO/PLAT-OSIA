---
title: "Multiplex : check-list de contrôle qualité"
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

# Multiplex : check-list de contrôle qualité

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Images multiplex avec canaux identifiés.
- Liste des marqueurs et contrôles disponible.
- Projet QuPath dédié au multiplex.

## Pas à pas
1. Vérifier la qualité image par canal (saturation, bruit, fond).
2. Contrôler la segmentation sur au moins 5 ROI par lame.
3. Comparer les taux de positivité aux contrôles biologiques.
4. Tracer les distributions de signal par marqueur.
5. Bloquer l'analyse si dérive majeure détectée.

## À copier-coller
```python
import pandas as pd

df = pd.read_csv('cells_multiplex.csv')
for marker in ['CD3_mean', 'CD8_mean', 'PDL1_mean']:
    print(marker, df[marker].describe()[['mean', 'std', 'min', 'max']].to_dict())
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
- [Quality control principles](https://www.iso.org/standard/62085.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
