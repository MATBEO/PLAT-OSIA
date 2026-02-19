---
title: "CytoMAP : workflow complet de A à Z"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cluster
tags:
  - CytoMAP
  - Workflow
  - Spatial
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# CytoMAP : workflow complet de A à Z

## Portée précise
- Référence article: `cluster-cytomap-workflow-complet`
- Périmètre: le clustering et l'analyse spatiale de populations.
- Axe technique dominant: **cytomap** (focus complémentaire: cluster, workflow, complet).
- Stack cible: CytoMAP + table cellulaire CSV.
- Entrées attendues: CSV cellule (x,y,z + marqueurs).
- Sorties attendues: clusters, neighborhoods, figures.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- colonnes coordonnées explicites: `X`, `Y`, `Z`.
- normalisation cohérente des marqueurs.
- nombre de clusters testé sur plage restreinte.
- graine aléatoire fixée quand possible.

## Procédure opératoire
1. Vérifier le schéma CSV avant import.
2. Importer un échantillon pilote et valider types de colonnes.
3. Lancer un clustering initial puis ajuster les paramètres.
4. Construire les neighborhoods et comparer entre échantillons.
5. Exporter les figures et tableaux de synthèse.

## Snippet prêt à adapter
```text
CSV minimal recommandé
CellID,X,Y,Z,Sample,MarkerA,MarkerB,MarkerC
c001,102.4,88.1,0,sample_01,0.72,0.05,0.33
c002,110.7,92.6,0,sample_01,0.61,0.12,0.41
```

## Validation rapide
- KPI: clusters biologiquement interprétables.
- KPI: stabilité inter-run.
- KPI: faible proportion de cellules non assignées.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: colonnes mal typées (texte au lieu de numérique). Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: comparaison de lots sans normalisation. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: interprétation sans contrôle de stabilité. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="_ytJbpCA_cA" provider="youtube" %}

![Illustration - CytoMAP : workflow complet de A à Z](https://qupath.github.io/assets/images/slideshow/qupath-getting-started.png)

## Sources
- Vidéo: [CIF Tutorial QuPath Installation](https://www.youtube.com/watch?v=_ytJbpCA_cA)
- Image: [QuPath - getting started](https://qupath.github.io/)
- Documentation technique: [Wiki CytoMAP](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
