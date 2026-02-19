---
title: "VALIS : contrôle qualité du résultat final"
date: 2026-02-19T00:00:00-01:00
categories:
  - Alignement
tags:
  - VALIS
  - QC
  - Alignement
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# VALIS : contrôle qualité du résultat final

## Portée précise
- Référence article: `alignement-valis-qc-resultat`
- Périmètre: le recalage interlames et la projection d'annotations.
- Axe technique dominant: **valis** (focus complémentaire: alignement, qc, resultat).
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
- Cible qualité recommandée: Sorties traçables et rejouables sur un second poste.

## Erreurs fréquentes et correctifs
- Risque: lancer sans vérifier dépendances système. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: mélanger des lames à résolutions incompatibles. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: ne pas conserver les logs de run. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="75J9nxhviV8" provider="youtube" %}

![Illustration](https://qupath.github.io/assets/images/slideshow/qupath-getting-started.png)

## Sources
- Vidéo: [How to Install QuPath](https://www.youtube.com/watch?v=75J9nxhviV8)
- Image: [Wikimedia Commons - Histology (1)](https://commons.wikimedia.org/wiki/File:Histology_(1).jpg)
- Documentation technique: [Documentation VALIS](https://valis.readthedocs.io/en/latest/)
