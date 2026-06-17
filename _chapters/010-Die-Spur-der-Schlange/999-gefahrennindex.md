---
title: Gefahrenstufen-Index
slug: threatlevel
abstract:
---

Damit ich nicht den Überblick verliere und genau weiß, bei wem ich aufpassen muss, habe ich diese Farbskala festgelegt. Es geht darum, wie sicher ich mich bei jemandem fühlen kann oder ob ich meine Abwehr hochfahren muss.

<br>

Farblegende:

  <span class="house-name gryffindor">Gryffindor</span>, <span class="house-name hufflepuff"> Hufflepuff</span>, <span class="house-name ravenclaw"> Ravenclaw</span>, <span class="house-name slytherin"> Slytherin</span>, <span class="house-name hogwarts"> Lehrkräfte & Hogwarts-Personal</span>, <span class="house-name other"> Sonstige Bekanntschaften</span>, <span class="house-name beasts"> Kreaturen & Tierwesen</span>

  <style>
    /* Gemeinsamer Halo-Effekt für alle Namen */
    .house-name {
      font-weight: bold;
      /* Ein leichter Glow: 0px Versatz, 8px Unschärfe */
      text-shadow: 0 0 8px rgba(255, 255, 255, 0.2);
    }
    .slytherin {
      color: #2E8B57; /* Grün */
      text-shadow: 0 0 10px rgba(46, 204, 113, 0.5);
    }
    .ravenclaw {
      color: #0D85D8; /* Blau */
      text-shadow: 0 0 10px rgba(52, 152, 219, 0.5);
    }
      .hufflepuff {
      color: #f1c40f; /* Gelb */
      text-shadow: 0 0 10px rgba(241, 196, 15, 0.5);
    }
      .gryffindor {
      color: #A91101; /* Rot */
      text-shadow: 0 0 10px rgba(231, 76, 60, 0.5);
    }
    .other {
      color: #000000;
      text-shadow: 0 0 10px rgba(220, 220, 220, 0.3);
    }
    .beasts {
      color: #74597f;
      text-shadow: 0 0 10px rgba(220, 220, 220, 0.3);
    }
    .hogwarts {
      color: #814d52;
      text-shadow: 0 0 10px rgba(220, 220, 220, 0.3);
    }
  </style>

<div class="danger-board">
  {% comment %} Alle Charaktere alphabetisch holen {% endcomment %}
  {% assign all_chars = site.chapters | sort: 'title' %}

  {% comment %} --- SPALTE 1: GRÜN --- {% endcomment %}
  <div class="danger-column">
    <h4 class="danger-header-gruen">sicher</h4>
    {% for char in all_chars %}
      {% if char.estimate_danger == 'grün' or char.estimate_danger == 'Grün' %}

        {% comment %} Haus-Klasse ermitteln (genau wie bei der Galerie) {% endcomment %}
        {% assign house_class = "other" %}
        {% if char.house_slug and char.house_slug != '—' and char.house_slug != '-' and char.house_slug != '' %}
          {% assign house_class = char.house_slug | downcase %}
        {% endif %}

        <div class="danger-entry">
          <span class="house-name {{ house_class }}">{{ char.title }}</span>
        </div>
      {% endif %}
    {% endfor %}
  </div>

  {% comment %} --- SPALTE 2: WEIß --- {% endcomment %}
  <div class="danger-column">
    <h4 class="danger-header-weiss">neutral</h4>
    {% for char in all_chars %}
      {% if char.estimate_danger == 'weiß' or char.estimate_danger == 'Weiß' %}
        {% assign house_class = "other" %}
        {% if char.house_slug and char.house_slug != '—' and char.house_slug != '-' and char.house_slug != '' %}
          {% assign house_class = char.house_slug | downcase %}
        {% endif %}
        <div class="danger-entry">
          <span class="house-name {{ house_class }}">{{ char.title }}</span>
        </div>
      {% endif %}
    {% endfor %}
  </div>

  {% comment %} --- SPALTE 3: GELB --- {% endcomment %}
  <div class="danger-column">
    <h4 class="danger-header-gelb">Warnung</h4>
    {% for char in all_chars %}
      {% if char.estimate_danger == 'gelb' or char.estimate_danger == 'Gelb' %}
        {% assign house_class = "other" %}
        {% if char.house_slug and char.house_slug != '—' and char.house_slug != '-' and char.house_slug != '' %}
          {% assign house_class = char.house_slug | downcase %}
        {% endif %}
        <div class="danger-entry">
          <span class="house-name {{ house_class }}">{{ char.title }}</span>
        </div>
      {% endif %}
    {% endfor %}
  </div>

  {% comment %} --- SPALTE 4: ORANGE --- {% endcomment %}
  <div class="danger-column">
    <h4 class="danger-header-orange">Gefahr</h4>
    {% for char in all_chars %}
      {% if char.estimate_danger == 'orange' or char.estimate_danger == 'Orange' %}
        {% assign house_class = "other" %}
        {% if char.house_slug and char.house_slug != '—' and char.house_slug != '-' and char.house_slug != '' %}
          {% assign house_class = char.house_slug | downcase %}
        {% endif %}
        <div class="danger-entry">
          <span class="house-name {{ house_class }}">{{ char.title }}</span>
        </div>
      {% endif %}
    {% endfor %}
  </div>

  {% comment %} --- SPALTE 5: ROT --- {% endcomment %}
  <div class="danger-column">
    <h4 class="danger-header-rot">Bedrohung</h4>
    {% for char in all_chars %}
      {% if char.estimate_danger == 'rot' or char.estimate_danger == 'Rot' %}
        {% assign house_class = "other" %}
        {% if char.house_slug and char.house_slug != '—' and char.house_slug != '-' and char.house_slug != '' %}
          {% assign house_class = char.house_slug | downcase %}
        {% endif %}
        <div class="danger-entry">
          <span class="house-name {{ house_class }}">{{ char.title }}</span>
        </div>
      {% endif %}
    {% endfor %}
  </div>

</div>

<br>

Aktueller Stand: 03.09.1950
<br>

- <span style="color: #4caf50; font-weight: bold;">sicher</span>
  - Personen, die berechenbar sind. Sie halten sich an Regeln, tun, was sie sagen, und lassen mich in Ruhe. Bei ihnen ist es am entspanntesten.

<br>

- <span style="color: #ccc; font-weight: bold;">neutral</span>
  - Die große Masse. Leute, die einfach da sind, aber keinen Einfluss auf mich haben. Sie sind wie Statisten im Hintergrund.

<br>

- <span style="color: #ffeb3b; font-weight: bold;">Warnung</span>
  - Hier schrillen die ersten Alarmglocken. Es muss nichts Bestimmtes sein, nur so ein Gefühl, dass irgendwas an der Person nicht stimmt oder nicht zusammenpasst. Wenn mein Instinkt sagt „Vorsicht“, kommen sie hierhin – egal, wie sie sich verhalten.

<br>

- <span style="color: #ff9800; font-weight: bold;">Gefahr</span>
  - Personen, die offensichtlich Ärger suchen, lügen oder unberechenbar sind. Bei denen halte ich den Mund fest geschlossen und die Augen weit offen. Volle Verteidigungshaltung.

  <br>

- <span style="color: #f44336; font-weight: bold;">Bedrohung</span>
  - Personen, die aktiv versuchen, mich fertigzumachen. Wer hier landet, für den existiere ich nicht mehr. Ich werde kein Wort mehr mit ihnen wechseln, außer es geht um Leben und Tod.

<br>
