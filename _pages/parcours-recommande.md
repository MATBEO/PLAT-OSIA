---
permalink: /parcours-recommande/
title: "Parcours recommandé"
layout: single
toc: true
toc_label: "Étapes"
toc_sticky: true
---

Ce parcours est organisé du plus fondamental au plus avancé.  
L'idée est de suivre les modules dans l'ordre pour construire un pipeline complet, reproductible et publication-ready.

Ressources externes centralisées : [Médias utiles]({{ site.baseurl }}/medias-utiles/)

## 1. Démarrage et environnement

1. [Performance : installer CUDA proprement]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %})
2. [Performance : vérifier CUDA côté système]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-verification %})
3. [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})

## 2. Fondamentaux QuPath

1. [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
2. [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
3. [QuPath : fondamentaux des annotations]({{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %})
4. [QuPath : organiser les classes d'objets]({{ site.baseurl }}{% post_url 2026-02-19-qupath-classes-objet %})
5. [QuPath : exporter les mesures au format CSV]({{ site.baseurl }}{% post_url 2026-02-19-qupath-mesures-export-csv %})

## 3. Segmentation cellulaire (InstanSeg / StarDist)

1. [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
2. [InstanSeg : paramètres clés à connaître]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-parametres-cles %})
3. [InstanSeg : segmentation sur zones annotées]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-zone-annotation %})
4. [InstanSeg : comparaison CPU, GPU et MPS]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-gpu-cpu-mps %})
5. [StarDist : installer l'extension dans QuPath]({{ site.baseurl }}{% post_url 2026-02-19-stardist-install-extension %})
6. [StarDist : utiliser un modèle H&E pré-entraîné]({{ site.baseurl }}{% post_url 2026-02-19-stardist-modele-he %})
7. [StarDist vs InstanSeg : quand utiliser quoi]({{ site.baseurl }}{% post_url 2026-02-19-stardist-vs-instanseg %})
8. [InstanSeg : contrôle qualité des segmentations]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-qc-segmentation %})

## 4. Alignement interlames (Warpy / VALIS)

1. [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
2. [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
3. [VALIS : installation pas à pas]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-installation %})
4. [VALIS : lancer un alignement en script Python]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-lancement %})
5. [Warpy vs VALIS : comparatif pratique]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-vs-valis %})
6. [Alignement : gérer l'échelle et la résolution]({{ site.baseurl }}{% post_url 2026-02-19-alignement-gestion-echelle %})
7. [Alignement de séries H&E et IHC]({{ site.baseurl }}{% post_url 2026-02-19-alignement-series-he-ihc %})

## 5. Clustering spatial (CytoMAP)

1. [CytoMAP : installation et démarrage]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-installation %})
2. [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
3. [CytoMAP : phénotypage cellulaire de base]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-phenotypage %})
4. [CytoMAP : définir les neighborhoods]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-neighborhoods %})
5. [CytoMAP : clustering des régions tissulaires]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-region-clustering %})
6. [CytoMAP : workflow complet de A à Z]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-workflow-complet %})

## 6. Multiplex

1. [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
2. [Multiplex : importer et nommer les canaux]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-import-canaux %})
3. [Multiplex : segmentation cellulaire adaptée]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-segmentation-cellulaire %})
4. [Multiplex : définir les seuils de marqueurs]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-seuils-marqueurs %})
5. [Multiplex : construire des phénotypes cellulaires]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-phenotypes-cellulaires %})
6. [Multiplex : check-list de contrôle qualité]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-controles-qualite %})

## 7. Scripts Python utiles

1. [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
2. [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
3. [Python : filtrer les tuiles sans tissu]({{ site.baseurl }}{% post_url 2026-02-19-python-filtre-tiles-vide %})
4. [Python : lire et écrire un GeoJSON]({{ site.baseurl }}{% post_url 2026-02-19-python-geojson-lire-ecrire %})
5. [Python : réparer des géométries GeoJSON invalides]({{ site.baseurl }}{% post_url 2026-02-19-python-geojson-reparer %})
6. [Python : exporter des ROI en images publication]({{ site.baseurl }}{% post_url 2026-02-19-python-roi-export-image %})

## 8. Classification de patterns

1. [Classification objet dans QuPath : bonnes pratiques]({{ site.baseurl }}{% post_url 2026-02-19-pattern-classification-objet %})
2. [Évaluer un modèle de classification dans QuPath]({{ site.baseurl }}{% post_url 2026-02-19-pattern-evaluer-modele %})
3. [Construire un workflow reproductible de pattern]({{ site.baseurl }}{% post_url 2026-02-19-pattern-workflow-reproductible %})

## 9. Qualité, performance, publication

1. [QC : check-list avant lancement d'analyse]({{ site.baseurl }}{% post_url 2026-02-19-qc-checklist-avant-analyse %})
2. [QC : qualité d'image à l'entrée du pipeline]({{ site.baseurl }}{% post_url 2026-02-19-qc-qualite-image-entree %})
3. [QC : détecter les erreurs de segmentation]({{ site.baseurl }}{% post_url 2026-02-19-qc-detection-erreurs-segmentation %})
4. [Performance : choisir CPU/GPU selon la tâche]({{ site.baseurl }}{% post_url 2026-02-19-perf-qupath-gpu-choix %})
5. [Performance : benchmark d'un pipeline complet]({{ site.baseurl }}{% post_url 2026-02-19-perf-benchmark-pipeline %})
6. [Publication : figure QuPath nette et lisible]({{ site.baseurl }}{% post_url 2026-02-19-publication-figure-qupath %})
7. [Publication : export haute résolution]({{ site.baseurl }}{% post_url 2026-02-19-publication-export-haute-resolution %})
8. [Publication : légendes cohérentes et utiles]({{ site.baseurl }}{% post_url 2026-02-19-publication-legendes-coherentes %})
9. [Publication : couleurs accessibles et contrastes]({{ site.baseurl }}{% post_url 2026-02-19-publication-couleurs-accessibles %})
