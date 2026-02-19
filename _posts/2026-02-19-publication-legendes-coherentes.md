---
title: "Publication : légendes cohérentes et utiles"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Publication
  - Légende
  - Figure
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Publication : légendes cohérentes et utiles

## Portée précise
- Référence article: `publication-legendes-coherentes`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **publication** (focus complémentaire: legendes, coherentes).
- Stack cible: QuPath + outil de mise en page.
- Entrées attendues: figures exportées + légendes.
- Sorties attendues: figures prêtes à soumission.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- résolution cible (300 dpi min).
- palette lisible et accessible.
- barre d'échelle et légende normalisées.
- format final conforme aux consignes journal.

## Procédure opératoire
1. Exporter une version brute haute résolution.
2. Vérifier lisibilité des annotations et textes.
3. Uniformiser couleurs, tailles de police et légendes.
4. Contrôler la figure à 100% et 50% de zoom.
5. Archiver la version finale + source.

## Snippet prêt à adapter
```text
Checklist figure finale
- Résolution >= 300 dpi
- Barre d'échelle visible
- Légende complète (marqueurs, classes, unité)
```

## Validation rapide
- KPI: lisibilité en taille de publication.
- KPI: cohérence visuelle entre figures.
- KPI: conformité aux instructions auteur.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: annotations trop fines ou peu contrastées. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: légende incomplète. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: export compressé avec perte excessive. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="J-47tzXAFdE" provider="youtube" %}

![Illustration - Publication : légendes cohérentes et utiles](https://commons.wikimedia.org/wiki/Special:FilePath/Microscope%20image.jpg)

## Sources
- Vidéo: [QuPath Tutorial Introduction](https://www.youtube.com/watch?v=J-47tzXAFdE)
- Image: [Wikimedia Commons - Microscope image](https://commons.wikimedia.org/wiki/File:Microscope_image.jpg)
- Documentation technique: [Guide publication figures (Nature)](https://www.nature.com/nature/for-authors/formatting-guide)
