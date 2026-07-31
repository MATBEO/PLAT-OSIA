---
title: "Importer une lame entière dans QuPath"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Sommaire"
layout: single
---

N'analysez pas une lame avant d'avoir vérifié son échelle. Une taille de pixel erronée fausse les distances, les surfaces et les réglages de segmentation.

## Importer la lame

1. Créez d'abord un [projet QuPath]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %}).
2. Dans la fenêtre du projet, choisissez **Project > Add images...**.
3. Sélectionnez les lames dans le dossier `lames/`; ne les copiez pas dans le dossier interne de QuPath.
4. Choisissez le lecteur proposé pour le format. Si QuPath demande une confirmation, vérifiez le nom et les dimensions de la lame avant de valider.
5. Ouvrez une lame, puis enregistrez le projet.

Les formats courants comprennent `.svs`, `.ndpi`, `.mrxs` et les TIFF pyramidaux. La [liste des formats de QuPath](https://qupath.readthedocs.io/en/latest/docs/intro/formats.html) précise les lecteurs disponibles.

## Contrôler la calibration

Dans la visionneuse, ouvrez **Image > Properties** et relevez la taille de pixel. Elle doit correspondre à la fiche du scanner. Une valeur réaliste en histologie est souvent exprimée en micrometres par pixel, par exemple `0.25 um/px` ou `0.50 um/px`.

Ce script affiche les métadonnées lues par QuPath:

```groovy
def metadata = getCurrentServer().getMetadata()
def calibration = metadata.getPixelCalibration()

println "Dimensions: ${metadata.getWidth()} x ${metadata.getHeight()} px"
println "Taille de pixel: ${calibration.getAveragedPixelSizeMicrons()} um/px"
println "Grossissement: ${metadata.getMagnification()}"
```

Si la taille de pixel est `NaN`, absente ou manifestement fausse, arrêtez-vous. Corrigez les métadonnées à partir de la documentation du scanner, puis documentez la valeur appliquée dans le `README.md` du projet.

## Vérifier visuellement

Zoomez dans une zone de tissu, une zone vide et un coin de la lame. Les couleurs doivent être normales, l'orientation correcte et le tissu net. Faites cette vérification sur une lame par scanner avant de lancer une analyse en série.

## Continuer

- [Créer des annotations utiles]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
- [Exporter les mesures en CSV]({{ site.baseurl }}{% post_url 2026-02-19-qupath-mesures-export-csv %})
