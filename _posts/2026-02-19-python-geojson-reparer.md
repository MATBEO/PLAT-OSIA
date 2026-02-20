---
title: "Python : réparer des géométries GeoJSON invalides"
date: 2026-02-19T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Python
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Python : réparer des géométries GeoJSON invalides

## Portée précise
- Référence article: `python-geojson-reparer`
- Périmètre: l'exploration visuelle, l'organisation du projet et la fiabilité des exports.
- Axe technique dominant: **python** (focus complémentaire: geojson, reparer).
- Stack cible: Python + bibliothèques d'imagerie.
- Entrées attendues: WSI/GeoJSON/CSV selon le cas.
- Sorties attendues: fichiers dérivés contrôlés.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- venv dédié avec dépendances figées.
- chemins d'entrée/sortie explicites.
- logs minimalistes mais exploitables.
- tests sur un sous-ensemble avant lot.

## Procédure opératoire
1. Créer l'environnement et installer les dépendances.
2. Valider les formats de fichiers d'entrée.
3. Exécuter un run pilote et inspecter les sorties.
4. Lancer le lot complet avec journal d'exécution.
5. Vérifier les métriques finales et archiver.

## Snippet prêt à adapter
```python
from pathlib import Path

inp = Path('/path/to/input')
out = Path('/path/to/output')
out.mkdir(parents=True, exist_ok=True)

for fp in sorted(inp.glob('*')):
    # TODO: adapter le traitement
    print(f"processing: {fp.name}")
```

## Validation rapide
- KPI: taux de succès des fichiers traités.
- KPI: temps moyen par échantillon.
- KPI: absence de fichiers corrompus en sortie.
- Cible qualité recommandée: Écart inter-opérateur limité via protocole écrit.

## Erreurs fréquentes et correctifs
- Risque: chemins implicites non portables. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence de gestion d'erreur par fichier. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: pas de validation post-traitement. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="75J9nxhviV8" provider="youtube" %}

![Illustration - Python : réparer des géométries GeoJSON invalides](https://qupath.github.io/assets/images/slideshow/qupath-jobs.png)

## Sources
- Vidéo: [How to Install QuPath](https://www.youtube.com/watch?v=75J9nxhviV8)
- Image: [QuPath - illustration](https://qupath.github.io/)
- Documentation technique: [Documentation OpenSlide Python](https://openslide.org/api/python/)

## Voir aussi
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Python + OpenSlide : premiers pas]({{ site.baseurl }}{% post_url 2026-02-19-python-openslide-premiers-pas %})
- [Python : extraction de tuiles depuis WSI]({{ site.baseurl }}{% post_url 2026-02-19-python-extraction-tiles %})
- [Python : filtrer les tuiles sans tissu]({{ site.baseurl }}{% post_url 2026-02-19-python-filtre-tiles-vide %})
- [Python : lire et écrire un GeoJSON]({{ site.baseurl }}{% post_url 2026-02-19-python-geojson-lire-ecrire %})
- [QuPath : exporter les mesures au format CSV]({{ site.baseurl }}{% post_url 2026-02-19-qupath-mesures-export-csv %})
