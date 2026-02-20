---
title: "Python : réparer des géométries GeoJSON invalides"
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

# Python : réparer des géométries GeoJSON invalides

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Python 3.10+ et environnement virtuel.
- Dépendances installées pour le script de l'article.
- Un dossier entrée/sortie clairement séparé.

## Pas à pas
1. Installer `shapely` compatible avec ton environnement.
2. Lire chaque géométrie du GeoJSON.
3. Appliquer `make_valid` (ou `buffer(0)` fallback).
4. Rejeter les géométries vides/invalides persistantes.
5. Exporter un GeoJSON nettoyé.

## À copier-coller
```python
import json
from shapely.geometry import shape, mapping
from shapely.validation import make_valid

with open('input.geojson', 'r', encoding='utf-8') as f:
    gj = json.load(f)

fixed = []
for ft in gj['features']:
    geom = shape(ft['geometry'])
    geom = make_valid(geom)
    if not geom.is_valid:
        geom = geom.buffer(0)
    if geom.is_empty:
        continue
    ft['geometry'] = mapping(geom)
    fixed.append(ft)

with open('fixed.geojson', 'w', encoding='utf-8') as f:
    json.dump({'type': 'FeatureCollection', 'features': fixed}, f)
```

## Vérifier que ça marche
- Le script s'exécute sans exception.
- Les fichiers de sortie sont bien créés.
- Le résultat est cohérent sur un petit lot test.

## En cas de problème
- Relancer dans un environnement virtuel propre.
- Vérifier chemins d'entrée/sortie et permissions.

## Documentation officielle
- [Shapely docs](https://shapely.readthedocs.io/en/stable/)
- [RFC GeoJSON](https://datatracker.ietf.org/doc/html/rfc7946)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
