---
title: "exporter des TMA de Qupath en GeoJson puis pouvoir les réimporter"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Qupath
  - Python
  - Geojson
  - TMA
toc: true
toc_sticky : true
layout: single
---

# définir la zone d'interet sur qupath

Ouvrir Qupath et creer les TMAs
pour cela, 
Allez dans **TMA → TMA dearray**
Préciser le nombre de lignes et colonnes et la tailles des cores

Déplacer les cores si nécessaire

# sauver le geojson

Sauver votre objet geojson 
Allez dans **File → Export objects as GeoJson**
selectionner : "All objects"

# lancer le script

```
import json

#modifier les chemins
in_path = "file_input.geojson"   # fichier en entrée 
out_path = "file_output.geojson"  # fichier transformé

with open(in_path, "r", encoding="utf-8") as f:
    data = json.load(f)

for feat in data.get("features", []):
    props = feat.get("properties", {})
    
    # Remplacer objectType
    props["objectType"] = "annotation"
    
    # Ajouter champ Missing core (ici par défaut False)
    props["classification"] = "Tumor"
    if props["isMissing"] ==True :
        props["classification"] = "no Tumor"
    feat["properties"] = props

# Sauvegarde
with open(out_path, "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)

print(f"Fichier exporté : {out_path}")
```

