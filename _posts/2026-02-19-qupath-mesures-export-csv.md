---
title: "Exporter les mesures QuPath en CSV"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Export
toc: true
toc_label: "Sommaire"
layout: single
---

Exportez les mesures seulement après avoir validé les détections sur une zone test. Un CSV propre contient les identifiants de lame, les classes et uniquement les mesures dont vous connaissez l'unité.

## Préparer la table

1. Ouvrez la lame et vérifiez la segmentation à fort grossissement.
2. Ouvrez **Measure > Show detection measurements**.
3. Contrôlez les colonnes essentielles: `Class`, aire, coordonnées et intensité éventuelle.
4. Vérifiez dix lignes prises au hasard: une ligne doit correspondre à une cellule visible dans la lame.
5. Exportez la table depuis la fenêtre de mesures, ou utilisez le script ci-dessous pour une sortie toujours au même emplacement.

Une surface n'a de sens que si la taille de pixel a été contrôlée lors de [l'import de la lame]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %}).

## Exporter les détections de la lame courante

Le script crée `exports/` dans le dossier du projet et y écrit un CSV pour la lame ouverte. Il refuse de s'exécuter si aucun projet n'est ouvert.

```groovy
import qupath.lib.common.GeneralTools

assert getProject() != null : 'Ouvrez un projet QuPath avant de lancer ce script.'

def name = GeneralTools.getNameWithoutExtension(getCurrentServer().getMetadata().getName())
def outputDir = buildFilePath(PROJECT_BASE_DIR, 'exports')
new File(outputDir).mkdirs()
def output = buildFilePath(outputDir, name + '_detections.csv')

saveDetectionMeasurements(output)
println "Mesures exportées: ${output}"
```

## Vérifier le fichier avant analyse statistique

Ouvrez le CSV dans un tableur ou un script R/Python. Vérifiez que le séparateur est correctement interprété, que les nombres ne sont pas devenus du texte et que la colonne `Class` contient les classes attendues. Conservez le CSV brut, puis réalisez les filtres et les regroupements dans un fichier séparé.

## Continuer

- [Organiser les classes d'objets]({{ site.baseurl }}{% post_url 2026-02-19-qupath-classes-objet %})
- [Scripts QuPath utiles]({{ site.baseurl }}{% post_url 2025-01-01-Liste-Script_Qupath %})
- [Documentation QuPath: exporter des résultats](https://qupath.readthedocs.io/en/latest/docs/advanced/exporting_results.html)
