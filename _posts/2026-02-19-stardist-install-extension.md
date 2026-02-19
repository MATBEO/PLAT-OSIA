---
title: "StarDist : installer l'extension dans QuPath"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cell
tags:
  - StarDist
  - QuPath
  - Installation
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# StarDist : installer l'extension dans QuPath

## Portée précise
- Référence article: `stardist-install-extension`
- Périmètre: la segmentation cellulaire et la quantification d'objets.
- Axe technique dominant: **stardist** (focus complémentaire: install, extension).
- Stack cible: QuPath avec extension StarDist.
- Entrées attendues: image H&E ou IF + zone d'intérêt.
- Sorties attendues: détections nuclei + mesures d'objets.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- modèle StarDist adapté (H&E/fluorescence).
- seuil de probabilité validé sur zone pilote.
- post-processing: suppression des petits objets aberrants.
- unité calibrée (µm/pixel) avant run.

## Procédure opératoire
1. Installer/activer l'extension StarDist dans QuPath.
2. Tester 2 à 3 paramètres de seuil sur une ROI de référence.
3. Valider la morphologie des noyaux détectés.
4. Exécuter le lot avec le même preset.
5. Exporter les mesures pour audit QC.

## Snippet prêt à adapter
```groovy
// Contrôle simple avant StarDist
println "Image: " + getCurrentImageName()
println "Pixel size (µm): " + getCurrentServer().getPixelCalibration().getAveragedPixelSizeMicrons()
```

## Validation rapide
- KPI: rappel visuel sur noyaux de petite taille.
- KPI: proportion de faux positifs en zones vides.
- KPI: stabilité des résultats entre lames proches.
- Cible qualité recommandée: Sorties traçables et rejouables sur un second poste.

## Erreurs fréquentes et correctifs
- Risque: seuil trop permissif en fond de lame. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: calibration absente ou erronée. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: comparaison inter-lot sans preset versionné. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="rQdVhCI3FbU" provider="youtube" %}

![Illustration - StarDist : installer l'extension dans QuPath](https://qupath.github.io/assets/images/slideshow/qupath-getting-started.png)

## Sources
- Vidéo: [StarDist Cell Segmentation in QuPath](https://www.youtube.com/watch?v=rQdVhCI3FbU)
- Image: [QuPath - getting started](https://qupath.github.io/)
- Documentation technique: [Documentation StarDist (QuPath)](https://github.com/qupath/qupath-extension-stardist)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({% post_url 2026-02-19-qupath-installation-propre %})
- [QuPath : importer des lames entières (WSI) correctement]({% post_url 2026-02-19-qupath-importer-wsi %})
- [InstanSeg : première segmentation cellule + noyau]({% post_url 2026-02-19-instanseg-premiere-segmentation %})
- [InstanSeg : paramètres clés à connaître]({% post_url 2026-02-19-instanseg-parametres-cles %})
- [InstanSeg : contrôle qualité des segmentations]({% post_url 2026-02-19-instanseg-qc-segmentation %})
- [StarDist vs InstanSeg : quand utiliser quoi]({% post_url 2026-02-19-stardist-vs-instanseg %})
