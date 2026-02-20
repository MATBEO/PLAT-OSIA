---
title: "Warpy : projeter des annotations interlames"
date: 2026-02-19T00:00:00-01:00
categories:
  - Alignement
tags:
  - Alignement
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Warpy : projeter des annotations interlames

## Portée précise
- Référence article: `alignement-warpy-projeter-annotations`
- Périmètre: le recalage interlames et la projection d'annotations.
- Axe technique dominant: **warpy** (focus complémentaire: alignement, projeter, annotations).
- Stack cible: QuPath + extension Warpy.
- Entrées attendues: lame de référence + lame(s) à projeter.
- Sorties attendues: matrice de transformation + annotations projetées.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- points de repère sur structures stables.
- répartition homogène des points sur la lame.
- vérification locale sur zones critiques.
- version des plugins conservée.

## Procédure opératoire
1. Choisir une lame pivot (référence) par série.
2. Poser des repères distribués (centre + périphérie).
3. Calculer la transformation et inspecter les zones denses.
4. Projeter les annotations uniquement après QC local.
5. Exporter les annotations projetées en GeoJSON.

## Snippet prêt à adapter
```groovy
// Contrôle avant projection
println "Reference image: " + getCurrentImageName()
println "N annotations: " + getAnnotationObjects().size()
```

## Validation rapide
- KPI: erreur visuelle faible sur points anatomiques.
- KPI: continuité des contours projetés.
- KPI: cohérence des surfaces d'annotations.
- Cible qualité recommandée: Sorties traçables et rejouables sur un second poste.

## Erreurs fréquentes et correctifs
- Risque: repères concentrés sur une seule zone. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: projection sans validation de bord. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence de versionnage des transformations. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="4wPUtUtSp-o" provider="youtube" %}

![Illustration - Warpy : projeter des annotations interlames](https://qupath.github.io/assets/images/slideshow/qupath-getting-started.png)

## Sources
- Vidéo: [Install NVIDIA CUDA Toolkit on Windows](https://www.youtube.com/watch?v=4wPUtUtSp-o)
- Image: [QuPath - getting started](https://qupath.github.io/)
- Documentation technique: [Documentation Warpy](https://github.com/BIOP/qupath-extension-warpy)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [VALIS : installation pas à pas]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-installation %})
- [VALIS : lancer un alignement en script Python]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-lancement %})
- [Warpy vs VALIS : comparatif pratique]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-vs-valis %})
- [Python : lire et écrire un GeoJSON]({{ site.baseurl }}{% post_url 2026-02-19-python-geojson-lire-ecrire %})
