---
title: "Alignement : gérer l'échelle et la résolution"
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

# Alignement : gérer l'échelle et la résolution

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Deux lames du même tissu (référence + cible).
- Outil d'alignement installé (Warpy ou VALIS).
- Un dossier de sortie dédié pour les transformations.

## Pas à pas
1. Lire le pixel size (µm/px) de chaque lame avant alignement.
2. Calculer le facteur d'échelle entre lame source et cible.
3. Resampler si nécessaire avant recalage.
4. Vérifier qu'une distance connue garde la même valeur après warp.
5. Bloquer la suite si l'écart d'échelle est incohérent.

## À copier-coller
```python
import openslide

ref = openslide.OpenSlide('ref.svs')
mov = openslide.OpenSlide('mov.svs')
ref_mpp = float(ref.properties.get('openslide.mpp-x', '0'))
mov_mpp = float(mov.properties.get('openslide.mpp-x', '0'))
scale = mov_mpp / ref_mpp if ref_mpp else None
print('ref_mpp:', ref_mpp, 'mov_mpp:', mov_mpp, 'scale:', scale)
```

## Vérifier que ça marche
- Les repères anatomiques se superposent correctement.
- Le décalage global est faible sur 3 zones de contrôle.
- Les sorties d'alignement sont bien générées.

## En cas de problème
- Vérifier que les lames ont des résolutions compatibles.
- Refaire le test sur une zone anatomique simple.

## Documentation officielle
- [OpenSlide properties](https://openslide.org/api/python/)
- [Registration example scikit-image](https://scikit-image.org/docs/stable/auto_examples/registration/plot_register_translation.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
