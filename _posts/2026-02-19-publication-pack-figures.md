---
title: "Publication : pack de figures prêt à soumettre"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Publication
  - Workflow
  - Final
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Publication : pack de figures prêt à soumettre

## Portée précise
- Référence article: `publication-pack-figures`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **publication** (focus complémentaire: pack, figures).
- Stack cible: QuPath + outil de mise en page.
- Entrées attendues: figures exportées + légendes.
- Sorties attendues: figures prêtes à soumission.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- résolution cible (300 dpi min).
- palette lisible et accessible.
- barre d'échelle et légende normalisées.
- format final conforme aux consignes journal.

## Procédure opératoire
1. Exporter une version brute haute résolution.
2. Vérifier lisibilité des annotations et textes.
3. Uniformiser couleurs, tailles de police et légendes.
4. Contrôler la figure à 100% et 50% de zoom.
5. Archiver la version finale + source.

## Snippet prêt à adapter
```text
Checklist figure finale
- Résolution >= 300 dpi
- Barre d'échelle visible
- Légende complète (marqueurs, classes, unité)
```

## Validation rapide
- KPI: lisibilité en taille de publication.
- KPI: cohérence visuelle entre figures.
- KPI: conformité aux instructions auteur.
- Cible qualité recommandée: Sorties traçables et rejouables sur un second poste.

## Erreurs fréquentes et correctifs
- Risque: annotations trop fines ou peu contrastées. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: légende incomplète. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: export compressé avec perte excessive. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="4wPUtUtSp-o" provider="youtube" %}

![Illustration - Publication : pack de figures prêt à soumettre](https://commons.wikimedia.org/wiki/Special:FilePath/Green%20Fluorescence%20Microscopy.jpg)

## Sources
- Vidéo: [Install NVIDIA CUDA Toolkit on Windows](https://www.youtube.com/watch?v=4wPUtUtSp-o)
- Image: [Wikimedia Commons - Green Fluorescence Microscopy](https://commons.wikimedia.org/wiki/File:Green_Fluorescence_Microscopy.jpg)
- Documentation technique: [Guide publication figures (Nature)](https://www.nature.com/nature/for-authors/formatting-guide)
