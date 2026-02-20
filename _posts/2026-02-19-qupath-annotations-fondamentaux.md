---
title: "QuPath : fondamentaux des annotations"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QuPath : fondamentaux des annotations

## Étapes
1. Créer des annotations uniquement sur des zones nettes et représentatives.
2. Nommer les annotations avec une classe explicite (`Tumor`, `Stroma`, `Artefact`).
3. Ne jamais mélanger classes biologiques et classes techniques.
4. Sauvegarder le projet après chaque lot d'annotations.
5. Exporter un GeoJSON de contrôle pour audit inter-opérateur.

## Exemple
```groovy
def ann = getAnnotationObjects()
println "Annotations totales: " + ann.size()
println "Classes: " + ann.collect{it.getPathClass()}.unique()
```

## Documentation
- [QuPath Annotations](https://qupath.readthedocs.io/en/latest/docs/starting/annotating.html)
- [QuPath Classification](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
