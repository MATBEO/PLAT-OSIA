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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath 0.7 installé et lancé une première fois.
- Au 3 mars 2026, la version officielle vérifiée est `v0.7.0-rc1`.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Ouvrir l'image dans le projet puis dessiner les ROI avec les outils d'annotation (`Rectangle`, `Polygon`, `Brush`).
2. Créer des annotations uniquement sur des zones nettes et représentatives.
3. Attribuer une classe claire à chaque annotation (`Tumor`, `Stroma`, `Artefact`).
4. Ne jamais mélanger classes biologiques et classes techniques.
5. Sauvegarder le projet après chaque lot puis exporter un GeoJSON de contrôle via `File > Export objects as GeoJSON...`.

## À copier-coller
```groovy
def ann = getAnnotationObjects()
println "Annotations totales: " + ann.size()
println "Classes: " + ann.collect{it.getPathClass()}.unique()
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
- [QuPath Annotations](https://qupath.readthedocs.io/en/latest/docs/starting/annotating.html)
- [QuPath Classification](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
