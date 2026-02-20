---
title: "Python : lire et écrire un GeoJSON"
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

# Python : lire et écrire un GeoJSON

## Étapes
1. Charger le GeoJSON et vérifier la structure `FeatureCollection`.
2. Valider que chaque feature contient une géométrie.
3. Modifier ou filtrer les features nécessaires.
4. Écrire un nouveau fichier GeoJSON UTF-8.
5. Contrôler l'ouverture dans QuPath/QGIS.

## Exemple
```python
import json

with open('input.geojson', 'r', encoding='utf-8') as f:
    gj = json.load(f)

assert gj['type'] == 'FeatureCollection'
features = [ft for ft in gj['features'] if ft.get('geometry')]

with open('output.geojson', 'w', encoding='utf-8') as f:
    json.dump({'type': 'FeatureCollection', 'features': features}, f, ensure_ascii=False)
```

## Documentation
- [RFC GeoJSON](https://datatracker.ietf.org/doc/html/rfc7946)
- [Python json module](https://docs.python.org/3/library/json.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
