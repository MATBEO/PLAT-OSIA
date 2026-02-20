---
title: "Warpy : installation et test rapide"
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

# Warpy : installation et test rapide

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Deux lames du même tissu (référence + cible).
- Outil d'alignement installé (Warpy ou VALIS).
- Un dossier de sortie dédié pour les transformations.

## Pas à pas
1. Installer l'extension Warpy depuis son dépôt officiel.
2. Vérifier la compatibilité avec la version QuPath.
3. Redémarrer QuPath puis vérifier la présence du menu Warpy.
4. Tester un alignement sur 2 lames pilotes.
5. Conserver la version Warpy utilisée dans les notes projet.

## À copier-coller
```text
Validation minimale:
- Menu Warpy présent
- Exécution sans erreur sur un test 2 lames
- Fichier de transformation généré
```

## Vérifier que ça marche
- Les repères anatomiques se superposent correctement.
- Le décalage global est faible sur 3 zones de contrôle.
- Les sorties d'alignement sont bien générées.

## En cas de problème
- Vérifier que les lames ont des résolutions compatibles.
- Refaire le test sur une zone anatomique simple.

## Documentation officielle
- [Warpy extension GitHub](https://github.com/BIOP/qupath-extension-warpy)
- [QuPath extensions](https://qupath.readthedocs.io/en/latest/docs/intro/extensions.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Warpy : projeter des annotations interlames]({{ site.baseurl }}{% post_url 2026-02-19-alignement-warpy-projeter-annotations %})
- [VALIS : installation pas à pas]({{ site.baseurl }}{% post_url 2026-02-19-alignement-valis-installation %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Alignement]({{ site.baseurl }}/align/)
