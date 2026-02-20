---
title: "CytoMAP : définir les neighborhoods"
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

# CytoMAP : définir les neighborhoods

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Un CSV cellules propre (X, Y, phénotype).
- CytoMAP installé.
- Un échantillon test pour valider le workflow.

## Pas à pas
1. Choisir un rayon de neighborhood cohérent avec la biologie tissulaire.
2. Tester 2-3 rayons (ex: 30, 50, 75 µm).
3. Comparer la stabilité des regroupements par rayon.
4. Retenir le rayon qui maximise interprétabilité + robustesse.
5. Documenter le rayon retenu et son rational.

## À copier-coller
```text
Règle pratique:
- Trop petit: bruit élevé
- Trop grand: perte d'information locale
- Commencer à 50 µm puis ajuster
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
- [Spatial analysis overview](https://www.nature.com/articles/s41592-021-01322-9)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
