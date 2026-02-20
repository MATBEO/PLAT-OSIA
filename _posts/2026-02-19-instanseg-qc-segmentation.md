---
title: "InstanSeg : contrôle qualité des segmentations"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cell
tags:
  - Segmentation
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# InstanSeg : contrôle qualité des segmentations

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Vérifier les faux positifs sur zones sans tissu.
2. Vérifier les faux négatifs dans les zones cellulaires denses.
3. Contrôler la taille moyenne des objets détectés.
4. Refaire un run si >10% des objets sont manifestement erronés.
5. Sauvegarder captures QC avant validation finale.

## À copier-coller
```python
import pandas as pd

df = pd.read_csv('detections.csv')
print('n_objects:', len(df))
print('area_q01_q99:', df['Cell: Area'].quantile([0.01, 0.99]).to_dict())
```

## Vérifier que ça marche
- Des objets sont bien détectés dans la ROI test.
- Pas de sur-segmentation massive en bordure.
- Les mesures exportées sont non vides.

## En cas de problème
- Tester d'abord en CPU puis passer en GPU/MPS.
- Réduire la taille de tuile si erreur mémoire.

## Documentation officielle
- [QuPath tutorials](https://qupath.readthedocs.io/en/latest/docs/tutorials/index.html)
- [InstanSeg extension](https://github.com/qupath/qupath-extension-instanseg)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
