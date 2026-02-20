---
title: "Performance : choisir CPU/GPU selon la tâche"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Performance
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Performance : choisir CPU/GPU selon la tâche

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Machine compatible avec la procédure.
- Droits administrateur si installation système.
- Un cas test pour valider avant production.

## Pas à pas
1. Mesurer temps CPU et GPU sur la même image test.
2. Comparer qualité des résultats (pas seulement vitesse).
3. Conserver le mode le plus stable sur la cohorte.
4. Documenter matériel exact (GPU, VRAM, driver).
5. Fixer un mode par pipeline pour reproductibilité.

## À copier-coller
```text
Décision pratique:
- CPU: plus lent mais souvent plus stable
- GPU: plus rapide sur lot volumineux
- Choisir GPU si gain > 2x et résultats identiques
```

## Vérifier que ça marche
- Les commandes de contrôle répondent correctement.
- Le gain (ou la stabilité) est mesuré sur cas test.
- Les versions logicielles sont tracées.

## En cas de problème
- Vérifier compatibilité driver/toolkit.
- Tester les commandes de diagnostic système.

## Documentation officielle
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)
- [CUDA docs](https://docs.nvidia.com/cuda/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Performance : installer CUDA proprement]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %})
- [Performance : vérifier CUDA côté système]({{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-verification %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
