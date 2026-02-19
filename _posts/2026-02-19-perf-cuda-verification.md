---
title: "Performance : vérifier CUDA côté système"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - CUDA
  - Debug
  - Performance
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Performance : vérifier CUDA côté système

## Portée précise
- Référence article: `perf-cuda-verification`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **cuda** (focus complémentaire: perf, verification).
- Stack cible: CUDA Toolkit + pilote NVIDIA.
- Entrées attendues: machine compatible GPU.
- Sorties attendues: environnement GPU fonctionnel.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- version pilote compatible toolkit.
- `PATH` et bibliothèques CUDA visibles.
- test `nvidia-smi` avant et après installation.
- test d'inférence court pour validation.

## Procédure opératoire
1. Installer/mettre à jour le pilote NVIDIA.
2. Installer CUDA Toolkit correspondant.
3. Vérifier la version de `nvcc`.
4. Tester l'utilisation GPU dans l'outil cible.
5. Archiver versions exactes dans le runbook.

## Snippet prêt à adapter
```bash
nvidia-smi
nvcc --version
# Linux/macOS
echo $PATH | tr ':' '
' | grep -i cuda || true
```

## Validation rapide
- KPI: GPU détecté sans erreur.
- KPI: version `nvcc` conforme.
- KPI: gain de temps d'inférence mesurable.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: incompatibilité pilote/toolkit. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: variables d'environnement incomplètes. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: validation faite uniquement sur un test trivial. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="_ytJbpCA_cA" provider="youtube" %}

![Illustration - Performance : vérifier CUDA côté système](https://commons.wikimedia.org/wiki/Special:FilePath/Fluorescence.microscope1.jpg)

## Sources
- Vidéo: [CIF Tutorial QuPath Installation](https://www.youtube.com/watch?v=_ytJbpCA_cA)
- Image: [Wikimedia Commons - Fluorescence microscope 1](https://commons.wikimedia.org/wiki/File:Fluorescence.microscope1.jpg)
- Documentation technique: [Documentation CUDA](https://docs.nvidia.com/cuda/)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : installer CUDA proprement]({% post_url 2026-02-19-perf-cuda-installation %})
- [Performance : choisir CPU/GPU selon la tâche]({% post_url 2026-02-19-perf-qupath-gpu-choix %})
- [Performance : benchmark d'un pipeline complet]({% post_url 2026-02-19-perf-benchmark-pipeline %})
- [InstanSeg : comparaison CPU, GPU et MPS]({% post_url 2026-02-19-instanseg-gpu-cpu-mps %})
