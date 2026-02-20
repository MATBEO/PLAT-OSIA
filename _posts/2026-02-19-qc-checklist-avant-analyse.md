---
title: "QC : check-list avant lancement d'analyse"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Qualite
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QC : check-list avant lancement d'analyse

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Résultats intermédiaires déjà exportés.
- Checklist projet disponible.
- Critères de validation définis en amont.

## Pas à pas
1. Vérifier intégrité des fichiers (taille non nulle, ouverture OK).
2. Contrôler calibration pixel et métadonnées.
3. Valider qualité focus/exposition sur zones clés.
4. Confirmer classes, seuils et paramètres de run.
5. Signer la checklist avant exécution complète.

## À copier-coller
```bash
# Exemple contrôle rapide dossier WSI
find data_wsi -type f | wc -l
find data_wsi -type f -size 0 -print
# Lister extensions attendues
find data_wsi -type f | sed 's|.*\.||' | sort | uniq -c
```

## Vérifier que ça marche
- Chaque point de checklist est renseigné.
- Les anomalies bloquantes sont isolées.
- La décision Go/No-Go est explicite.

## En cas de problème
- Revenir à l'étape précédente avec un lot plus petit.
- Comparer avec un cas validé de référence.

## Documentation officielle
- [Quality management principles](https://www.iso.org/standard/62085.html)
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QC : détecter les erreurs de segmentation]({{ site.baseurl }}{% post_url 2026-02-19-qc-detection-erreurs-segmentation %})
- [QC : qualité d'image à l'entrée du pipeline]({{ site.baseurl }}{% post_url 2026-02-19-qc-qualite-image-entree %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
