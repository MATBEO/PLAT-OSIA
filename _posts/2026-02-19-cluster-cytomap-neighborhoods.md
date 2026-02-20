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
1. Vérifier le schéma CSV avant import.
2. Importer un échantillon pilote et valider types de colonnes.
3. Lancer un clustering initial puis ajuster les paramètres.
4. Construire les neighborhoods et comparer entre échantillons.
5. Exporter les figures et tableaux de synthèse.

## Exemple
```text
CSV minimal recommandé
CellID,X,Y,Z,Sample,MarkerA,MarkerB,MarkerC
c001,102.4,88.1,0,sample_01,0.72,0.05,0.33
c002,110.7,92.6,0,sample_01,0.61,0.12,0.41
```

## Documentation
- Documentation technique: [Wiki CytoMAP](https://gitlab.com/gernerlab/cytomap/-/wikis/home)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
