---
title: "Automatiser et exporter"
permalink: /automatiser/
layout: single
classes: wide
---

{% include guide-fallback.html %}

<div class="guide-page">
  <p class="guide-kicker">Scripts et sorties</p>
  <p class="guide-page__intro">Ces tutoriels servent quand la manipulation fonctionne déjà sur une lame. Gardez les scripts avec votre projet afin de pouvoir refaire exactement la même analyse.</p>

  <div class="guide-list">
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-Liste-Script_Qupath %}">
      <strong>Scripts Groovy QuPath</strong>
      <span>Exporter des annotations, convertir des objets et définir une calibration.</span>
    </a>
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-exporter_TMA-en-geosjon %}">
      <strong>Exporter une TMA en GeoJSON</strong>
      <span>Transformer une grille TMA en annotations puis l'exporter.</span>
    </a>
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-sauvegarde-image %}">
      <strong>Préparer une image pour publication</strong>
      <span>Exporter une ROI et produire une image à partir d'un GeoJSON.</span>
    </a>
    <a href="{{ site.baseurl }}{% post_url 2026-02-19-perf-cuda-installation %}">
      <strong>Activer CUDA, si nécessaire</strong>
      <span>Uniquement pour accélérer les extensions de deep learning sur GPU NVIDIA.</span>
    </a>
  </div>
</div>
