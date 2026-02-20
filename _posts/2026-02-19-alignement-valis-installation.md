---
title: "VALIS : installation pas à pas"
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

# VALIS : installation pas à pas

## Étapes
1. Créer un environnement virtuel propre dédié à VALIS.
2. Tester l'alignement sur un petit sous-ensemble de lames.
3. Contrôler les superpositions sur zones anatomiques stables.
4. Exécuter le lot complet avec logs conservés.
5. Archiver paramètres et version VALIS utilisée.

## Exemple
```python
# Exemple VALIS (adapter chemins et options)
from valis import registration

registrar = registration.Valis(
    src_dir="/path/to/src_slides",
    dst_dir="/path/to/output"
)
registrar.register()
registrar.warp_and_save_slides()
```

## Documentation
- Documentation technique: [Documentation VALIS](https://valis.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
