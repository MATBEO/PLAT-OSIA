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

## Étapes
1. Définir une arborescence de classes avant la détection (`Cell`, `Tumor`, `Immune`, etc.).
2. Associer une couleur fixe par classe (éviter les changements en cours de projet).
3. Éviter les classes redondantes (`Tumeur` et `Tumor`).
4. Valider les classes sur 3 lames avant lot complet.
5. Versionner la nomenclature dans un fichier `classes.md`.

## Exemple
```groovy
def classes = ['Tumor', 'Stroma', 'Immune', 'Artefact']
classes.each { name ->
    def pc = getPathClass(name)
    println "Classe OK: " + pc
}
```

## Documentation
- [PathClass dans QuPath](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)
- [Bonnes pratiques de classification](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
