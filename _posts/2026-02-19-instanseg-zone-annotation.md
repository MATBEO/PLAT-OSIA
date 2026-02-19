---
title: "InstanSeg : segmentation sur zones annotées"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cell
tags:
  - InstanSeg
  - Annotation
  - QuPath
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# InstanSeg : segmentation sur zones annotées

## Portée précise
- Référence article: `instanseg-zone-annotation`
- Périmètre: la segmentation cellulaire et la quantification d'objets.
- Axe technique dominant: **instanseg** (focus complémentaire: zone, annotation).
- Stack cible: QuPath 0.6+ avec extension InstanSeg.
- Entrées attendues: WSI calibrée + ROI d'analyse.
- Sorties attendues: objets segmentés + table de mesures.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- `device`: `gpu` (si CUDA dispo), sinon `cpu`/`mps`.
- `tile size`: 512 ou 1024 selon la mémoire.
- `interTilePadding`: 16 à 32 pour limiter les effets de bord.
- sortie: noyaux, cellules ou noyaux+cellules selon le besoin.

## Procédure opératoire
1. Définir 3 ROI tests (faible, moyenne, forte densité cellulaire).
2. Lancer InstanSeg sur ces ROI avec paramètres constants.
3. Comparer visuellement le contour cellule/noyau sur chaque ROI.
4. Ajuster `tile size` et padding si artefacts de bord.
5. Appliquer au lot complet et exporter les mesures.

## Snippet prêt à adapter
```groovy
// QuPath - exemple minimal InstanSeg (adapter selon votre installation)
def rois = getAnnotationObjects()
if (rois.isEmpty()) throw new Exception('Aucune ROI sélectionnée')
println "InstanSeg sur ${rois.size()} ROI"
// Lancer ensuite via Extensions > InstanSeg > Run InstanSeg avec paramètres notés
```

## Validation rapide
- KPI: densité d'objets plausible biologiquement.
- KPI: faible taux de fusion/sur-segmentation.
- KPI: temps d'inférence stable par lame.
- Cible qualité recommandée: Sorties traçables et rejouables sur un second poste.

## Erreurs fréquentes et correctifs
- Risque: modèle inadapté au type de marquage. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: ROI avec artefacts non filtrés. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: run lot sans validation locale préalable. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="_ytJbpCA_cA" provider="youtube" %}

![Illustration - InstanSeg : segmentation sur zones annotées](https://commons.wikimedia.org/wiki/Special:FilePath/Dividing%20Cell%20Fluorescence.jpg)

## Sources
- Vidéo: [CIF Tutorial QuPath Installation](https://www.youtube.com/watch?v=_ytJbpCA_cA)
- Image: [Wikimedia Commons - Dividing Cell Fluorescence](https://commons.wikimedia.org/wiki/File:Dividing_Cell_Fluorescence.jpg)
- Documentation technique: [Documentation InstanSeg (QuPath)](https://github.com/qupath/qupath-extension-instanseg)
