---
title: "StarDist : utiliser un modèle H&E pré-entraîné"
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

# StarDist : utiliser un modèle H&E pré-entraîné

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Charger une lame H&E correctement calibrée.
2. Sélectionner un modèle StarDist entraîné pour H&E.
3. Lancer sur petite ROI pour ajuster les paramètres.
4. Étendre au lot si le résultat visuel est acceptable.
5. Exporter les objets et mesures pour revue.

## À copier-coller
```yaml
model: he_pretrained
probability_threshold: 0.5
nms_threshold: 0.4
pixel_size_um: 0.5
output: nuclei
```

## Vérifier que ça marche
- Des objets sont bien détectés dans la ROI test.
- Pas de sur-segmentation massive en bordure.
- Les mesures exportées sont non vides.

## En cas de problème
- Tester d'abord en CPU puis passer en GPU/MPS.
- Réduire la taille de tuile si erreur mémoire.

## Documentation officielle
- [StarDist extension QuPath](https://github.com/qupath/qupath-extension-stardist)
- [QuPath tutorials](https://qupath.readthedocs.io/en/latest/docs/tutorials/index.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
