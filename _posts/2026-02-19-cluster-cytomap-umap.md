---
title: "CytoMAP : projection UMAP et interprétation"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cluster
tags:
  - CytoMAP
  - UMAP
  - Visualisation
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# CytoMAP : projection UMAP et interprétation

## Portée précise
- Référence article: `cluster-cytomap-umap`
- Périmètre: le clustering et l'analyse spatiale de populations.
- Axe technique dominant: **cytomap** (focus complémentaire: cluster, umap).
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
- Cible qualité recommandée: Taux d'échec de run < 5% sur lot homogène.

## Erreurs fréquentes et correctifs
- Risque: colonnes mal typées (texte au lieu de numérique). Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: comparaison de lots sans normalisation. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: interprétation sans contrôle de stabilité. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="75J9nxhviV8" provider="youtube" %}

![Illustration - CytoMAP : projection UMAP et interprétation](https://commons.wikimedia.org/wiki/Special:FilePath/Fluorescence.microscope1.jpg)

## Sources
- Vidéo: [How to Install QuPath](https://www.youtube.com/watch?v=75J9nxhviV8)
- Image: [Wikimedia Commons - Fluorescence microscope 1](https://commons.wikimedia.org/wiki/File:Fluorescence.microscope1.jpg)
- Documentation technique: [Wiki CytoMAP](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
