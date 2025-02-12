---
title: "superposition cellules positives de lames sériées"
date: 2025-01-01T00:00:00-01:00
categories:
  - Cell
tags:
  - Qupath
  - Groovy
  - Geojson
layout: single
toc: true
toc_label: "Table des Matieres"
classes: wide
---

<img src="{{ site.baseurl }}/assets/images/align.svg" width="50">

# Superposition de cellules positives

## prerequis
- avoir une lame HES
- avoir des lames IHC

## recette

### aligner les lanes

vous pouvez soit faire cette étape initialement et enregistrer les .tif Soit alignées à posteriori les annotations que vous auriez définies.  
Il vous faut définir les lames d'intérêt comme la lame HES et les autres lames à aligner sont les IHC. 

### detection des cellules positives

Dans un premier temps, vous devez vérifier si vous avez bien la version 0.6.0 de QuPath 
1. sélectionnez votre lame IHC 
2. Grâce à un outil d'annotation, sélectionnez la zone sur laquelle vous voulez détecter les cellules. 
3. Allez dans **Extensions → InstanSeg → Run InstanSeg**
4. Dans la boîte de dialogue, sélectionnez une ou plusieurs annotations sur lesquelles appliquer InstanSeg.
   - Cliquez sur **Run** pour lancer la segmentation. 
>**Info :** Le processus lancera le modèle sur les régions sélectionnées et créera des détections (noyaux et/ou cellules) dans QuPath.[pour plus d'info sur InstanSeg]({{'/cell/InstaSeg/' | relative_url }})

5. Allez dans **Classify → Object Classification → Set cell intensity classifications**
    - dans le champs **Measurement** selectionné **DAB : mean**
    - cliquez sur apply quand vous serez content du seuil de positivé

### exportez seulement les cellules positives

1. Allez dans **Objects → Select... → Select objects by classification**
    - choississez **négative** et validez

2. Allez dans **Objects → Delete... → Delete selected objects**

3. Allez dans **File → Export objects as GeoJSON**

