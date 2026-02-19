---
title: "Warpy vs VALIS : comparatif pratique"
date: 2026-02-19T00:00:00-01:00
categories:
  - Alignement
tags:
  - Warpy
  - VALIS
  - Comparaison
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Warpy vs VALIS : comparatif pratique

## Portée précise
- Référence article: `alignement-warpy-vs-valis`
- Périmètre: le recalage interlames et la projection d'annotations.
- Axe technique dominant: **valis** (focus complémentaire: alignement, warpy, vs).
- Stack cible: Python 3.9/3.10 + valis-wsi.
- Entrées attendues: dossier source de lames + dossier destination.
- Sorties attendues: transformations d'alignement + images warps.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- version Python alignée avec la doc VALIS.
- mémoire suffisante (>=16 Go conseillé).
- niveaux pyramidaux vérifiés avant run.
- répertoire de sortie dédié par lot.

## Procédure opératoire
1. Créer un environnement virtuel propre dédié à VALIS.
2. Tester l'alignement sur un petit sous-ensemble de lames.
3. Contrôler les superpositions sur zones anatomiques stables.
4. Exécuter le lot complet avec logs conservés.
5. Archiver paramètres et version VALIS utilisée.

## Snippet prêt à adapter
```python
# Exemple VALIS (adapter chemins et options)
from valis import registration

registrar = registration.Valis(
    src_dir="/path/to/src_slides",
    dst_dir="/path/to/output"
)
registrar.register()
registrar.warp_and_save_slides()
```

## Validation rapide
- KPI: cohérence des structures anatomiques superposées.
- KPI: absence de distorsion excessive.
- KPI: temps moyen de traitement par lame.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: lancer sans vérifier dépendances système. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: mélanger des lames à résolutions incompatibles. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: ne pas conserver les logs de run. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="MBrAVUsUdio" provider="youtube" %}

![Illustration - Warpy vs VALIS : comparatif pratique](https://commons.wikimedia.org/wiki/Special:FilePath/Tissue_Microarray_12X10.JPG)

## Sources
- Vidéo: [From Zero to QuPath Hero](https://www.youtube.com/watch?v=MBrAVUsUdio)
- Image: [Wikimedia Commons - Tissue Microarray 12X10](https://commons.wikimedia.org/wiki/File:Tissue_Microarray_12X10.JPG)
- Documentation technique: [Documentation VALIS](https://valis.readthedocs.io/en/latest/)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [VALIS : installation pas à pas]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-installation %})
- [VALIS : lancer un alignement en script Python]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-lancement %})
- [Python : lire et écrire un GeoJSON]({{ site.baseurl }}{% post_url 2026-02-19-python-geojson-lire-ecrire %})
