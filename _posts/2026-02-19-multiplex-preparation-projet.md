---
title: "Multiplex : préparer un projet QuPath propre"
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

# Multiplex : préparer un projet QuPath propre

## Étapes
1. Créer un projet QuPath dédié au multiplex (pas mélanger avec H&E).
2. Lister tous les marqueurs avec canal, clone et seuil attendu.
3. Ajouter des contrôles positifs/négatifs dans le lot.
4. Harmoniser le nommage des images et des canaux.
5. Geler le plan d'analyse avant segmentation.

## Exemple
```text
Table minimale à préparer:
- Marker
- Canal
- Contrôle positif
- Contrôle négatif
- Seuil initial
```

## Documentation
- [QuPath fluorescence](https://qupath.readthedocs.io/en/latest/docs/intro/images.html)
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Multiplex : segmentation cellulaire adaptée]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-segmentation-cellulaire %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
