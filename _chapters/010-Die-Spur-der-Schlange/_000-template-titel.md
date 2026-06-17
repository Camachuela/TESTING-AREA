---
title: 'Titel: Aliteration'
slug: eintrag-000
abstract: One Line Summary
date: 1950-09-01
---

<img src="assets/images/session_pic/Ella_S00_Diary_header.webp" alt="S00 Header">

---

**Samstag, der 30. August 1950, 21:50 Uhr, Im Schwarzen Kater, irgendwo in London**

---

Liebe Emma,

...

Deine Ella

---

**Haushaltsbuch**

Aktueller Stand: 01.09.1950

ALTER SALDO: <span style="text-decoration: underline; text-decoration-style: double;"> xxx Galeonen (G)</span>


| Datum | Betrag | Bezeichnung | Rechtfertigung |
| :--- | :--- | :--- | :--- |
| 01.09.1950 | - 12 G | Kauf: 2 Schokofrösche | Verpflegungsmehraufwand (Reisekosten) |


NEUER SALDO: <span style="text-decoration: underline; text-decoration-style: double;">xxx G</span>

—

_AUFSCHLÜSSELUNG_

-

---

**Nachtrag: 00:12 Uhr, 30./31. August 1950**


---

<img src="assets/images/session_pic/Ella_S00_Diary_full.webp" alt="S00 Full">


---


<style>
/* Tränenoptik */
  .strike-container {
    position: relative;
    display: inline-block;
  }

  /* Der verblurte Text */
  .blur-text {
    filter: blur(1.9px);
    display: inline-block;
  }

  /* Die scharfe Linie zum Durchstreichen */
  .strike-container::after {
    content: "";
    position: absolute;
    left: 0;
    top: 50%;
    width: 100%;
    height: 2px;
    background-color: currentColor; /* farbangepasst und scharf */
    z-index: 10;
    transform: rotate(-0.5deg); /* Ein Hauch von "manuell durchgestrichen" */
  }
</style>

<!-- --- Lesezeichen & Bleistift-Fortschrittsbalken --- -->
<style>
  /* 1. Der Fortschrittsbalken am unteren Rand */
    .progress-container {
      position: fixed;
      bottom: 5px;

      /* Left und Width werden jetzt dynamisch per JavaScript gesetzt! */

      height: 12px;
      z-index: 9999;
      pointer-events: none;

      /* Design */
      background: rgba(128, 128, 128, 0.15);
      backdrop-filter: blur(6px);
      -webkit-backdrop-filter: blur(6px);
      color: currentColor;
      border: 2px solid currentColor;
      border-radius: 255px 25px 225px 25px/25px 225px 25px 255px;
      box-shadow: 4px 6px 15px rgba(0, 0, 0, 0.15);
      overflow: hidden;
    }

  .progress-bar {
    height: 100%;
    width: 0%;
    background-color: currentColor;
    opacity: 0.85;
    transition: width 0.1s ease-out;
  }

  /* 2. Die runden Lesezeichen-Buttons rechts am Rand */
  .bookmark-widget {
    position: fixed;
    bottom: 20px;
    right: 10px;
    z-index: 1000;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .bookmark-widget .btn {
    width: 45px;
    height: 45px;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;

    /* Der Milchglas-Effekt (Frosted Glass) */
    background-color: rgba(128, 128, 128, 0.15);
    backdrop-filter: blur(6px);
    -webkit-backdrop-filter: blur(6px);

    /* Passt sich vollautomatisch der Schriftfarbe des aktuellen Themes an */
    color: currentColor;
    border: 2px solid currentColor;

    border-radius: 50%;
    cursor: pointer;
    font-size: 20px;
    box-shadow: 2px 2px 5px rgba(0,0,0,0.1);
  }

  .bookmark-widget .btn:hover {
    background-color: rgba(128, 128, 128, 0.3); /* Wird beim Antippen minimal sichtbarer */
  }
</style>

<div class="progress-container">
  <div class="progress-bar" id="myBar"></div>
</div>

<div id="bookmark-container" class="bookmark-widget">
  <button id="save-bookmark" class="btn" title="Lesezeichen setzen">🔖</button>
  <button id="load-bookmark" class="btn" style="display: none;" title="Zum Lesezeichen springen">📖</button>
</div>

<!-- Die Logik für Balken und Speichern -->
<script>
document.addEventListener("DOMContentLoaded", function() {

  // --- A. Lesezeichen-Logik ---
  const saveBtn = document.getElementById("save-bookmark");
  const loadBtn = document.getElementById("load-bookmark");

  // Generiert für jedes Kapitel einen eigenen Schlüssel
  const pageKey = "bookmark-" + window.location.pathname;

  // Prüft, ob es für dieses Kapitel schon ein Lesezeichen gibt
  const savedPosition = localStorage.getItem(pageKey);
  if (savedPosition) {
    loadBtn.style.display = "inline-block";
  }

  // Was passiert beim Speichern
  saveBtn.addEventListener("click", function() {
    localStorage.setItem(pageKey, window.scrollY);
    alert('„Dein Lesezeichen wurde erfolgreich gespeichert!“');
    loadBtn.style.display = "inline-block";
  });

  // Was passiert beim Laden
  loadBtn.addEventListener("click", function() {
    window.scrollTo({
      top: parseInt(localStorage.getItem(pageKey), 10),
      behavior: "smooth"
    });
  });

  // --- B. Fortschrittsbalken-Logik ---
  window.addEventListener('scroll', function() {
    let winScroll = document.body.scrollTop || document.documentElement.scrollTop;
    let height = document.documentElement.scrollHeight - document.documentElement.clientHeight;

    // Berechnet die Prozente
    let scrolled = (winScroll / height) * 100;

    // Verhindert, dass der Balken über den Rand hinauswächst (z.B. bei Handys)
    if (scrolled > 100) scrolled = 100;
    if (scrolled < 0) scrolled = 0;

    // Zeichnet den Balken
    document.getElementById("myBar").style.width = scrolled + "%";
  });
  // --- C. Fortschrittsbalken exakt an die Textbox anpassen ---
  // HIER BITTE DEN KLASSENNAMEN DEINER TEXTBOX EINTRAGEN (z.B. .content oder .story-container)
  const textBox = document.querySelector('.markdown-section');
  const progressContainer = document.querySelector('.progress-container');

  function matchProgressToTextBox() {
    if (textBox && progressContainer) {
      const rect = textBox.getBoundingClientRect();

      // Setzt die Position und Breite des Balkens exakt auf die Werte der Textbox
      progressContainer.style.left = rect.left + 'px';
      progressContainer.style.width = rect.width + 'px';
    }
  }

  // Beim Laden, beim Scrollen und bei Größenänderung des Fensters anpassen
  matchProgressToTextBox();
  window.addEventListener('resize', matchProgressToTextBox);
  window.addEventListener('scroll', matchProgressToTextBox);
});
</script>
