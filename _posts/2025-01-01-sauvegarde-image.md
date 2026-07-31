---
title: "Exporter une zone QuPath en image"
date: 2025-01-01T00:00:00-01:00
categories:
  - Visualisation
tags:
  - Export
toc: true
toc_label: "Sommaire"
layout: single
---

Cette méthode exporte une région dessinée dans QuPath en JPEG, en gardant uniquement les pixels situés dans l'annotation. Utilisez-la pour préparer une image de figure ou un contrôle visuel; gardez toujours l'image source et le GeoJSON avec le résultat.

## 1. Exporter l'annotation depuis QuPath

1. Dessinez et sélectionnez la ou les annotations à exporter.
2. Utilisez **File > Export objects as GeoJSON...**.
3. Choisissez **Selected objects** si vous avez sélectionné les annotations, puis enregistrez `lame_001.geojson`.
4. Créez un dossier `exports/images/` dans le dossier du projet.

## 2. Installer les dépendances Python

Le script lit les lames SVS avec OpenSlide et crée l'image avec Pillow.

```bash
python -m pip install openslide-python pillow
```

Sous macOS, installez aussi la bibliothèque OpenSlide si elle n'est pas déjà présente:

```bash
brew install openslide
```

## 3. Exporter les régions

Enregistrez ce script sous `export_roi.py`. Remplacez `LEVEL = 0` par un niveau plus élevé pour une image plus légère; le niveau `0` conserve la résolution maximale.

```python
import json
import math
import sys
from pathlib import Path

import openslide
from PIL import Image, ImageDraw


def polygons(geometry):
    if geometry["type"] == "Polygon":
        return [geometry["coordinates"][0]]
    if geometry["type"] == "MultiPolygon":
        return [polygon[0] for polygon in geometry["coordinates"]]
    return []


def export_rois(slide_path, geojson_path, output_dir, level=0):
    slide = openslide.OpenSlide(str(slide_path))
    downsample = float(slide.level_downsamples[level])
    output_dir.mkdir(parents=True, exist_ok=True)

    with open(geojson_path, encoding="utf-8") as handle:
        features = json.load(handle)["features"]

    output_index = 0
    for feature in features:
        for polygon in polygons(feature["geometry"]):
            xs, ys = zip(*polygon)
            min_x, max_x = math.floor(min(xs)), math.ceil(max(xs))
            min_y, max_y = math.floor(min(ys)), math.ceil(max(ys))
            width = math.ceil((max_x - min_x) / downsample)
            height = math.ceil((max_y - min_y) / downsample)

            region = slide.read_region((min_x, min_y), level, (width, height)).convert("RGB")
            mask = Image.new("L", region.size, 0)
            scaled = [((x - min_x) / downsample, (y - min_y) / downsample) for x, y in polygon]
            ImageDraw.Draw(mask).polygon(scaled, fill=255)

            result = Image.new("RGB", region.size, "white")
            result.paste(region, mask=mask)
            output_index += 1
            result.save(output_dir / f"{slide_path.stem}_roi_{output_index}.jpg", quality=95, subsampling=0)


if __name__ == "__main__":
    if len(sys.argv) != 4:
        raise SystemExit("Usage: python export_roi.py lame.svs annotations.geojson dossier_sortie")
    LEVEL = 0
    export_rois(Path(sys.argv[1]), Path(sys.argv[2]), Path(sys.argv[3]), level=LEVEL)
```

Exécutez-le ainsi:

```bash
python export_roi.py lames/lame_001.svs exports/lame_001.geojson exports/images
```

## Vérifier la sortie

Ouvrez chaque JPEG et comparez-le à l'annotation QuPath: le contour doit correspondre à la ROI et l'extérieur doit être blanc. Vérifiez la taille en pixels avant une figure de publication; le script ne redimensionne pas l'image au niveau choisi.

## Continuer

- [Exporter un TMA en GeoJSON]({{ site.baseurl }}{% post_url 2025-01-01-exporter_TMA-en-geosjon %})
- [Scripts QuPath utiles]({{ site.baseurl }}{% post_url 2025-01-01-Liste-Script_Qupath %})
