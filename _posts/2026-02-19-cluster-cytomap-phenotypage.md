---
title: "CytoMAP : phénotypage cellulaire de base"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cluster
tags:
  - CytoMAP
  - Phénotypage
  - Cell
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# CytoMAP : phénotypage cellulaire de base

## Portée précise
- Référence article: `cluster-cytomap-phenotypage`
- Périmètre: le clustering et l'analyse spatiale de populations.
- Axe technique dominant: **cytomap** (focus complémentaire: cluster, phenotypage).
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
{% include video id="_ytJbpCA_cA" provider="youtube" %}

![Illustration - CytoMAP : phénotypage cellulaire de base](https://commons.wikimedia.org/wiki/Special:FilePath/Red%20Fluorescence%20Microscopy.jpg)

## Sources
- Vidéo: [CIF Tutorial QuPath Installation](https://www.youtube.com/watch?v=_ytJbpCA_cA)
- Image: [Wikimedia Commons - Red Fluorescence Microscopy](https://commons.wikimedia.org/wiki/File:Red_Fluorescence_Microscopy.jpg)
- Documentation technique: [Wiki CytoMAP](https://gitlab.com/gernerlab/cytomap/-/wikis/home)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [CytoMAP : définir les neighborhoods]({% post_url 2026-02-19-cluster-cytomap-neighborhoods %})
- [CytoMAP : clustering des régions tissulaires]({% post_url 2026-02-19-cluster-cytomap-region-clustering %})
- [CytoMAP : workflow complet de A à Z]({% post_url 2026-02-19-cluster-cytomap-workflow-complet %})
