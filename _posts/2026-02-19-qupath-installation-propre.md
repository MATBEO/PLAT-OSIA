---
title: "QuPath : installation propre et vérification initiale"
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

# QuPath : installation propre et vérification initiale

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé et lancé une première fois.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Télécharger QuPath depuis la page Release officielle.
2. Installer puis ouvrir QuPath une première fois pour créer le dossier de configuration.
3. Ajuster la mémoire JVM (Preferences > Memory) selon la RAM machine.
4. Activer seulement les extensions nécessaires pour éviter les conflits.
5. Valider l'installation sur une lame test (ouverture + annotation + export).

## À copier-coller
```groovy
println "QuPath version: " + getVersion()
println "Image ouverte: " + getCurrentImageName()
println "Annotations: " + getAnnotationObjects().size()
```

## Vérifier que ça marche
- La manipulation se lance sans erreur dans QuPath.
- Le résultat attendu est visible sur l'image test.
- Le projet se sauvegarde correctement.

## En cas de problème
- Redémarrer QuPath puis relancer sur une image plus petite.
- Vérifier la version QuPath et l'extension installée.

## Documentation officielle
- [QuPath Releases](https://github.com/qupath/qupath/releases)
- [Documentation QuPath](https://qupath.readthedocs.io/en/latest/)
- [QuPath Scripting](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)

## Articles liés
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [QuPath : fondamentaux des annotations]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
