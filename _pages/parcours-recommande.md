---
permalink: /parcours-recommande/
title: "Parcours recommandé"
layout: single
classes: wide
---

{% include guide-fallback.html %}

<div class="guide-page">
  <p class="guide-kicker">Le parcours complet</p>
  <p class="guide-page__intro">Suivez l'ordre ci-dessous. Ne passez à l'étape suivante que lorsque la vérification indiquée dans l'article précédent est réussie.</p>

  <h2>1. Préparer QuPath</h2>
  <div class="guide-list">
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-Installation-de-QuPath %}"><strong>Installer QuPath</strong><span>Télécharger la version finale 0.7 et vérifier l'ouverture.</span></a>
    <a href="{{ site.baseurl }}{% post_url 2026-02-19-qupath-creer-projet-standard %}"><strong>Créer un projet</strong><span>Choisir un dossier projet et une convention de nommage.</span></a>
    <a href="{{ site.baseurl }}{% post_url 2026-02-19-qupath-importer-wsi %}"><strong>Importer une lame</strong><span>Contrôler le format et la taille de pixel.</span></a>
    <a href="{{ site.baseurl }}{% post_url 2026-02-19-qupath-annotations-fondamentaux %}"><strong>Créer des annotations</strong><span>Définir les zones réellement utiles à l'analyse.</span></a>
  </div>

  <h2>2. Analyser les cellules</h2>
  <div class="guide-list">
    <a href="{{ site.baseurl }}{% post_url 2026-02-19-qupath-classes-objet %}"><strong>Organiser les classes</strong><span>Éviter les noms de classes incohérents avant la détection.</span></a>
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-InstaSeg %}"><strong>Segmenter avec InstanSeg</strong><span>Tester une annotation, puis appliquer le réglage validé.</span></a>
  </div>

  <h2>3. Exporter et reproduire</h2>
  <div class="guide-list">
    <a href="{{ site.baseurl }}{% post_url 2026-02-19-qupath-mesures-export-csv %}"><strong>Exporter les mesures</strong><span>Obtenir un CSV lisible et traçable.</span></a>
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-Liste-Script_Qupath %}"><strong>Conserver un script</strong><span>Rejouer les tâches répétitives sous QuPath 0.7.</span></a>
    <a href="{{ site.baseurl }}{% post_url 2025-01-01-sauvegarde-image %}"><strong>Préparer une image</strong><span>Créer une sortie propre pour une publication ou un rapport.</span></a>
  </div>
</div>
