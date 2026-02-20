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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Deux lames du même tissu (référence + cible).
- Outil d'alignement installé (Warpy ou VALIS).
- Un dossier de sortie dédié pour les transformations.

## Pas à pas
1. Choisir H&E comme référence morphologique.
2. Aligner chaque lame IHC individuellement vers H&E.
3. Vérifier les repères (glandes, vaisseaux, frontières tissulaires).
4. Projeter ensuite les ROI/masques de la référence vers IHC.
5. Valider sur au moins 3 zones critiques par lame.

## À copier-coller
```text
Ordre conseillé:
1) QC image
2) Alignement H&E vs IHC
3) Projection ROI
4) Segmentation/mesure
```

## Vérifier que ça marche
- Les repères anatomiques se superposent correctement.
- Le décalage global est faible sur 3 zones de contrôle.
- Les sorties d'alignement sont bien générées.

## En cas de problème
- Vérifier que les lames ont des résolutions compatibles.
- Refaire le test sur une zone anatomique simple.

## Documentation officielle
- [VALIS documentation](https://valis.readthedocs.io/en/latest/)
- [Warpy extension](https://github.com/BIOP/qupath-extension-warpy)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
