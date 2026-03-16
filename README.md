<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Al Ghosia Transport — Réservation Privée</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --gold: #C9A84C;
      --gold-light: #E8C97A;
      --dark: #0A0A0A;
      --dark-2: #111111;
      --dark-3: #1A1A1A;
      --dark-4: #222222;
      --text: #E8E4DC;
      --text-muted: #888880;
      --border: rgba(201,168,76,0.18);
      --white: #FAFAF8;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--dark);
      color: var(--text);
      font-family: 'Montserrat', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
      cursor: default;
    }

    /* ── NOISE OVERLAY ── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
      pointer-events: none; z-index: 9999; opacity: .5;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.4rem 4rem;
      background: linear-gradient(to bottom, rgba(10,10,10,.95), transparent);
      backdrop-filter: blur(2px);
    }
    .nav-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.35rem; font-weight: 600; letter-spacing: .15em;
      color: var(--gold); text-transform: uppercase; text-decoration: none;
    }
    .nav-logo span { color: var(--text); font-weight: 300; }
    nav ul { list-style: none; display: flex; gap: 2.5rem; }
    nav ul a {
      color: var(--text-muted); text-decoration: none;
      font-size: .72rem; letter-spacing: .18em; text-transform: uppercase;
      transition: color .3s;
    }
    nav ul a:hover { color: var(--gold); }

    /* ── HERO ── */
    .hero {
      position: relative; height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center; text-align: center;
      overflow: hidden;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 80% 60% at 50% 60%, #1a1408 0%, #0A0A0A 70%);
    }
    .hero-line {
      position: absolute; width: 1px; background: linear-gradient(to bottom, transparent, var(--gold), transparent);
      opacity: .35;
    }
    .hero-line:nth-child(1) { left: 20%; height: 60%; top: 20%; animation: fadeIn 2s 0.3s both; }
    .hero-line:nth-child(2) { right: 20%; height: 40%; top: 30%; animation: fadeIn 2s 0.6s both; }
    .hero-line:nth-child(3) { left: 50%; height: 30%; top: 10%; animation: fadeIn 2s 0.9s both; }

    .hero-eyebrow {
      font-size: .68rem; letter-spacing: .35em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.5rem;
      animation: slideUp .9s .2s both;
    }
    .hero h1 {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3.2rem, 8vw, 7rem);
      font-weight: 300; line-height: 1.05;
      letter-spacing: .04em;
      animation: slideUp .9s .4s both;
    }
    .hero h1 em { font-style: italic; color: var(--gold-light); }
    .hero-sub {
      font-size: .8rem; letter-spacing: .15em; color: var(--text-muted);
      margin-top: 1.5rem; max-width: 36ch; line-height: 1.9;
      animation: slideUp .9s .6s both;
    }
    .hero-cta {
      display: flex; gap: 1rem; margin-top: 3rem;
      animation: slideUp .9s .8s both;
    }

    /* ── BUTTONS ── */
    .btn-gold {
      display: inline-flex; align-items: center; gap: .6rem;
      padding: .9rem 2.2rem;
      background: linear-gradient(135deg, var(--gold), #a87a28);
      color: var(--dark); font-size: .72rem; font-weight: 600;
      letter-spacing: .15em; text-transform: uppercase;
      text-decoration: none; border: none; cursor: pointer;
      transition: opacity .3s, transform .3s;
    }
    .btn-gold:hover { opacity: .88; transform: translateY(-2px); }
    .btn-outline {
      display: inline-flex; align-items: center; gap: .6rem;
      padding: .9rem 2.2rem;
      border: 1px solid var(--border);
      color: var(--text); font-size: .72rem; font-weight: 400;
      letter-spacing: .15em; text-transform: uppercase;
      text-decoration: none; background: transparent; cursor: pointer;
      transition: border-color .3s, color .3s, transform .3s;
    }
    .btn-outline:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }

    /* ── SECTION SHARED ── */
    section { padding: 7rem 4rem; }
    .section-label {
      font-size: .65rem; letter-spacing: .35em; text-transform: uppercase;
      color: var(--gold); margin-bottom: .8rem; display: block;
    }
    .section-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 4vw, 3.2rem); font-weight: 300;
      line-height: 1.15; margin-bottom: 1.5rem;
    }
    .section-title em { font-style: italic; color: var(--gold-light); }
    .divider {
      width: 4rem; height: 1px;
      background: linear-gradient(to right, var(--gold), transparent);
      margin-bottom: 2rem;
    }

    /* ── FLEET ── */
    #fleet { background: var(--dark-2); }
    .fleet-header { text-align: center; margin-bottom: 4rem; }
    .fleet-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
      gap: 1.5px; max-width: 1200px; margin: 0 auto;
    }
    .car-card {
      background: var(--dark-3); position: relative; overflow: hidden;
      cursor: pointer; transition: transform .4s;
    }
    .car-card:hover { transform: translateY(-6px); }
    .car-card:hover .car-overlay { opacity: 1; }
    .car-badge {
      position: absolute; top: 1.2rem; left: 1.2rem; z-index: 2;
      background: var(--gold); color: var(--dark);
      font-size: .6rem; font-weight: 600; letter-spacing: .15em;
      text-transform: uppercase; padding: .3rem .8rem;
    }
    .car-img {
      width: 100%; height: 240px; object-fit: cover;
      display: flex; align-items: center; justify-content: center;
      font-size: 5rem; background: linear-gradient(135deg, #181408, #1a1a12);
    }
    .car-overlay {
      position: absolute; inset: 0; background: rgba(10,8,2,.7);
      display: flex; align-items: center; justify-content: center;
      opacity: 0; transition: opacity .4s;
    }
    .car-overlay a {
      color: var(--gold); font-size: .7rem; letter-spacing: .2em;
      text-transform: uppercase; text-decoration: none;
      border: 1px solid var(--gold); padding: .7rem 1.6rem;
    }
    .car-info { padding: 1.8rem; }
    .car-brand {
      font-size: .65rem; letter-spacing: .2em; text-transform: uppercase;
      color: var(--gold); margin-bottom: .4rem;
    }
    .car-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.65rem; font-weight: 600; margin-bottom: .8rem;
    }
    .car-desc { font-size: .78rem; color: var(--text-muted); line-height: 1.8; margin-bottom: 1.2rem; }
    .car-specs { display: flex; gap: 1.5rem; flex-wrap: wrap; }
    .spec {
      display: flex; flex-direction: column; gap: .2rem;
    }
    .spec-val { font-size: .9rem; font-weight: 500; color: var(--text); }
    .spec-key { font-size: .6rem; letter-spacing: .15em; text-transform: uppercase; color: var(--text-muted); }
    .car-price {
      margin-top: 1.4rem; padding-top: 1.2rem;
      border-top: 1px solid var(--border);
      display: flex; align-items: baseline; gap: .5rem;
    }
    .price-from { font-size: .62rem; color: var(--text-muted); letter-spacing: .1em; text-transform: uppercase; }
    .price-val {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.8rem; color: var(--gold); font-weight: 600;
    }
    .price-unit { font-size: .65rem; color: var(--text-muted); }

    /* ── PRICING ESTIMATOR ── */
    #pricing { background: var(--dark); }
    .pricing-wrap {
      max-width: 900px; margin: 0 auto;
      display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start;
    }
    .estimator {
      background: var(--dark-3); border: 1px solid var(--border);
      padding: 2.5rem;
    }
    .estimator h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.5rem; margin-bottom: 2rem; font-weight: 400;
    }
    .field { margin-bottom: 1.4rem; }
    .field label {
      display: block; font-size: .65rem; letter-spacing: .2em;
      text-transform: uppercase; color: var(--text-muted); margin-bottom: .6rem;
    }
    .field select, .field input {
      width: 100%; background: var(--dark-4); border: 1px solid var(--border);
      color: var(--text); font-family: 'Montserrat', sans-serif;
      font-size: .82rem; padding: .85rem 1rem;
      appearance: none; outline: none;
      transition: border-color .3s;
    }
    .field select:focus, .field input:focus { border-color: var(--gold); }
    .field select option { background: var(--dark-4); }
    .range-wrap { position: relative; }
    .field input[type=range] {
      padding: 0; border: none; background: transparent;
      accent-color: var(--gold);
    }
    .range-val {
      position: absolute; right: 0; top: -1.8rem;
      font-size: .78rem; color: var(--gold);
    }
    .estimate-result {
      margin-top: 2rem; padding: 1.5rem;
      background: linear-gradient(135deg, rgba(201,168,76,.08), rgba(201,168,76,.03));
      border: 1px solid var(--border); text-align: center;
    }
    .estimate-label {
      font-size: .62rem; letter-spacing: .2em; text-transform: uppercase;
      color: var(--text-muted); margin-bottom: .5rem; display: block;
    }
    .estimate-price {
      font-family: 'Cormorant Garamond', serif;
      font-size: 3rem; color: var(--gold); font-weight: 600;
    }
    .estimate-note { font-size: .68rem; color: var(--text-muted); margin-top: .4rem; }

    /* pricing table */
    .pricing-table h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.5rem; margin-bottom: 1.5rem; font-weight: 400;
    }
    .p-row {
      display: flex; justify-content: space-between; align-items: center;
      padding: 1rem 0; border-bottom: 1px solid var(--border);
    }
    .p-row:last-child { border-bottom: none; }
    .p-service { font-size: .8rem; color: var(--text); }
    .p-car { font-size: .65rem; color: var(--text-muted); margin-top: .2rem; }
    .p-price { font-size: .95rem; color: var(--gold); font-weight: 500; }

    /* ── BOOKING / CONTACT ── */
    #reservation { background: var(--dark-2); }
    .booking-wrap {
      max-width: 800px; margin: 0 auto;
      display: grid; grid-template-columns: 1fr 1fr; gap: 4rem;
    }
    .booking-form { }
    .booking-form .field { margin-bottom: 1.2rem; }
    .booking-form input, .booking-form select, .booking-form textarea {
      width: 100%; background: var(--dark-4); border: 1px solid var(--border);
      color: var(--text); font-family: 'Montserrat', sans-serif;
      font-size: .82rem; padding: .85rem 1rem; outline: none;
      transition: border-color .3s; resize: none;
    }
    .booking-form input:focus,
    .booking-form select:focus,
    .booking-form textarea:focus { border-color: var(--gold); }
    .booking-form textarea { height: 90px; }

    .contact-side { display: flex; flex-direction: column; gap: 2rem; padding-top: .5rem; }
    .contact-item { display: flex; flex-direction: column; gap: .4rem; }
    .contact-item .c-label {
      font-size: .62rem; letter-spacing: .2em; text-transform: uppercase; color: var(--gold);
    }
    .contact-item .c-val { font-size: .88rem; color: var(--text); }

    .wa-btn {
      display: inline-flex; align-items: center; gap: .8rem;
      padding: 1rem 2rem;
      background: #128C7E;
      color: #fff; font-size: .72rem; font-weight: 600;
      letter-spacing: .12em; text-transform: uppercase;
      text-decoration: none; transition: background .3s, transform .3s;
      margin-top: .5rem;
    }
    .wa-btn:hover { background: #075E54; transform: translateY(-2px); }
    .wa-icon { width: 20px; height: 20px; }

    /* ── SERVICES ── */
    #services { background: var(--dark); }
    .services-grid {
      display: grid; grid-template-columns: repeat(3, 1fr);
      gap: 1px; max-width: 1100px; margin: 3rem auto 0;
    }
    .service-item {
      background: var(--dark-3); padding: 2.5rem 2rem;
      border-top: 2px solid transparent;
      transition: border-color .3s, background .3s;
    }
    .service-item:hover { border-color: var(--gold); background: var(--dark-4); }
    .service-icon { font-size: 2rem; margin-bottom: 1.2rem; }
    .service-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.3rem; margin-bottom: .7rem; font-weight: 400;
    }
    .service-desc { font-size: .76rem; color: var(--text-muted); line-height: 1.85; }

    /* ── FOOTER ── */
    footer {
      background: var(--dark-2); border-top: 1px solid var(--border);
      padding: 3rem 4rem; text-align: center;
    }
    .footer-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.5rem; color: var(--gold); letter-spacing: .15em; margin-bottom: 1rem;
    }
    .footer-copy { font-size: .68rem; color: var(--text-muted); letter-spacing: .1em; }

    /* ── ANIMATIONS ── */
    @keyframes slideUp {
      from { opacity: 0; transform: translateY(28px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity: 0; } to { opacity: 1; }
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 1.2rem 1.5rem; }
      nav ul { display: none; }
      section { padding: 5rem 1.5rem; }
      .pricing-wrap, .booking-wrap { grid-template-columns: 1fr; gap: 2.5rem; }
      .services-grid { grid-template-columns: 1fr; }
      .fleet-grid { grid-template-columns: 1fr; }
      .hero-cta { flex-direction: column; align-items: center; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <a class="nav-logo" href="#"><span>Al</span> Ghosia <span>Transport</span></a>
  <ul>
    <li><a href="#fleet">Notre Flotte</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#pricing">Tarifs</a></li>
    <li><a href="#reservation">Réserver</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-line"></div>
  <div class="hero-line"></div>
  <div class="hero-line"></div>
  <p class="hero-eyebrow">Transport Privé Premium · Paris & Île-de-France</p>
  <h1>L'excellence du<br>transport <em>privé</em></h1>
  <p class="hero-sub">Chauffeurs privés, véhicules d'exception — BYD Seal & Mercedes AMG. Une expérience pensée pour ceux qui exigent le meilleur.</p>
  <div class="hero-cta">
    <a href="#reservation" class="btn-gold">Réserver maintenant</a>
    <a href="#fleet" class="btn-outline">Découvrir la flotte</a>
  </div>
</section>

<!-- FLEET -->
<section id="fleet">
  <div class="fleet-header">
    <span class="section-label">Notre Flotte</span>
    <h2 class="section-title">Des véhicules <em>d'exception</em></h2>
    <div class="divider" style="margin:0 auto;"></div>
  </div>
  <div class="fleet-grid">

    <!-- BYD Seal -->
    <div class="car-card">
      <span class="car-badge">Électrique</span>
      <div class="car-img">🚗</div>
      <div class="car-overlay">
        <a href="#reservation">Réserver ce véhicule</a>
      </div>
      <div class="car-info">
        <p class="car-brand">BYD</p>
        <h3 class="car-name">Seal</h3>
        <p class="car-desc">Berline électrique haut de gamme, silencieuse et technologique. L'élégance moderne au service de votre confort.</p>
        <div class="car-specs">
          <div class="spec"><span class="spec-val">530 km</span><span class="spec-key">Autonomie</span></div>
          <div class="spec"><span class="spec-val">5</span><span class="spec-key">Passagers</span></div>
          <div class="spec"><span class="spec-val">100% Élec.</span><span class="spec-key">Motorisation</span></div>
        </div>
        <div class="car-price">
          <span class="price-from">À partir de</span>
          <span class="price-val">55€</span>
          <span class="price-unit">/ trajet</span>
        </div>
      </div>
    </div>

    <!-- Mercedes AMG -->
    <div class="car-card">
      <span class="car-badge">Prestige</span>
      <div class="car-img">🏎️</div>
      <div class="car-overlay">
        <a href="#reservation">Réserver ce véhicule</a>
      </div>
      <div class="car-info">
        <p class="car-brand">Mercedes-Benz</p>
        <h3 class="car-name">AMG</h3>
        <p class="car-desc">L'icône du luxe sportif. Puissance, raffinement et prestance pour vos déplacements les plus exigeants.</p>
        <div class="car-specs">
          <div class="spec"><span class="spec-val">450 ch</span><span class="spec-key">Puissance</span></div>
          <div class="spec"><span class="spec-val">4</span><span class="spec-key">Passagers</span></div>
          <div class="spec"><span class="spec-val">AMG Line</span><span class="spec-key">Finition</span></div>
        </div>
        <div class="car-price">
          <span class="price-from">À partir de</span>
          <span class="price-val">85€</span>
          <span class="price-unit">/ trajet</span>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div style="text-align:center; margin-bottom: 1rem;">
    <span class="section-label">Nos Services</span>
    <h2 class="section-title">Une offre <em>sur-mesure</em></h2>
    <div class="divider" style="margin:0 auto;"></div>
  </div>
  <div class="services-grid">
    <div class="service-item">
      <div class="service-icon">✈️</div>
      <h3 class="service-name">Transfert Aéroport</h3>
      <p class="service-desc">CDG, Orly, Le Bourget. Prise en charge à l'heure, suivi de vol en temps réel, accueil personnalisé.</p>
    </div>
    <div class="service-item">
      <div class="service-icon">🏢</div>
      <h3 class="service-name">Mise à Disposition</h3>
      <p class="service-desc">Chauffeur disponible à la demi-journée ou à la journée pour vos déplacements professionnels ou personnels.</p>
    </div>
    <div class="service-item">
      <div class="service-icon">🌙</div>
      <h3 class="service-name">Soirées & Événements</h3>
      <p class="service-desc">Mariage, soirée privée, gala. Arrivez avec style et repartez l'esprit serein.</p>
    </div>
    <div class="service-item">
      <div class="service-icon">🏥</div>
      <h3 class="service-name">Transport Médical</h3>
      <p class="service-desc">Accompagnement pour vos rendez-vous médicaux, avec discrétion et ponctualité absolue.</p>
    </div>
    <div class="service-item">
      <div class="service-icon">🚉</div>
      <h3 class="service-name">Gares Parisiennes</h3>
      <p class="service-desc">Gare du Nord, Gare de Lyon, Gare Montparnasse… Départ et arrivée en toute sérénité.</p>
    </div>
    <div class="service-item">
      <div class="service-icon">🗺️</div>
      <h3 class="service-name">Longue Distance</h3>
      <p class="service-desc">Paris–Lyon, Paris–Bruxelles, Paris–Monaco. Trajets longue distance en véhicule premium.</p>
    </div>
  </div>
</section>

<!-- PRICING ESTIMATOR -->
<section id="pricing">
  <span class="section-label">Estimation Tarifaire</span>
  <h2 class="section-title">Calculez votre <em>trajet</em></h2>
  <div class="divider"></div>
  <div class="pricing-wrap">

    <div class="estimator">
      <h3>Simulateur de Prix</h3>

      <div class="field">
        <label>Véhicule</label>
        <select id="carSelect" onchange="calcPrice()">
          <option value="byd">BYD Seal — Électrique</option>
          <option value="amg">Mercedes AMG — Prestige</option>
        </select>
      </div>

      <div class="field">
        <label>Type de service</label>
        <select id="serviceSelect" onchange="calcPrice()">
          <option value="airport">Transfert Aéroport</option>
          <option value="city">Trajet Urbain</option>
          <option value="dispo">Mise à Disposition (h)</option>
          <option value="longue">Longue Distance</option>
        </select>
      </div>

      <div class="field">
        <label>Distance estimée (km) — <span id="kmLabel">30</span> km</label>
        <div class="range-wrap">
          <input type="range" id="kmRange" min="5" max="500" value="30"
                 oninput="document.getElementById('kmLabel').textContent=this.value; calcPrice()">
        </div>
      </div>

      <div class="field">
        <label>Nombre de passagers</label>
        <select id="paxSelect" onchange="calcPrice()">
          <option value="1">1 passager</option>
          <option value="2">2 passagers</option>
          <option value="3">3 passagers</option>
          <option value="4">4 passagers</option>
          <option value="5">5 passagers (BYD uniquement)</option>
        </select>
      </div>

      <div class="estimate-result">
        <span class="estimate-label">Estimation du trajet</span>
        <div class="estimate-price" id="priceResult">55 €</div>
        <p class="estimate-note">Prix indicatif TTC · Devis personnalisé sur demande</p>
      </div>
    </div>

    <div class="pricing-table">
      <h3>Grille tarifaire</h3>
      <div class="p-row">
        <div><div class="p-service">Aéroport Paris intra-muros</div><div class="p-car">BYD Seal</div></div>
        <div class="p-price">55 – 75 €</div>
      </div>
      <div class="p-row">
        <div><div class="p-service">Aéroport Paris intra-muros</div><div class="p-car">Mercedes AMG</div></div>
        <div class="p-price">85 – 110 €</div>
      </div>
      <div class="p-row">
        <div><div class="p-service">Mise à dispo — ½ journée</div><div class="p-car">BYD Seal</div></div>
        <div class="p-price">180 €</div>
      </div>
      <div class="p-row">
        <div><div class="p-service">Mise à dispo — ½ journée</div><div class="p-car">Mercedes AMG</div></div>
        <div class="p-price">280 €</div>
      </div>
      <div class="p-row">
        <div><div class="p-service">Paris → Lyon</div><div class="p-car">BYD Seal</div></div>
        <div class="p-price">390 €</div>
      </div>
      <div class="p-row">
        <div><div class="p-service">Paris → Lyon</div><div class="p-car">Mercedes AMG</div></div>
        <div class="p-price">550 €</div>
      </div>
      <div class="p-row">
        <div><div class="p-service">Paris → Monaco</div><div class="p-car">Mercedes AMG</div></div>
        <div class="p-price">950 €</div>
      </div>
    </div>

  </div>
</section>

<!-- RESERVATION & CONTACT -->
<section id="reservation">
  <span class="section-label">Réservation</span>
  <h2 class="section-title">Réservez votre <em>trajet</em></h2>
  <div class="divider"></div>
  <div class="booking-wrap">

    <div class="booking-form">
      <div class="field"><label>Nom complet</label><input type="text" placeholder="Votre nom"></div>
      <div class="field"><label>Téléphone</label><input type="tel" placeholder="+33 6 XX XX XX XX"></div>
      <div class="field"><label>Adresse de prise en charge</label><input type="text" placeholder="Départ"></div>
      <div class="field"><label>Destination</label><input type="text" placeholder="Arrivée"></div>
      <div class="field">
        <label>Véhicule souhaité</label>
        <select>
          <option>BYD Seal — Électrique Premium</option>
          <option>Mercedes AMG — Prestige</option>
        </select>
      </div>
      <div class="field"><label>Date & Heure</label><input type="datetime-local"></div>
      <div class="field"><label>Informations complémentaires</label><textarea placeholder="Bagages, options, demandes spéciales…"></textarea></div>
      <a id="waBook" href="#" class="btn-gold" style="width:100%; justify-content:center; margin-top:.5rem;" onclick="sendWhatsApp(event)">
        📲 Envoyer via WhatsApp
      </a>
    </div>

    <div class="contact-side">
      <div>
        <span class="section-label">Contact Direct</span>
        <h3 style="font-family:'Cormorant Garamond',serif;font-size:1.6rem;font-weight:300;margin-bottom:1rem;">
          Disponible <em>24h/24</em>
        </h3>
        <p style="font-size:.78rem;color:var(--text-muted);line-height:1.9;">
          Réservation rapide et confirmation immédiate. Notre équipe vous répond en moins de 15 minutes via WhatsApp.
        </p>
      </div>

      <div class="contact-item">
        <span class="c-label">WhatsApp</span>
        <span class="c-val">+33 6 XX XX XX XX</span>
      </div>
      <div class="contact-item">
        <span class="c-label">Email</span>
        <span class="c-val">contact@alghosia-transport.com</span>
      </div>
      <div class="contact-item">
        <span class="c-label">Zone de service</span>
        <span class="c-val">Paris · Île-de-France · France entière</span>
      </div>

      <a href="https://wa.me/33600000000?text=Bonjour%2C%20je%20souhaite%20r%C3%A9server%20un%20v%C3%A9hicule%20Al%20Ghosia%20Transport."
         class="wa-btn" target="_blank">
        <svg class="wa-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/>
          <path d="M12 0C5.374 0 0 5.373 0 12c0 2.117.549 4.107 1.51 5.842L.06 23.386a.75.75 0 0 0 .92.92l5.544-1.45A11.936 11.936 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.808 9.808 0 0 1-5.001-1.369l-.359-.214-3.721.975.993-3.63-.234-.373A9.818 9.818 0 0 1 2.182 12C2.182 6.57 6.569 2.182 12 2.182S21.818 6.57 21.818 12 17.431 21.818 12 21.818z"/>
        </svg>
        Contacter sur WhatsApp
      </a>
    </div>

  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">AL GHOSIA TRANSPORT</div>
  <p class="footer-copy">© 2025 Al Ghosia Transport · Transport Privé Premium · Paris</p>
</footer>

<script>
  // ── Price estimator ──
  function calcPrice() {
    const car = document.getElementById('carSelect').value;
    const service = document.getElementById('serviceSelect').value;
    const km = parseInt(document.getElementById('kmRange').value);

    const rates = {
      byd:  { base: 15, perKm: 1.8,  airport: 55, dispo: 35, min: 35 },
      amg:  { base: 25, perKm: 2.6,  airport: 85, dispo: 55, min: 55 },
    };
    const r = rates[car];
    let price = 0;

    if (service === 'airport') {
      price = r.airport + Math.max(0, (km - 25)) * r.perKm;
    } else if (service === 'dispo') {
      price = r.dispo * Math.max(1, Math.round(km / 30));
    } else if (service === 'longue') {
      price = r.base + km * r.perKm * 1.2;
    } else {
      price = r.base + km * r.perKm;
    }

    price = Math.max(r.min, Math.round(price));
    document.getElementById('priceResult').textContent = price + ' €';
  }

  // ── WhatsApp booking form ──
  function sendWhatsApp(e) {
    e.preventDefault();
    const nom   = document.querySelector('input[placeholder="Votre nom"]').value || 'Non renseigné';
    const tel   = document.querySelector('input[type=tel]').value || 'Non renseigné';
    const dep   = document.querySelector('input[placeholder="Départ"]').value || 'Non renseigné';
    const arr   = document.querySelector('input[placeholder="Arrivée"]').value || 'Non renseigné';
    const car   = document.querySelectorAll('.booking-form select')[0].value;
    const dt    = document.querySelector('input[type=datetime-local]').value || 'Non renseigné';
    const notes = document.querySelector('textarea').value || '';

    const msg = `🚗 *Réservation Al Ghosia Transport*\n\n` +
      `👤 *Nom :* ${nom}\n` +
      `📞 *Tél :* ${tel}\n` +
      `📍 *Départ :* ${dep}\n` +
      `🏁 *Arrivée :* ${arr}\n` +
      `🚘 *Véhicule :* ${car}\n` +
      `📅 *Date/Heure :* ${dt}\n` +
      (notes ? `📝 *Notes :* ${notes}\n` : '') +
      `\n_Merci de confirmer la disponibilité._`;

    const encoded = encodeURIComponent(msg);
    // ⚠️ Remplacez 33600000000 par votre vrai numéro WhatsApp
    window.open(`https://wa.me/33600000000?text=${encoded}`, '_blank');
  }

  // ── Scroll animations ──
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.car-card, .service-item, .estimator, .pricing-table, .booking-form, .contact-side')
    .forEach(el => {
      el.style.opacity = '0';
      el.style.transform = 'translateY(30px)';
      el.style.transition = 'opacity .7s ease, transform .7s ease';
      observer.observe(el);
    });
</script>
</body>
</html>
