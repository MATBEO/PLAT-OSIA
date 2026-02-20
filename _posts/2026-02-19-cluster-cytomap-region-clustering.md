---
title: "CytoMAP : clustering des régions tissulaires"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cluster
tags:
  - Cluster
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# CytoMAP : clustering des régions tissulaires

## Portée précise
- Référence article: `cluster-cytomap-region-clustering`
- Périmètre: le clustering et l'analyse spatiale de populations.
- Axe technique dominant: **cytomap** (focus complémentaire: cluster, region, clustering).
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
{% include video id="rQdVhCI3FbU" provider="youtube" %}

![Illustration - CytoMAP : clustering des régions tissulaires](https://commons.wikimedia.org/wiki/Special:FilePath/Fluorescence.microscope3.jpg)

## Sources
- Vidéo: [StarDist Cell Segmentation in QuPath](https://www.youtube.com/watch?v=rQdVhCI3FbU)
- Image: [Wikimedia Commons - Fluorescence microscope 3](https://commons.wikimedia.org/wiki/File:Fluorescence.microscope3.jpg)
- Documentation technique: [Wiki CytoMAP](https://gitlab.com/gernerlab/cytomap/-/wikis/home)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [CytoMAP : phénotypage cellulaire de base]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-phenotypage %})
- [CytoMAP : définir les neighborhoods]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-neighborhoods %})
- [CytoMAP : workflow complet de A à Z]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-workflow-complet %})
