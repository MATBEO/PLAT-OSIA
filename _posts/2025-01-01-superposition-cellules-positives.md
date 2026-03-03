---
title: "Superposition de cellules positives de lames sériées"
date: 2025-01-01T00:00:00-01:00
categories:
  - Cell
tags:
  - Segmentation
layout: single
toc: true
toc_label: "Table des matières"
classes: wide
---

<img src="{{ site.baseurl }}/assets/images/align.svg" width="50">

# Superposition de cellules positives

## Prérequis
- Avoir une lame HES
- Avoir des lames IHC

## Recette

### Aligner les lames

Vous pouvez soit faire cette étape initialement et enregistrer les `.tif`, soit aligner à posteriori les annotations que vous auriez définies.
Définissez la lame HES comme lame de référence, et utilisez les lames IHC comme lames à aligner.

### Détection des cellules positives

Dans un premier temps, vérifiez que vous utilisez bien une version récente de QuPath 0.7. Au **3 mars 2026**, la version officielle que j'ai pu vérifier est **`v0.7.0-rc1`**.
1. Sélectionnez votre lame IHC.
2. Grâce à un outil d'annotation, sélectionnez la zone sur laquelle vous voulez détecter les cellules. 
3. Allez dans **Extensions → InstanSeg → Run InstanSeg**.
4. Dans la boîte de dialogue, sélectionnez une ou plusieurs annotations sur lesquelles appliquer InstanSeg.
  - Cliquez sur **Run** pour lancer la segmentation. 

    Le processus lancera le modèle sur les régions sélectionnées et créera des détections (noyaux et/ou cellules) dans QuPath. 
    {: .notice--info}


5. Allez dans **Classify → Object classification → Set cell intensity classifications...**
  - Dans le champ **Measurement**, sélectionnez **DAB: Mean**
  - Réglez le seuil puis cliquez sur **Apply**

### Exporter seulement les cellules positives

1. Allez dans **Objects → Select... → Select objects by classification**
  - Choisissez **Negative** et validez

2. Allez dans **Objects → Delete... → Delete selected objects**

3. Allez dans **File → Export objects as GeoJSON...**
  - Sélectionnez **Selected objects** si vous avez déjà filtré la liste
