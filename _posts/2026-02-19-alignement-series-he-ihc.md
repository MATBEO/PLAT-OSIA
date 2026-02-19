---
title: "Alignement de séries H&E et IHC"
date: 2026-02-19T00:00:00-01:00
categories:
  - Alignement
tags:
  - IHC
  - H&E
  - Alignement
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Alignement de séries H&E et IHC

## Portée précise
- Référence article: `alignement-series-he-ihc`
- Périmètre: le recalage interlames et la projection d'annotations.
- Axe technique dominant: **alignement** (focus complémentaire: series, he, ihc).
- Stack cible: pipeline de recalage interlames.
- Entrées attendues: lame référence + lames cible.
- Sorties attendues: transformation + projections validées.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- référence anatomique stable.
- repères distribués spatialement.
- contrôle local centre+bords.
- export des transformations.

## Procédure opératoire
1. Choisir une lame pivot robuste comme référence.
2. Définir les repères et calculer la transformation.
3. Mesurer l'erreur visuelle sur zones critiques.
4. Projeter les annotations après validation.
5. Archiver transformation et outputs.

## Snippet prêt à adapter
```text
Points de contrôle recommandés
- 2 points centre
- 4 points périphérie
- 2 points zones riches en structures
```

## Validation rapide
- KPI: erreur de recalage faible.
- KPI: cohérence des contours projetés.
- KPI: stabilité entre lames consécutives.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: repères insuffisants ou mal répartis. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: référence instable. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: projection sans revue locale. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="rQdVhCI3FbU" provider="youtube" %}

![Illustration - Alignement de séries H&E et IHC](https://commons.wikimedia.org/wiki/Special:FilePath/Tissue_MicroArray_Slide.jpg)

## Sources
- Vidéo: [StarDist Cell Segmentation in QuPath](https://www.youtube.com/watch?v=rQdVhCI3FbU)
- Image: [Wikimedia Commons - Tissue MicroArray Slide](https://commons.wikimedia.org/wiki/File:Tissue_MicroArray_Slide.jpg)
- Documentation technique: [Image registration concepts](https://scikit-image.org/docs/stable/auto_examples/registration/plot_register_translation.html)
