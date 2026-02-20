---
title: "Alignement de séries H&E et IHC"
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

# Alignement de séries H&E et IHC

## Étapes
1. Choisir H&E comme référence morphologique.
2. Aligner chaque lame IHC individuellement vers H&E.
3. Vérifier les repères (glandes, vaisseaux, frontières tissulaires).
4. Projeter ensuite les ROI/masques de la référence vers IHC.
5. Valider sur au moins 3 zones critiques par lame.

## Exemple
```text
Ordre conseillé:
1) QC image
2) Alignement H&E vs IHC
3) Projection ROI
4) Segmentation/mesure
```

## Documentation
- [VALIS documentation](https://valis.readthedocs.io/en/latest/)
- [Warpy extension](https://github.com/BIOP/qupath-extension-warpy)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
