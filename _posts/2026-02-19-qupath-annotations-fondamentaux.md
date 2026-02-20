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
- QuPath installé et lancé une première fois.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Créer des annotations uniquement sur des zones nettes et représentatives.
2. Nommer les annotations avec une classe explicite (`Tumor`, `Stroma`, `Artefact`).
3. Ne jamais mélanger classes biologiques et classes techniques.
4. Sauvegarder le projet après chaque lot d'annotations.
5. Exporter un GeoJSON de contrôle pour audit inter-opérateur.

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
- [QuPath Annotations](https://qupath.readthedocs.io/en/latest/docs/starting/annotating.html)
- [QuPath Classification](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
