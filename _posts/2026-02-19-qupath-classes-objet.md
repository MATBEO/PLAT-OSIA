---
title: "Organiser les classes d'objets dans QuPath"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Sommaire"
layout: single
---

Les classes permettent de distinguer les annotations et les détections. Une nomenclature courte et stable évite les erreurs lors des exports et des analyses groupées.

## Définir une nomenclature avant l'analyse

Écrivez la liste dans le `README.md` du projet avant d'annoter. Exemple pour une lame H&E:

```text
Tumor
Stroma
Immune
Necrosis
Artefact
```

Choisissez une seule langue et une seule orthographe. `Tumor`, `Tumeur` et `tumor` sont trois classes différentes pour QuPath et pour un tableur.

## Appliquer les classes

1. Sélectionnez un ou plusieurs objets dans la liste des objets ou dans la visionneuse.
2. Dans le panneau **Classifications**, choisissez la classe voulue ou créez-la.
3. Attribuez une couleur fixe, facile à distinguer sur vos lames.
4. Vérifiez que la même classe est appliquée aux mêmes objets sur une deuxième lame.

Utilisez une classe `Artefact` pour exclure explicitement une zone. Ne supprimez pas un artefact si son exclusion doit être traçable.

## Créer les classes par script

Le script suivant initialise les classes de la nomenclature. Il ne modifie aucun objet existant.

```groovy
['Tumor', 'Stroma', 'Immune', 'Necrosis', 'Artefact'].each { name ->
    println "Classe disponible: ${getPathClass(name)}"
}
```

## Contrôle avant export

Dans la liste des objets, filtrez chaque classe une fois. Aucun objet sans classe ne doit rester si cette classe est nécessaire à votre analyse. Exportez ensuite les mesures ou le GeoJSON avec les classes visibles dans la table.

## Continuer

- [Créer des annotations utiles]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Exporter les mesures en CSV]({{ site.baseurl }}{% post_url 2026-02-19-qupath-mesures-export-csv %})
- [Documentation QuPath: classification](https://qupath.readthedocs.io/en/latest/docs/starting/classification.html)
