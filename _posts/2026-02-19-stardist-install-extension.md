---
title: "StarDist : installer l'extension dans QuPath"
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

# StarDist : installer l'extension dans QuPath

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath installé.
- Extension InstanSeg ou StarDist installée selon l'article.
- Une ROI test pour valider rapidement le résultat.

## Pas à pas
1. Installer l'extension StarDist compatible QuPath.
2. Vérifier qu'un moteur deep learning est disponible (CPU/GPU).
3. Redémarrer QuPath après installation.
4. Tester l'extension sur une image H&E simple.
5. Conserver la version extension dans le runbook.

## À copier-coller
```text
Contrôles minimum:
- Menu StarDist visible dans QuPath
- Aucun message d'erreur au lancement
- Détections générées sur une ROI test
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
- [QuPath extensions](https://qupath.readthedocs.io/en/latest/docs/intro/extensions.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({{ site.baseurl }}{% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cell]({{ site.baseurl }}/cell/)
