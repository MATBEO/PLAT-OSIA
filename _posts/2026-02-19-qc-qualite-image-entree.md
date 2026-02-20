---
title: "QC : qualité d'image à l'entrée du pipeline"
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

# QC : qualité d'image à l'entrée du pipeline

## Étapes
1. Établir les critères d'acceptation du lot.
2. Contrôler chaque étape clé sur zones sentinelles.
3. Quantifier les écarts vs valeurs attendues.
4. Documenter décision OK/KO et actions correctives.
5. Archiver la fiche QC avec les exports.

## Exemple
```text
QC_LOG
date,article,status,artifact_rate,comment
2026-02-19,<article>,OK,0.03,"validation lot pilote"
```

## Documentation
- Documentation technique: [Quality control principles](https://www.iso.org/standard/62085.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [QC : check-list avant lancement d'analyse]({{ site.baseurl }}{% post_url 2026-02-19-qc-checklist-avant-analyse %})
- [QC : détecter les erreurs de segmentation]({{ site.baseurl }}{% post_url 2026-02-19-qc-detection-erreurs-segmentation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Visualisation]({{ site.baseurl }}/visualisation/)
