
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MILIONÁRIO — Sua Riqueza Começa Aqui</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Cinzel:wght@400;700;900&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C9A84C;
    --gold-light: #F0D080;
    --gold-dark: #8B6914;
    --black: #050505;
    --deep: #0A0A0A;
    --surface: #111111;
    --surface2: #181818;
    --text: #E8E0CC;
    --muted: #888880;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    cursor: default;
  }

  /* ─── GRAIN OVERLAY ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: 0.35;
  }

  /* ─── CUSTOM CURSOR ─── */
  .cursor {
    width: 12px; height: 12px;
    background: var(--gold);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease;
    mix-blend-mode: screen;
  }

  /* ─── NAV ─── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 24px 60px;
    background: linear-gradient(to bottom, rgba(5,5,5,0.95), transparent);
    backdrop-filter: blur(2px);
  }

  .nav-logo {
    font-family: 'Cinzel', serif;
    font-size: 22px;
    font-weight: 700;
    letter-spacing: 6px;
    color: var(--gold);
    text-transform: uppercase;
  }

  .nav-links {
    display: flex;
    gap: 40px;
    list-style: none;
  }

  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    transition: color 0.3s;
  }

  .nav-links a:hover { color: var(--gold); }

  /* ─── HERO ─── */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    padding: 120px 60px 80px;
    text-align: center;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 40%, rgba(201,168,76,0.12) 0%, transparent 70%),
      radial-gradient(ellipse 40% 40% at 20% 80%, rgba(201,168,76,0.06) 0%, transparent 60%),
      radial-gradient(ellipse 40% 40% at 80% 20%, rgba(201,168,76,0.06) 0%, transparent 60%);
  }

  /* Floating coins */
  .coin {
    position: absolute;
    width: 60px; height: 60px;
    border-radius: 50%;
    border: 2px solid rgba(201,168,76,0.3);
    background: radial-gradient(circle at 35% 35%, rgba(240,208,128,0.15), transparent);
    animation: float linear infinite;
  }
  .coin::after {
    content: '₿';
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    color: rgba(201,168,76,0.4);
  }
  .coin:nth-child(1) { left: 5%; top: 20%; width: 50px; height: 50px; animation-duration: 14s; animation-delay: 0s; }
  .coin:nth-child(2) { left: 88%; top: 30%; width: 70px; height: 70px; animation-duration: 18s; animation-delay: -5s; }
  .coin:nth-child(3) { left: 15%; top: 70%; width: 40px; height: 40px; animation-duration: 12s; animation-delay: -3s; }
  .coin:nth-child(4) { left: 75%; top: 65%; width: 55px; height: 55px; animation-duration: 16s; animation-delay: -8s; }
  .coin:nth-child(5) { left: 50%; top: 10%; width: 45px; height: 45px; animation-duration: 20s; animation-delay: -1s; }

  @keyframes float {
    0% { transform: translateY(0) rotate(0deg); opacity: 0; }
    10% { opacity: 1; }
    90% { opacity: 1; }
    100% { transform: translateY(-100vh) rotate(720deg); opacity: 0; }
  }

  /* Decorative lines */
  .deco-line {
    position: absolute;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--gold), transparent);
    opacity: 0.2;
  }
  .deco-line:nth-child(6) { left: 15%; top: 0; height: 100%; }
  .deco-line:nth-child(7) { right: 15%; top: 0; height: 100%; }

  .hero-eyebrow {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    letter-spacing: 8px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 1s ease forwards 0.3s;
  }

  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(64px, 10vw, 130px);
    font-weight: 900;
    line-height: 0.9;
    letter-spacing: -2px;
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 1s ease forwards 0.6s;
  }

  .hero-title em {
    font-style: italic;
    background: linear-gradient(135deg, var(--gold-dark), var(--gold), var(--gold-light), var(--gold));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-size: 16px;
    color: var(--muted);
    max-width: 520px;
    margin: 0 auto 48px;
    line-height: 1.8;
    letter-spacing: 0.5px;
    opacity: 0;
    animation: fadeUp 1s ease forwards 0.9s;
  }

  .btn-primary {
    display: inline-block;
    padding: 18px 52px;
    background: linear-gradient(135deg, var(--gold-dark), var(--gold), var(--gold-light));
    color: var(--black);
    font-family: 'Cinzel', serif;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 4px;
    text-transform: uppercase;
    text-decoration: none;
    border: none;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    opacity: 0;
    animation: fadeUp 1s ease forwards 1.2s;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    box-shadow: 0 0 40px rgba(201,168,76,0.3);
  }

  .btn-primary::before {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
    transition: left 0.5s ease;
  }

  .btn-primary:hover { transform: translateY(-3px); box-shadow: 0 8px 60px rgba(201,168,76,0.5); }
  .btn-primary:hover::before { left: 100%; }

  .hero-stats {
    display: flex;
    justify-content: center;
    gap: 60px;
    margin-top: 80px;
    padding-top: 60px;
    border-top: 1px solid rgba(201,168,76,0.15);
    opacity: 0;
    animation: fadeUp 1s ease forwards 1.5s;
  }

  .stat-item { text-align: center; }
  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 42px;
    font-weight: 700;
    color: var(--gold);
    display: block;
  }
  .stat-label {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-top: 6px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ─── MARQUEE ─── */
  .ticker {
    overflow: hidden;
    border-top: 1px solid rgba(201,168,76,0.2);
    border-bottom: 1px solid rgba(201,168,76,0.2);
    background: rgba(201,168,76,0.04);
    padding: 14px 0;
  }

  .ticker-track {
    display: flex;
    gap: 0;
    animation: ticker 30s linear infinite;
    white-space: nowrap;
  }

  .ticker-item {
    font-family: 'Cinzel', serif;
    font-size: 12px;
    letter-spacing: 4px;
    color: var(--gold);
    padding: 0 40px;
    text-transform: uppercase;
    flex-shrink: 0;
  }

  .ticker-sep {
    color: rgba(201,168,76,0.3);
    padding: 0 10px;
  }

  @keyframes ticker {
    0% { transform: translateX(0); }
    100% { transform: translateX(-50%); }
  }

  /* ─── SECTION BASE ─── */
  section { padding: 120px 60px; max-width: 1300px; margin: 0 auto; }

  .section-label {
    font-family: 'Cinzel', serif;
    font-size: 10px;
    letter-spacing: 6px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, var(--gold), transparent);
    max-width: 80px;
    opacity: 0.5;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(36px, 5vw, 64px);
    font-weight: 700;
    line-height: 1.1;
    margin-bottom: 20px;
  }

  .section-title em {
    font-style: italic;
    color: var(--gold);
  }

  /* ─── PHILOSOPHY ─── */
  .philosophy {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
  }

  .philosophy-text p {
    color: var(--muted);
    line-height: 1.9;
    margin-top: 24px;
    font-size: 15px;
  }

  .philosophy-quote {
    border-left: 2px solid var(--gold);
    padding-left: 32px;
    margin-top: 40px;
  }

  .philosophy-quote blockquote {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    font-style: italic;
    color: var(--text);
    line-height: 1.5;
  }

  .philosophy-quote cite {
    display: block;
    margin-top: 12px;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
  }

  .philosophy-visual {
    position: relative;
  }

  .wealth-card {
    background: var(--surface2);
    border: 1px solid rgba(201,168,76,0.2);
    padding: 48px;
    position: relative;
    overflow: hidden;
  }

  .wealth-card::before {
    content: '';
    position: absolute;
    top: 0; right: 0;
    width: 180px; height: 180px;
    background: radial-gradient(circle, rgba(201,168,76,0.12), transparent);
    border-radius: 50%;
    transform: translate(50%,-50%);
  }

  .wealth-card-icon {
    font-size: 48px;
    margin-bottom: 20px;
  }

  .wealth-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 28px;
    font-weight: 700;
    margin-bottom: 12px;
  }

  .wealth-card p {
    color: var(--muted);
    line-height: 1.8;
    font-size: 14px;
  }

  .wealth-card-2 {
    position: absolute;
    right: -30px;
    bottom: -30px;
    background: var(--surface);
    border: 1px solid rgba(201,168,76,0.15);
    padding: 28px;
    width: 220px;
  }

  .mini-chart {
    display: flex;
    gap: 6px;
    align-items: flex-end;
    height: 60px;
    margin-bottom: 14px;
  }

  .bar {
    flex: 1;
    background: linear-gradient(to top, var(--gold-dark), var(--gold));
    opacity: 0.8;
    border-radius: 2px 2px 0 0;
  }

  .bar:nth-child(1) { height: 30%; }
  .bar:nth-child(2) { height: 50%; }
  .bar:nth-child(3) { height: 40%; }
  .bar:nth-child(4) { height: 70%; }
  .bar:nth-child(5) { height: 60%; }
  .bar:nth-child(6) { height: 85%; }
  .bar:nth-child(7) { height: 100%; }

  .mini-num {
    font-family: 'Playfair Display', serif;
    font-size: 24px;
    font-weight: 700;
    color: var(--gold);
  }

  .mini-label { font-size: 11px; color: var(--muted); letter-spacing: 1px; }

  /* ─── PILLARS ─── */
  .pillars-section { background: var(--surface); padding: 120px 60px; max-width: 100%; }
  .pillars-inner { max-width: 1300px; margin: 0 auto; }

  .pillars-header { text-align: center; margin-bottom: 80px; }

  .pillars-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }

  .pillar {
    background: var(--deep);
    padding: 52px 40px;
    border: 1px solid rgba(201,168,76,0.1);
    position: relative;
    overflow: hidden;
    transition: border-color 0.4s, background 0.4s;
  }

  .pillar:hover {
    border-color: rgba(201,168,76,0.4);
    background: rgba(201,168,76,0.04);
  }

  .pillar::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(to right, transparent, var(--gold), transparent);
    transform: scaleX(0);
    transition: transform 0.4s ease;
  }

  .pillar:hover::after { transform: scaleX(1); }

  .pillar-num {
    font-family: 'Playfair Display', serif;
    font-size: 72px;
    font-weight: 900;
    line-height: 1;
    color: rgba(201,168,76,0.12);
    margin-bottom: 16px;
    transition: color 0.4s;
  }

  .pillar:hover .pillar-num { color: rgba(201,168,76,0.25); }

  .pillar-icon { font-size: 32px; margin-bottom: 20px; }

  .pillar h3 {
    font-family: 'Playfair Display', serif;
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 16px;
    color: var(--text);
  }

  .pillar p { color: var(--muted); line-height: 1.8; font-size: 14px; }

  /* ─── TESTIMONIALS ─── */
  .testimonials-header { text-align: center; margin-bottom: 70px; }

  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
  }

  .testi {
    background: var(--surface2);
    border: 1px solid rgba(201,168,76,0.12);
    padding: 40px;
    position: relative;
  }

  .testi::before {
    content: '"';
    font-family: 'Playfair Display', serif;
    font-size: 120px;
    line-height: 0.8;
    color: rgba(201,168,76,0.1);
    position: absolute;
    top: 20px; left: 30px;
  }

  .testi-text {
    font-family: 'Playfair Display', serif;
    font-size: 17px;
    font-style: italic;
    line-height: 1.7;
    color: var(--text);
    margin-bottom: 28px;
    position: relative;
    z-index: 1;
    margin-top: 30px;
  }

  .testi-author {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .testi-avatar {
    width: 48px; height: 48px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--gold-dark), var(--gold));
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 20px;
    font-weight: 700;
    color: var(--black);
    flex-shrink: 0;
  }

  .testi-name {
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--text);
  }

  .testi-role { font-size: 11px; color: var(--gold); margin-top: 3px; letter-spacing: 1px; }

  /* ─── CTA SECTION ─── */
  .cta-section {
    background: var(--deep);
    border-top: 1px solid rgba(201,168,76,0.15);
    border-bottom: 1px solid rgba(201,168,76,0.15);
    padding: 140px 60px;
    text-align: center;
    position: relative;
    overflow: hidden;
    max-width: 100%;
  }

  .cta-section::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse 70% 70% at 50% 50%, rgba(201,168,76,0.08), transparent);
  }

  .cta-section .section-title { font-size: clamp(40px, 6vw, 80px); }

  .cta-section p {
    color: var(--muted);
    font-size: 16px;
    line-height: 1.8;
    max-width: 560px;
    margin: 24px auto 48px;
  }

  .cta-inner { position: relative; z-index: 1; }

  .btn-secondary {
    display: inline-block;
    padding: 18px 52px;
    border: 1px solid rgba(201,168,76,0.4);
    color: var(--gold);
    font-family: 'Cinzel', serif;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 4px;
    text-transform: uppercase;
    text-decoration: none;
    cursor: pointer;
    margin-left: 20px;
    transition: all 0.3s;
    background: transparent;
  }

  .btn-secondary:hover {
    background: rgba(201,168,76,0.1);
    border-color: var(--gold);
  }

  /* ─── FOOTER ─── */
  footer {
    padding: 60px 60px 40px;
    border-top: 1px solid rgba(201,168,76,0.1);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
  }

  .footer-logo {
    font-family: 'Cinzel', serif;
    font-size: 18px;
    font-weight: 700;
    letter-spacing: 6px;
    color: var(--gold);
  }

  .footer-copy { font-size: 12px; color: var(--muted); letter-spacing: 1px; }

  .footer-links { display: flex; gap: 32px; }
  .footer-links a {
    font-size: 11px;
    letter-spacing: 2px;
    color: var(--muted);
    text-decoration: none;
    text-transform: uppercase;
    transition: color 0.3s;
  }
  .footer-links a:hover { color: var(--gold); }

  /* ─── SCROLL REVEAL ─── */
  .reveal {
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ─── COUNTER ANIMATION ─── */
  .count-up { display: inline-block; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    nav { padding: 20px 28px; }
    .nav-links { display: none; }
    section { padding: 80px 28px; }
    .philosophy { grid-template-columns: 1fr; gap: 48px; }
    .pillars-grid { grid-template-columns: 1fr; }
    .testimonials-grid { grid-template-columns: 1fr; }
    .hero { padding: 100px 28px 60px; }
    .hero-stats { gap: 30px; flex-wrap: wrap; }
    footer { flex-direction: column; text-align: center; }
    .wealth-card-2 { display: none; }
    .pillars-section { padding: 80px 28px; }
    .cta-section { padding: 100px 28px; }
    .btn-secondary { margin-left: 0; margin-top: 16px; display: block; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">Milionário</div>
  <ul class="nav-links">
    <li><a href="#filosofia">Filosofia</a></li>
    <li><a href="#pilares">Pilares</a></li>
    <li><a href="#depoimentos">Resultados</a></li>
    <li><a href="#cta">Começar</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="coin"></div>
  <div class="coin"></div>
  <div class="coin"></div>
  <div class="coin"></div>
  <div class="coin"></div>
  <div class="deco-line"></div>
  <div class="deco-line"></div>

  <div>
    <p class="hero-eyebrow">✦ O Caminho Para a Liberdade Financeira ✦</p>
    <h1 class="hero-title">
      Você<br>
      Merece Ser<br>
      <em>Milionário</em>
    </h1>
    <p class="hero-sub">
      Mais de 12.000 pessoas já transformaram suas finanças com os nossos métodos comprovados. 
      A riqueza não é sorte — é estratégia, disciplina e o conhecimento certo.
    </p>
    <a href="#cta" class="btn-primary">Quero Mudar Minha Vida Agora</a>

    <div class="hero-stats">
      <div class="stat-item">
        <span class="stat-num count-up" data-target="12847">0</span>
        <span class="stat-label">Vidas Transformadas</span>
      </div>
      <div class="stat-item">
        <span class="stat-num count-up" data-target="487">0</span>
        <span class="stat-label">Milhões Gerados</span>
      </div>
      <div class="stat-item">
        <span class="stat-num count-up" data-target="98">0</span>
        <span class="stat-label">% de Satisfação</span>
      </div>
    </div>
  </div>
</div>

<!-- TICKER -->
<div class="ticker">
  <div class="ticker-track" id="ticker">
    <span class="ticker-item">Liberdade Financeira</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Investimentos Inteligentes</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Mentalidade Milionária</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Patrimônio Real</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Renda Passiva</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Prosperidade Abundante</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Liberdade Financeira</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Investimentos Inteligentes</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Mentalidade Milionária</span>
    <span class="ticker-item ticker-sep">✦</span>
    <span class="ticker-item">Patrimônio Real</span>
    <span class="ticker-item 