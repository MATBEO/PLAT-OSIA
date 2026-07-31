---
title: "Scripts QuPath utiles"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Script
layout: single
toc: true
toc_label: "Sommaire"
classes: wide
---

Ces scripts sont prévus pour QuPath 0.7. Ouvrez **Automate > Show script editor**, collez un script, puis enregistrez-le dans le dossier du projet. Les anciens workflows enregistrés ne sont plus une solution fiable pour rejouer une analyse.

## Exporter toutes les annotations du projet en GeoJSON

Le script crée `exports/annotations/` dans le dossier du projet et produit un fichier GeoJSON par lame. Ouvrez un projet avant de l'exécuter.

```groovy
import qupath.lib.common.GeneralTools

def project = getProject()
assert project != null : 'Ouvrez un projet QuPath avant de lancer ce script.'

def outputDir = buildFilePath(PROJECT_BASE_DIR, 'exports', 'annotations')
new File(outputDir).mkdirs()

for (entry in project.getImageList()) {
    def imageData = entry.readImageData()
    def annotations = imageData.getHierarchy().getAnnotationObjects()
    def name = GeneralTools.getNameWithoutExtension(imageData.getServer().getMetadata().getName())
    def output = buildFilePath(outputDir, name + '.geojson')
    exportObjectsToGeoJson(annotations, output, 'FEATURE_COLLECTION')
    println "Exporté: ${output}"
}
```

## Transformer les détections en annotations

Utilisez ce script seulement si vous voulez éditer manuellement les objets détectés. Il supprime les détections d'origine.

```groovy
import qupath.lib.objects.PathObjects

def detections = getDetectionObjects()
def annotations = detections.collect {
    PathObjects.createAnnotationObject(it.getROI(), it.getPathClass())
}
removeObjects(detections, true)
addObjects(annotations)
fireHierarchyUpdate()
```

## Transformer les annotations en détections

```groovy
import qupath.lib.objects.PathObjects

def annotations = getAnnotationObjects()
def detections = annotations.collect {
    PathObjects.createDetectionObject(it.getROI(), it.getPathClass())
}
addObjects(detections)
fireHierarchyUpdate()
```

## Définir le type d'image et la calibration

Renseignez la taille de pixel réellement fournie par le scanner. Ne copiez pas `0.262100` sans la vérifier dans les métadonnées de votre lame.

```groovy
setImageType('BRIGHTFIELD_H_E')
setColorDeconvolutionStains('{"Name":"H&E default","Stain 1":"Hematoxylin","Values 1":"0.65111 0.70119 0.29049","Stain 2":"Eosin","Values 2":"0.2159 0.8012 0.5581","Background":"255 255 255"}')
setPixelSizeMicrons(0.262100, 0.262100)
```

## Continuer

- [Créer un projet QuPath reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [Exporter des mesures en CSV]({{ site.baseurl }}{% post_url 2026-02-19-qupath-mesures-export-csv %})
- [Exporter un TMA en GeoJSON]({{ site.baseurl }}{% post_url 2025-01-01-exporter_TMA-en-geosjon %})
