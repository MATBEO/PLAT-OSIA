---
title: "QuPath : importer des lames entières (WSI) correctement"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
  - WSI
  - Import
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QuPath : importer des lames entières (WSI) correctement

## Portée précise
- Référence article: `qupath-importer-wsi`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **qupath** (focus complémentaire: importer, wsi).
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
- Cible qualité recommandée: Taux d'échec de run < 5% sur lot homogène.

## Erreurs fréquentes et correctifs
- Risque: workflow implicite non documenté. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: calibration oubliée avant mesures. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: classes renommées en cours de lot. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="MBrAVUsUdio" provider="youtube" %}

![Illustration - QuPath : importer des lames entières (WSI) correctement](https://qupath.github.io/assets/images/slideshow/qupath-youtube.png)

## Sources
- Vidéo: [From Zero to QuPath Hero](https://www.youtube.com/watch?v=MBrAVUsUdio)
- Image: [QuPath - tutoriels YouTube](https://qupath.github.io/)
- Documentation technique: [Documentation QuPath](https://qupath.readthedocs.io/en/latest/)
