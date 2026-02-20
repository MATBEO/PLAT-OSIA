---
title: "Warpy : projeter des annotations interlames"
date: 2026-02-19T00:00:00-01:00
categories:
  - Alignement
tags:
  - Alignement
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Warpy : projeter des annotations interlames

## Étapes
1. Définir une lame de référence et une lame cible.
2. Calculer l'alignement interlames dans Warpy.
3. Projeter les annotations de la référence vers la cible.
4. Contrôler la projection sur des repères anatomiques fixes.
5. Corriger manuellement les ROI problématiques.

## Exemple
```text
Checklist projection:
- mêmes zones anatomiques couvertes
- pas de décalage systématique en bordure
- ROI projetées exploitables pour segmentation
```

## Documentation
- [Warpy extension](https://github.com/BIOP/qupath-extension-warpy)
- [Image registration concepts (scikit-image)](https://scikit-image.org/docs/stable/auto_examples/registration/plot_register_translation.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [VALIS : installation pas à pas]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-installation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
