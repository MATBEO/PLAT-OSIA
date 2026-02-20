---
title: "Publication : couleurs accessibles et contrastes"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Publication
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Publication : couleurs accessibles et contrastes

## Étapes
1. Choisir une palette compatible daltonisme.
2. Éviter rouge/vert sans différenciation de luminance.
3. Vérifier contraste texte/fond >= 4.5.
4. Tester la figure en niveaux de gris.
5. Conserver la même palette sur tout le manuscrit.

## Exemple
```python
# Contraste WCAG simple

def rel_lum(rgb):
    def f(c):
        c = c/255
        return c/12.92 if c <= 0.03928 else ((c+0.055)/1.055)**2.4
    r,g,b = [f(v) for v in rgb]
    return 0.2126*r + 0.7152*g + 0.0722*b

def contrast(a, b):
    l1, l2 = sorted([rel_lum(a), rel_lum(b)], reverse=True)
    return (l1 + 0.05) / (l2 + 0.05)

print('contrast ratio:', round(contrast((0,0,0), (255,255,255)), 2))
```

## Documentation
- [WCAG contrast](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
- [Nature formatting guide](https://www.nature.com/nature/for-authors/formatting-guide)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Publication : figure QuPath nette et lisible]({{ site.baseurl }}{% post_url 2026-02-19-publication-figure-qupath %})
- [Publication : export haute résolution]({{ site.baseurl }}{% post_url 2026-02-19-publication-export-haute-resolution %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
