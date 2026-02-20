---
title: "VALIS : lancer un alignement en script Python"
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

# VALIS : lancer un alignement en script Python

## Étapes
1. Placer les lames source dans un dossier unique.
2. Définir un dossier de sortie vide pour les résultats.
3. Lancer le script VALIS avec paramètres par défaut d'abord.
4. Vérifier visuellement les overlays générés.
5. Relancer avec réglages fins si nécessaire.

## Exemple
```python
from valis import registration

registrar = registration.Valis(
    src_dir='slides_in',
    dst_dir='valis_out'
)
registrar.register()
registrar.warp_and_save_slides()
```

## Documentation
- [VALIS quick start](https://valis.readthedocs.io/en/latest/)
- [OpenSlide Python](https://openslide.org/api/python/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
