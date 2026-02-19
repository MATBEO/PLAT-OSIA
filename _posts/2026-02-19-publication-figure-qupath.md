---
title: "Publication : figure QuPath nette et lisible"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Publication
  - QuPath
  - Figure
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Publication : figure QuPath nette et lisible

## Portée précise
- Référence article: `publication-figure-qupath`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **qupath** (focus complémentaire: publication, figure).
- Stack cible: QuPath (GUI + scripting optionnel).
- Entrées attendues: projet, images, classes, ROI.
- Sorties attendues: pipeline d'analyse documenté.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- version QuPath fixée pour l'équipe.
- convention de classes partagée.
- structure projet standardisée.
- exports dans dossier dédié par lot.

## Procédure opératoire
1. Créer/ouvrir le projet avec arborescence standard.
2. Importer les images puis vérifier calibration.
3. Appliquer la procédure cible (détection/classification/export).
4. Effectuer une revue QC sur zones sentinelles.
5. Exporter et documenter les paramètres utilisés.

## Snippet prêt à adapter
```groovy
// Vérification de contexte projet QuPath
println "Project: " + (getProject() == null ? 'none' : getProject().toString())
println "Image: " + getCurrentImageName()
println "Annotations: " + getAnnotationObjects().size()
```

## Validation rapide
- KPI: projet rejouable par un second opérateur.
- KPI: cohérence des classes entre images.
- KPI: sorties exportées sans ambiguïté.
- Cible qualité recommandée: Sorties traçables et rejouables sur un second poste.

## Erreurs fréquentes et correctifs
- Risque: workflow implicite non documenté. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: calibration oubliée avant mesures. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: classes renommées en cours de lot. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="75J9nxhviV8" provider="youtube" %}

![Illustration - Publication : figure QuPath nette et lisible](https://commons.wikimedia.org/wiki/Special:FilePath/Tissue_Microarray_12X10.JPG)

## Sources
- Vidéo: [How to Install QuPath](https://www.youtube.com/watch?v=75J9nxhviV8)
- Image: [Wikimedia Commons - Tissue Microarray 12X10](https://commons.wikimedia.org/wiki/File:Tissue_Microarray_12X10.JPG)
- Documentation technique: [Documentation QuPath](https://qupath.readthedocs.io/en/latest/)
