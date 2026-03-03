---
title: "QuPath : exporter les mesures au format CSV"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - QuPath
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QuPath : exporter les mesures au format CSV

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- QuPath 0.7 installé et lancé une première fois.
- Au 3 mars 2026, la version officielle vérifiée est `v0.7.0-rc1`.
- Une image test ouverte dans un projet QuPath.
- Droits d'écriture sur le dossier de sortie.

## Pas à pas
1. Vérifier que la détection est terminée et gelée (pas de recalcul en parallèle).
2. Choisir les mesures utiles (aire, circularité, intensité marqueur).
3. Exporter en CSV depuis la table de mesures ou avec un script Groovy dédié.
4. Inclure l'identifiant image et ROI dans le fichier exporté.
5. Contrôler 10 lignes aléatoires dans un tableur avant import aval.

## À copier-coller
```groovy
def out = buildFilePath(PROJECT_BASE_DIR, 'exports', 'detections.csv')
mkdirs(new File(out).getParent())
saveDetectionMeasurements(out)
println 'Export: ' + out
```

## Vérifier que ça marche
- La manipulation se lance sans erreur dans QuPath.
- Le résultat attendu est visible sur l'image test.
- Le projet se sauvegarde correctement.

## En cas de problème
- Redémarrer QuPath puis relancer sur une image plus petite.
- Vérifier la version QuPath et l'extension installée.

## Documentation officielle
- [QuPath `v0.7.0-rc1`](https://github.com/qupath/qupath/releases/tag/v0.7.0-rc1)
- [Exporting results in QuPath](https://qupath.readthedocs.io/en/latest/docs/advanced/exporting_results.html)
- [QuPath scripting API](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : créer un projet standard reproductible]({{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %})
- [QuPath : importer des lames entières (WSI) correctement]({{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
