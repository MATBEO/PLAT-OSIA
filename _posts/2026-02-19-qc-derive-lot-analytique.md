---
title: "QC : surveiller la dérive entre lots"
date: 2026-02-19T00:00:00-01:00
categories:
  - Pattern
tags:
  - QC
  - Lot
  - Analyse
toc: true
toc_label: "Table des matières"
toc_sticky : true
layout: single
---

# QC : surveiller la dérive entre lots

## Portée précise
- Référence article: `qc-derive-lot-analytique`
- Périmètre: la classification de structures tissulaires et l'interprétation du modèle.
- Axe technique dominant: **qc** (focus complémentaire: derive, lot, analytique).
- Stack cible: pipeline QC transversal.
- Entrées attendues: résultats intermédiaires + finaux.
- Sorties attendues: statut QC (OK/KO) justifié.

## Préparation
- Créer un lot pilote (3 à 5 lames/échantillons) avant exécution complète.
- Noter version outil, date, opérateur et paramètres dans un journal de run.
- Verrouiller le dossier de sortie (`results/<date>/<article_slug>/`).
- Définir la règle de décision QC (OK/KO) avant lancement.

## Paramètres conseillés
- critères QC définis avant run.
- zones sentinelles fixes.
- seuils d'acceptation explicites.
- journal QC horodaté.

## Procédure opératoire
1. Établir les critères d'acceptation du lot.
2. Contrôler chaque étape clé sur zones sentinelles.
3. Quantifier les écarts vs valeurs attendues.
4. Documenter décision OK/KO et actions correctives.
5. Archiver la fiche QC avec les exports.

## Snippet prêt à adapter
```text
QC_LOG
date,article,status,artifact_rate,comment
2026-02-19,<article>,OK,0.03,"validation lot pilote"
```

## Validation rapide
- KPI: taux d'artefacts sous seuil.
- KPI: cohérence inter-opérateur.
- KPI: décisions QC traçables.
- Cible qualité recommandée: Taux d'échec de run < 5% sur lot homogène.

## Erreurs fréquentes et correctifs
- Risque: QC uniquement visuel sans métrique. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: seuils modifiés sans traçabilité. Correctif: documenter le paramètre et rejouer sur lot pilote.
- Risque: absence d'action corrective documentée. Correctif: documenter le paramètre et rejouer sur lot pilote.

## Livrables à archiver
- Paramètres du run (fichier texte/JSON) + version des outils.
- Exports principaux (annotations, mesures, figures) avec nommage stable.
- Note QC courte: décisions prises, limites observées, actions suivantes.

## Média
{% include video id="cL05xtTocmY" provider="youtube" %}

![Illustration - QC : surveiller la dérive entre lots](https://commons.wikimedia.org/wiki/Special:FilePath/Histology.jpg)

## Sources
- Vidéo: [Installing CUDA Toolkit on Windows (NVIDIA Developer)](https://www.youtube.com/watch?v=cL05xtTocmY)
- Image: [Wikimedia Commons - Histology](https://commons.wikimedia.org/wiki/File:Histology.jpg)
- Documentation technique: [Quality control principles](https://www.iso.org/standard/62085.html)
