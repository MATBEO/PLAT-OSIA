---
title: "Évaluer un modèle de classification dans QuPath"
date: 2026-02-19T00:00:00-01:00
categories:
  - Pattern
tags:
  - Pattern
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# Évaluer un modèle de classification dans QuPath

## Objectif
À la fin, vous aurez reproduit cette étape de bout en bout sur un cas test.

## Avant de commencer
- Annotations d'entraînement déjà préparées.
- Classes cibles définies sans ambiguïté.
- Jeu de validation séparé.

## Pas à pas
1. Exporter les prédictions et la vérité terrain en CSV.
2. Calculer matrice de confusion et F1-score par classe.
3. Identifier les classes avec rappel faible.
4. Revoir les erreurs typiques sur image.
5. Valider le modèle avant déploiement cohorte.

## À copier-coller
```python
import pandas as pd
from sklearn.metrics import classification_report, confusion_matrix

df = pd.read_csv('pred_vs_gt.csv')
y_true, y_pred = df['gt'], df['pred']
print(confusion_matrix(y_true, y_pred))
print(classification_report(y_true, y_pred, digits=3))
```

## Vérifier que ça marche
- Les métriques du modèle sont calculées.
- Les erreurs majeures sont identifiées.
- Le modèle final est sauvegardé et traçable.

## En cas de problème
- Rééquilibrer les classes d'entraînement.
- Vérifier la qualité des annotations de vérité terrain.

## Documentation officielle
- [scikit-learn metrics](https://scikit-learn.org/stable/modules/model_evaluation.html)
- [QuPath docs](https://qupath.readthedocs.io/en/latest/)

## Articles liés
- [QuPath : installation propre et vérification initiale]({{ site.baseurl }}{% post_url 2026-02-19-qupath-installation-propre %})
- [Classification objet dans QuPath : bonnes pratiques]({{ site.baseurl }}{% post_url 2026-02-19-pattern-classification-objet %})
- [Construire un workflow reproductible de pattern]({{ site.baseurl }}{% post_url 2026-02-19-pattern-workflow-reproductible %})
- [Parcours recommandé]({{ site.baseurl }}/parcours-recommande/)
- [Médias utiles]({{ site.baseurl }}/medias-utiles/)
- [Page thématique : Pattern]({{ site.baseurl }}/pattern/)
