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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath 0.7 installé et lancé une première fois.
- Au 3 mars 2026, la version officielle vérifiée est `v0.7.0-rc1`.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Créer un dossier projet avec sous-dossiers `raw/`, `project/`, `exports/`, `logs/`.
2. Dans QuPath: `File > Project > Create project...` puis sélectionner `project/`.
3. Définir une convention de nommage unique (`cohorte_patient_lame`).
4. Sauvegarder une liste de classes standard avant toute annotation.
5. Tester l'export CSV et GeoJSON sur une image pilote.
6. Garder à côté du projet les scripts Groovy utiles, car QuPath 0.7 ne réutilise plus les anciens workflows enregistrés.

## À copier-coller
```text
raw/
project/
exports/
logs/
README_pipeline.md
```

## Vérifier que ça marche
- La manipulation se lance sans erreur dans QuPath.
- Le résultat attendu est visible sur l'image test.
- Le projet se sauvegarde correctement.

## En cas de problème
- Redémarrer QuPath puis relancer sur une image plus petite.
- Vérifier la version QuPath et l'extension installée.

## Documentation officielle
- [QuPath `v0.7.0-rc1`](https://github.com/qupath/qupath/releases/tag/v0.7.0-rc1)
- [QuPath Projects](https://qupath.readthedocs.io/en/latest/docs/starting/projects.html)
- [QuPath Data Export](https://qupath.readthedocs.io/en/latest/docs/advanced/exporting_results.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [QuPath : fondamentaux des annotations]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
