---
title: "QuPath : organiser les classes d'objets"
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

# QuPath : organiser les classes d'objets

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé et lancé une première fois.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Définir une arborescence de classes avant la détection (`Cell`, `Tumor`, `Immune`, etc.).
2. Associer une couleur fixe par classe (éviter les changements en cours de projet).
3. Éviter les classes redondantes (`Tumeur` et `Tumor`).
4. Valider les classes sur 3 lames avant lot complet.
5. Versionner la nomenclature dans un fichier `classes.md`.

## À copier-coller
```groovy
def classes = ['Tumor', 'Stroma', 'Immune', 'Artefact']
classes.each { name ->
    def pc = getPathClass(name)
    println "Classe OK: " + pc
}
```

## Vérifier que ça marche
- La manipulation se lance sans erreur dans QuPath.
- Le résultat attendu est visible sur l'image test.
- Le projet se sauvegarde correctement.

## En cas de problème
- Redémarrer QuPath puis relancer sur une image plus petite.
- Vérifier la version QuPath et l'extension installée.

## Documentation officielle
- [PathClass dans QuPath](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)
- [Bonnes pratiques de classification](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
