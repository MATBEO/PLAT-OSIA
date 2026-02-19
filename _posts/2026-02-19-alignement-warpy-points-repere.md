---
title: "Warpy : placer des points de repère robustes"
date: 2026-02-19T00:00:00-01:00
categories:
  - Alignement
tags:
  - Warpy
  - Alignement
  - Repères
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Warpy : placer des points de repère robustes

## Portée précise
- Référence article: `alignement-warpy-points-repere`
- Périmètre: le recalage interlames et la projection d'annotations.
- Axe technique dominant: **warpy** (focus complémentaire: alignement, points, repere).
- Stack cible: QuPath + extension Warpy.
- Entrées attendues: lame de référence + lame(s) à projeter.
- Sorties attendues: matrice de transformation + annotations projetées.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- points de repère sur structures stables.
- répartition homogène des points sur la lame.
- vérification locale sur zones critiques.
- version des plugins conservée.

## Procédure opératoire
1. Choisir une lame pivot (référence) par série.
2. Poser des repères distribués (centre + périphérie).
3. Calculer la transformation et inspecter les zones denses.
4. Projeter les annotations uniquement après QC local.
5. Exporter les annotations projetées en GeoJSON.

## Snippet prêt à adapter
```groovy
// Contrôle avant projection
println "Reference image: " + getCurrentImageName()
println "N annotations: " + getAnnotationObjects().size()
```

## Validation rapide
- KPI: erreur visuelle faible sur points anatomiques.
- KPI: continuité des contours projetés.
- KPI: cohérence des surfaces d'annotations.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: repères concentrés sur une seule zone. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: projection sans validation de bord. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence de versionnage des transformations. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="rQdVhCI3FbU" provider="youtube" %}

![Illustration - Warpy : placer des points de repère robustes](https://commons.wikimedia.org/wiki/Special:FilePath/Cell-universe.jpg)

## Sources
- Vidéo: [StarDist Cell Segmentation in QuPath](https://www.youtube.com/watch?v=rQdVhCI3FbU)
- Image: [Wikimedia Commons - Cell-universe](https://commons.wikimedia.org/wiki/File:Cell-universe.jpg)
- Documentation technique: [Documentation Warpy](https://github.com/BIOP/qupath-extension-warpy)
