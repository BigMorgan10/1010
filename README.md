<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Big M 모건 — Univers Interactif</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&display=swap');

  /* Reset */
  * { margin:0; padding:0; box-sizing: border-box; }
  body, html {
    width: 100%; height: 100%;
    font-family: 'Orbitron', sans-serif;
    background: radial-gradient(circle at center, #0f0c29 0%, #24243e 70%);
    color: #00fff7;
    overflow: hidden;
  }

  /* ----------------- Intro ----------------- */
  #introScreen {
    position: fixed; top:0; left:0; right:0; bottom:0;
    background: radial-gradient(circle at center, #12131b, #0a0a12);
    display: flex; flex-direction: column; justify-content: center; align-items: center;
    gap: 2rem; z-index: 9999; text-align: center; padding: 1rem;
  }
  #introScreen h1 {
    font-size: 4rem;
    text-shadow: 0 0 30px #00fff7;
    user-select: none;
    animation: glowPulse 2.5s ease-in-out infinite;
  }
  #introScreen label {
    font-size: 1.5rem;
    user-select: none;
  }
  #languageSelect {
    font-size: 1.5rem;
    padding: 1rem 2rem;
    border-radius: 15px;
    border: 2px solid #00fff7;
    background: transparent;
    color: #00fff7;
    cursor: pointer;
    outline: none;
    box-shadow: 0 0 15px rgba(0,255,247,0.6);
    user-select: none;
    transition: background 0.3s ease;
  }
  #languageSelect:hover {
    background: #00fff7;
    color: #12131b;
  }
  #enterButton {
    margin-top: 1.5rem;
    padding: 1.2rem 3rem;
    border-radius: 25px;
    background: linear-gradient(135deg, #111, #222);
    border: 2px solid #00fff7;
    color: #00fff7;
    font-weight: 700;
    font-size: 1.4rem;
    cursor: pointer;
    box-shadow: 0 0 25px #00fff7;
    transition: all 0.3s ease;
    user-select: none;
  }
  #enterButton:hover {
    background: #00fff7;
    color: #12131b;
    transform: scale(1.1);
    box-shadow: 0 0 40px #00fff7;
  }

  /* Glow pulse animation */
  @keyframes glowPulse {
    0%, 100% { text-shadow: 0 0 15px #00fff7; }
    50% { text-shadow: 0 0 35px #00fff7; }
  }

  /* ----------------- App Container ----------------- */
  #appContainer {
    display: none;
    padding: 2rem 1rem 4rem 1rem;
    min-height: 100vh;
    background: radial-gradient(circle at center, #0f0c29 0%, #24243e 70%);
    color: #00fff7;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    overflow-x: hidden;
  }

  /* ----------------- Navbar ----------------- */
  nav.navbar {
    position: fixed;
    top: 0; left: 0; right: 0;
    height: 70px;
    background: #0b0c10dd;
    backdrop-filter: blur(8px);
    border-bottom: 2px solid #00fff7;
    display: flex;
    align-items: center;
    padding: 0 1.5rem;
    gap: 1rem;
    z-index: 1000;
  }
  .navbar .profile-img {
    width: 48px; height: 48px;
    border-radius: 50%;
    border: 3px solid #00fff7;
    object-fit: cover;
    box-shadow: 0 0 15px #00fff7;
    transition: transform 0.4s ease;
    cursor: pointer;
  }
  /* Parallax-like hover effect */
  .navbar .profile-img:hover {
    transform: scale(1.15) rotate(10deg);
  }
  .navbar .title {
    font-size: 1.5rem;
    font-weight: 700;
    flex-grow: 1;
    user-select: none;
    text-shadow: 0 0 12px #00fff7;
  }
  .navbar button.back-button {
    background: transparent;
    border: 2px solid #00fff7;
    border-radius: 12px;
    padding: 0.5rem 1.2rem;
    color: #00fff7;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 0 10px #00fff7;
  }
  .navbar button.back-button:hover {
    background: #00fff7;
    color: #12131b;
    box-shadow: 0 0 30px #00fff7;
    transform: scale(1.1);
  }
  .navbar button.back-button.pulse {
    animation: pulseGlow 2.5s infinite;
  }
  @keyframes pulseGlow {
    0%, 100% { box-shadow: 0 0 10px #00fff7; }
    50% { box-shadow: 0 0 30px #00fff7; }
  }

  /* ----------------- Main Menu ----------------- */
  main#main-menu {
    max-width: 640px;
    width: 100%;
    margin-top: 90px;
    text-align: center;
    user-select: none;
  }
  #main-menu .link-button {
    display: block;
    margin: 1rem auto;
    padding: 1.5rem 3rem;
    background: linear-gradient(135deg, #111, #222);
    border: 2px solid #00fff7;
    border-radius: 20px;
    color: #00fff7;
    font-weight: 800;
    font-size: 1.4rem;
    text-decoration: none;
    cursor: pointer;
    box-shadow: 0 0 20px rgba(0,255,247,0.5);
    transition: all 0.35s ease;
    max-width: 360px;
    user-select: none;
  }
  #main-menu .link-button:hover {
    background: #00fff7;
    color: #12131b;
    box-shadow: 0 0 45px #00fff7;
    transform: scale(1.1);
  }

  /* Cascade animation for main buttons */
  #main-menu .link-button {
    opacity: 0;
    transform: translateY(40px);
    animation-fill-mode: forwards;
  }
  #main-menu .link-button:nth-child(1) { animation: slideFadeIn 0.6s 0.2s ease forwards; }
  #main-menu .link-button:nth-child(2) { animation: slideFadeIn 0.6s 0.4s ease forwards; }
  #main-menu .link-button:nth-child(3) { animation: slideFadeIn 0.6s 0.6s ease forwards; }
  #main-menu .link-button:nth-child(4) { animation: slideFadeIn 0.6s 0.8s ease forwards; }
  #main-menu .link-button:nth-child(5) { animation: slideFadeIn 0.6s 1s ease forwards; }

  @keyframes slideFadeIn {
    to { opacity: 1; transform: translateY(0); }
  }

  /* ----------------- Menu Sections ----------------- */
  section.menu-section {
    display: none;
    background: #12131bdd;
    border-radius: 25px;
    padding: 2rem 3rem;
    box-shadow: 0 0 55px #00fff7bb;
    position: relative;
    min-height: 280px;
    color: #00fff7;
    user-select: text;
    animation: fadeInSlide 0.5s ease forwards;
    max-width: 640px;
    margin-top: 90px;
  }
  section.menu-section.active {
    display: block;
  }

  section.menu-section h2 {
    margin-bottom: 1.2rem;
    font-size: 2.4rem;
    text-shadow: 0 0 15px #00fff7;
  }
  section.menu-section a, section.menu-section p {
    color: #00fff7;
    font-size: 1.2rem;
    margin: 1.2rem 0;
    text-decoration: none;
    display: block;
    user-select: text;
    transition: color 0.3s ease;
  }
  section.menu-section a:hover {
    color: #00ddd7;
    text-decoration: underline;
  }

  /* Cinematic text animation */
  .cinematic-text {
    font-size: 1.3rem;
    font-style: italic;
    opacity: 0;
    animation: cinematicFadeIn 2.8s ease forwards;
    max-width: 550px;
    margin: 1.5rem auto 0 auto;
    color: #00fff7cc;
    text-shadow: 0 0 20px #00fff7aa;
  }
  @keyframes cinematicFadeIn {
    to { opacity: 1; }
  }

  /* Background subtle animation on menu */
  @keyframes bgPulse {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
  }
  section.menu-section:nth-child(odd) {
    background: linear-gradient(270deg, #12131b, #1f2237, #12131b);
    background-size: 400% 400%;
    animation: bgPulse 10s ease infinite;
  }
  section.menu-section:nth-child(even) {
    background: linear-gradient(270deg, #12131b, #24243e, #12131b);
    background-size: 400% 400%;
    animation: bgPulse 15s ease infinite;
  }

</style>
</head>
<body>

  <!-- Intro plein écran -->
  <div id="introScreen" role="dialog" aria-modal="true" aria-labelledby="introTitle" aria-describedby="introDesc">
    <h1 id="introTitle">Bienvenue dans mon univers</h1>
    <label for="languageSelect">Choisis ta langue / Choose your language :</label>
    <select id="languageSelect" aria-describedby="languageDesc">
      <option value="fr">Français 🇫🇷</option>
      <option value="en">English 🇬🇧</option>
    </select>
    <button id="enterButton" aria-label="Entrer dans le site">Entrer</button>
  </div>

  <!-- App principal -->
  <div id="appContainer" aria-live="polite" aria-atomic="true">
    <nav class="navbar" aria-label="Barre de navigation principale">
      <img src="https://i.imgur.com/7q0kM6f.jpg" alt="Photo de profil Morgan" class="profile-img" />
      <div class="title">🌌 Big M 모건</div>
      <button class="back-button pulse" id="backButton" aria-label="Retour au menu principal" style="display:none;">← Retour</button>
    </nav>

    <main id="main-menu" aria-label="Menu principal des liens">
      <button class="link-button" data-menu="instagram" aria-haspopup="true" aria-controls="menu-instagram">📸 Instagram</button>
      <button class="link-button" data-menu="youtube" aria-haspopup="true" aria-controls="menu-youtube">▶️ YouTube</button>
      <button class="link-button" data-menu="mail" aria-haspopup="true" aria-controls="menu-mail">✉️ Email</button>
      <button class="link-button" data-menu="phone" aria-haspopup="true" aria-controls="menu-phone">📞 Téléphone</button>
      <button class="link-button" data-menu="twitter" aria-haspopup="true" aria-controls="menu-twitter">🐦 Twitter</button>
    </main>

    <!-- Menus individuels -->
    <section id="menu-instagram" class="menu-section" role="region" aria-label="Menu Instagram">
      <h2>Instagram</h2>
      <p>Rejoins-moi sur Instagram pour découvrir mes dernières créations et moments forts.</p>
      <a href="https://instagram.com/i_am_24carrats_morgan" target="_blank" rel="noopener noreferrer" tabindex="0">Visiter Instagram</a>
      <p class="cinematic-text">“Là où les pixels brillent comme des diamants...”</p>
    </section>

    <section id="menu-youtube" class="menu-section" role="region" aria-label="Menu YouTube">
      <h2>YouTube</h2>
      <p>Regarde mes vidéos, vlogs et performances exclusives sur ma chaîne YouTube.</p>
      <a href="https://youtube.com/@johnnymorgan" target="_blank" rel="noopener noreferrer" tabindex="0">Voir YouTube</a>
      <p class="cinematic-text">“Chaque vidéo est une porte vers un autre univers...”</p>
    </section>

    <section id="menu-mail" class="menu-section" role="region" aria-label="Menu Email">
      <h2>Email</h2>
      <p>Pour toute collaboration ou question, envoie-moi un mail.</p>
      <a href="mailto:24carratsmorgan@gmail.com" tabindex="0">Envoyer un email</a>
      <p class="cinematic-text">“Les mots écrits sont des ponts entre les âmes.”</p>
    </section>

    <section id="menu-phone" class="menu-section" role="region" aria-label="Menu Téléphone">
      <h2>Téléphone</h2>
      <p>Tu préfères une conversation directe ? Voici mon numéro.</p>
      <a href="tel:+242061098011" tabindex="0">Appeler Morgan</a>
      <p class="cinematic-text">“La voix humaine, l’onde la plus vraie.”</p>
    </section>

    <section id="menu-twitter" class="menu-section" role="region" aria-label="Menu Twitter">
      <h2>Twitter</h2>
      <p>Pour suivre mes pensées et actualités instantanées.</p>
      <a href="https://twitter.com/24morgan" target="_blank" rel="noopener noreferrer" tabindex="0">Voir Twitter</a>
      <p class="cinematic-text">“140 caractères pour illuminer la toile.”</p>
    </section>
  </div>

  <script>
    const introScreen = document.getElementById('introScreen');
    const enterButton = document.getElementById('enterButton');
    const languageSelect = document.getElementById('languageSelect');
    const appContainer = document.getElementById('appContainer');
    const mainMenu = document.getElementById('main-menu');
    const menuSections = document.querySelectorAll('.menu-section');
    const backButton = document.getElementById('backButton');

    // Textes traduits
    const translations = {
      fr: {
        welcome: "Bienvenue dans mon univers",
        chooseLang: "Choisis ta langue :",
        enter: "Entrer",
        navTitle: "🌌 Big M 모건",
        back: "← Retour",
        menus: {
          instagram: {
            title: "Instagram",
            desc: "Rejoins-moi sur Instagram pour découvrir mes dernières créations et moments forts.",
            linkText: "Visiter Instagram",
            cinematic: "“Là où les pixels brillent comme des diamants...”"
          },
          youtube: {
            title: "YouTube",
            desc: "Regarde mes vidéos, vlogs et performances exclusives sur ma chaîne YouTube.",
            linkText: "Voir YouTube",
            cinematic: "“Chaque vidéo est une porte vers un autre univers...”"
          },
          mail: {
            title: "Email",
            desc: "Pour toute collaboration ou question, envoie-moi un mail.",
            linkText: "Envoyer un email",
            cinematic: "“Les mots écrits sont des ponts entre les âmes.”"
          },
          phone: {
            title: "Téléphone",
            desc: "Tu préfères une conversation directe ? Voici mon numéro.",
            linkText: "Appeler Morgan",
            cinematic: "“La voix humaine, l’onde la plus vraie.”"
          },
          twitter: {
            title: "Twitter",
            desc: "Pour suivre mes pensées et actualités instantanées.",
            linkText: "Voir Twitter",
            cinematic: "“140 caractères pour illuminer la toile.”"
          }
        }
      },
      en: {
        welcome: "Welcome to my universe",
        chooseLang: "Choose your language:",
        enter: "Enter",
        navTitle: "🌌 Big M 모건",
        back: "← Back",
        menus: {
          instagram: {
            title: "Instagram",
            desc: "Join me on Instagram to discover my latest creations and highlights.",
            linkText: "Visit Instagram",
            cinematic: "“Where pixels shine like diamonds...”"
          },
          youtube: {
            title: "YouTube",
            desc: "Watch my videos, vlogs and exclusive performances on my YouTube channel.",
            linkText: "Watch YouTube",
            cinematic: "“Each video is a door to another universe...”"
          },
          mail: {
            title: "Email",
            desc: "For any collaboration or questions, send me an email.",
            linkText: "Send an email",
            cinematic: "“Written words are bridges between souls.”"
          },
          phone: {
            title: "Phone",
            desc: "Prefer a direct conversation? Here's my number.",
            linkText: "Call Morgan",
            cinematic: "“The human voice, the truest wave.”"
          },
          twitter: {
            title: "Twitter",
            desc: "Follow my thoughts and instant updates.",
            linkText: "See Twitter",
            cinematic: "“140 characters to light up the web.”"
          }
        }
      }
    };

    // Charge la langue enregistrée
    function getSavedLang() {
      return localStorage.getItem('lang') || 'fr';
    }
    function saveLang(lang) {
      localStorage.setItem('lang', lang);
    }

    // Met à jour tous les textes selon la langue choisie
    function updateTexts(lang) {
      const t = translations[lang];
      document.getElementById('introTitle').textContent = t.welcome;
      document.querySelector('#introScreen label').textContent = t.chooseLang;
      enterButton.textContent = t.enter;
      document.querySelector('.navbar .title').textContent = t.navTitle;
      backButton.textContent = t.back;

      // Met à jour chaque section
      for (const key in t.menus) {
        const section = document.getElementById('menu-' + key);
        if (section) {
          section.querySelector('h2').textContent = t.menus[key].title;
          section.querySelector('p').textContent = t.menus[key].desc;
          const link = section.querySelector('a');
          link.textContent = t.menus[key].linkText;
          section.querySelector('.cinematic-text').textContent = t.menus[key].cinematic;
        }
      }
    }

    // Affiche l'app, cache l'intro
    function showApp() {
      introScreen.style.display = 'none';
      appContainer.style.display = 'flex';
    }

    // Ouvre un menu individuel
    function openMenu(menuId) {
      mainMenu.style.display = 'none';
      menuSections.forEach(section => {
        if(section.id === menuId){
          section.classList.add('active');
          section.style.display = 'block';
        } else {
          section.classList.remove('active');
          section.style.display = 'none';
        }
      });
      backButton.style.display = 'inline-block';
      backButton.focus();
    }

    // Ferme le menu individuel pour revenir au principal
    function closeMenu() {
      menuSections.forEach(section => {
        section.classList.remove('active');
        section.style.display = 'none';
      });
      mainMenu.style.display = 'block';
      backButton.style.display = 'none';
      mainMenu.querySelector('button').focus();
    }

    // Événements
    enterButton.addEventListener('click', () => {
      const lang = languageSelect.value;
      saveLang(lang);
      updateTexts(lang);
      showApp();
    });

    // Si la langue est déjà sauvegardée, saute l'intro
    window.addEventListener('load', () => {
      const lang = getSavedLang();
      languageSelect.value = lang;
      updateTexts(lang);
      showApp();
    });

    // Gestion boutons menu principal
    mainMenu.querySelectorAll('button').forEach(btn => {
      btn.addEventListener('click', () => {
        openMenu('menu-' + btn.dataset.menu);
      });
    });

    // Bouton retour
    backButton.addEventListener('click', closeMenu);

    // Touche Echap pour revenir en arrière
    document.addEventListener('keydown', e => {
      if(e.key === 'Escape' && backButton.style.display === 'inline-block') {
        closeMenu();
      }
    });
  </script>
</body>
</html>
