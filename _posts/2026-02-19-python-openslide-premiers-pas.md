---
title: "Python + OpenSlide : premiers pas"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Python
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Python + OpenSlide : premiers pas

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Python 3.10+ et environnement virtuel.
- Dépendances installées pour le script de l'article.
- Un dossier entrée/sortie clairement séparé.

## Pas à pas
1. Installer la librairie système OpenSlide.
2. Créer un environnement Python dédié.
3. Installer `openslide-python`, `numpy`, `pillow`.
4. Ouvrir une lame et lire ses métadonnées.
5. Extraire une petite région test pour valider.

## À copier-coller
```bash
# Ubuntu
sudo apt install -y openslide-tools libopenslide0
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install openslide-python numpy pillow
```

## Vérifier que ça marche
- Le script s'exécute sans exception.
- Les fichiers de sortie sont bien créés.
- Le résultat est cohérent sur un petit lot test.

## En cas de problème
- Relancer dans un environnement virtuel propre.
- Vérifier chemins d'entrée/sortie et permissions.

## Documentation officielle
- [OpenSlide Python API](https://openslide.org/api/python/)
- [OpenSlide project](https://openslide.org/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Python : filtrer les tuiles sans tissu]({{ site.baseurl }}{% post_url 2026-02-19-python-filtre-tiles-vide %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
