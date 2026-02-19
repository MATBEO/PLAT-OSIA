---
title: "Multiplex : cartographie spatiale des populations"
date: 2026-02-19T00:00:00-01:00
categories:
  - Multiplex
tags:
  - Multiplex
  - Spatial
  - Carte
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Multiplex : cartographie spatiale des populations

## Portée précise
- Référence article: `multiplex-cartographie-spatiale`
- Périmètre: l'analyse multi-canaux et le phénotypage.
- Axe technique dominant: **multiplex** (focus complémentaire: cartographie, spatiale).
- Stack cible: QuPath (Multiplex IF) + pipeline de phénotypage.
- Entrées attendues: image multi-canaux + table marqueurs.
- Sorties attendues: phénotypes cellulaires + carte spatiale.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- nommage canaux stable (ex: DAPI, CD3, CD8, ...).
- seuils validés sur ROI représentatives.
- compensation/bleed-through vérifiée.
- export par échantillon et par population.

## Procédure opératoire
1. Contrôler l'alignement et l'intensité de chaque canal.
2. Segmenter les cellules avec un preset versionné.
3. Définir les règles de phénotypes (gates).
4. Appliquer la classification et vérifier les cas limites.
5. Exporter populations et cartes de distribution.

## Snippet prêt à adapter
```text
Exemple de règle de phénotype
T_CD8 = DAPI+ AND CD3+ AND CD8+ AND NOT CD20+
```

## Validation rapide
- KPI: cohérence des phénotypes sur champs voisins.
- KPI: stabilité des seuils entre lames.
- KPI: faible taux d'objets non classés.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: seuils fixés sans QC visuel. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: noms de canaux non standardisés. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence de validation inter-opérateur. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="75J9nxhviV8" provider="youtube" %}

![Illustration - Multiplex : cartographie spatiale des populations](https://commons.wikimedia.org/wiki/Special:FilePath/Green%20Fluorescence%20Microscopy.jpg)

## Sources
- Vidéo: [How to Install QuPath](https://www.youtube.com/watch?v=75J9nxhviV8)
- Image: [Wikimedia Commons - Green Fluorescence Microscopy](https://commons.wikimedia.org/wiki/File:Green_Fluorescence_Microscopy.jpg)
- Documentation technique: [Documentation QuPath (Multiplex)](https://qupath.readthedocs.io/en/latest/)
