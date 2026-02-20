---
title: "Warpy : installation et test rapide"
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

# Warpy : installation et test rapide

## Étapes
1. Choisir une lame pivot (référence) par série.
2. Poser des repères distribués (centre + périphérie).
3. Calculer la transformation et inspecter les zones denses.
4. Projeter les annotations uniquement après QC local.
5. Exporter les annotations projetées en GeoJSON.

## Exemple
```groovy
// Contrôle avant projection
println "Reference image: " + getCurrentImageName()
println "N annotations: " + getAnnotationObjects().size()
```

## Documentation
- Documentation technique: [Documentation Warpy](https://github.com/BIOP/qupath-extension-warpy)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [VALIS : installation pas à pas]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-installation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
