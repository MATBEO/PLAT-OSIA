---
title: "CytoMAP : installation et démarrage"
date: 2026-02-19T00:00:00-01:00
categories:
  - Cluster
tags:
  - Cluster
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# CytoMAP : installation et démarrage

## Étapes
1. Installer MATLAB version supportée par CytoMAP.
2. Télécharger CytoMAP depuis le wiki officiel.
3. Ajouter le dossier CytoMAP au `path` MATLAB.
4. Sauvegarder le `path` pour les prochaines sessions.
5. Lancer un dataset test pour confirmer l'installation.

## Exemple
```matlab
addpath(genpath('/path/to/CytoMAP'))
savepath
which CytoMAP
disp('CytoMAP prêt')
```

## Documentation
- [CytoMAP wiki](https://gitlab.com/gernerlab/cytomap/-/wikis/home)
- [MATLAB documentation](https://www.mathworks.com/help/matlab/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [CytoMAP : importer un CSV cellulaire propre]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-import-csv %})
- [CytoMAP : phénotypage cellulaire de base]({{ site.baseurl }}{% post_url 2026-02-19-cluster-cytomap-phenotypage %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Cluster]({{ site.baseurl }}/cluster/)
