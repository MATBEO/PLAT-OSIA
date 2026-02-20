---
title: "QuPath : créer un projet standard reproductible"
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

# QuPath : créer un projet standard reproductible

## Étapes
1. Créer un dossier projet avec sous-dossiers `raw/`, `project/`, `exports/`, `logs/`.
2. Dans QuPath: `File > Project > Create project...` puis sélectionner `project/`.
3. Définir une convention de nommage unique (`cohorte_patient_lame`).
4. Sauvegarder une liste de classes standard avant toute annotation.
5. Tester l'export CSV et GeoJSON sur une image pilote.

## Exemple
```text
raw/
project/
exports/
logs/
README_pipeline.md
```

## Documentation
- [QuPath Projects](https://qupath.readthedocs.io/en/latest/docs/starting/projects.html)
- [QuPath Data Export](https://qupath.readthedocs.io/en/latest/docs/advanced/exporting_results.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [QuPath : fondamentaux des annotations]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
