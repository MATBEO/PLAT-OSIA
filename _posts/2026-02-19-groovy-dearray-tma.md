---
title: "Groovy : transformer un TMA en annotations"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Groovy
  - TMA
  - QuPath
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Groovy : transformer un TMA en annotations

## Portée précise
- Référence article: `groovy-dearray-tma`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **groovy** (focus complémentaire: dearray, tma).
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
{% include video id="J-47tzXAFdE" provider="youtube" %}

![Illustration - Groovy : transformer un TMA en annotations](https://commons.wikimedia.org/wiki/Special:FilePath/Red%20Fluorescence%20Microscopy.jpg)

## Sources
- Vidéo: [QuPath Tutorial Introduction](https://www.youtube.com/watch?v=J-47tzXAFdE)
- Image: [Wikimedia Commons - Red Fluorescence Microscopy](https://commons.wikimedia.org/wiki/File:Red_Fluorescence_Microscopy.jpg)
- Documentation technique: [Scripting QuPath](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)
