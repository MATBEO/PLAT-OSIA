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
1. Créer un environnement Python dédié à VALIS.
2. Installer `valis-wsi` et dépendances scientifiques.
3. Vérifier import Python sans erreur.
4. Tester un run minimal sur 2 lames.
5. Sauvegarder `requirements.txt` du projet.

## Exemple
```bash
python -m venv .venv-valis
source .venv-valis/bin/activate
python -m pip install --upgrade pip
python -m pip install valis-wsi openslide-python
python -c "from valis import registration; print('VALIS OK')"
```

## Documentation
- [VALIS documentation](https://valis.readthedocs.io/en/latest/)
- [VALIS package](https://pypi.org/project/valis-wsi/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
