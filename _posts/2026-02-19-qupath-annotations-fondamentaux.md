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
1. Créer/ouvrir le projet avec arborescence standard.
2. Importer les images puis vérifier calibration.
3. Appliquer la procédure cible (détection/classification/export).
4. Effectuer une revue QC sur zones sentinelles.
5. Exporter et documenter les paramètres utilisés.

## Exemple
```groovy
// Vérification de contexte projet QuPath
println "Project: " + (getProject() == null ? 'none' : getProject().toString())
println "Image: " + getCurrentImageName()
println "Annotations: " + getAnnotationObjects().size()
```

## Documentation
- Documentation technique: [Documentation QuPath](https://qupath.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
