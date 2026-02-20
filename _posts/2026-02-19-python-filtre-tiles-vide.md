---
title: "Python : filtrer les tuiles sans tissu"
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

# Python : filtrer les tuiles sans tissu

## Étapes
1. Créer l'environnement et installer les dépendances.
2. Valider les formats de fichiers d'entrée.
3. Exécuter un run pilote et inspecter les sorties.
4. Lancer le lot complet avec journal d'exécution.
5. Vérifier les métriques finales et archiver.

## Exemple
```python
from pathlib import Path

inp = Path('/path/to/input')
out = Path('/path/to/output')
out.mkdir(parents=True, exist_ok=True)

for fp in sorted(inp.glob('*')):
    # TODO: adapter le traitement
    print(f"processing: {fp.name}")
```

## Documentation
- Documentation technique: [Documentation OpenSlide Python](https://openslide.org/api/python/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
