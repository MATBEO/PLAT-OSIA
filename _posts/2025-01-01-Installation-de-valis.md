---
title: "Installation de Valis"
date: 2024-04-18T15:34:30-04:00
categories:
  - Alignement
tags:
  - Installation
  - Python
  - Geojson
toc: true
toc_label: "Table des Matieres"
toc_sticky : true
layout: single
---

# Tutoriel d'installation de VALIS

Ce document présente plusieurs méthodes pour installer VALIS, ainsi que les prérequis nécessaires.

---

## 1. Contexte et prérequis

### Version de Python requise
VALIS fonctionne actuellement avec **Python 3.9** ou **3.10**.

### Prérequis système
Avant d’installer VALIS, assurez-vous d’installer les éléments suivants :

- **Java Development Kit (JDK) et Java Runtime Environment (JRE)**  
  VALIS utilise Bioformats pour lire de nombreux formats de diapositives. Bioformats est écrit en Java et est accessible via le package Python *jpype*.
  - Téléchargez un JDK approprié (par exemple depuis [Oracle Java Downloads](https://www.oracle.com/java/technologies/javase-downloads.html)).
  - Configurez la variable d’environnement `JAVA_HOME` :
    ```bash
    export JAVA_HOME=/usr/libexec/java_home
    echo $JAVA_HOME  # pour vérifier l'installation
    ```

- **Maven**  
  Nécessaire pour Bioformats, Maven doit être installé depuis [le site officiel](https://maven.apache.org/index.html).

- **OpenSlide (pour certains formats de fichiers)**  
  Si vous travaillez avec des fichiers ayant les extensions `.vmu`, `.mrxs` ou `.svslide`, installez OpenSlide (attention, ce n’est pas le package Python *openslide-python*).  
  > **Note importante :** OpenSlide requiert la bibliothèque *pixman* en version **0.40.0** pour éviter des distorsions lors de la lecture à des niveaux pyramidaux autres que 0.

- **Libvips et pyvips**  
  VALIS utilise *pyvips* pour appliquer des transformations et sauvegarder les images en format ome.tiff. Installez libvips (version ≥ 8.11) en suivant les instructions disponibles dans les notes d'installation de [pyvips](https://github.com/libvips/pyvips).

---

## 2. Installation via Docker

VALIS est disponible en image Docker sur DockerHub, ce qui permet de bénéficier d’un environnement prêt à l’emploi.

### Étapes

1. **Installer Docker** sur votre machine.
2. **Lancer l'image Docker de VALIS.**  
   Par exemple, pour exécuter un script `register.py` qui enregistre les images d’un dossier source vers un dossier de destination, utilisez :

    ```bash
    docker run --memory=20g -v "$HOME:$HOME" cdgatenbee/valis-wsi python3 /full/path/to/register.py -src_dir /full/path/to/images_to_align -dst_dir /full/path/to/where_to_save_results
    ```

    > **Astuce :** Veillez à spécifier des limites mémoire suffisamment élevées (ici 20 Go) pour éviter que le conteneur ne s’arrête prématurément.

---

## 3. Installation via pip

VALIS est disponible sur PyPI sous le nom de package **valis-wsi**. Cette méthode est recommandée pour une installation dans votre environnement Python local.

### Étapes

1. **Création d’un environnement virtuel (optionnel mais conseillé) :**
    ```bash
    python3 -m venv venv_valis
    source ./venv_valis/bin/activate
    ```

2. **Mise à jour de pip :**
    ```bash
    python3 -m pip install --upgrade pip
    ```

3. **Installation de VALIS via pip :**
    ```bash
    pip install valis-wsi
    ```

4. **Alternative :** Installer directement depuis le dépôt GitHub :
    ```bash
    pip install git+https://github.com/MathOnco/valis.git
    ```

---

## 4. Installation depuis le code source

Pour installer VALIS directement depuis le code source, utilisez [Poetry](https://python-poetry.org/) pour gérer les dépendances Python.

### Étapes

1. **Cloner le dépôt Git de VALIS :**
    ```bash
    git clone https://github.com/MathOnco/valis.git
    cd valis
    ```

2. **Créer et activer un environnement virtuel :**
    ```bash
    python3 -m venv venv_valis
    source ./venv_valis/bin/activate
    ```

3. **Installer Poetry (si ce n’est pas déjà fait) :**
    ```bash
    pip install poetry
    ```

4. **Installer les dépendances via Poetry :**
    ```bash
    poetry install
    ```

> **Remarque :** Poetry ne gère que les dépendances Python. Vous devez donc vous assurer d’avoir installé le JDK, Maven, libvips et OpenSlide selon les prérequis précédents.

---

## 5. Options supplémentaires : SimpleElastix (facultatif)

Certaines fonctionnalités avancées de VALIS reposent sur [SimpleElastix](http://simpleelastix.github.io) :

### Modules concernés

- `affine_optimizer.AffineOptimizerMattesMI`
- `non_rigid_registrars.SimpleElastixWarper`
- `non_rigid_registrars.SimpleElastixGroupwiseWarper`

### Pour installer SimpleElastix

1. Désinstallez la version actuelle de SimpleITK si elle est présente.
2. Suivez les instructions d’installation dans la [documentation de SimpleElastix](https://simpleelastix.readthedocs.io).

---

## Conclusion

Vous disposez de plusieurs méthodes pour installer VALIS :

- **Docker :** Pour une installation rapide et isolée.
- **pip :** Pour intégrer VALIS dans votre environnement Python habituel.
- **Source :** Pour contribuer ou utiliser la version la plus récente directement depuis GitHub.

Assurez-vous de respecter scrupuleusement les étapes des prérequis pour éviter tout problème lié aux dépendances. Pour plus de détails et les mises à jour, consultez la [documentation officielle](https://valis.readthedocs.io/en/latest/installation.html).

---

Ce fichier est prêt à être intégré dans votre wiki GitHub. Il vous suffit de l’ajouter à votre dépôt ou de copier son contenu dans la page de votre choix.
