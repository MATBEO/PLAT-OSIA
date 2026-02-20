---
title: "VALIS : installation pas à pas"
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

# VALIS : installation pas à pas

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Deux lames du même tissu (référence + cible).
- Outil d'alignement installé (Warpy ou VALIS).
- Un dossier de sortie dédié pour les transformations.

## Pas à pas
1. Créer un environnement Python dédié à VALIS.
2. Installer `valis-wsi` et dépendances scientifiques.
3. Vérifier import Python sans erreur.
4. Tester un run minimal sur 2 lames.
5. Sauvegarder `requirements.txt` du projet.

## À copier-coller
```bash
python -m venv .venv-valis
source .venv-valis/bin/activate
python -m pip install --upgrade pip
python -m pip install valis-wsi openslide-python
python -c "from valis import registration; print('VALIS OK')"
```

## Vérifier que ça marche
- Les repères anatomiques se superposent correctement.
- Le décalage global est faible sur 3 zones de contrôle.
- Les sorties d'alignement sont bien générées.

## En cas de problème
- Vérifier que les lames ont des résolutions compatibles.
- Refaire le test sur une zone anatomique simple.

## Documentation officielle
- [VALIS documentation](https://valis.readthedocs.io/en/latest/)
- [VALIS package](https://pypi.org/project/valis-wsi/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : installation et test rapide]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-installation %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
