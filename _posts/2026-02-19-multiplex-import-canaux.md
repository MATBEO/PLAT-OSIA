---
title: "Multiplex : importer et nommer les canaux"
date: 2026-02-19T00:00:00-01:00
categories:
  - Multiplex
tags:
  - Multiplex
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Multiplex : importer et nommer les canaux

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Images multiplex avec canaux identifiés.
- Liste des marqueurs et contrôles disponible.
- Projet QuPath dédié au multiplex.

## Pas à pas
1. Importer les images multiplex dans un projet séparé.
2. Renommer chaque canal avec le nom du marqueur réel.
3. Vérifier l'ordre des canaux pour éviter les inversions.
4. Contrôler le bruit de fond par canal.
5. Sauvegarder la configuration canaux avant suite.

## À copier-coller
```groovy
def channels = getCurrentServer().getMetadata().getChannels()
channels.eachWithIndex { ch, i ->
    println "${i}: ${ch.getName()}"
}
```

## Vérifier que ça marche
- Les canaux sont correctement nommés.
- Les seuils/phénotypes produisent des classes cohérentes.
- Les exports sont complets pour le lot test.

## En cas de problème
- Vérifier l'ordre des canaux et les seuils de base.
- Contrôler une lame témoin avant lot complet.

## Documentation officielle
- [QuPath channels](https://qupath.readthedocs.io/en/latest/docs/intro/images.html)
- [QuPath scripting](https://qupath.readthedocs.io/en/latest/docs/scripting/overview.html)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Multiplex : préparer un projet QuPath propre]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-preparation-projet %})
- [Multiplex : segmentation cellulaire adaptée]({{ site.baseurl }}{% post_url 2026-02-19-multiplex-segmentation-cellulaire %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Multiplex]({{ site.baseurl }}/multiplex/)
