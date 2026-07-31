---
title: "Créer des annotations utiles dans QuPath"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Sommaire"
layout: single
---

Une annotation est une zone dessinée manuellement qui délimite ce que vous voulez mesurer ou analyser. Elle n'est pas une détection: les détections sont les objets créés par un algorithme à l'intérieur de cette zone.

## Dessiner une zone d'analyse

1. Ouvrez une lame dont l'échelle a été contrôlée.
2. Dans la barre d'outils, choisissez **Rectangle**, **Polygon** ou **Brush**.
3. Entourez uniquement du tissu représentatif. Excluez plis, bulles, bords de lame et zones floues.
4. Dans la liste des objets, renommez ou classez l'annotation immédiatement.
5. Enregistrez le projet avant de lancer une détection.

Pour un premier réglage, créez trois annotations distinctes: une zone dense, une zone peu dense et une zone difficile. Elles servent à vérifier qu'un réglage fonctionne sur la variabilité réelle de la lame.

## Donner une classe à une annotation

Utilisez des classes biologiques simples, par exemple `Tumor`, `Stroma`, `Necrosis` et `Artefact`. Ne mélangez pas l'information biologique et une note technique dans une même classe: écrivez `Tumor` et non `Tumor_a_verifier`.

Pour lister les annotations et leurs classes dans le script editor:

```groovy
def annotations = getAnnotationObjects()
println "Nombre d'annotations: ${annotations.size()}"
annotations.each { annotation ->
    println "${annotation.getName()} : ${annotation.getPathClass()}"
}
```

## Exporter une copie de contrôle

Après une session d'annotation, utilisez **File > Export objects as GeoJSON...** et choisissez **All objects**. Gardez ce fichier dans `exports/` avec le même identifiant que la lame. Il peut être relu hors de QuPath et protège le travail manuel en plus du fichier projet.

## Continuer

- [Organiser les classes d'objets]({{ site.baseurl }}{% post_url 2026-02-19-qupath-classes-objet %})
- [Segmenter des cellules avec InstanSeg]({{ site.baseurl }}{% post_url 2025-01-01-InstaSeg %})
- [Documentation QuPath: annotations](https://qupath.readthedocs.io/en/latest/docs/starting/annotating.html)
