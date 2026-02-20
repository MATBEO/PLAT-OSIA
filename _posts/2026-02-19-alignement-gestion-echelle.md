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

## Étapes
1. Lire le pixel size (µm/px) de chaque lame avant alignement.
2. Calculer le facteur d'échelle entre lame source et cible.
3. Resampler si nécessaire avant recalage.
4. Vérifier qu'une distance connue garde la même valeur après warp.
5. Bloquer la suite si l'écart d'échelle est incohérent.

## Exemple
```python
import openslide

ref = openslide.OpenSlide('ref.svs')
mov = openslide.OpenSlide('mov.svs')
ref_mpp = float(ref.properties.get('openslide.mpp-x', '0'))
mov_mpp = float(mov.properties.get('openslide.mpp-x', '0'))
scale = mov_mpp / ref_mpp if ref_mpp else None
print('ref_mpp:', ref_mpp, 'mov_mpp:', mov_mpp, 'scale:', scale)
```

## Documentation
- [OpenSlide properties](https://openslide.org/api/python/)
- [Registration example scikit-image](https://scikit-image.org/docs/stable/auto_examples/registration/plot_register_translation.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
