---
title: "Groovy : convertir détection vers annotation"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Groovy
  - QuPath
  - Objets
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Groovy : convertir détection vers annotation

## Portée précise
- Référence article: `groovy-detection-vers-annotation`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **groovy** (focus complémentaire: detection, vers, annotation).
- Stack cible: QuPath Groovy scripting.
- Entrées attendues: projet QuPath + annotations/détections.
- Sorties attendues: objets modifiés + exports.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- script testé sur une image avant lot.
- sauvegarde projet avant opérations destructives.
- logs explicites (comptes d'objets).
- dossier export versionné.

## Procédure opératoire
1. Ouvrir une image de test et exécuter le script en mode dry-run.
2. Comparer nombre d'objets avant/après.
3. Corriger la logique de filtrage si nécessaire.
4. Déployer sur le projet complet.
5. Exporter les résultats et conserver le script utilisé.

## Snippet prêt à adapter
```groovy
// Exemple QuPath: export GeoJSON des annotations courantes
def anns = getAnnotationObjects()
def outDir = buildFilePath(PROJECT_BASE_DIR, 'exports_geojson')
mkdirs(outDir)
def outFile = buildFilePath(outDir, getCurrentImageName() + '.geojson')
exportObjectsToGeoJson(anns, outFile, 'FEATURE_COLLECTION')
println "Exported: ${outFile}"
```

## Validation rapide
- KPI: écart attendu du nombre d'objets.
- KPI: temps de run par image.
- KPI: absence d'erreur Groovy en batch.
- Cible qualité recommandée: Taux d'échec de run < 5% sur lot homogène.

## Erreurs fréquentes et correctifs
- Risque: suppression d'objets sans sauvegarde. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: script appliqué à la mauvaise hiérarchie. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence de trace des paramètres. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="rQdVhCI3FbU" provider="youtube" %}

![Illustration - Groovy : convertir détection vers annotation](https://commons.wikimedia.org/wiki/Special:FilePath/Green%20Fluorescence%20Microscopy.jpg)

## Sources
- Vidéo: [StarDist Cell Segmentation in QuPath](https://www.youtube.com/watch?v=rQdVhCI3FbU)
- Image: [Wikimedia Commons - Green Fluorescence Microscopy](https://commons.wikimedia.org/wiki/File:Green_Fluorescence_Microscopy.jpg)
- Documentation technique: [Scripting QuPath](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)
