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
1. Choisir une lame pivot robuste comme référence.
2. Définir les repères et calculer la transformation.
3. Mesurer l'erreur visuelle sur zones critiques.
4. Projeter les annotations après validation.
5. Archiver transformation et outputs.

## Exemple
```text
Points de contrôle recommandés
- 2 points centre
- 4 points périphérie
- 2 points zones riches en structures
```

## Documentation
- Documentation technique: [Image registration concepts](https://scikit-image.org/docs/stable/auto_examples/registration/plot_register_translation.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
