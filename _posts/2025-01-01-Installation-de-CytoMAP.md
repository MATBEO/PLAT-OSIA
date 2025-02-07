---
title: "Installation de CytoMAP"
date: 2025-01-01T00:00:00-01:00
categories:
  - Cluster
tags:
  - Installation
  - CytoMAP
toc: true
toc_label: "Table des Matieres"
toc_sticky : true
layout: single
---

# Tutoriel CytoMAP : Installation via l’Exécutable (.exe) et Utilisation

Ce tutoriel vous guide à travers l’installation de **CytoMAP** en utilisant la version autonome distribuée sous forme d’exécutable (.exe) pour Windows, ainsi que les étapes de base pour l’utilisation de cet outil d’analyse spatiale des données cellulaires.

---

## 1. Introduction

**CytoMAP** est une boîte à outils destinée à l’analyse des données issues d’imagerie multiplexée. Elle permet de :
- Visualiser des données en 2D/3D,
- Identifier et phénotyper des populations cellulaires via des algorithmes de clustering,
- Analyser la composition des microenvironnements et la distribution spatiale des cellules.

Pour en savoir plus sur les fonctionnalités et le guide d’installation complet, consultez le [Guide d’installation sur GitLab]( [oai_citation_attribution:0‡gitlab.com](https://gitlab.com/gernerlab/cytomap/-/wikis/Installation-Guide)).

---

## 2. Installation via l’Exécutable (.exe)

### 2.1. Téléchargement de l’Installateur

1. **Accéder au fichier d’installation :**  
   Téléchargez la version compilée de CytoMAP pour Windows depuis le lien suivant :  
   [Télécharger l’installateur CytoMAP (.exe)](https://gitlab.com/gernerlab/cytomap/raw/master/StandaloneInstaller/CytoMAP_Installer_Windows.exe?inline=false).

### 2.2. Exécution de l’Installateur

2. **Installation :**
   - Localisez le fichier téléchargé sur votre ordinateur.
   - Double-cliquez sur le fichier `.exe` pour lancer l’assistant d’installation.
   - Suivez les instructions à l’écran pour installer CytoMAP sur votre système.

> **Remarque :**  
> La version autonome offre une interface simplifiée et ne nécessite pas l’installation de MATLAB ni de ses toolboxes associés.

### 2.3. Lancement de CytoMAP

3. **Démarrage de l’application :**
   - Une fois l’installation terminée, lancez CytoMAP via le raccourci créé sur le bureau ou depuis le menu Démarrer.
   - L’application s’ouvrira et vous pourrez accéder aux différentes fonctionnalités d’analyse.

---

## 3. Utilisation de CytoMAP

Après avoir installé CytoMAP via l’exécutable, voici les étapes essentielles pour démarrer votre analyse :

### 3.1. Préparation et Importation des Données

- **Format des fichiers :**  
  Préparez vos données sous forme de fichiers CSV où chaque ligne représente une cellule et chaque colonne une variable (intensité des marqueurs, coordonnées spatiales X, Y, Z).  
  > **Astuce :** Pour les données en 2D (X et Y uniquement), CytoMAP ajoutera automatiquement une colonne Z avec des zéros.

- **Importation des échantillons :**  
  Dans l’interface de CytoMAP, utilisez la fonction **Import Multiple Samples** pour charger vos fichiers. Vous aurez la possibilité de renommer les échantillons et d’ajuster les noms des canaux si nécessaire.

### 3.2. Visualisation des Données

- **Création d’une Figure :**  
  Créez une nouvelle figure via le menu de CytoMAP pour visualiser vos échantillons.
- **Exploration interactive :**  
  Sélectionnez des canaux spécifiques (par exemple, un marqueur d’intérêt) pour colorer et explorer la distribution spatiale des cellules.

### 3.3. Phénotypage et Clustering

- **Clustering des cellules :**  
  Utilisez la commande **Cluster Cells** pour regrouper les cellules selon leurs intensités de marqueurs.  
  Ajustez les paramètres tels que le nombre de clusters et les canaux utilisés afin d’obtenir une classification pertinente.

- **Affichage des résultats :**  
  Les cellules seront colorées en fonction de leur appartenance à un cluster, facilitant ainsi l’identification visuelle des différents groupes cellulaires.

### 3.4. Annotation des Clusters

- **Nommer les clusters :**  
  À l’aide de l’outil d’annotation, attribuez un nom descriptif à chaque cluster (par exemple, « Macrophages » pour un cluster présentant une forte expression de CD64/CD169).

### 3.5. Analyse des Microenvironnements

- **Définition des voisinages :**  
  Utilisez l’interface **Define Neighborhoods** pour créer des zones (ex. zones de 50 µm en balayage raster) qui permettront de quantifier la composition cellulaire locale.
  
- **Clustering des voisinages en régions :**  
  Appliquez une méthode de clustering sur ces voisinages pour identifier des régions tissulaires distinctes, et analysez ensuite leurs statistiques (nombre de cellules, intensité moyenne, etc.).

---

## 4. Ressources et Support

- **Documentation complète :**  
  Pour plus de détails sur toutes les fonctionnalités de CytoMAP, consultez le [Wiki officiel sur GitLab](https://gitlab.com/gernerlab/cytomap/-/wikis/Installation-Guide) ( [oai_citation_attribution:1‡gitlab.com](https://gitlab.com/gernerlab/cytomap/-/wikis/Installation-Guide)).

- **Support communautaire :**  
  En cas de questions ou de problèmes, rendez-vous sur le forum [image.sc](https://forum.image.sc) et postez votre requête en utilisant le tag *cytomap*.

---

## 5. Conclusion

En suivant ces étapes, vous disposez d’une installation fonctionnelle de CytoMAP via l’exécutable (.exe) sur Windows. Vous pouvez désormais exploiter cet outil puissant pour :
- Visualiser et explorer vos données d’imagerie,
- Effectuer des analyses de clustering et de phénotypage,
- Définir et analyser les microenvironnements cellulaires.

Bonne exploration et analyse avec CytoMAP !

---

{% include video id="jud_PSzBWUw" provider="youtube" %}


*Sources :*  
Guide d’installation sur GitLab ( [oai_citation_attribution:2‡gitlab.com](https://gitlab.com/gernerlab/cytomap/-/wikis/Installation-Guide))