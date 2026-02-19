---
title: "Performance : choisir CPU/GPU selon la tâche"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Performance
  - QuPath
  - GPU
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Performance : choisir CPU/GPU selon la tâche

## Portée précise
- Référence article: `perf-qupath-gpu-choix`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **gpu** (focus complémentaire: perf, qupath, choix).
- Stack cible: runtime GPU + outil d'inférence.
- Entrées attendues: workload de test reproductible.
- Sorties attendues: comparatif CPU/GPU.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- jeu de test fixe.
- paramètres identiques CPU et GPU.
- monitoring VRAM actif.
- 3 runs minimum pour moyenne robuste.

## Procédure opératoire
1. Mesurer un baseline CPU sur échantillon fixe.
2. Activer GPU et relancer à paramètres constants.
3. Comparer temps, mémoire et qualité de sortie.
4. Ajuster batch/tile size si saturation mémoire.
5. Conserver le tableau comparatif final.

## Snippet prêt à adapter
```bash
# Mesure rapide
/usr/bin/time -l python run_pipeline.py --device cpu
/usr/bin/time -l python run_pipeline.py --device gpu
nvidia-smi --query-gpu=utilization.gpu,memory.used --format=csv
```

## Validation rapide
- KPI: speedup GPU/CPU.
- KPI: taux d'erreur identique ou meilleur.
- KPI: stabilité de la consommation mémoire.
- Cible qualité recommandée: Taux d'échec de run < 5% sur lot homogène.

## Erreurs fréquentes et correctifs
- Risque: comparer des runs avec paramètres différents. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: VRAM saturée non détectée. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: ne pas contrôler la qualité de sortie. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="75J9nxhviV8" provider="youtube" %}

![Illustration - Performance : choisir CPU/GPU selon la tâche](https://commons.wikimedia.org/wiki/Special:FilePath/Fluorescence.microscope2.jpg)

## Sources
- Vidéo: [How to Install QuPath](https://www.youtube.com/watch?v=75J9nxhviV8)
- Image: [Wikimedia Commons - Fluorescence microscope 2](https://commons.wikimedia.org/wiki/File:Fluorescence.microscope2.jpg)
- Documentation technique: [Documentation NVIDIA SMI](https://developer.nvidia.com/system-management-interface)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : installer CUDA proprement]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %})
- [Performance : vérifier CUDA côté système]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-verification %})
- [Performance : benchmark d'un pipeline complet]({{ site.baseurl }}{% post_url 2026-02-19-perf-benchmark-pipeline %})
- [InstanSeg : comparaison CPU, GPU et MPS]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-gpu-cpu-mps %})
