---
title: "Multiplex : construire des phénotypes cellulaires"
date: 2026-02-19T00:00:00-01:00
categories:
  - Multiplex
tags:
  - Multiplex
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Multiplex : construire des phénotypes cellulaires

## Portée précise
- Référence article: `multiplex-phenotypes-cellulaires`
- Périmètre: l'analyse multi-canaux et le phénotypage.
- Axe technique dominant: **multiplex** (focus complémentaire: phenotypes, cellulaires).
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
- Cible qualité recommandée: Taux d'échec de run < 5% sur lot homogène.

## Erreurs fréquentes et correctifs
- Risque: seuils fixés sans QC visuel. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: noms de canaux non standardisés. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence de validation inter-opérateur. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="4wPUtUtSp-o" provider="youtube" %}

![Illustration - Multiplex : construire des phénotypes cellulaires](https://commons.wikimedia.org/wiki/Special:FilePath/Tissue_MicroArray_Slide.jpg)

## Sources
- Vidéo: [Install NVIDIA CUDA Toolkit on Windows](https://www.youtube.com/watch?v=4wPUtUtSp-o)
- Image: [Wikimedia Commons - Tissue MicroArray Slide](https://commons.wikimedia.org/wiki/File:Tissue_MicroArray_Slide.jpg)
- Documentation technique: [Documentation QuPath (Multiplex)](https://qupath.readthedocs.io/en/latest/)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
- [Multiplex : segmentation cellulaire adaptée]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-segmentation-cellulaire %})
- [Multiplex : définir les seuils de marqueurs]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-seuils-marqueurs %})
- [Multiplex : check-list de contrôle qualité]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-controles-qualite %})
