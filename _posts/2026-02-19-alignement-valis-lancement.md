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

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Deux lames du même tissu (référence + cible).
- Outil d'alignement installé (Warpy ou VALIS).
- Un dossier de sortie dédié pour les transformations.

## Pas à pas
1. Placer les lames source dans un dossier unique.
2. Définir un dossier de sortie vide pour les résultats.
3. Lancer le script VALIS avec paramètres par défaut d'abord.
4. Vérifier visuellement les overlays générés.
5. Relancer avec réglages fins si nécessaire.

## À copier-coller
```python
from valis import registration

registrar = registration.Valis(
    src_dir='slides_in',
    dst_dir='valis_out'
)
registrar.register()
registrar.warp_and_save_slides()
```

## Vérifier que ça marche
- Les repères anatomiques se superposent correctement.
- Le décalage global est faible sur 3 zones de contrôle.
- Les sorties d'alignement sont bien générées.

## En cas de problème
- Vérifier que les lames ont des résolutions compatibles.
- Refaire le test sur une zone anatomique simple.

## Documentation officielle
- [VALIS quick start](https://valis.readthedocs.io/en/latest/)
- [OpenSlide Python](https://openslide.org/api/python/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
