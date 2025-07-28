<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Big M 모건 — Univers Infini</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&display=swap" rel="stylesheet" />
<style>
  /* Reset & base */
  * {
    margin: 0; padding: 0; box-sizing: border-box;
    font-family: 'Orbitron', sans-serif;
  }
  html, body {
    height: 100%;
    background: radial-gradient(circle at center, #0f0c29, #24243e);
    color: #00fff7;
    overflow-x: hidden;
  }
  body.dark-mode {
    background: radial-gradient(circle at center, #01010a, #121125);
    color: #0ff;
  }
  /* Galaxy background & rotation */
  #galaxy-bg {
    position: fixed; top: 0; left: 0;
    width: 100vw; height: 100vh;
    background: url('https://images.unsplash.com/photo-1470770903676-69b98201ea1c?auto=format&fit=crop&w=1950&q=80') no-repeat center center;
    background-size: cover;
    filter: brightness(0.6);
    animation: spinGalaxy 300s linear infinite;
    z-index: -10;
  }
  @keyframes spinGalaxy {
    from {transform: rotate(0deg);}
    to {transform: rotate(360deg);}
  }
  /* Container styling */
  .container {
    max-width: 900px;
    margin: 4rem auto 2rem;
    padding: 2rem;
    background: rgba(15,12,41,0.7);
    border-radius: 20px;
    box-shadow: 0 0 40px #00fff7;
    text-align: center;
  }
  h1 {
    font-size: 3rem;
    text-shadow: 0 0 25px #00fff7;
    margin-bottom: 0.5rem;
    letter-spacing: 3px;
    user-select: none;
  }
  h2 {
    margin-bottom: 1rem;
  }
  .welcome-msg {
    font-style: italic;
    color: #aaa;
    margin-bottom: 2rem;
    text-shadow: 0 0 12px #00fff7aa;
  }
  p {
    font-size: 1.1rem;
    line-height: 1.5;
  }
  a.link-btn {
    display: block;
    margin: 0.5rem auto;
    padding: 1rem 1.5rem;
    max-width: 350px;
    background: #000a;
    border: 2px solid #00fff7;
    border-radius: 15px;
    color: #00fff7;
    text-decoration: none;
    font-weight: 700;
    letter-spacing: 1.5px;
    font-size: 1.1rem;
    transition: all 0.3s ease;
    user-select: none;
  }
  a.link-btn:hover {
    background: #00fff7;
    color: #111;
    transform: translateY(-5px);
    box-shadow: 0 0 30px #00fff7;
  }
  /* Tabs navigation */
  .tabs {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 2rem;
    user-select: none;
  }
  .tab {
    padding: 0.8rem 2rem;
    cursor: pointer;
    background: linear-gradient(135deg, #111, #222);
    border: 2px solid #00fff7;
    border-radius: 15px;
    color: #00fff7;
    font-weight: 700;
    transition: all 0.3s ease;
    letter-spacing: 1px;
    text-transform: uppercase;
    font-size: 1rem;
  }
  .tab:hover:not(.active) {
    background: #00fff7;
    color: #111;
    transform: scale(1.1);
    box-shadow: 0 0 25px #00fff7;
  }
  .tab.active {
    background: #00fff7;
    color: #111;
    box-shadow: 0 0 30px #00fff7;
    transform: scale(1.15);
    cursor: default;
  }
  /* Sections */
  .content-section {
    display: none;
    background: linear-gradient(135deg, #111, #222);
    border-radius: 20px;
    padding: 2rem;
    box-shadow: 0 0 40px #00fff7bb;
    max-width: 600px;
    margin: 0 auto;
    text-align: left;
    color: #00fff7;
    font-size: 1rem;
  }
  .content-section.active {
    display: block;
    animation: fadeInUp 1s ease forwards;
  }
  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  /* Admin Panel */
  #admin-panel {
    margin-top: 2rem;
    padding: 1rem;
    background: rgba(0,0,0,0.7);
    border-radius: 15px;
    box-shadow: 0 0 25px #00fff7;
    display: none;
    max-width: 600px;
    color: #00fff7;
    user-select: text;
  }
  #admin-panel h2 {
    margin-bottom: 1rem;
    font-weight: 700;
    font-size: 1.5rem;
    text-align: center;
  }
  #admin-panel textarea {
    width: 100%;
    height: 120px;
    border-radius: 10px;
    border: none;
    background: #111;
    color: #00fff7;
    font-family: 'Orbitron', sans-serif;
    font-size: 1rem;
    padding: 1rem;
    resize: vertical;
  }
  #admin-panel button {
    margin-top: 1rem;
    padding: 0.7rem 1.5rem;
    border-radius: 15px;
    border: 2px solid #00fff7;
    background: linear-gradient(135deg, #111, #222);
    color: #00fff7;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  #admin-panel button:hover {
    background: #00fff7;
    color: #111;
    box-shadow: 0 0 25px #00fff7;
    transform: scale(1.05);
  }
  /* Gallery */
  .gallery {
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
  }
  .gallery img {
    width: 120px;
    height: 120px;
    border-radius: 15px;
    object-fit: cover;
    box-shadow: 0 0 15px #00fff7;
    transition: transform 0.4s ease;
    cursor: pointer;
  }
  .gallery img:hover {
    transform: scale(1.1) rotate(5deg);
  }
  /* Chatbot */
  #chatbot {
    margin-top: 2rem;
    background: #111a;
    border-radius: 15px;
    padding: 1rem;
    max-width: 600px;
    color: #0ff;
    font-size: 0.9rem;
    user-select: text;
  }
  #chatbot-messages {
    height: 150px;
    overflow-y: auto;
    border: 1px solid #00fff7;
    padding: 1rem;
    border-radius: 10px;
    background: #000c;
    margin-bottom: 1rem;
  }
  #chatbot-input {
    width: calc(100% - 100px);
    padding: 0.7rem;
    border-radius: 15px;
    border: none;
    background: #111;
    color: #00fff7;
    font-family: 'Orbitron', sans-serif;
    font-size: 1rem;
    outline: none;
    margin-right: 0.5rem;
  }
  #chatbot-send {
    width: 80px;
    padding: 0.7rem;
    border-radius: 15px;
    border: 2px solid #00fff7;
    background: linear-gradient(135deg, #111, #222);
    color: #00fff7;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  #chatbot-send:hover {
    background: #00fff7;
    color: #111;
    box-shadow: 0 0 20px #00fff7;
  }
  /* Badge */
  #badge {
    margin-top: 1rem;
    font-weight: 700;
    color: #0ff;
    user-select: none;
  }
  /* Toggle mode */
  #toggle-mode {
    position: fixed;
    top: 10px;
    right: 10px;
    background: none;
    border: 2px solid #00fff7;
    border-radius: 15px;
    color: #00fff7;
    padding: 0.5rem 1rem;
    cursor: pointer;
    font-weight: 700;
    user-select: none;
    transition: all 0.3s ease;
    z-index: 999;
  }
  #toggle-mode:hover {
    background: #00fff7;
    color: #111;
    box-shadow: 0 0 20px #00fff7;
    transform: scale(1.05);
  }
</style>
</head>
<body>
  <div id="galaxy-bg"></div>

  <button id="toggle-mode" aria-label="Changer le mode sombre/clair">Mode Sombre</button>

  <main class="container" role="main" aria-label="Portail Big M Morgan">
    <h1 id="main-title" aria-live="polite">Chargement de l’univers…</h1>
    <div class="welcome-msg" id="welcomeMessage"></div>

    <nav class="tabs" role="tablist" aria-label="Menu principal">
      <div class="tab active" role="tab" tabindex="0" aria-selected="true" aria-controls="section-links" id="tab-links">LIENS</div>
      <div class="tab" role="tab" tabindex="-1" aria-selected="false" aria-controls="section-gallery" id="tab-gallery">GALERIE</div>
      <div class="tab" role="tab" tabindex="-1" aria-selected="false" aria-controls="section-chatbot" id="tab-chatbot">CHATBOT</div>
      <div class="tab" role="tab" tabindex="-1" aria-selected="false" aria-controls="section-about" id="tab-about">À PROPOS</div>
      <div class="tab" role="tab" tabindex="-1" aria-selected="false" aria-controls="section-contact" id="tab-contact">CONTACT</div>
      <div class="tab" role="tab" tabindex="-1" aria-selected="false" aria-controls="section-admin" id="tab-admin">ADMIN</div>
    </nav>

    <section id="section-links" class="content-section active" role="tabpanel" aria-labelledby="tab-links" tabindex="0">
      <h2>Liens officiels de Morgan</h2>
      <div id="links-list"></div>
    </section>

    <section id="section-gallery" class="content-section" role="tabpanel" aria-labelledby="tab-gallery" tabindex="0">
      <h2>Galerie d'Images Cosmiques</h2>
      <div class="gallery" aria-label="Galerie d'images">
        <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=400&q=80" alt="Nebuleuse mystique" />
        <img src="https://images.unsplash.com/photo-1462331940025-496dfbfc7564?auto=format&fit=crop&w=400&q=80" alt="Explosion stellaire" />
        <img src="https://images.unsplash.com/photo-1446776811953-b23d57bd21aa?auto=format&fit=crop&w=400&q=80" alt="Voie lactée" />
      </div>
    </section>

    <section id="section-chatbot" class="content-section" role="tabpanel" aria-labelledby="tab-chatbot" tabindex="0">
      <h2>Assistant Digital Morgan</h2>
      <div id="chatbot-messages" aria-live="polite" aria-atomic="true"></div>
      <input type="text" id="chatbot-input" placeholder="Pose ta question..." aria-label="Message chatbot" />
      <button id="chatbot-send" aria-label="Envoyer le message au chatbot">Envoyer</button>
      <p id="badge">🎖️ Badge Visiteur : <span id="badge-name">Nouveau</span></p>
    </section>

    <section id="section-about" class="content-section" role="tabpanel" aria-labelledby="tab-about" tabindex="0">
      <h2>À propos de Morgan</h2>
      <p>Explorateur infatigable, passionné de recherche, je crée cet univers digital pour partager mes découvertes et mon art. Que chaque visite soit un voyage inspirant à travers les étoiles.</p>
    </section>

    <section id="section-contact" class="content-section" role="tabpanel" aria-labelledby="tab-contact" tabindex="0">
      <h2>Contact</h2>
      <p>Envie de discuter, collaborer ou juste dire bonjour ?</p>
      <a href="mailto:24carratsmorgan@gmail.com" class="link-btn">✉️ Envoie-moi un mail</a>
      <a href="tel:+242061098011" class="link-btn">📞 Appelle-moi</a>
    </section>

    <section id="section-admin" class="content-section" role="tabpanel" aria-labelledby="tab-admin" tabindex="0">
      <h2>Administration</h2>
      <p>⚠️ Zone réservée aux administrateurs.</p>
      <textarea id="adminLinksInput" placeholder='Liste JSON des liens personnalisés, exemple : [{"label":"Instagram","url":"https://instagram.com/i_am_24carrats_morgan"}]'></textarea>
      <button id="adminSaveBtn">💾 Sauvegarder</button>
      <p id="adminStatus" style="margin-top:1rem; font-style: italic; color:#0ff;"></p>
    </section>
  </main>

  <footer>
    &copy; 2025 Big M — Univers en expansion
  </footer>

  <script>
    // Initialisation
    const tabs = document.querySelectorAll('.tab');
    const sections = document.querySelectorAll('.content-section');
    let currentTab = 0;

    // Activation onglets + access clavier
    tabs.forEach((tab, idx) => {
      tab.addEventListener('click', () => activateTab(idx));
      tab.addEventListener('keydown', e => {
        if(e.key === 'ArrowRight') {
          const next = (idx + 1) % tabs.length;
          activateTab(next);
          tabs[next].focus();
        } else if(e.key === 'ArrowLeft') {
          const prev = (idx - 1 + tabs.length) % tabs.length;
          activateTab(prev);
          tabs[prev].focus();
        } else if(e.key === 'Enter' || e.key === ' ') {
          activateTab(idx);
        }
      });
    });

    function activateTab(idx) {
      tabs[currentTab].classList.remove('active');
      tabs[currentTab].setAttribute('aria-selected', 'false');
      tabs[currentTab].setAttribute('tabindex', '-1');
      sections[currentTab].classList.remove('active');

      currentTab = idx;

      tabs[currentTab].classList.add('active');
      tabs[currentTab].setAttribute('aria-selected', 'true');
      tabs[currentTab].setAttribute('tabindex', '0');
      sections[currentTab].classList.add('active');
      sections[currentTab].focus();
    }

    // Mode sombre clair auto + toggle
    const toggleBtn = document.getElementById('toggle-mode');
    function detectDarkMode() {
      const h = new Date().getHours();
      if(h >= 19 || h <= 6) {
        document.body.classList.add('dark-mode');
        toggleBtn.textContent = 'Mode Clair';
      } else {
        document.body.classList.remove('dark-mode');
        toggleBtn.textContent = 'Mode Sombre';
      }
    }
    toggleBtn.addEventListener('click', () => {
      document.body.classList.toggle('dark-mode');
      toggleBtn.textContent = document.body.classList.contains('dark-mode') ? 'Mode Clair' : 'Mode Sombre';
    });
    detectDarkMode();

    // Gestion des liens personnalisés avec stockage local + admin
    const adminPanel = document.getElementById('section-admin');
    const adminLinksInput = document.getElementById('adminLinksInput');
    const adminSaveBtn = document.getElementById('adminSaveBtn');
    const adminStatus = document.getElementById('adminStatus');
    const linksList = document.getElementById('links-list');

    // Liens par défaut (les tiens, avec classe et style)
    const defaultLinks = [
      {label: 'Instagram', url: 'https://instagram.com/i_am_24carrats_morgan', icon:'📸'},
      {label: 'YouTube', url: 'https://youtube.com/@johnnymorgan', icon:'▶️'},
      {label: 'Email', url: 'mailto:24carratsmorgan@gmail.com', icon:'✉️'},
      {label: 'Téléphone', url: 'tel:+242061098011', icon:'📞'},
      {label: 'GitHub', url: 'https://github.com/morgan100', icon:'💻'},
    ];

    // Récupération liens stockés localement
    function loadLinks() {
      let savedLinks = localStorage.getItem('morganLinks');
      if(savedLinks) {
        try {
          const parsed = JSON.parse(savedLinks);
          if(Array.isArray(parsed)) return parsed;
        } catch(e) { }
      }
      return defaultLinks;
    }

    // Affichage liens dans la section LIENS
    function renderLinks() {
      const links = loadLinks();
      linksList.innerHTML = '';
      links.forEach(link => {
        const a = document.createElement('a');
        a.href = link.url;
        a.target = '_blank';
        a.rel = 'noopener noreferrer';
        a.className = 'link-btn';
        a.textContent = `${link.icon ? link.icon + ' ' : ''}${link.label}`;
        linksList.appendChild(a);
      });
    }

    renderLinks();

    // Admin panel : sauvegarder nouveaux liens JSON
    adminSaveBtn.addEventListener('click', () => {
      try {
        const json = JSON.parse(adminLinksInput.value);
        if(!Array.isArray(json)) throw 'JSON doit être un tableau';
        // Vérifier la structure minimale
        for(const obj of json) {
          if(typeof obj.label !== 'string' || typeof obj.url !== 'string') {
            throw 'Chaque élément doit avoir "label" et "url" en chaîne de caractères.';
          }
        }
        localStorage.setItem('morganLinks', JSON.stringify(json));
        adminStatus.textContent = '✅ Liens sauvegardés avec succès.';
        renderLinks();
      } catch (err) {
        adminStatus.textContent = '❌ Erreur: ' + err;
      }
    });

    // Remplir admin textarea avec liens actuels
    function loadAdminLinks() {
      let savedLinks = localStorage.getItem('morganLinks');
      if(savedLinks) {
        adminLinksInput.value = savedLinks;
      } else {
        adminLinksInput.value = JSON.stringify(defaultLinks, null, 2);
      }
    }
    loadAdminLinks();

    // Welcome message dynamique selon heure locale
    function welcomeMessage() {
      const h = new Date().getHours();
      if(h < 6) return "Nuit étoilée, Morgan. Prêt pour un voyage astral ?";
      if(h < 12) return "Bonjour Morgan, que la lumière de l'aube éclaire ta créativité.";
      if(h < 18) return "Après-midi cosmique, Morgan, l'univers t'inspire !";
      return "Bonsoir Morgan, les étoiles brillent pour toi.";
    }
    document.getElementById('welcomeMessage').textContent = welcomeMessage();
    document.getElementById('main-title').textContent = "Bienvenue chez Big M 모건";

    // Chatbot ultra-basique (prototype, remplace par IA plus tard)
    const chatbotMessages = document.getElementById('chatbot-messages');
    const chatbotInput = document.getElementById('chatbot-input');
    const chatbotSend = document.getElementById('chatbot-send');
    const badgeNameSpan = document.getElementById('badge-name');

    // Badge visiteur stocké localement
    function assignBadge() {
      let badge = localStorage.getItem('morganBadge');
      if(!badge) {
        badge = "Novice Cosmique";
        localStorage.setItem('morganBadge', badge);
      }
      badgeNameSpan.textContent = badge;
    }
    assignBadge();

    // Fonction basique de réponse chatbot
    function chatbotResponse(message) {
      message = message.toLowerCase();
      if(message.includes('bonjour') || message.includes('salut')) return "Salut Morgan! Que puis-je faire pour toi aujourd’hui ?";
      if(message.includes('comment ça va')) return "Je suis un flot d’étoiles, toujours prêt à t’aider !";
      if(message.includes('liens')) return "Regarde dans l’onglet Liens, tout est à portée de clic.";
      if(message.includes('aide')) return "Pose-moi ta question, je ferai de mon mieux pour te répondre.";
      if(message.includes('musique')) return "Je n’ai pas encore de playlist cosmique, mais ça arrive bientôt!";
      return "Hmm... Je ne suis pas sûr de comprendre, mais je continue à apprendre.";
    }

    // Ajouter message au chatbot
    function addChatMessage(sender, text) {
      const p = document.createElement('p');
      p.textContent = (sender === 'user' ? 'Tu: ' : 'Bot: ') + text;
      chatbotMessages.appendChild(p);
      chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
    }

    chatbotSend.addEventListener('click', () => {
      const msg = chatbotInput.value.trim();
      if(!msg) return;
      addChatMessage('user', msg);
      chatbotInput.value = '';
      setTimeout(() => {
        addChatMessage('bot', chatbotResponse(msg));
      }, 800);
    });
    chatbotInput.addEventListener('keydown', e => {
      if(e.key === 'Enter') {
        chatbotSend.click();
      }
    });

  </script>
</body>
</html>
