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

## Étapes
1. Choisir un rayon de neighborhood cohérent avec la biologie tissulaire.
2. Tester 2-3 rayons (ex: 30, 50, 75 µm).
3. Comparer la stabilité des regroupements par rayon.
4. Retenir le rayon qui maximise interprétabilité + robustesse.
5. Documenter le rayon retenu et son rational.

## Exemple
```text
Règle pratique:
- Trop petit: bruit élevé
- Trop grand: perte d'information locale
- Commencer à 50 µm puis ajuster
```

## Documentation
- [CytoMAP wiki](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
- [Spatial analysis overview](https://www.nature.com/articles/s41592-021-01322-9)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
