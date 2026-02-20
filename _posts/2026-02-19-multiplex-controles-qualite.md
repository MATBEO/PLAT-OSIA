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

## Étapes
1. Contrôler l'alignement et l'intensité de chaque canal.
2. Segmenter les cellules avec un preset versionné.
3. Définir les règles de phénotypes (gates).
4. Appliquer la classification et vérifier les cas limites.
5. Exporter populations et cartes de distribution.

## Exemple
```text
Exemple de règle de phénotype
T_CD8 = DAPI+ AND CD3+ AND CD8+ AND NOT CD20+
```

## Documentation
- Documentation technique: [Documentation QuPath (Multiplex)](https://qupath.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
