---
title: "CytoMAP : workflow complet de A à Z"
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

# CytoMAP : workflow complet de A à Z

## Étapes
1. Exporter les cellules depuis QuPath (coordonnées + phénotypes).
2. Nettoyer le CSV puis importer dans CytoMAP.
3. Définir neighborhoods et lancer clustering spatial.
4. Interpréter les régions et comparer entre échantillons.
5. Exporter figures + tables pour rapport final.

## Exemple
```text
Pipeline minimal:
QuPath export -> CSV QC -> CytoMAP import -> Neighborhoods -> Region clustering -> Export résultats
```

## Documentation
- [CytoMAP wiki](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
- [QuPath export docs](https://qupath.readthedocs.io/en/latest/docs/advanced/exporting_results.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
