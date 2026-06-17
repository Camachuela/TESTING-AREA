---
layout: schuljahr
slug: cv_theme
schuljahr_unnumbered: true
schuljahr_label: "Freundebuch"
---

{% comment %} 1. Wir holen alle Kapitel und sortieren sie alphabetisch (A-Z) {% endcomment %}
{% assign sorted_chapters = site.chapters | sort: 'title' %}

{% comment %} 2. Wir spalten die große Liste in vier kleine, gefilterte Listen auf {% endcomment %}
{% assign students = sorted_chapters | where: "layout", "cvstudent" %}
{% assign teachers = sorted_chapters | where: "layout", "cvteacher" %}
{% assign beasts = sorted_chapters | where: "layout", "cvbeasts" %}
{% assign others = sorted_chapters | where: "layout", "cvother" %}


{% comment %} --- GRUPPE 1: SCHÜLER --- {% endcomment %}
{% if students.size > 0 %}
  <h3 style="margin-top: 2em; margin-bottom: 10px; border-bottom: 1px solid #ddd; padding-bottom: 5px; font-weight: normal; color: #666; text-transform: uppercase; font-size: 14px; letter-spacing: 1px;">Schülerschaft</h3>

  <div class="npc-gallery">
    {% for char in students %}
      {% assign card_color_class = "type-cvstudent" %}
      {% if char.house_slug and char.house_slug != '—' and char.house_slug != '-' and char.house_slug != '' %}
        {% assign card_color_class = "house-" | append: char.house_slug | downcase %}
      {% endif %}

      <a href="{{ site.baseurl }}{{ char.url }}" class="npc-card {{ card_color_class }}">
        <img src="{{ site.baseurl }}/assets/images/cvs/{{ char.token_img | default: 'pb-placeholder_Token.webp' }}" alt="{{ char.title }}">
        <span class="npc-name">{{ char.title }}</span>
      </a>
    {% endfor %}
  </div>
{% endif %}


{% comment %} --- GRUPPE 2: LEHRER & PERSONAL --- {% endcomment %}
{% if teachers.size > 0 %}
  <h3 style="margin-top: 3em; margin-bottom: 10px; border-bottom: 1px solid #ddd; padding-bottom: 5px; font-weight: normal; color: #666; text-transform: uppercase; font-size: 14px; letter-spacing: 1px;">Lehrkräfte & Hogwarts-Personal</h3>

  <div class="npc-gallery">
    {% for char in teachers %}
      <a href="{{ site.baseurl }}{{ char.url }}" class="npc-card type-cvteacher">
        <img src="{{ site.baseurl }}/assets/images/cvs/{{ char.token_img | default: 'pb-placeholder_Token.webp' }}" alt="{{ char.title }}">
        <span class="npc-name">{{ char.title }}</span>
      </a>
    {% endfor %}
  </div>
{% endif %}


{% comment %} --- GRUPPE 3: TIERWESEN --- {% endcomment %}
{% if beasts.size > 0 %}
  <h3 style="margin-top: 3em; margin-bottom: 10px; border-bottom: 1px solid #ddd; padding-bottom: 5px; font-weight: normal; color: #666; text-transform: uppercase; font-size: 14px; letter-spacing: 1px;">Kreaturen & Tierwesen</h3>

  <div class="npc-gallery">
    {% for char in beasts %}
      <a href="{{ site.baseurl }}{{ char.url }}" class="npc-card type-cvbeasts">
        <img src="{{ site.baseurl }}/assets/images/cvs/{{ char.token_img | default: 'pb-placeholder_Token.webp' }}" alt="{{ char.title }}">
        <span class="npc-name">{{ char.title }}</span>
      </a>
    {% endfor %}
  </div>
{% endif %}


{% comment %} --- GRUPPE 4: SONSTIGE --- {% endcomment %}
{% if others.size > 0 %}
  <h3 style="margin-top: 3em; margin-bottom: 10px; border-bottom: 1px solid #ddd; padding-bottom: 5px; font-weight: normal; color: #666; text-transform: uppercase; font-size: 14px; letter-spacing: 1px;">Sonstige Bekanntschaften</h3>

  <div class="npc-gallery">
    {% for char in others %}
      <a href="{{ site.baseurl }}{{ char.url }}" class="npc-card type-cvother">
        <img src="{{ site.baseurl }}/assets/images/cvs/{{ char.token_img | default: 'pb-placeholder_Token.webp' }}" alt="{{ char.title }}">
        <span class="npc-name">{{ char.title }}</span>
      </a>
    {% endfor %}
  </div>
{% endif %}

<style>
  /* Versteckt das automatische Text-Inhaltsverzeichnis nur auf dieser Seite */
  ul.toc-chapters-full {
      display: none !important;
  }
</style>
