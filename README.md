
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Reto Rejuvenese — 10 Semanas de Transformación Integral</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,300;1,700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #0a0a0a;
    --carbon: #111111;
    --dark: #1a1a1a;
    --mid: #252525;
    --titanium: #888888;
    --light-gray: #c8c8c8;
    --white: #f5f5f0;
    --gold: #c9a84c;
    --gold-light: #e8c96a;
    --gold-pale: #f0dfa0;
    --green-teal: #2a6b5c;
    --green-glow: #3a8b74;
    --green-accent: #4db899;
    --electric: #1a6fa0;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'Poppins', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    cursor: none;
  }

  /* CURSOR */
  .cursor {
    width: 8px; height: 8px;
    background: var(--gold);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s;
    transform: translate(-50%, -50%);
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(201,168,76,0.4);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: transform 0.18s ease, width 0.2s, height 0.2s, opacity 0.2s;
    transform: translate(-50%, -50%);
  }
  a:hover ~ .cursor-ring, button:hover ~ .cursor-ring { width: 60px; height: 60px; }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 3px; }
  ::-webkit-scrollbar-track { background: var(--black); }
  ::-webkit-scrollbar-thumb { background: var(--gold); }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    padding: 0 5%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 72px;
    transition: background 0.4s, backdrop-filter 0.4s;
  }
  nav.scrolled {
    background: rgba(10,10,10,0.92);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(201,168,76,0.15);
  }
  .nav-logo-img {
    display: flex;
    align-items: center;
    text-decoration: none;
  }

  .nav-logo { color: var(--gold); }
  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
  .nav-links a {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--titanium);
    text-decoration: none;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-cta {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--black);
    background: var(--gold);
    padding: 10px 22px;
    text-decoration: none;
    transition: background 0.3s, transform 0.2s;
  }
  .nav-cta:hover { background: var(--gold-light); transform: translateY(-1px); }

  /* HERO */
  #hero {
    min-height: 100vh;
    position: relative;
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    overflow: hidden;
  }
  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 80% at 70% 50%, rgba(42,107,92,0.18) 0%, transparent 60%),
      radial-gradient(ellipse 40% 60% at 30% 30%, rgba(201,168,76,0.08) 0%, transparent 50%),
      linear-gradient(135deg, #0a0a0a 0%, #111111 50%, #0d1a16 100%);
  }
  .hero-grid-lines {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
    background-size: 80px 80px;
  }
  .hero-content {
    position: relative;
    z-index: 2;
    padding: 140px 5% 80px 8%;
  }
  .hero-eyebrow {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.3s forwards;
  }
  .hero-eyebrow-line {
    width: 40px;
    height: 1px;
    background: var(--gold);
  }
  .hero-eyebrow-text {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
  }
  .hero-title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    line-height: 0.92;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.5s forwards;
  }
  .hero-title .line1 { font-size: clamp(3rem, 6vw, 5.5rem); color: var(--white); display: block; }
  .hero-title .line2 { font-size: clamp(3.5rem, 7vw, 6.5rem); color: var(--gold); display: block; letter-spacing: -0.02em; }
  .hero-title .line3 { font-size: clamp(2rem, 4vw, 3.5rem); color: var(--light-gray); display: block; font-weight: 300; letter-spacing: 0.1em; font-style: italic; }
  .hero-desc {
    font-size: 0.95rem;
    line-height: 1.8;
    color: var(--titanium);
    max-width: 480px;
    margin-bottom: 2.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.7s forwards;
  }
  .hero-checks {
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
    margin-bottom: 2.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.9s forwards;
  }
  .hero-check {
    display: flex;
    align-items: center;
    gap: 12px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--light-gray);
  }
  .check-icon {
    width: 20px; height: 20px;
    border: 1px solid var(--gold);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    color: var(--gold);
    font-size: 0.6rem;
  }
  .hero-actions {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 1.1s forwards;
  }
  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: var(--gold);
    color: var(--black);
    font-family: 'Montserrat', sans-serif;
    font-size: 0.7rem;
    font-weight: 800;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    padding: 16px 32px;
    text-decoration: none;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s;
    cursor: none;
  }
  .btn-primary::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--gold-light);
    transform: translateX(-100%);
    transition: transform 0.3s;
  }
  .btn-primary:hover::before { transform: translateX(0); }
  .btn-primary:hover { transform: translateY(-2px); }
  .btn-primary span { position: relative; z-index: 1; }
  .btn-secondary {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--titanium);
    text-decoration: none;
    border-bottom: 1px solid rgba(136,136,136,0.3);
    padding-bottom: 2px;
    transition: color 0.3s, border-color 0.3s;
    cursor: none;
  }
  .btn-secondary:hover { color: var(--white); border-color: var(--white); }

  /* HERO VISUAL */
  .hero-visual {
    position: relative;
    z-index: 2;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .hero-photo-frame {
    width: 420px;
    height: 580px;
    position: relative;
  }
  .hero-photo-placeholder {
    width: 100%;
    height: 100%;
    background: linear-gradient(160deg, #1a2a24 0%, #0d1a15 40%, #111111 100%);
    position: relative;
    overflow: hidden;
    clip-path: polygon(0 0, 88% 0, 100% 8%, 100% 100%, 12% 100%, 0 92%);
  }
  .hero-photo-placeholder::before {
    content: 'FOTO\AMODELO\AHERO';
    white-space: pre;
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    color: rgba(201,168,76,0.2);
    text-align: center;
  }
  .hero-photo-placeholder .silhouette {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 260px;
    height: 480px;
  }
  .hero-photo-border {
    position: absolute;
    top: -8px; right: -8px;
    width: 200px; height: 200px;
    border-top: 1px solid var(--gold);
    border-right: 1px solid var(--gold);
  }
  .hero-photo-border-b {
    position: absolute;
    bottom: -8px; left: -8px;
    width: 200px; height: 200px;
    border-bottom: 1px solid var(--gold);
    border-left: 1px solid var(--gold);
  }
  .hero-badge {
    position: absolute;
    bottom: 40px;
    left: -60px;
    background: var(--carbon);
    border: 1px solid rgba(201,168,76,0.3);
    padding: 16px 20px;
    min-width: 180px;
  }
  .hero-badge-num {
    font-family: 'Montserrat', sans-serif;
    font-size: 2rem;
    font-weight: 900;
    color: var(--gold);
    line-height: 1;
  }
  .hero-badge-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--titanium);
    margin-top: 4px;
  }
  .hero-badge2 {
    position: absolute;
    top: 40px;
    right: -50px;
    background: var(--green-teal);
    padding: 12px 16px;
    text-align: center;
  }
  .hero-badge2-num {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.2rem;
    font-weight: 900;
    color: var(--white);
    line-height: 1;
  }
  .hero-badge2-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.7);
    margin-top: 3px;
  }

  /* COUNTDOWN */
  .countdown-bar {
    background: var(--mid);
    border-top: 1px solid rgba(201,168,76,0.12);
    padding: 18px 8%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }
  .countdown-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
  }
  .countdown-units {
    display: flex;
    gap: 1.5rem;
    align-items: center;
  }
  .countdown-unit {
    text-align: center;
  }
  .countdown-num {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.8rem;
    font-weight: 900;
    color: var(--white);
    line-height: 1;
    display: block;
  }
  .countdown-unit-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.5rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--titanium);
    margin-top: 2px;
  }
  .countdown-sep {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.5rem;
    font-weight: 300;
    color: var(--gold);
    margin-bottom: 12px;
  }
  .countdown-spots {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    color: var(--light-gray);
  }
  .countdown-spots strong { color: var(--gold-light); }

  /* STATS BAR */
  .stats-bar {
    padding: 60px 8%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background: rgba(201,168,76,0.1);
  }
  .stat-item {
    background: var(--black);
    padding: 40px 30px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .stat-item:hover { background: var(--carbon); }
  .stat-item::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    transform: scaleX(0);
    transition: transform 0.4s;
  }
  .stat-item:hover::before { transform: scaleX(1); }
  .stat-num {
    font-family: 'Montserrat', sans-serif;
    font-size: 2.8rem;
    font-weight: 900;
    color: var(--gold);
    line-height: 1;
    display: block;
  }
  .stat-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--titanium);
    margin-top: 8px;
    display: block;
  }

  /* SECTIONS */
  section { padding: 100px 8%; }

  .section-eyebrow {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 1.2rem;
  }
  .section-eyebrow-line {
    width: 32px;
    height: 1px;
    background: var(--gold);
  }
  .section-eyebrow-text {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    font-weight: 700;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
  }
  .section-title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    font-size: clamp(2rem, 4vw, 3.2rem);
    text-transform: uppercase;
    line-height: 0.95;
    margin-bottom: 1.5rem;
  }
  .section-title em {
    font-style: normal;
    color: var(--gold);
  }
  .section-sub {
    font-size: 0.9rem;
    line-height: 1.9;
    color: var(--titanium);
    max-width: 520px;
  }

  /* QUÉ INCLUYE */
  #incluye {
    background: var(--carbon);
    position: relative;
    overflow: hidden;
  }
  #incluye::before {
    content: '10';
    position: absolute;
    right: -2%;
    top: -10%;
    font-family: 'Montserrat', sans-serif;
    font-size: 28vw;
    font-weight: 900;
    color: rgba(201,168,76,0.03);
    line-height: 1;
    pointer-events: none;
    user-select: none;
  }
  .incluye-header {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: end;
    margin-bottom: 5rem;
  }
  .incluye-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: rgba(201,168,76,0.08);
  }
  .incluye-card {
    background: var(--dark);
    padding: 40px 30px;
    position: relative;
    overflow: hidden;
    transition: background 0.3s, transform 0.3s;
  }
  .incluye-card:hover { background: var(--mid); transform: translateY(-4px); }
  .incluye-card-num {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 700;
    letter-spacing: 0.3em;
    color: var(--gold);
    margin-bottom: 1.5rem;
  }
  .incluye-card-icon {
    width: 40px; height: 40px;
    margin-bottom: 1.5rem;
    color: var(--green-accent);
  }
  .incluye-card-icon svg { width: 100%; height: 100%; }
  .incluye-card-title {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.75rem;
    font-weight: 800;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--white);
    margin-bottom: 0.8rem;
  }
  .incluye-card-desc {
    font-size: 0.78rem;
    line-height: 1.8;
    color: var(--titanium);
  }
  .incluye-card-items {
    list-style: none;
    margin-top: 1rem;
  }
  .incluye-card-items li {
    font-size: 0.72rem;
    color: var(--titanium);
    padding: 4px 0;
    padding-left: 14px;
    position: relative;
    line-height: 1.5;
  }
  .incluye-card-items li::before {
    content: '—';
    position: absolute;
    left: 0;
    color: var(--gold);
    font-size: 0.6rem;
  }

  /* PROCESO */
  #proceso {
    position: relative;
  }
  .proceso-header {
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    gap: 4rem;
    margin-bottom: 5rem;
  }
  .proceso-timeline {
    position: relative;
  }
  .proceso-line {
    position: absolute;
    left: 24px;
    top: 40px;
    bottom: 40px;
    width: 1px;
    background: linear-gradient(to bottom, var(--gold), var(--green-teal), var(--gold));
  }
  .proceso-steps {
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .proceso-step {
    display: grid;
    grid-template-columns: 48px 1fr;
    gap: 2rem;
    align-items: start;
    padding: 30px 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    position: relative;
    opacity: 0;
    transform: translateX(-20px);
    transition: opacity 0.5s, transform 0.5s;
  }
  .proceso-step.visible { opacity: 1; transform: translateX(0); }
  .proceso-dot {
    width: 48px; height: 48px;
    border: 1px solid var(--gold);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    color: var(--gold);
    background: var(--black);
    flex-shrink: 0;
    position: relative;
    z-index: 1;
    transition: background 0.3s, color 0.3s;
  }
  .proceso-step:hover .proceso-dot {
    background: var(--gold);
    color: var(--black);
  }
  .proceso-step-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 700;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--green-accent);
    margin-bottom: 6px;
  }
  .proceso-step-title {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.85rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--white);
    margin-bottom: 6px;
  }
  .proceso-step-desc {
    font-size: 0.78rem;
    line-height: 1.7;
    color: var(--titanium);
  }
  .proceso-visual {
    position: sticky;
    top: 120px;
  }
  .proceso-card-visual {
    background: var(--carbon);
    border: 1px solid rgba(201,168,76,0.12);
    padding: 40px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .proceso-card-visual::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold), var(--green-accent), transparent);
  }
  .semana-display {
    font-family: 'Montserrat', sans-serif;
    font-size: 5rem;
    font-weight: 900;
    color: var(--gold);
    opacity: 0.2;
    line-height: 1;
  }
  .proceso-card-title {
    font-family: 'Montserrat', sans-serif;
    font-size: 1rem;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    color: var(--white);
    margin: 1rem 0 0.5rem;
  }
  .proceso-card-sub {
    font-size: 0.8rem;
    color: var(--titanium);
    line-height: 1.8;
  }

  /* PRECIO */
  #precio {
    background: var(--carbon);
  }
  .precio-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    align-items: center;
  }
  .precio-card {
    border: 1px solid rgba(201,168,76,0.25);
    padding: 50px 40px;
    position: relative;
    overflow: hidden;
    background: linear-gradient(135deg, rgba(201,168,76,0.05) 0%, transparent 60%);
  }
  .precio-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--gold), var(--green-accent));
  }
  .precio-label {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    font-weight: 700;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.5rem;
  }
  .precio-amount {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    font-size: 4rem;
    color: var(--white);
    line-height: 1;
    margin-bottom: 0.5rem;
  }
  .precio-amount span { color: var(--gold); }
  .precio-period {
    font-size: 0.75rem;
    color: var(--titanium);
    margin-bottom: 2rem;
    font-family: 'Montserrat', sans-serif;
    letter-spacing: 0.1em;
  }
  .precio-divider {
    width: 100%;
    height: 1px;
    background: rgba(201,168,76,0.15);
    margin-bottom: 2rem;
  }
  .precio-features {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.8rem;
    margin-bottom: 2.5rem;
  }
  .precio-features li {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 0.78rem;
    color: var(--light-gray);
    line-height: 1.6;
  }
  .precio-features li::before {
    content: '✓';
    color: var(--green-accent);
    font-weight: 700;
    flex-shrink: 0;
    margin-top: 1px;
  }
  .precio-note {
    font-size: 0.65rem;
    color: var(--titanium);
    font-style: italic;
  }

  /* PREMIO */
  #premio {
    position: relative;
    min-height: 600px;
    display: flex;
    align-items: center;
    overflow: hidden;
    padding: 100px 8%;
  }
  .premio-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 100% at 50% 50%, rgba(201,168,76,0.12) 0%, transparent 70%),
      linear-gradient(135deg, #0d1208 0%, #0a0a0a 40%, #1a1000 100%);
  }
  .premio-content {
    position: relative;
    z-index: 1;
    text-align: center;
    width: 100%;
  }
  .premio-eyebrow {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.5rem;
  }
  .premio-title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    font-size: clamp(2.5rem, 6vw, 5rem);
    text-transform: uppercase;
    line-height: 0.9;
    margin-bottom: 1.5rem;
    color: var(--white);
  }
  .premio-amount {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    font-size: clamp(4rem, 10vw, 9rem);
    color: var(--gold);
    line-height: 0.85;
    display: block;
    margin: 1rem 0;
    text-shadow: 0 0 80px rgba(201,168,76,0.3);
  }
  .premio-subtitle {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--titanium);
    margin-bottom: 3rem;
  }
  .premio-items {
    display: flex;
    justify-content: center;
    gap: 3rem;
    flex-wrap: wrap;
    margin-bottom: 3rem;
  }
  .premio-item {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--light-gray);
    position: relative;
  }
  .premio-item::before {
    content: '◆';
    color: var(--gold);
    margin-right: 8px;
    font-size: 0.4rem;
    vertical-align: middle;
  }
  .premio-fine {
    font-size: 0.65rem;
    color: var(--titanium);
    font-style: italic;
  }

  /* APP */
  #app {
    background: var(--dark);
    overflow: hidden;
    position: relative;
  }
  #app::after {
    content: '';
    position: absolute;
    right: -100px; top: -100px;
    width: 500px; height: 500px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(42,107,92,0.12) 0%, transparent 70%);
    pointer-events: none;
  }
  .app-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
  }
  .app-phone {
    display: flex;
    justify-content: center;
    position: relative;
  }
  .phone-frame {
    width: 280px;
    height: 560px;
    background: var(--carbon);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 36px;
    position: relative;
    overflow: hidden;
    box-shadow: 0 40px 80px rgba(0,0,0,0.5), inset 0 0 0 1px rgba(255,255,255,0.05);
  }
  .phone-notch {
    width: 80px;
    height: 20px;
    background: var(--black);
    border-radius: 0 0 12px 12px;
    position: absolute;
    top: 0; left: 50%;
    transform: translateX(-50%);
    z-index: 2;
  }
  .phone-screen {
    padding: 30px 16px 20px;
    height: 100%;
  }
  .phone-status {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    padding-top: 10px;
  }
  .phone-time {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 700;
    color: var(--white);
  }
  .phone-logo {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    color: var(--gold);
    text-align: center;
  }
  .phone-greeting {
    font-size: 0.65rem;
    color: var(--titanium);
    margin-bottom: 4px;
  }
  .phone-name {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 16px;
  }
  .phone-week-bar {
    background: linear-gradient(90deg, var(--green-teal), var(--gold));
    height: 3px;
    border-radius: 2px;
    margin-bottom: 4px;
    position: relative;
  }
  .phone-week-bar::after {
    content: 'SEMANA 4 / 10';
    position: absolute;
    right: 0;
    top: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.45rem;
    font-weight: 700;
    color: var(--gold);
    letter-spacing: 0.1em;
  }
  .phone-week-bar-bg {
    height: 3px;
    background: rgba(255,255,255,0.05);
    border-radius: 2px;
    margin-bottom: 20px;
  }
  .phone-metrics {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    margin-bottom: 12px;
  }
  .phone-metric {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(201,168,76,0.1);
    padding: 10px;
    border-radius: 8px;
  }
  .phone-metric-val {
    font-family: 'Montserrat', sans-serif;
    font-size: 1rem;
    font-weight: 900;
    color: var(--white);
    line-height: 1;
  }
  .phone-metric-lbl {
    font-size: 0.45rem;
    font-family: 'Montserrat', sans-serif;
    color: var(--titanium);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-top: 2px;
  }
  .phone-metric-chg {
    font-size: 0.5rem;
    color: var(--green-accent);
    font-weight: 600;
  }
  .phone-section-title {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--gold);
    margin: 12px 0 8px;
  }
  .phone-task {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
  }
  .phone-task-check {
    width: 14px; height: 14px;
    border: 1px solid;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    font-size: 0.45rem;
  }
  .phone-task-check.done { border-color: var(--green-accent); color: var(--green-accent); }
  .phone-task-check.todo { border-color: rgba(255,255,255,0.2); color: transparent; }
  .phone-task-text {
    font-size: 0.6rem;
    color: var(--light-gray);
  }
  .phone-nav {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    background: rgba(10,10,10,0.95);
    border-top: 1px solid rgba(201,168,76,0.1);
    padding: 10px 0;
    display: flex;
    justify-content: space-around;
  }
  .phone-nav-item {
    text-align: center;
    font-size: 0.4rem;
    font-family: 'Montserrat', sans-serif;
    letter-spacing: 0.05em;
    color: var(--titanium);
  }
  .phone-nav-item.active { color: var(--gold); }
  .phone-nav-icon {
    font-size: 0.9rem;
    display: block;
    margin-bottom: 2px;
  }
  .phone-glow {
    position: absolute;
    bottom: -40px; left: 50%;
    transform: translateX(-50%);
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(42,107,92,0.3) 0%, transparent 70%);
    pointer-events: none;
  }
  .app-features {
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .app-feature {
    padding: 24px 0;
    border-bottom: 1px solid rgba(255,255,255,0.05);
    display: grid;
    grid-template-columns: 48px 1fr;
    gap: 1.5rem;
    align-items: start;
    transition: padding-left 0.3s;
  }
  .app-feature:hover { padding-left: 8px; }
  .app-feature-icon {
    width: 48px; height: 48px;
    background: rgba(201,168,76,0.06);
    border: 1px solid rgba(201,168,76,0.15);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    flex-shrink: 0;
  }
  .app-feature-title {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.75rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--white);
    margin-bottom: 5px;
  }
  .app-feature-desc {
    font-size: 0.75rem;
    line-height: 1.7;
    color: var(--titanium);
  }

  /* TESTIMONIOS PLACEHOLDER */
  #testimonios {
    background: var(--carbon);
  }
  .testimonios-header {
    text-align: center;
    margin-bottom: 4rem;
  }
  .testimonios-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: rgba(201,168,76,0.08);
  }
  .testimonio-card {
    background: var(--dark);
    padding: 40px 30px;
    position: relative;
    overflow: hidden;
  }
  .testimonio-quote {
    font-family: 'Montserrat', sans-serif;
    font-size: 3rem;
    font-weight: 900;
    color: var(--gold);
    opacity: 0.3;
    line-height: 0.8;
    margin-bottom: 1rem;
  }
  .testimonio-text {
    font-size: 0.82rem;
    line-height: 1.9;
    color: var(--light-gray);
    margin-bottom: 2rem;
    font-style: italic;
  }
  .testimonio-author {
    display: flex;
    align-items: center;
    gap: 14px;
  }
  .testimonio-avatar {
    width: 44px; height: 44px;
    background: linear-gradient(135deg, var(--green-teal), var(--gold));
    border-radius: 50%;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 0.8rem;
    color: var(--black);
  }
  .testimonio-name {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--white);
  }
  .testimonio-meta {
    font-size: 0.65rem;
    color: var(--titanium);
    margin-top: 2px;
  }
  .testimonio-result {
    position: absolute;
    top: 30px; right: 30px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--green-accent);
    border: 1px solid var(--green-accent);
    padding: 4px 8px;
  }

  /* FAQ */
  #faq {
    position: relative;
  }
  .faq-inner {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 5rem;
    align-items: start;
  }
  .faq-list {
    display: flex;
    flex-direction: column;
    gap: 0;
  }
  .faq-item {
    border-bottom: 1px solid rgba(255,255,255,0.06);
    overflow: hidden;
  }
  .faq-question {
    width: 100%;
    background: none;
    border: none;
    color: var(--white);
    font-family: 'Montserrat', sans-serif;
    font-size: 0.78rem;
    font-weight: 600;
    text-align: left;
    padding: 20px 0;
    cursor: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    transition: color 0.3s;
  }
  .faq-question:hover { color: var(--gold); }
  .faq-question.open { color: var(--gold); }
  .faq-icon {
    flex-shrink: 0;
    width: 20px; height: 20px;
    border: 1px solid currentColor;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.7rem;
    transition: transform 0.3s;
  }
  .faq-question.open .faq-icon { transform: rotate(45deg); }
  .faq-answer {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.4s ease, padding 0.3s;
  }
  .faq-answer.open { max-height: 300px; padding-bottom: 16px; }
  .faq-answer p {
    font-size: 0.78rem;
    line-height: 1.9;
    color: var(--titanium);
  }

  /* CTA FINAL */
  #cta {
    background: linear-gradient(135deg, #0a0f08 0%, var(--dark) 50%, #0f0a00 100%);
    position: relative;
    overflow: hidden;
    text-align: center;
    padding: 120px 8%;
  }
  #cta::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(201,168,76,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
  }
  .cta-inner { position: relative; z-index: 1; }
  .cta-restrict {
    font-size: 0.65rem;
    color: var(--titanium);
    font-style: italic;
    margin-top: 1.5rem;
  }
  .cta-contact {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 3rem;
    margin-top: 3rem;
    flex-wrap: wrap;
  }
  .cta-contact-item {
    display: flex;
    align-items: center;
    gap: 10px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--titanium);
    text-decoration: none;
    transition: color 0.3s;
    cursor: none;
  }
  .cta-contact-item:hover { color: var(--gold); }
  .cta-contact-icon {
    font-size: 1.1rem;
  }

  /* FOOTER */
  footer {
    background: var(--black);
    border-top: 1px solid rgba(201,168,76,0.1);
    padding: 40px 8%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }
  .footer-logo {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 0.9rem;
    letter-spacing: 0.2em;
    color: var(--white);
  }
  .footer-logo span { color: var(--gold); }
  .footer-legal {
    font-size: 0.62rem;
    color: var(--titanium);
    font-style: italic;
  }
  .footer-links {
    display: flex;
    gap: 1.5rem;
  }
  .footer-links a {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.55rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--titanium);
    text-decoration: none;
    transition: color 0.3s;
    cursor: none;
  }
  .footer-links a:hover { color: var(--gold); }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes shimmer {
    0% { background-position: -200% center; }
    100% { background-position: 200% center; }
  }
  @keyframes pulse-gold {
    0%, 100% { box-shadow: 0 0 0 0 rgba(201,168,76,0.4); }
    50% { box-shadow: 0 0 0 12px rgba(201,168,76,0); }
  }
  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-12px); }
  }

  .animate-on-scroll {
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.7s, transform 0.7s;
  }
  .animate-on-scroll.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .gold-shimmer {
    background: linear-gradient(90deg, var(--gold), var(--gold-pale), var(--gold), var(--gold-light), var(--gold));
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: shimmer 4s linear infinite;
  }

  /* FLOATING WA BUTTON */
  .wa-float {
    position: fixed;
    bottom: 30px;
    right: 30px;
    z-index: 500;
    background: #25D366;
    color: white;
    width: 56px;
    height: 56px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.6rem;
    text-decoration: none;
    box-shadow: 0 4px 20px rgba(37,211,102,0.4);
    animation: pulse-gold 2.5s infinite;
    transition: transform 0.2s;
    cursor: none;
  }
  .wa-float:hover { transform: scale(1.1); }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    #hero { grid-template-columns: 1fr; }
    .hero-visual { display: none; }
    .hero-content { padding: 120px 6% 60px; }
    .incluye-header { grid-template-columns: 1fr; }
    .incluye-grid { grid-template-columns: 1fr; }
    .proceso-header { grid-template-columns: 1fr; }
    .proceso-visual { display: none; }
    .precio-inner { grid-template-columns: 1fr; }
    .app-inner { grid-template-columns: 1fr; }
    .testimonios-grid { grid-template-columns: 1fr; }
    .faq-inner { grid-template-columns: 1fr; }
    .stats-bar { grid-template-columns: repeat(2, 1fr); }
    .nav-links { display: none; }
  }

  /* PROGRESS BAR */
  .progress-bar {
    position: fixed;
    top: 0;
    left: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--gold), var(--green-accent));
    z-index: 2000;
    transition: width 0.1s;
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>
<div class="progress-bar" id="progressBar"></div>

<!-- NAV -->
<nav id="navbar">
  <a href="#" class="nav-logo-img"><img src="data:image/png;base64,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STMTVy5j3PVx8srhcXkb2k69nBXo4nu9Rd0NVVWIpcNegqxM8k9Pc9PaM9Xm40Oe0M7ejimc1W5nw6O/t6KuZzGMR3jxb2n2q5MTeuclizR967enlo/KfFi5nV56ztvNyzFHecZ8vfLe0+z509eqruU2rFE+3du4pt0/n4z7odrf3badJamjb7E627HSq5ciabX5R3q/s85umo1WtvRe1l6apzPJTMYoo+WntDHyVroz1W60aan1O11V0UxmKtRVHLcrj/R/LHv7uiuTTV1iZnPu/u5tZTNdMU00z07z4R+bj0Vi7raqbGisV6q/OYmaMxbpj31doPtWpVnPtximfOejveGuH9bu1U3LERp9JmKfXV0zmrziinvMvYcDejDX7pft112atZVTOZzHLp7X5/xS+ybZtWwcKxF65jVa23Tnmqj2KPhBqfpO0jqOBPRhpdDt9q9udH2XRRi5VRcnN2/76p8vc2uP+MNt2uiLOjmmuaaeW1ap6RR8HlOOuPtXqKq7Ggv9apmPWc3s0fDzfK911tyu9NdzUV3blXWquqe644bZuW3Z73vut3HUV39VcpnrmKaZ7PM63XRP8WZmXBq9RzT0nt/d1Wpv81XNDvhixcnLf1M1TM1dWjfvzVOfFw3b/SWpcuS7Yxzyyct69MT0a9d6rDiuXJa9yurHSYbkcrk55uzM94T1mJzlqTcnxPWZ8GtM9nY27vTLctXY9nMumt1zju2rVU9OucJcWpk72zd9qPJ2Wk1M0VxPV56xd6Q7Cxd97ncW5XsNv1sxXmJqjt4vVbZd0es0N/bNxuTTt2riKbtUd7NURPJdj30z/WJmHznR3piend3236iuiqKontiYp8M57uGU9dca0d42zVbZuFzQ66iIvxMclVP3LlHhcpnxif7NKaeuOWY8X0jb42zftro2fc7vqZtVVTodXFOatNVV4T50TPePDvDx/EOza7YtxnRbhaii5V1oqjrRep/npq8Yc8pr6dI6umZp7VY6d5dzwnxJq+HNyp11ufWWao5NRamfZu0eP5ulvRyRnMTns4+aeSI5cw41rt7p98nTaPddot73tdybukvRnEd6J8qvKXRanTTEzE94nq8NwVxbreHrtz1UzVpbnS/Zq60Vx+k+99B23dto36iK9BqKKLkz1tXKoiY90T4larqbulmZcf2TE5l6i5su4c3s6G/X16TTTmGN3ZdVbp9ZqKaNJbjvVfrimI/uzckkecjTxHtRn4RDYo0dGm0le4bhdp02io+9cnvXPhTRHjV7jdOI+G9jt1Tau/4zro+7aszizTP+urx+EPAb/wAQ7lvOujVa69Fc0dLduiMUWY8qaf17szJrTc4n3W5rbvrL0xp9NR002liczR/qqx3qn+zylmi7rtbTbs2Zm7dq5YtUe18G9pNv1+8bhTZ0Vmuu9c/hjt8Znwh9i9HvBOh2HRV63WXLMXaYzf1df3LX+mjzn4O2Oe11px+jLhGxs+ku6rVXIp1PL/vd7wsUf9nT511ds+DPjTiqvU4sW6KbUUU+rt247W6Y/XzXjLiixFH+H7Ti3prf+XEx1mfGqrzmXzfctVVNybk1zMz4zPX83TH2sZZeGu1VXLM1YqnMxl0Ot1M4mGer1PTv4un1eonM9XbHFwubi1Vyaqu7r9RPiuouVc3dpX7k5xl3kcssmF+ufNrV3ZjPVjeuTmYiWrduYju6SOVctd2Z8XDXcnHdxes6d3HVV7116jkquzHjLGq517uCuphNUy31LdNma58JYTXVnu4ZqnxljNU+ErpnbZ5p8ZYzd6tfmqJqnxXqbc/rcSyi5EtXmhec6rtszcjzT1nva3PMk1SnU22PW9e6zd6d2rzSsVL1NtiL+PDuy9bHdq85Nf5HVNuequJlIra8VLzfFdG2zz+89ZPm1uafNlFRpZWzF3Ed19ZGPe1czlYqnPdNLa2vWREJF73tfOfFjM48Tqxtt03ZntK88xnq0ornPSViurzNLK2/WecsfWe9rTVPmnNPmdTs2puT4VJ6+qejWzPmZnMdTr6XJsRcqWK583BmfMyvRjbYi5V5rNyprxPuWOqdWpWxFyqfJnTciI692nM1fzLzdPvJcV23ouUk3KfNo83vXM+E4Tqu25E+9Yrx3qakVT3momqe81ZOo3aLmf4mUV+9oU1zE92XrKvODRtvc0z/ABHPHjLR9ZX5r62rPVNDeiuJ6ZZRVHm6+bs+/wDoeumPM6q7HnjzT1kebR9bOO5FyfNOo3aruO0sJvVZ+9LV5s+KTVjxOo2vW1fzSzi9PbLS9ZC8/TOTQ3ZuzjuRdnzaU3M+KRWdRvTc97Cb0w1Kq2M1z4SdRuTe+LiqvS1+efNjVVPmvU25/WZnuk3fe1ZqnPdJqnzWRjs2pu9O7H1rWmZx3TPvamKdmzNyZcdVUuPPRJqg6t72ymr3saqvewqqY83fq31RZnqxmWMymVkNLM9WMkyixZFyVIZVQADM+bKiWMMqe4lZgDBAQMVFgIWAMR5Nra/xFXyz9YazZ2v8RV8s/WCNR2QDagAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAAkKAkKAZI7hHcGdM9XNRLgp+85qcMVG3aqhsUVYnu0bdceTnt1Q5WDsrVyejbs3Il1dqrs27FWJc7G3b6W5irrLt9JqYmYp7R73QWauuW5YvctUREueeLeF19vW6HcLlqqmaK485x4PSbXqtPf5KblzkmZ+/HSYn3x5Pn1nVYqh3W26uM57uGeDvhm9rqNNVapi7m3etVR9+3VzUTPw70yxtW4qjNOJnPfPZobXu1zTxHq8U0x1mfP4vW7FHC+64o19yds1dfSi9ZqxTVPvifZ+jy5cbrMnUXYiImKa4bmy79u+1XJnQ6+5YzHSInNPwmHqL3o93e57e07pt24U4zFNcerq/r2dBuXCHFeimftHD2qn/Xp8Vw43idZlHe2vSZqIiijetn0msqmOtyzPJV/Ro7jxHwprrs3rm1blp6qu8WppxLyup2jfKc1Xdk3KaafH1MzhoXI1FMctWm1lGPCbUxhzw47Ftxegu7vw7FeaNJukx/qmIYRv+zxzTZ2e9cnHszdv4j+kOitUXruKbek1Vc++mWdjbt3u3eW3tl2mfOaZenHDKudsdjf4i1tdMRpdLodLiOk0W+aqPzl1Gr1Op1Nym5fu1Xa4j2qq6sxH5dneaLg3ibW1xFrS8kz06W5ql6LQ+iHfdVNudXZ1Exnr62uLdEtXCxnvHzG9qtNaxnU0zXPTERmqZ+DZ0W37tuOZ0mguRan/rtTPJR8evWX3bZvRbsG36abm4bho9Nf8bentxcqj/vT4vQaTQcBbTYru1U0aiuI+9qK84n3QTG6a7x8Z4S9FGt327Hro+1TmJzXV6qxEefnU+qbVwXw3w1RRTulydZdtz0sWqOSxR+Ud/zdZv8A6RNh0VEU6S56y5R0t0WPo+d8T+kDeN0uVUU50lGZ7TmufixMcsvtnb6vxH6Q9Htukr0tmLVFER+7tWcRMe7EPkXE3Fut3WaqaqvVWp7UUz1n4y8ld13Ncmar0zVPeqesz+bR1mtiZmOeXbDi0xlpua3XzNGJuRPTvh0t/VRNU5nMy4NTq5nLr71+Inmz2h3xxcrk2r+pomJiOjrb12c4iqHDXfmqJme7Tu3urrji53JzXLsxExlq3LtXXq467vectW5cmZzzNzFjs2K7kuC5PWfalxzcnHdx1XIdNMuXm96xXnpzNea4Y01xlWa36K5iMZc9m51zl19NxyU3PeNYu4s3YzGJb1i9GO7oLV2Yx1blq7iY9pyyjcek097pmJdppdVOY9qXmdPqMRiHYaa/VGHGz10lex27VTTXFdFcxy9cPfcNbntnEGkq2PiKxF7S1RPqqpn95aq86Ku9M/2l8j0Wqqjm/J2un11VF3Hv6dXPLF1xyd9xpwFvWzxXrNJP+KbXTHs6i3T7VqPKunz98dHjqeszERn6vpnC3H2u265RTqLvrbEezNyunm5afGKo/ih6rWcNcCcZUfbLdNO26q5Tzev01WLVc+ePB589x1klfELFuYp5o5omZxMua3Rat0RzWusTnNPSZl9M13oh3eixTXtuv0+vopnMzRVHNHXxjxdPf9G/FlFyaaturq98UyzvbVdBpt+3rT0zTp911duiP4KL1XT+7p903DVaq5z6q9rblU/9pmqJe4s+jriarEfYbtE+OKJd9tHog3K7NN7X1TYo/wDeXP0WYMzJ8k0s6m/TV6nTTmPLpn8nqeH+Dtw3GKK79i7Tz9opp6z8Z8H13RcEcN7Viu/q7Vdyn+GmMtTirinb9u0FWi0tyiqqYxTRbmIq/rBcGu7S2PbNs4b01Vu9FE3MdbVE9/ml0nFXFlWsmNPauW6ot9KYpjFu3Hujz97y247vrNXTi5VFu1HemJ9qXUanU00xmIxGOmG8MNM3Ntay/M81UXKpme/NPV0G4aqf5smr1k45s1Tl1GsvZnmxLvji4ZZLe1HNEw6/UXs9C7exM9Wlfvw6zFyq3rseUtG7djMzPRNRfzPScNG9czMxno64xzZXbvWZhrXa89pK6v6OCuqOrpIi+siIwwquOGqevdjMukxZtclVeY7sYrywnCZamLNrOqrqx5pYVSkTBpdOXmJlx80HNBo05IqXmcXN5JNRo05Zqg5ocOViV0ack1eSczjmTJo05YqYzVnxYZMml6s4lZqnzYRJk0mmcVSc0+bDJk0OSK5815/e4oxK9fA0OWap80zLj9oiZ8TSWOTJlhlJqTSacmUmWEVpNUeRpdOSJXLiiqPgsTnxNL1cs3IhOfLjwT2U05aa+vSVmufNwxOFz7yw05OefNJqnPdx595MpoZzXMMouVT4uLOIXm6GhzxXPaZXna8VdSapNLK2OY5ujXiqcrzSliObmSbnXvLi5kqq6khuuaLn+qV9b/qlwc3UirzXS7rY558JWK5x3a/P4ZXn6d0uLTY5+ndJq85cPP5STVKdUtrmiuMrNXlLXmUmrp3OqW1zc8/zHrMeLgykysxJWx6ye+T1kuCmrouTSub1k+bGa/e48pKzFmuTnTLDOJSajTOtuSaky48+8iffBpZi5Jq6MObr3MsavFZFJmcmWKT3WNsplAUAAEVJAhUhQZR2KSMYWnxSpVjsdSFGABKVlSsJSqIuGztn4ir5f1hreDZ2z/Pq+X9YIsdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAAAmVTCgLShkGdOMs6ZcUMss1muamXPbqhqxLltywztu0T5Nm1XMd2jRW56a8x06M1vbsrd2qI7uexdxOZl1dqrr1bdFcRDlY3HcWrtPSYdppb0REYnDzmnude7sdPfinHXLnY6Y16nTanrDuNDqqeSYnlqz3ie0vH27/AGmHY6HU8vtTLjcHSZPZ6Lc9TpcRpdfq9JEfw27k4/o9RsnpB4n0GItbjOotx3i5PX+75pb1sT1z+Tnta7EY5oZvHtvs+77b6Y4pm3TuG31xVPeeSOWf6NjUek3hjUXJ9fpNJTnwn/5Pg1Otpp7XMe6HLG4RPTFFXxYvE12fedDx7wnNymbek0cT5xMT+ja1HpG2SxTm1OktT50xEz9HwCnXU46U0ZYVa+Y/hpj8oXGWMvs+u9LWks5qtauKqonpFqzMy6HdPSlrdZTzRZ1dc46TX7MPlt7cq47Rlq16uuZ9qqcd8Zb1az9Pc6/jHd9ZifXUaarzjrM/m6PU6/UamqftF+7XMeNVcvP1ayYiZie09nDe19XPM9pyswXs7W9copqxHaIaeo1FMZimrDrbuqmrrzdZ97Wr1ER1rrg6M9m1fvdc5al6/Ez1lwXdTRMTiqJaF+97XSW+rNrn1N7vhoXLsVd3Hdvd/NrXLvR0kc7XNcuREzHVq13I65cdd2evVr11z8W9ObOurPi4q6oYV1uGuv3tSDkquRHRxzXHg4a6urGamtM2ufMGYy4YqnHcmpZGd7bEVxDkory04qlyUVYXquPjft19urbtVxmMust19nPRdxLnlG9u4s3YzEOwtXZ6dXQ2b2Jjzbtm9VzR1c7G5Xf6W/y9Kp8XYW9RnOZdBau5iJy2rV+evVzuLpK9FpdVVmPbxDt9JrZ0eoo1Fm9VamfvTbnGZ98eLyFrUYmOrdt6yZjHSZ83LLDbeOdj6Nt3HO7WL0RVVbqp7c1uqaKsO9p9I+ts0+zrdxo+FyZfJbepiY9ucy5betqomO0x72Pia77fU6/SbufJMRrdyufGqYaGq9IG736fZmqMf9tVl8/q1nPMz5terUzTPSZw10Ts9RuHEm6auZ9ZrKuWe9NHSHUzqLcZqnPNPefGXT16zE4mqYcNespxPtTMtdDu7a/qKZ7S63VarvHM1K9XMR0aF/VZmctddJcm1e1Ez07w6/WX5xj3uK5fnPsz0aequTMZy3jHO5MtRdiIy0rl2Jju4797mzT2atdzEd3SYudrO9XDVrqjK3K8x3a9dTpIxtnVV0cFc9Uqr97jmp0mKWkzDGZSZYz3b0mtrzEzDGCZaWRKpQBoAAiQSQUSFAI7gDLEZXEeTDPmsyCziGOQAyZAFiZg5pYyoMsz5pFU+aALMzKAC9EzGQBTOPFiYBlzT5mZ80AMz5mZ8wAzPmZnzAFzPmmZAFiejLLGOyTIaZZJliBplljMznuAGZMz5gBmfNZlAFiZyy5mADkiYx1Y1+5jmTIGZMyALmfM5p80AZc3ROZANLkmUAXMLmPBiAuUyAAAAAAAAAAAM6YjlEiehE5SiwBhGGQLEFSkMmK5RFbW2f59Xy/rDUy29s/EVfJP1gn2sdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAmVYsgAABJUF6L+TEBnEuSiXDlnRVDNjNjYpnq5qKp82nRX7Tmpr692LEbdNc+Eue1cq8WnRXGXPbrjDnY237VzE9JbVq9Ed5dZRW5qLnvYsald1b1M+EtzS6nHSZdHZue9t2r0UxjOXOxuZO8o1HXLmp1XTpDpI1MRDkt6mE007unUzHerDkjU5/i/s6anU0uSnU0+9n0ldzGpj+aUq1ET/FLq6dVTjxSdTBpezfqvRGZy469RGO7r69T0nq4Lt+fCWupcnZVajpPtQ4q9R73W1X5w4q9TCs7djXqYjxj+jXu34mc5aVWo6OKu/jqG21cvTjwat27MTnLguXs/m4a68zjLWmK5bt3m6NWq51xMsbtXWergqqx1y3Im2ddeY6y4qq/ewm5Hg4q6ustyMuSqvo4qq89GMz0cdVTUiVnM9e6TLDPRMt9WGeTmcc1e8io0mnLTLOJcUVRheaEGzbr6Q5qa4jwy06Koc1uuM4Suk+m5ROZictyzcxPd19FcR8HLTchysXbtrd6nEYnDZtXo8JdPavREREtmi95SxY1K7i3e97Yt35/mdLRqIjxbFF+PNjTUyd1Rfqx0qZ036/GXUW9REQ5ftUGm9uynUT5ld3MZmuXWTqGNWpnGE0bdhXejzmXBXqIju0Jv5qzM4cV2/Ge6yM2t2vVYy07l+Zmcz0at2/Ez3cNV2Z7TC9Wbk2bt6PCWtdu5ju4qrnnLhrrjDcxY+2N2vEuCuvotyvplwV1dHSRCuvDiqqyVVQwmYb6sX7SphM4nDKZYTPVuEmyZTuxqRp0Z497EAAAAAAAAABJIBQAAAAAAAAAAAAASFAAAAAAAAAAAAAAAAAASQCSFAAAAAAAAAAAAAAAAAAARQAAAAAZUMWVBUrLEE91RhlYVDIlZRhEzCwIYbm2R/vFXX+CfrDTbe1/iavk/WFix2QDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoACYMqmAMqmFAABJViyAI6B0BlDkpmcuPLKKoZ0zfXNTVhzW6+jWiWdNWGE7Nymr3uaipo0V+9z0VMWNRu0V48Wxauzh19NbkpuzHZz0rf8AX+Dkt3583Xes692dN6Y7QdWuzsPtXXGf7OWjUVT4uuovdXLTdWxduxi9OO7Gb8+bS9bP5MZuR5ufptuVX569XDcvT5tabkz2cVdyc+TUTs2ar3vYV3fe1aq583HVXPm11TbYqvT5sJuz5teapYzUdTbYquzj7ziqrmfFxVVcssKrkzPdqYM9mddyfNw1VTPixqq97jmvq6dUtZVVMJqY1SxmWtJtlNU47se6RiUzjsujS1Mckz0RprSrHdjlYlFZLDDmWKuiaZ05InEuSmfFwxOZyziU0srnprnzc1FbUpmcw5YlmxW3RXDmpudOktGmZ83JTVjxc9DeouY8XLF7r4uui7EMqb/U6Dtabs4zEr66fN1fr581i9nxTqvZ2nr6vNhVqKv5nXxcmfFlzTjuzpdtuq/73DdvTHWOrXqrnLHnx1n+hIlclV+ZnMsKruXFXXEuOqvPi3pHLVc97Ca+jhqq97Cap82pE25a6pw4ap80qqlx1VS3In7WqWPMkywz1a0WM5lhKzMI01BJUBPAhQAAAAAAAAAAAAAAAAAAAAASVAAAAAAASVAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAASO6gAAAAAAAyoYrbSlZ5TK+DHKMMwCgsIsd0Sja2v8TV8n6w1W1tf4mr5P1hYR2YDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoAAkqAAACZUEwoAAALgXKIyiplTLiZIlxckVOaivHeWvHmsVQnUjbi5BFz3tf8zmiGOrVbdNzPi5Yr97Sor7ORnrU226Lk57uSLnvaNNcxLkivodTba9bOMZY1XOvdrc3vSa00dmz6z3pXcz4taa+vdeeDqrkmqc92NVU5cc19UqqyuhyTU46q8T3Y1VOK5X1akZcldeZYVVx4OOauiZbSs5qY5Y5JkNLOMMFmejBVkJnEiK00CSQAonUFE6r1BaZ8GUSwhlCMs6apclNXm4oMou3Pz9WXP07tbmZRUlxTbnirz7M6a6Ya3N1XLK7bXPThYrp8OjU5vOViqPNNG25Fz3r6yY6ZakTELNZ0TbnruTnuxi7iXDNSc0L1WVnXdnyYTWwmphMrMVck1MZn3sIkjqumbF5ssJlZYy3CGQSe40oAAAAYAAAAABYhJAAAAAEhQAABJUAAAAAAAAAAAAAAAAAAASV6gBgAAAAAAAE8VAEkjIKAAB4AHgYURE8WUpMYkUAAE6nUFAAABPioAAAAALbRlRAVZ7JDKYSlGYs9lRWUpC+KR3WO4lG3tf4mr5P1hqNravxNXyfrCwjswGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groBJUUAAAAABMKAAAAAGQAWGURVPaDkmJmIx0d9wfwxuvEmv+xbbpa7tU4zXnlot++qZZtkm6sm3R+GMJEdO2fg+9WPRPwpw1oLet424km1VVHSzp+kVe6Ok1VfHo665qfQbT/utGh36qI6evouTmffia/0YnJL9RZhp8W68+M4g6xVjr17Th9kvejbhTiKxN3gbiy3qLuczotdRy3Y92YjP1dV6SuArHCXC2z3rkzXuF27XTqblFUzR2zEREnyTfVel1t83imqIjM9Y7xhzU265p5p6R7/Pye29G/DvC+86qzHEXEVemqu3Yop01u1M1VT76+1MS+v+kng/hbZfRjuUbdsumsV2qKcXpp5rueaO9Xdzz58cbMdJOK2bfmSaqs91zXjpPT3wuopxcq8IzPR7P0McNaTiXi+3pNw00X9FatVXb9PNNMzERiOse/DdymM2xMd3TxXNX7OZ79esYWKuk5mMx732f0y7ZwBwvtn2Hbdkt07xqKMRPra59RRn70xM9Znw/q+J3Kp5ulXRcL2m1yx1XJ1nrllTPTq4Ir6suacNdWNuScZ6MJrxVjwY83QoiJqz4M6VyVRFUfe5ejgnPi+//s/8N8Ma/hq/rNdpdJr9dN6qm7buxFc27eI5ek9o75l8y9Me37NtnHGr0mx+rjRxFNUU25zTRVMe1TE+6WcOSXLq6dJJt4uJMsWURMu7JlJlJ7nUAMLFMggswkxMAigARGWVNM1RmG7tO163c9bb0eh09y/fuTim3RHWff8AA3JN01a04omf/mvJMU/dmX2/h/0Q7ftu0/b+NN+t6C30mbdqYjGevWqYmZn3RDkv6z0GaOJ09vTbzreT2artN2qnPv8AvR9HL5Zfpvrr7fDYtTPWekFVE0xnHT4vt9jhL0V8W6n1HDnEOr2zXXIiLVnVxzRVV5de8/CphvPoqscPcAb5uW6129RrrNVurTVWqpimm3FdEVdJ/imJnpPZLyyXVJhubfE4pln6uIomua4xHhPj8HLVRTF2qMTGJxHXyfpngnhDgm9wBpLt3Rbfd09/SU3NVq68VVU1THt+33pmJzGOnZcuSY/pMcZX5dqjlqx5MZnq293tWbO56i1p6pqs03Ji3V5056S1J7uku4zrSxLOJcU9smZNDkmoz4pTEzPUq6QjJzT5nNPmxmRo0s1SnNPmixGSmljJMMqYYzMeTLSfBacz0iMp37NrQaeb2potxTzTVOMFups04JommcVRMThjNPXExh+lt39HvAHC/C1G479tnNXprFHr6vXVxXdvTEezTGcZmcxiO3d+c9zv2L+vv3dPpqdNZruTVbtUzM8lOekZnv8AFnjz7rlh1adeM9EWoxl0RAmMABHeIHY8Oxtk7tZ/xiNRVouvrIsVRTXPScYmenfBvQ0IxjtKxTEz4vuHAvBHo74s0ldW363e7V21Ga7N2qjmiPPMRiYdrvPot9HWy2rd3dt73HS03JxTNU5z/Shwy/IwmWnWcWWU2/PcWpntEpVRjvMPvu2ejj0a7zVOn2jinU3L9WYpomqKapx5RVTGXluO/RDu2z6a9rNquxueltZmumKOS7REeOPH8lnPjvV8T46+VzTC0UZpmqIzicY82zo9PTdvUW7t+izTVXFNVdUTMUR5z7n3j0Z8AcC6rT1arT6yN9v2YiLk3bc0UU1T4xRPh8V5eWcc7VMcez8/V0csR26sKol9J9P+36PbuMKbGh0tnTWqdLbnktURTHWZ8IfN+/SO7WGXabjNmrpjEOW3YqrmmImOvvZ2LFVyqKYxMzMRGfN+jNh4H4F2PgLSbrxTtNNd6nTRe1Fdd2uJmqrrTTEROM4mIZ5OXppZja/NtdM0TiYxLF23Fuo0Oq3y/e23RUaLS1VfurFNU1RRT4Rmes/83UukZAwRCh4GJXlmezOmmZ6cspscePNyU2805cut0mo0d+bGps12rlP3qa4xMeP6rpYiq7TRMzETPXHkW6g4ZtzMefux1YTHTo/UFvg3gSrgS5VTotJVpY0VV2NfGJriuKJmJ5vCc+D806+iijU1+qiYtTPs5xnDHHyXP9NWaagswkw6MgJIKJGVwAAABiQATqCiKAB4wDKKfdM/AmPc2tumzGpojUVV02uaIqmjvjMZx+WX17gPhX0Z8WXvsmn1e/afWzFU027ldHLXjviYju58nJMJutY43K6fF+n/AKk6S/Q+/eingDZNFOt3Ldt209iKop55qies+GIp9zz8cO+h2J68T7tPX+Sf/wCRnH8jHKeRu8Vj4xFOfA5er7louFfQ5qLtNqjindaaqpxE10zTT+czR0dH6ZuAtl4U0W3azaNTqtRZ1M1RXN2umqOkZiYmPOFnLu60xcLHymunlYs62DqyAsUzMZBBlRbrqqimKczPZzavSXtNcm3ftV2q4iJmmqMTiYzE/wBJBrsqMeLHDktR1jEZnPYEmnriYnr5JVRMT2mPjD7h6HPR9sW7cLXt54g0tV+Kr1VNr97VRTFFERzVTiY6Zmf6PnvpJ1HDFzfJ03DGhp02h08TRF2blVc36vGrrPSPL/z6c8eTtdRrWo8f1WI6MoonOZ6tnTaLUaii5VZs1XItUTcr5fCmJiJmfd1x8Zb2y1Y7sppnOPGe0E04r5Zjt3e89Ce0bHu3FtqzvVVFdEUVVWbNc4puVxMYpmfhMz+SZZTGbJN14OaYiO8f1YVYz3fa/wBobh/hvbLW3Xdq0djR627NVNdizEU5ojGKqqfDrn4vityPax2mPAxy7Ta2aYhgiOrSAY95j3gAYkATqoAAAAAALEdGVPZKeyx4pUrJIjCiVkAQEiZyqAyht7X+Jq+SfrDUjs29rnOoq+SfrCwdkA0oAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AkqKAAAAAAAAAAAAGBcg7jhjZtXvu9aXbdJb5r2oucke6PGfg/UO1aLavR3wXemm37Glo9ZduTHW9XjpzfGXzj9mPa7dzW6/d7tOZ01qm1bnHaa+s/2iHof2kNfXp+E9Loaa5/3u/VVVEeNNEdp/OXzuXO580wn6enDDrh2fEOMuKNy4h3W/uGuv1VVXKsRTnpTHhEe556qZn/5sevL7kp7vfjNfTz27dpsG66zatzsa7S36rV21XE01ROPyn3PtXpU3qzxP6Ktl3qmimq5TrJt36aZ6U18k5jP93wSmZpmO3R6HTcTa+nhK7w1NVuNBc1NOp+7HNFyIxnPftLGXHMr2Wclk04eH7tdvdtLy1Yj1tH1fqP00R/7Lt1qjPW3Rn/4oflLabk/4ppsf9tR9X6n9NFc/9FG6TE9fV0f8UPLzz+eLrxZfwr8n3apm9VnMxEy+leiTijZ+DuH963O7M6jeNRTRa0WniieWKc55qqvLOOnueA2zQXNx3Wxord6xZr1FXLTXer5aKffVPg+48A+iLZKtHTrd03Sxu81VY5NLX+5pn3zHWrHR6OTLDHH+Tnx423b4VxBuut3fc72u1t6q7qLlXNXXVPef0jHTDrcTMZjr9Xu/TBtWh23jzXaLQaajT2KJpim1T0pjNumc/wB3qvRt6LNo3q3b1Gu33Tai9FNNdWi0lWaqObt6yqe3eInHbzavLjjhsmNt0+OU9I/Vs6e1cuRV6umZiIzOPB9z9JPo00l7VbJt3DW16fT1V1Xq9TfmcU02qIozXXVM9usuw4T4c9FG310bXqty0G77jVXNNV6/NUUTV16R05Yhi8+Nm4vw21+eK4qiOuPcxpjp4PvXpm9Fm2aLZtVv3D+nqsTpoidVpY7RT0zVT5Ymese+PKXxradru63X2NHF3T2KrtyaIrv1ctFOIzMzPg1hyTObZyw63TU0mr1WniadLeu26qoxPJVMTMd2neruV1zVcqmavGZ7v0XwN6IeHKdHa1+57jRu9UZzGmrxZ5u+Mx1l8j9Me2aDaePty0O3WbdnTWr000UUdogw5Mcs7Itwsm3jMMqaZnpES39m2rV7xuFjQ6GzVe1N2rloojvU+txwjwVwHord3i2qd13S5TzRpbU4pp/8vfLeWcl0zMbfXxiqzVFEzy9ae/WGGMxjHV+geDLfo141uXtso4Wo27U8nPTEV9aojvMVR5eTxPpb9Hl3hS9a1eluVX9uvzNNNdUYqoqj+GfyYnNLl1rXx3ruPm1NPWPJzxYrm3z025xPTL1Ho84N1/Fm9xt+mxat0Rz37tUZiin9Z9z6PxbpPR/6PabW36jYP8Y19y3FdU36+lNM+M+XwhcuWS9WZjbN18MrtXKes0TDinMzGYfonhXYPR56Qdgv16HZadr1lmIi7RbnFVGekVxPaYz5vjvpB4X1PCu917bfqi7RjmtXYjHPR4T8Vx5ZcrjWrx3W3l5hOjKucRhhDow29FRNdcUxTNUz0iI7zPg/Ufou4N0vCXDn2vXWqKNyv2Yu6i9VHW1TjPJE+ERHWXxL0FbTTuvHOipvW6a7Gn5tTczHeKIzEf1x/V+g/S9r69F6Ot71FuvkquWabEVR/wC8qimf7TL535XJfknHHp4sf42vzv6VOMNXxLxDfu03Jp0VvNGmtZ6RR5zHnPf83iaoqqxzVZxHmz1EzVduVeE1OB7sJMZqPNld1t6K7csXqK6a5pxOYmJ6w++7RxZe4r9DXEG26u9z67bdHFdVeetyzFVOJ/LGJ/LzfnuicUx8cOz2re9dtNnXW9HeminW6arS34xnmt1TEzH9aYY5OPtdtYclk00L9UzfrrieWJqno5rWu1tFivTW712LVUdaIqnEy7jhHYbe+am7Tqd10G22LfJz3tTX1zVM45aY7y+7bX6J+E9s2W/fu2690u+orqpvXKvZzyTMVU0x4dI6nJy48etrjjcpt+Za6pmqZnutFFVc9KZmceDsre306zebWiouWtPF67TRFdyrFFOZ7zPk+3+j70VcMTTTqtZulre6qZ9qmxXizExHafGfBeTlxwm6Y4XK6fn/ANXVnFUTEx4MqrNdNMVVU1RE+L73unAOwVekTX6zc6bO18PaKbNFVEezFy5NMexH6z4PV8XcB8FWeFtXuM7Dp7VvS2/XU12rk0c8R2p5o75cv/Jl/TV4tPy1RRPNhK6J5ez9F+jrhn0c8YbXXqbPDuo016xVFF2irV11d+sTE5fLvTFsW1cP8YavbtqtV2tPRFE0UVVTVjMZnrPVrDmmWWmLx2evATROeh1l9F9GdXBGrnTbVv8AsWov6q9e5I1VvU1UxGZ6RNL23pi4A4V2Hgy5uG1aGvT6im9RTFU3aqukz16TK5c8xymNWYWzcfBIhlboqrq5aYzPk5abfNXinrHZ9g9Gvox0N7aZ4j4qzb0FFE3KbGcVV0x/FV5R5ebefJMftnHC5PkNOmvdf3fb3sJt098TMPrd3jHgKnVzop9H+hnQxVERd559dNPhMz2z4vX6j0T8I8RaWxuuya69pNPqKOaim3Gafzirt4uV55j9x0x4uz85VU4ntL0fo7ubTb4v227vd+rT6G1ei5drijmzFPWKcR5zEQ9tx56PeGtj2C7rtBxTa1motzT+4iqiqqqJnE4iGPo49Ge37zcsXNz4k00euoi7To9JXFd+qnvOfCnDV5MbjtOl7ajrPTBx9quMd4mbdNyztliqqnTWp7zE966vOqcf0fOZiqqcvt/pv4Q2Hh7hLbq9n0EW71Wqqt13qqpqruRFuqesz74fINp0d7Wa2zptPaqu3btdNFu3HeuqZiIpj39V4ssem59GcvbVdfTRM9IiZlyepriJmaMREdcy+92/RzwvwdwvXvnF9udw1NMxHqLdfLbi5M9KI8/HMz5NLg3ePRpxJvNraNRwdpttq1E8li7zc0VVTHSJnwz2z54Sc8vsT49X18NmjliJmGMx17vrfpo9Glnhaindtnmurb7lXJVbqnPqap7Rnxievd8jq7uuGczm4mWPW6JhlRMxPScMYhlTHVay+0/syRM79uMz1/3OJ/8Aznc/tLVTRpdommZpz6zrDqP2Y5j/AB7cY/8AuUf8btf2nKojSbPEf+9/R87L/wCRI9eP+p8Q024aizeovW71dNyirmiqKp5o+D9VejPfq+IuDtNuGpiJvxmze8qpjpn84fkq1FVdfLTMRGcTM9ofqT0KbZqdt4D0lrVUTRVqLtV2Invie0497X5skw3+2eG33b4v6btg0+wcb340VuLdjUU036aIjpTM94j83uP2bK6q53Sias5tW5//ADnm/wBpDcLOr42+zWq4mdJZotV4/m7zHxd5+zNVi9uvX/qbf/EvLLeD0wsnJqOk/aVoxxtMx/8AVLX1l8op+8+r/tJz/wDTb/8A1Lf1l4bgzh7XcTb9Z2rQURNy5Oaqp7UUx1mqfdD0cV1xzblyTeTk4ItbbXvukr3bU/Z9HTepqvVTTM+xHWf+X5vU+lzj2/xRr402imu1tWnnFmjxuTHTmqj6R4f1ey4o4f4F9Hm0aWjdNqr3vcb0Tj1lzkp6d5x5dYw5eEND6OOPdLc0Vvh2jatbbt88UW68TMfzU1R3xPhLGWWN1lWsZfqPz9dqmurMx7ujGInPaZe19KnBt7g7eKdLF2dRpL9M1WL004mrE4mJ98dP6w6rgjh3V8R8Q6TadJTTNy9ciJmrtTHeZn3RES7/ACSztHLrd6dFTbrq+7TM474ZeqriPaoqjPZ9z4ksejvgLG1VcPTv24W8evvai5y0xM05xy/CYn3dG3wJoPRbxvuHqf8AAK9s3C3+8jTU35m3epiOuPPHfDn83m9N9HwKKcVTHl4vf+iPgu7xPvVv11FcaKzMV6q5jpEZ6URPnV0+EOHjbb9o230ja/RTbr0m2Wtxu259TTmqi3TVjERPu8/N969GO58M6vh25pOGbF+xpdLVTRcm/ERXXVMZmqqY7y5/kc1mO41xYS5ar4X6erU/9JG6cluIp9ZRiIjt+7ofPs10T09mX3z0k3fRpTxZrI4g0+53NxxT62bNcxR9yMY6+WHzfa+Gdk4i4o1lOg3nTbTtNF6PVV62v25pnMxER4ziO+XTjz3jusZY6yeUjW62bH2f19yLPTNHNPL/AEa1U5nx/N+lP+izhTZ+Fdwv1WK9dqKNHcu0371WfaimZjFMdIfnDU0RGoqt09KYqXi5Mc/8TPGz7cGMRlyU6e9XEVU25xPXu9t6OfR/uHGGqqp09cWbFrE370xMxR7vfMvZ7rR6MOEtTG1/4RVvWoonlu3arsRGY7x1zH9MF5p9RJh4+J3LVyiImqiYy4474mH6W2zgzgLjnh37btO3VbVciZomaP8AqqvfHaXw7jPhnWcNb9e23W0RzUzmirwrp8Ko+JhzY5XTWXH1jzkUxnpLkizcmMxT/d9Z9E3oxtcQ6GN33u5XY0HNMW6KOlV3Hec+FLn1u++jTad5uaC1wdTqtNbr5Kr9yuJqnHSZiJ6nzzeoz1s+3xu5RVTHWJYQ/Ru9ejLhbibYKd14Vo+x3b1ua7FMT7Fc/wAsxPafDo/Put01Wn1V2xcpmm5bqmmqPKYnEw1x8sz+jLHq1WcRVPRhVDZ0tMVTETGfzdN6Zrj9VX4QVWq4pmZfe/RxsPo44u0FVFradRZ1untUzdt16qqeaO01x7s/0zDg9KPDnAnCu00eq2PUXdVrKLtNir7VVEW6qYiMz54mY6OE5/5dW+l1t8GjrHZlTT0y5IppoudfajOJx4vtfol4e4D4o2GunU7Jfp12itW/tN6dTV6u5NWfajE4p7dnTPPrEk2+HzEx3R7P0pVcIxr7VjhPSXrVm1NVN27cuzV62emMRPaI6/F4xrG7m2ayiqcdH0f9n+5X/wBIm2+1OJquU/8A7up82h9H9AFWPSFtef8AtLn/AIVTl+R/qydOG6zj63+0LNX/AEdVTzTP+9W4/wCJ+ZZqu1dYmcePV+nfT97fo7qjOP8AereP/wA5+aPst6MxmjrP8zz/AIV/43Xn3tx27tyivPNVOI7Ze73rifSbj6Mds2a/eu3Nw0OquY5o6RZqiOXq1fRRwtd3rjbb7V/TRqNFbuxXqenNRyR1mJ+Lz/Flq3p991tu1TFFqNRciimO1NPNOIenctcNWfbp/vT4yyos11xmmmZ+Dt+D9j1W/wC+abbNJRNV2/ViPKmPGqfdD6vvljgDgSadsu8PTv8AuNOI1F3UXOWimryppXLk1dEx36+JeouR15cr6mvPaZjGcw/QHBGi9F/GetjTRw/XtmvpjnixTqJmi7Ed4jHTp5PnfHWi2rQcfa3b6rX2Xb6NVy8tmmJmmjEdo/qxjy3emrhpwei3g7UcS8Q6e1NNdGkt1Rd1F7Hs00R4fGe2HP6e7UWfSHuFFu3FFMRaimmPCPV09P7Punoq1/DGs2G5puGLGotafS1U+sqv0xFdyqYn2pw8f6S/+jG3xdq/9pNNutevxRN2qxM8lXsxjHXycePnyy5LK658eMx3H54nM9HLpYiLlNUz2ns7febW16jiHU0bPTct7fVexp/W/eij3+99B2T0d7Nsmw2uIOONXcs03ZibOhtR7dzxxP5dfc9eWeMnrzyVjxzx1pNJwJtvB3DGoquWadNRGu1MUzTzTPWqimJ645pnM+PZ8pmJz1/v0fceHd09EW7a21tl3h77FN2eSi7epzGZnEZqjrDU9Knomp2nS3d34fi5d0luOa/pqvaqtU/zUz4xHjHeHHHkxxunS4W/T5Bp7M13aaeXOZ833HhLg+rafRNxHu+qsVUazXaH1dmiqjFVFmK6Z5p8uaeuPKIeP9GWq4M2zUTrOIrGq1Ort3Y+z2qbcVWYjEe1V5zE56dn6H4lq2yeF9zr3Ka69vnTZvRTPtTbny/s48/NlMpI3hxyx+N9XRVTqK5qpnpVPg47Ny7buRVZqqoqjtNPSYfUeKavRXXseoo2PSbpTuM8vqartc8sdfamevlluejj0X7Tvv77X8QWLsxEVVaPSV5uRExH3qpjEd47eL0fLMcd5OXT3UfJ9ZqtVq7s3NVeuXKvOurMtOr7z696feFtk4c0m1RtOip003OemuYmZmrlxjMz3nq+S2LdV2uKaeszOGsOSZY7iXGy6Y0xzTEUxMy5KbF2r/q5fW+FfRptm3bF/tHxper0+k5Yqt6aJxXXM+fjn3N3ZN69Fmp3OjQTwjNu1XVFFOouVRXMZ6dY8P6peaL0fEptzFWJiYSaeXv1fePSj6J9Fp9uvbvw1TVbi1Tz3dJNWYmnxmmXxza9q1O5bla0WktzXdu1xRTR4zMymHNjnjuGWGrp11FqqcTET7mVVi9HtVUTEeL77/sDwdwPw1/i3FMXt01EzFHqrc8tE1z2piPrMtXhTV+jXi3cY2q9wrRtuornls3KK5xXPlmO0pOeWbh0fBp7yxnL6l6ZPR1b4Vm3uW2V1XNvv1TTNNf3rNflPnE+D5hXGOk+TrhlMpuM2WMMqkd1aQAAABaZZR4sIZ0FSsgGWQBUqwniyx0YwlRlERhtbX+Iq+T9YauW1tn4ir5P1gjUdkA0oAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Gu/JP0cjj1X4a78k/QV5+e6pKigJIKAAAAAAAAAABGPEH6N/Zmn/wCjO6UxiZ+00Z6f6Iw0f2nZqjS7RiMU8l3r78w0P2ZN3otbjuG2XL0URes03bdM/wAVVPSf7Yeo/aF22rceCY1tFuqu7or+Ymn+SrpMz/SHytdPyt39vbvfF4/NdWeTu447sq4mIwxxL6rxOTvHUzCYmY6Mrdmuumqqmiuqmj70xHSP+R4ja2mqf8U0v/4tH1h+p/THVM+indP/AMOj60vyttFMxu2lp/8Ae0/WH6n9MUVR6LNzjp1tUfWl4/yP88Xfin8a/KFVyqi/zUziYnMPvv7Mmou3tv3e3crmqiiu1VTR4RMxOen5Q+AXo/e1fF95/Zdj/c96z52vpU1+V/rTh+3ivTzVP/SRuk5/joj/APdUNj0C6q7T6QdHRRVNNNym7FcROIq/dz3/AD6tb08x/wC0fdP/AMSj/wAOhn6BY/8AaHt/vi7/AOHKZf6ln+x9L/aI3jXbbw1o9Do71Vm1r5u03+XvXTTFMxTny69Y8X5/sau/maaq55eWrpHujL7h+01Gdr2PP82o/wCGh8H0/wDmT8tX/DJwe8ZyX+b9b6O7O5+i6bmun1039jmq7NXeqZsdZl+S9fqrn2u5VTXjM/WH6t2Sf/ZRZx/9hR/4D8k6v/Pqz5/oz+J95N88+n6K/Z0v118ObnbnM00ayjljy/d0vlXpxmJ9JO8VeP2ifpD6d+zbV/8AqPdY/wDvVH/hQ+Y+nCP/AGj7vH/3mfpBxec1TO/8ce+/Zt4ft00arf7tETVVV9ms1eNMYzXMf1x+T5v6WN6v7xxruOprmcReqt289OWinpTHwiIfbvQBXZngHT8nWaNTc5/dPN/yw+J+lTaq9t433PT10Yj7RVXT0701dYleLPtzWVM8dYTTX9HvEP8As3xHo90m366mzMxVRzY5omMTD6D6WvSXtXEvC9vadBpL9Fc3qbtdd2I6REdofHqaJz07NijQ6vUWL96xYuXLWnpiu7VTGYoie0y7XjxuXZzmdk0+hehzjzauFr2vtbnbvcmqpp5a7cRVMTTLovStxJa4s4rr1+is3IsRbptW4mPaqiPGYafo/wCD9z4t3WNHo8WrNM5v6iqPZtx+s+59K4h1vB3owinbNo2ujdd+5M3tTqo5ot593bPug1j33F3evrk/Z52fiLb9zv6vWbXqdPt97S1W/WXaeWO+Yjr1aH7T1MU7ttVWMf7vVif+9DtPQrxbvvE3HNyNy3K9fsU6a5VTamcUU47YiPJo/tT043Haq4zP7iuP7w80387tfeJ8Oq61dTCxTVPVYe95X179mCObivW04iZ+w18uZ/1Uy+p+m6ibno01luZj2r+niPd+8j/m+G+g7drW0cdbfcv3PVWb1U2K6pnpEVxiM/nh+hPSdpKdx4K3bQUxM3KtPNdqPGa6PaiI/wDhfK57cfyJk9fH/rr8hVxMU1R07uCejkvZ9ZXERjrnEuPEzHZ9OPJYRVMRj35JqmfFJicZc2j013VXabOnt1Xb1XammMz5/pLQy0Vdfr6IzmJqjo/WfAtdVXol0NdyublX+GV+1P8A+HV0flHRWp+2W4x/FH6v1dwJGPRBoMf/AGZc/wCCt4PzL/j/APr0cH7flLV1VUa6qqjp1w+6fsx3qqtJu1FdU4mq1OPKZiXw3coxq6/i+3/svY9Ru2Y65tfSXT8n/Wzw3+bpv2i+INRPE/8Ahdiuq3a0lNMTH81dURM1f3iHzS5xNvdzb5227uepq0s97XrJ5enueu/aFmZ9JG4T5+r/AOCl83q6OnBhLhKnJldv0F+y7fqq0278059q3P8AZ4b9oSr/ANpGu7fct/8AC9j+y5ONLvE9Ok2/o8V+0FTMekbWzM/w2/8Ahefjn/sZN5X/AI3luCa+Xifbqqe8am3j/wCJ+if2gomfRxcrme+pt9Pzfnfgin/6Tbf5fabf1h+jv2gKM+jm5j/6xb+q8/8Auxicf+NfmzhrT/at70tmvl5Kr9MVZ8pqfqf0qWq9J6Ndyt2It0+r08WoijvFETHT4YflDSXatNq4u0zy1UTMxPl1fp/gfifaeP8AhW5s+qriNfXppt6ixOcziMc8fVPycbcpV4rLLH5jv3J+01+14/q/RnoB1c3eA4t3YmqLeqrojr5xExH1fLN89FnFmm3y5pdPs2q1Vmqr93et0+zMZ7+59T0N3bPRlwJRp9w1Nm5uMU1XZ01Fcc9dyekU48I7dfic+88ZIcV6b2+G+lO19h453fR2oiizRqaoppp8In2sf3/s3fQ3qb3/AEhbLbpq5aZ1VETEdMx5PKb9r725bxqdffqmq5qLk3a5nxmZzL0vobn/ANomyz4/bKP1ejOa4tOcv89vr37SMVU8IbV/+WV/+FW+JcC7ta2LijbN3v25u29FqKb1VEd5iJ64fc/2l8RwhtEf/fKv/CrfnbbdLqtfr7Oj0lubt69cpooojvVM9Ihy/G94/Wufffx9o9L/AKRNi4j4Zo2ra/X3q7l2Llddy1yzbimJp5ffMzV/R864H4e33cd50up27bb+pii7TXzU0TyxirOeaenTH9n03RcC8N8BcP1cRcZV/wCKauKpp0+jonFuao8PfiIzOXmd19KPEO8avT6PR3be16H1lNMabR0RRTy80YifPos1MbMV1/L19W9OcZ9G+51T1nntT18+eH5Qq+9L9b+m+1z+jTdJ7e1a/wCOH5LqonPgn4V/hV5vtjC5wdmMzEy9ded9l/Zlrn/aDcf/AMij/je79MWm4W1ul0NPEu5avQzFVcWKrFvn+OXgf2Zv/wBv7jEf/Uo/4ndftK80bftHxu/o+dnjv8mPXj/qaHDWweifb9VRrdZxXXuFNNUVUWa7M0xMx54jq9Bxp6YNn0m33NJw1bqv36qOS3ero5KLcds0x44fnv1lVMZzV/VwzX8cPTl+Pjld2uHyamo2901V7XauvVX7ldyu5VzVVVTmapnvMvsP7MvXUbpGP+po/wCJ8Upqie77l+zFREarc/fZo/4j8n/VV4bvN5/9pCrHG8RP/wBVt/WXWehfinb+FOKbm4blRenT3LFdqardMTVTmO+PF237SkRHHXWIn/dLf1l4jgnhjdOKN7tbbttGa6varrmfZt0eNUmGrxepl/l49X6a+L9Fxbu+hjaouzp9NZ5Ka66cVVzM5l2PoG2DiCxxdpN0ubZqregopriu9XTNMYmmqMYnv3d7v2n4O9FmmtWqNJRvW/XLfNTVej93bj4eHuju1vRjxzxBxR6Rdt0+v1lX2aZr/cW45beOSZ7R+TGV/wCPWP03h5lutz9p6iidv2SuaJ5vW3o+HSmcf2h5n9nDUaexx/FN6Y9Ze0t2mz5zc5ekR75jMPZftPW4na9orznF69M5+Wl8M2nW6vQa+3qdFVXRetVRXTXT3ox15vyTjly49Gd1nt9p9N/AW77zvNzibZ7f2uK7dNF/T0/foqojlmYj+LpEPk3Duu1vDXE+i19dq9YvaPUU3JomiaZmImMxifOImPzfZ+DvS/tuvi3peILVWkvxGPtFqP3dXvmnvH/m97u2wcM8XbbF7V2dPrLVVOadTaxz0+Gaao6590uePLlxzrlPG7jM/Y/L/Hu9Wd64s3LdNNRXbs6rV3b1FFfeKapzET78YfVf2cLk1bHvOZzPr7f/AIcvmHpU4X1XCvEVegu3PX2eSK7F6Yxz0dv6xOYn4PpX7NkxO0bxH/v7X/BLpz6vFuMce5n68B6cq6qvSFucTP8A1tMf/uqHjdJVVTeoiJ71Yl7P04Uz/wBIW5//AI1P/h0PHaWmfXUZ/mejG/wjjlb2fqfQXq7vohi7ermuurZp5qp7zPq35ZqpmvcZpiMzMv09tmZ9DluPPZp/8N+Z9JTy7tFVXhMT/eHn4POztn7p+otLYjg70RVzo7dPrtPoeeqqOkzXVERNXvnq/LW5am5d11yuqqeaapmZ8/N+tuLdNVr/AEa7jp7Ec1VWgzTjxxES/IWuoqi/V4dT8W73V5vNafTPRF6QbPC1vVabcbV6/pb+K49VMZoqjpnE+50vpW4vscWcRUa3SWLlqxbs02qIufen3y8RRFUZ/s569LqKLNu7cs10U3ImaJqiYiuPHE+L0fFjjduPa6fa+CfSZse2cDWNv1FOqt6nS2arcW6LfNTc749rw7vjlNjW7ruUxotNdv3Lteabdumapzn3Po3or9F9zftFG875qa9FtUe1TRTOK7sR3n3U+9vb96Q9t2GuraOBNq0+36eirl+2csVXbkx05oy543HDL+H23d3W3070M7duO2cF2NJumlr01+L9VVFFc9eWYjE+7xfnH0g2qbXF2800RFNMa27iP+8/RXoP3HV7rwrd1mv1F3UX6tbXmu5OZxEQ/O/pK/8A6z3n/wDLbv8AxOX4+++W2+bXWPLzgprmmek4SWMd3ued6r0a8Q3+H+LNLuFNVU26Z5btvwron70fr8YffvSxsFviTgW/d0VM3LmmojWaSqmOtdExmqmn5qevxiH5c00zF2JpnE+b9P8A7P3EMbzwj/h2puc2o2+Yooieszaqn2fyiY5fhh4/yJ0szj08P8pqvzP6ir1nLnOJnr4fF9otWZ4G9B9VdfsbhvdXWJ6VRbqp7f8A/Pp8a3Buno+pp9L9rYrVnO3ay9Grpx2p08Tz1U/lMTT+cOl/aF4ijcuMZ2rT1R9k22n1NMU9ueetc/1iKf8Aut9vkskZuPR8xvXKq5jmmZxHi44ZVzGOjHMPS4Lh9C9AkT/0g7XMf9pc/wDCqfPo6vovoEon/pA2v/8AFuf+FU5c/wDrrpx/5R9z9JG/UcP8LVa6vb9Nr8XaKItainNGZz1/s+UVelrSTnm4L4dqqjw9XL3Xp/p5eAKv/wAqt/8A6T8zdas9Xk/B45eKWuvPlrJ+nPRf6TNp3rco2WnZ9Htt3UUz6qdL0pqqjryzE+L8+8Y4/wAf1mfDUXO/zS1+Ht21Wy7rY3PRV006nTVxXaqqjMRJqPte762u7Taru6i9XNU026czVM9ZxEPVjhMbtxyy7R7v9nXV6bT+kCinUTTzXdNcotZnHtzHSHsfTL6Pty3PdLnEe0Wp1Vd6mPX6en2ZpmIxzU+b4dt1zWaHc7eo0s3bd+xVzRNMdaZie77xwL6YNBq7VvS8R2K7N+mMfardOaZ99UeHxcefHPHLvi68XXrqvkvD2o1/C/Euk1ersX9Pe0t6m5NuqmaZmM9Y6+5w+kPeLO88XbhuejouWrGovTXbpr6VUxMR3979P73snDnF+z01aiixrbF2P3eptTE1RPnEx9H5m9JXCmr4W4jr2+5c9dZqj1mnuz/HTP6+a8HLjnf+2eTj6zy+Pq/7L1VVW17zEzn97a+lTwP7QU/+0ncpiOubX/BD3X7L1X/6u3iJ6fvLWf6VPCen/MekjcvOZtf8EOfF/vrWf+uVq+hLZbO88caSjU26blixFV+5TV2q5YzET+eH0z0s8G8Q8T79Td0+4bXa0lmxFFm3qNVFFUTPWurE+c4j4PJ/s14nifWRMU806G5FMT4+1Q2f2itv1el4m0+4UUzTZ1Okp9rPTnomYqj/AIWssr82kk/ht12n9EnENm7TXG5bFMx5a6n4P0Fw7Xp7Wy6HSbprtvvXaNLRa1MRqqKoqnlimrrnrmI6vxp9rv8AhX4NnS3dbqK7dqxE3K66opoppiZmqqZxERHnMunJwfJ7azjya8dtxRpLG18S6/Rae9Rds6e9fs0VUVZiaaaqoiY90xiX6P47rx6Lt2mnpP8Ah1P1pflW7Z1FjVXLWooqt3aIrprpqjE0zicxPwnMP1FxtM1ejDdIj/7Pp/8A0XH8jHVxb4ruV+W7tyv7RXPNOcy976B9Veo9IWgiLlURc9ZFcRPSqOSZ6/m+e3av31c+97b0GVxHpE2343P/AA5enln8K5YW9nvf2oIpnS7LPb/Nmff1peK9A+x29143083aIqt6Wmq/XExmOmIj+85ey/aanm0eyzPb97/+i6v9mWqn/abcc4ir7JGPyq6vPjlrgdbN8jd/aW3W79q2/a6Ziimi1N6qP5pmcR/SI/u+MaTU3LN2mqmuYmJ6T5Ps37T+310bhtmt5fZu2Joz5TTV2/pMPiVMVTVh2/Hsy44xy7mT77/0ybZXwtNi/tuqr1/2X1UzNVM0TVNOMz49XzDgbfNNsvFWj3XUWprt2b3NXTT3xjrj+rzuk02ov3KbFqzXdu1TiKKYzM/CHNt23azcNytaDSWaqtRdriiinxzlZx4YyxiZWvqPpp482niTadJt20zqK4t3PWXKrlHLjpiIx+rxvo22nf8AVcQaLVbbt2pv0UXqa+eKZiiMT1mZ7Po9jg/hbgHh+je+Lo/xjce1nS82LfN5R5485eYu+krfN93XS6PTVW9q0EaiiKdNpKeSJiZ8Zju5zUwsxnjpJ7NvqH7QNFu56PNRXNEc0Xrcx7vafl691uVZ8Oj9TenWjm9GusmIxi5b+r8sXf8AMqz5r+NlvE5/8nH4qTCQ9TioAAADOnxYM47FSshFYZABKyieiBAg29r/ABNXyfrDUht7X+Jq+T9YIsdkA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FefUBQAAEyCgAJ4qgKABImFAAB3PDG66jZt50m46arlu2K4rpz2nzifd4P1bwnvOz8c8N13aYorpu0er1WmzGbee8T+kvx3FWI6O54W4i3Ph7WRq9s1l3TXY71UT3jymPGHn5uCZ+z7dOPkuPj2HpN9F258Nay5qtJbuana7lU1Wr1FM1cseFNWO0vntenriZ6RmPDL7rs3p7vRpLVjedko1ETHt3LFcU8+PGaZ6ODVekz0c6nU3L97gibtyrrmbduPoYZck+41lMb9PlHDfDm6b9uFrR7dormouVzETyRmKffM9oh7Hji5tfCPDM8F7X6jVbhqK6bu6aunExmPu2qZ8onu5eKPS3q7+iu7fwzoNNsGjrjlqjT0R625Hvqjs+X371y7dquV1VTVXOapme7rJb7XK6/Ts9gtzd3fS0RRE1V36e0eOX6j9MVrn9Gu526e9NunP5TGX554B4o23h2/Rq9Xw9pdxvW64qtXL1yY5JiPKO73mt9O1Wqs12NRw1oblu5E03Kar1UxVE94no8/LhllnK6ceUk0+J3qZ9fVE4zFWH3r9mGzXGh3mrE8s1Wo/PEzh8p4j3fatw3uzrdLw7pNv0sRTz6ezcqmm516+1PWMve7B6YtFsWgq0O08J7dpbHNzTEX65mqfOZ8W+fG54aiceUxy26P0+W5j0jbjE9M1W57eE2qMT/aXL6BLVVXpE2/ljMYvT08P3c/83Jxh6QNr4ri5VquFNBGuqpii1qKb1fNHlnzwz4B9I23cI6CmnTcLaKvW1TMV6uu7VFdVMz5eER2ZuN+PS7nfb2P7Tdqr/CdlqiM4r1ET5Z5aHwW1TMV5jtMVf8AC+u8QemTb990U6HduENv1Vias001X6s0zMd4nweB2Dftj0G4ai9ruGtNr6Ll3mtW671VNNmPKMd4+K8WNxw0Z2ZZ7fpDYqZ/6LbNM0z/APsOOkd/8h+TddZqp1dVOM9emPHo+2WPTx6umKKeGtBRREcsURfq5YjGOXGO3g+d8TcR7Jum+aXXaXhnSaO1bq59TYt3quW/n3/w/kz+Phlhva8ufZ9X/Zts1xw9ud2qmYpnVURn4W4z+j5z6cLMx6Rd3qmO9/PXxiaYem2P0zaPZtvo0G18JaHSaamJn1dOoq61eMz0dDx9x3tvFtqq5e4Z0VjcJiI+1271U18secdpTHDLHluS3OXDT1H7OW/aaxq72w37/JOomLtmKpxzVx0mI/KI/pL2npe9HtfFlNrcdvuU0a6xRyTbq6Rdpjt18JfmjRau/o9Xb1Fi5Nq5bqiqiqmetMx4w+zcKem6uxofU7/oK9XXRGPXWaoiqqPOYnpMscvFlMu2LXHyTrrJ4ix6NOMbmtq08bHfpxMxzVVRFP8AV6TjfQ6b0ecARw3Vft3t33iqm5rKqZz6u3T2pd5vXp10/wBlqp2baLkX5jFNeqriaaZ88R3fE+Jd51u+bnc124X672ouTM1V1d5/8nbinJf8vpzz6/p9+/Z6taeODdXctcvrKtZPrPOYx0h859MPDe66XjXWaivT3Lmn1VfrLV2KZmJifDPm6f0c8c6/hLUzVaopv6a5H7yxVPSrHjHlL6lf9Ou2/wCGx6rYKq9Tn2ftFcTbpn3+LHTkx5blPpuZTLHVcf7PnCe87buNW+a3R1afTXbFdu16yOWquZ8YieuPeftDbRuu87/s2m0Ogu35u0VW6ZojPtZjMfk8no/S1vNPGVG+a+/XrKOWbVdiZ5bdNE+FMeGHbcc+ma/ue21aDYdNVoJriYuX6q4qucs96aZjsz8fJeSZaXtjMNPkGr09Wl1N/TVzTNdquqiqaZzGYnE4anaWzfuTXzVTHWZzMtWcPdHmbOjv1WqomJ7VRMfGH6W9EvG1nibaY0OtuUzummtxRMT3vUR05vjEd35fbm1bhqtv1dGp0l+5YvUTmmuirExLhzcM5HTDO4vrPpc9Fupsbjf3jh7S1XtLennu2bfWbNXjMR4xPf3ZfJLli5RX6uaZpqjvE9JfXuFfTbuOjs0Wt80Ma+iMRN63PJc6eM+Ey7nVelb0e6y9N3V8HzqK5jvXat5mfjCYXkx8rVmNfENs2jW7hqbdjR6a5qLtyrlpot080zL6rY2/S+i7h7VXddRp73F+46aqi1anExt1mqJiaqv9dUTMRHh3Z7x6YtHpLFy1wZw5o9luXKOSb80Uzcpjzpx2fJ923LV7jrbmq1uouX79yrmruV1ZqqnzmXWXK31yuoy0Mz9st4j+OJfqzgezdp9FO2aeqnF27t9yKKfPmoq5Y/vD8w8L7ttu2a2dRue0WtztxR7Nqu5NEZ5o69PdEx+b6rHp7uWbVFqxwzt9u1apii3RTeqiKaY6Rjo835HFeTWnTiz6x8a3Gmr7ZcpqjFUT1j3vuX7Mti7Z0u711U+zFVumZj4S+bcTcU7Fve42txs8LaLQ1Vaibupps3qsXY6ZjH8Md+z2Ww+mbQ7Dt0aLaOEtu0tqZ5piL9czM+cz4t82Fzw1DCyXboP2hrM0+kPWV1RiKqbVXuxNEf8AJ8yuT1fU+NPSXtXFNuqdw4R26u/Tbmi1ei/XzUZz19+Hy2uOsz5u3FOuOmMru7fbv2XtXYp1G8aWq5i9ctUVUUecR3lo/tCcO7hVxPTu9nT3Lml1VumOemmZimuIxMTh864L4h13DW82ty0NyKblGYmJjMVUz3ifc+17b6ctqnQZ12y6ib0R2tzTNFU+fXs82XHnjy946Y5S46rw/ox4D3LV6/T7trcbbtti9RVVqdR7PPOelNMT3mez7V6Z9Df3H0fay1prVy7ctVU3IpojMzET16Pi/EfpN1e/b1or2qt+q0Gkvxct6S193pPefOXpeKfThq/ss2+H9FGj5uk3b0xVX+Udmc+PkzymTcyxmOnyLU7VrNJr7dnV2Lti5ciKqablE0zMT2nEv0HVwdu3C/o7q0/CtHNvOqpt/ab8Y55pqiJmmmfCMS+B6/ddz4i3adVrL97Vaq5VEc9fWrPhD7nqOPNdwLwrtej4konX7ndtRVTZo9mq1ZiMRzz5t80z80zxam7XgtdsPpTiuqOTdqaJiImmi9Vj6vOblwpxnVXXe122bjXVMe1VVRNcy+mR6d9Fnrsl2PPF+HZbZ6ctmu3qIvbRqqIj+Km7TOPPp4sduXH3TXXDL9vzxrNNc0+oqt3aKqa6fvU1RjD1Xocpqj0h7NiM41lMz8Iicvpvpx0fDu+8IaHjXZabVNVV+LNzloima85zmPOJw8HwXxvtXCkU3rPDWj1W40UzE6u5fq5szM9o8HbveTDWvXLrMcn0/wDaV56uEtop6c32yr4f5VT5p6AKNPX6SNHbv0xNdNF2u1mOvPFucfrP9Hc756ZrO97fOg3ThbbtVp5nm5Kr1WMx7/B89je50vEH+L7PZjbardyK7Fu3XNXq8eETPf8ANji48px9a1lnLlt9y/aB2jW7rsG16zS26rlvS3blOopopmZp54jFf9pj83yfgHhDfd73WzTotJXVbtVxVdvV5pt0REx3qn4PpGz+nXQRoqf8T2O7XqMTFc2a4i3XPwns8rxx6Wt03q1RpNBbt7Vt8XOf1GnpxNdUTmma5jvjyY48OTHHq1lljb2fZ/TJTXqfR9uum09FV27NNuqKaKZqxiuMvy7xFsWv2OuxRuOnnT3dRai9Tar+9TTMzjMeGcZ+Ew+xf9O2njaqb9vaKqt05MTzXI9TzeM474z1w+LcT7zr993W9uW46u5qdTenNdyues+UfCI6N/jYZYeZM82Uy+nVVz1lKI65xlJbmz3rGn3Gze1Omo1VmmrNdmuuaaa48pmOz1VxfXf2X9PXXvu43YieWNLFM/Gapx9HoP2lNLdq2fbL8U5po9ZTMx5zh5nhb0u6Dh7TzY2fg/bNFRX1rxeqmqqffLa3v006feNDc0O5cK7ZqtPX3prvVdPh5PHlxZ3mmUemZz49PjF2rE4cU/F2nFGv0G47lGo27arW2WeSI9TbrmqM+M5l1Uva8zltR7n3j9me3VFe6X+X2abNEZ8s1PhWluRRMTXTzUxVnl8/c+rcL+lzTcO7fVpNs4X0FimvE3aov1TNdUR4zh5/yMMs8OuLfFeuW6x/aXoqnjfmmOk6W31x75ej/Zhp00aLdrmIi/zWoqnxin2v1w8pxd6Ttv4mszTuXC233btNE0273r6uen4PLcB8Xa3hTevt2n5btFVPJds1fdrp8vy8GMuPLLh6fVdJlO23svT5sG6Rxrc3GLFdzS6y3RVZrimZimYjExPlPT+7sfQVwnvOl4n0W/arS1abR24qiK7scs3Kppqj2Y8Xd1em/avsOY2S9cvTHSiu7TNvP1eFv+ljfL/Fuj3rUTE2tLM00aSmcWopqjFUR75jxYxx5Lh10tuPbs+h/tHaXX6/btps6TT3L+b1yIi3RNUxmIxnDxPof4fnTelDV7Fulu3NVGh1Fq/TMxMU81rE/nHN/WHacUemyLu3V6fZNBd0uquRib9yuKpt/LEePveF9HnGH+zfFNe937FWurqs3LcxXVjNVUd5n4t8XHyY4VnPKZXbr+KeH9x4d3u5tmrt1UX7EzR0jpVHWYqifKYxP5ve+gHeN1scX6fbaa669Fqort3rcz7PS3VPNjwmJjv75dlr/Svw3v8Ap7VrifhGzqq6YxFyzdjNPwmevfLRp9JXDHD1m9VwfwrTpNdcomj7TqrnPNMeUf0TPHLPHrYS9buVsftQ6zS17ltGhorpr1ensV+ujxiK5iac/wBJn83Yfs0xFe2bzH/vrM4/7kx/zfFN+3TV73u17ctdqLl/U3p5rldfeZ/5PS+jTjTUcH7hVeooi9Yu0xTeszOIqx2n4x1/qvJxX4ukTHPee3femvZ9Zc9IWp5NHeuzqpt1WOSmZ555KYxGPfEw8RxDs+v4e327teupt06qxia6aa4nlmaYnHxjL6vv3pxt1aGadp2qizq8T6u/emK5tz50+98p2jfbFnerm5bzttG713KprmL9yaeavOczMd2+OZddVM9W7fpDYdPdr9FFuxj2/wDB5jE9P+ry/MuopmjXzNUYxOOnk+tWPTldotzajYNBFmmnkiiLtWOXyx5PnPGe97ZvGp+06DY9PtlX/WU2bk1U1T5xnsxxcdlu2s8pdafpD0Rb/pOIOELFqaqatTprcafUW5nPSI7/AAmHzD0leiPcrO439w2Cz9r0t6ua5sU9K7cz4fB864N4r3XhndKNZtt6aaojFduetNynymH2LR+nTaa9NTOv2TV0X6ae9muJon+vZxvFycWW8G/kxymsnzzhv0VcT7jrqaNTobmg00T+8vaiccseLD0p7lt2q4i0uz7ZMf4dtGnjS2aoj71Ufeq/q7zjj0y63d9DXt+06KrQae5GLlya83Jjy9z5PVcn1tVcVTM5zn3vXhM7P5OWXXfj9dabSUa3gG1otBNNMXttiizVHbM0f88vzRXw3vMbpOjq0OpnUxXy+ri1Oc57PZ+jb0sXeHdvo27X6WdXprX+VMVxTVRE94694d7xP6bvtGlqo2XbqNJqKonGpu1RXXT8MPPx48mGVkdMsscpH0D0TbNuHDfCNGk3C3RTqKr1V2qiKs8sTjpOPHo+C+kDYd11HEHEm4fYrlGm0uoqu3btcctMRVV7MR5zOXpOAPS1Vs2339Fu2nva3nuVXKbkXIirNXeJz5vOekz0i63i239kt0xo9vpnmjT0TnnmO01T4yvDx54521OTLG46jwFcRHiwjuyqnPdjjye1wZ2qppr5o8HvPRFxT/sxxXotTcuTTpblXqdTGcfu6+kz+U4n8nhLURn2uza0dqvU36LFmmqq5XVFNEY7zPSI/u58mMyllawtl8fsPivcdLsO0a3iO9Zteu0Omqos3I71TViKaInymqKf6Px/vGquavWXdRdrmq7crmquqfGqZmZ+r7H6e901O18M7Dwfc1c3dRZsUXdXV/NNMclEe/rFc/lD4dVVMz1cvxuLp66cufbxjKYWR6XFlbxE9er6b6AKKrvpB22immc01XK56eHq5jP94fNtJVFFzNURNPjl9T4V9KO08OUTXtfB+32L9dMRXdnUVzXP546ZcuXG5Y2R04tTLdfTv2gNPXd9H171dNVUUaiiqcRnEYn/AJvzB6qqmZiJpzPTu+23vTvXes1W7vDuhuUVRiqiu9VVEx74w6mr0s7ZM9eCtj/pP/Jx/Hwy48etdOWzK7fLdPpb1y5FFEU11T0iInMy+zcA8KXeEOD9w423ez9n1UWpt7fZr6VRVXGOfHn3aOh9MGg0d6L9jg/ZbVyP4qc5+jrfSN6VNVxbs9rbatFY01um5zzVRcqqmqffns3l2rP8ZHN6D9Da3jjXV2NVFNdOp0V+iZmM9Zju8Pxfsmu4d3/U7VqaK7VdquYicTHNHhMe53Po14xp4S3qdxjR0amYs124pqr5Y6vZbp6VuHuJrNFPFHBun1FdMYpuWbuKoj3TKy5TJmasdX6At73TT8X2dri5cq0mroq9ZbmfZjEdKojwdn+0prtLe37a9LTVT6+xYqqve6Kp6R8ektO16SOFuH7FyrhDhSjR6y5Ty/adTciuqn4RD5pvu56ndd0v67U37l+7dr5q6656yzOLfJ3W5/x6vtP7MlzGj3qiJjm57dcR7vaeb9Oe0a7UekC9Xb0d27Ospt1WeSmZz05cRjxy8n6POMtXwlvE6vT26b1q5RyXbVc4iqPj5w+l7v6b7FWhn/C9ni1ruWeW9eriuLXvp97HxZ48vaNTKZYaeP4LuXuAfSJpqNzimmbFcWtXTTOeWK6YiqJ98RMZ98P0DxpwzoOMOG69v1FcR2uabUUdeWqYxEx5xPTPufkjXbhqL2tuaqu5XXerqmquuuczVVPWZn+r6L6OfSzuXDu307ZrrMa/RUf5dNVWK7fuiry9yc3Dnb2x+zjzk8rV3n0P8X6DWTb0+2Va61mOS7ZriYqj3x4PV8B8Ff7C27nG3F1Fq1G3U+t0ekirM13v4M/96Okd/Hwd9qPTlw9a0HrNPs+uuX6v4a64iI/PyfI/SDx/uvFuoirVV02NNRVNVrTWp9iJmMc0+c48V47yX/IymE+nmd311zXblqNXeq5r+ou13LtUeNVWZq/vVL9Q8QWL+u9Hmt0+mo57t7bc0Ux1mfZiqMefSJflGzcijUU3Mdp7PrnA3pgjadk0227poK9VOlp5LV63cxVyZ6ROe+O35Q1z8WWeuv6Z48pNvAaLhbddfpNy1tnTVUWdBbm7qblz2aaYziKYmfGfJ33oMs1V+kLbZojpT6yavd7Eub0j+k7W8T2v8P0di3t22RVzTYpxm7V4TXMd/gw4C4+0fClqbmn4d0V7W1U8lWpqvVRVNPljwdM5lljYzNTLb337SmmuTtez3OWOSJu05/8AhfOfRJv1HDnFun1d+YjT1ZtX/D2Ku8/l0n8nqOI/S5pd+0MaHdOGNv1Vj71MVX6s0VecT4PlOsv0zqq67NFNujmmaaYnMR5dXPDit4+tbuU7bfrrj3hfR8ZcNVaO9cppqnF3TX468szHT8ph+d9z9GHFeg1tenr2i/eiJxTcsxzU1++Jdz6PPS7uOwaGjb9dp53HS0dKKZr5a7ceUT4x7ns9X6ddlp08zptl1s3sfcruUxTE++XDjx5eO9Z9N3LHL2uk4Y4Y/wBgNi1nF/ENNFrV27FVrb9NVMTV62qMc0+/q6L0BV2L3HtN2/yzenT3a7ef5/P493mPSBxxufF+rm9rIi1ao6WbFufYtx+sz5uj4c3bU7NudrX6O7Nu/aqiqirw/N67hlcLK5dpK+4ftC7Pr9w2/b9do7Vd2zY56L1NEZ5M/wAUvnvo34N3vdN7013T6SumxavUV3b12OSiIifOe73e2emzQV6SI1uy3atRMYqi3cj1dU/CXleL/Snum8amzRpaKNBo7F2LlGns9qpiek1T4vPxY8vS4OtuNu32T00aXUX/AEca+ii3NcxVTVNNEZnEVdX5h4l2fWbRfsU63TTp69RZi/RRVPXlnOJmPDs+z6j05WZ2qaqdo59bVRiee7E2+b3x37+D4xxVvOt3/eL26bhqKr+ovfeqnw90R4REOn43HljPWOXKZXx1Mwh4EPU4wTJJgFEnuoGWUMMMqJSlZwrGJnLJK50JWElEWCCDxBY7Nna/xNXyfrDXiOjY2v8AE1fJ+sEWOzAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugTKpgVUyqYBUwoAAAAAAACZBQADM4wALzSc8+aJAMuafM5p80AZTcqiMZTmnzQBl6yrGMnrK/P+zEBnFyqZic9YZTcqnv16YcRkHJXcqnvOWEV1ROYnqk9UgGfPV7v6JzT7kAWKpiXJF2rHfDhUHJNc4SblXLjLABfWVYxkzMxGWOFBcyRVMIAsV1ZzlfWVTMTOP6MQGU1TMdfFiABE4AF56ojETOPIpqqjrEoRMR0BlFU9/EykTkyIyiqYjpLCapXPRifSs6JnHc5pifBiAy5p7GWCgy5pjpCc1XmgDOLtcdpSa6p8WIGn0z9nextt/jm1VuNduKqKKqtNTcn2arsdvz8nv/TX6Od54g3T/GNmiNTc9XEXLE1Yq6Z60579+z8+aLU3NLdouW6q6ZpqiqJpnExMdpiX0zhv01cUbVao09+5Y3G1TGP95pnniPmh5uTjz7dsHXDOa1Xm9R6P+L7MzN3Ydwp8/wBxLteFvRdxhueopztV3R2Y61X9THq6KI8Z6vZT+0LucW5i3sOioueFU6mqY/ph47jT0tcV8T2Z02q18aXTT3saSmaIn4z3lZeXLzKM24Ruek3edBodq0XBWzainUaPba667+pp+7qb05zMe6M4fNL1VVWaswl29zV80zMy4ZqzGPB1xx6sW7Myy56pqmZnMyxGxnzzExMdyblXTr2YALNUzGOiTMyAC0zhAGXPMT0SquZnwYwoLnPdJAFiqYImUAWJmJIqnvnqgDOblXhLGapnugCzVM9+rKmuYhhADk9bM9ZYc85mWMKf9DLnk9ZV7mIBzTPeVmqZnqxUGdNcwVVzjEdI8mBILzz5r6yrtnow7mAZTXPY5pz4McKDKKpx1X1lX5MJAZc8pzT1QAclijmn2ukeMuNnRXMYiJwEfVvRz6KKuJeH/wDGdTr69Jbu11UWKKaOaauXpMz7svZcEejDb+Fd7vb/AL7uWn1Gj2+Ju2p5cRExH3qs+MeEeeHzzgD0pbpwrorm3U2LOs0nNzUWrszHLM4ziY88NTjn0k7zxRamxfqo0+jz+Hs5iiffMz3l5enLcv8Ap2mWMjq/SPv1fEnFOt3aqJpov3ZqtUTOZt2+1FM++IiP6vLT3cly5zT0/u4/F6McdTTlld0AaRaapp7GZQBlFU9iJx4QxzgyDKKp8cHPV5sQGVNdUT0lfWTjw/owAXmk5pxEeSAE1T3ZU11dfexAZTcq7Z7lNUwwXJoZ1Xa6oxVVMsZqmUAZc8+5OaYjogBFUrFUwxwoMuefcvPOMMAGUVzGMTjCc083NOJlAF5pTMxAAyouVR2nC+snp1cagyqrqmcpmcYQAMgCKAIoALRCLRKUrKO7JjC+KVhcgSgZAErKJ6NnavxNXyT9Yarb2v8AE1fJ+sEI7IBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6ASZUUEyZAyqYUAAAAAABMGVAAABIBUUAAAAAAAAATsYAUSDIKJlQATIKAAAAmFASFgAAAEJlYAAAAAJACAAAAAADM5yAMuefNMznugBPWcgAAAAAAAAAAAAkyCiZIACSAUCQAgBFAAAAEkFEhQAAAAASQUABOygLFUwc0ygAACSqd1AAABJBQAAAAAAlIkFAAAAAAAAAACUyCkplQSFAAAAEz1Az1VDIKBIJDKljHZlEdCpWVPVlgpjomZYZXxGOOrKBKCpgQy3Nr/E1fJ+sNPDb2qJ+0VZ/kn6wsajswGlAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CvPqAqYMKAAAAAJlUwCiZUGLJMKCZVMKAigJlUwoAAAAJKgAAAACGFAYsoTCgmTBgBQAAAAAAABJlYBMKAAAAAAAAAAAAAAAAAAAJMkGFAAAAAAAAASVTAIsGAAUAAAEhQAAAASTuACgAAACSCpJEqCQqYUAAAJxgABPEFSVSQIlUhQAAAABJWAAAEwoASAJEqmFAAAAAAASYUBjDJMKAJCgAAIoBLGGUsQZCZUBlT2YQzpKlZx0hIVIZjB4rCRDIqCwkLEoK2ts/z6vl/WGq2ts/EVfJ+sEWOxAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAEkyAoAJlUwoJhQBMqmFAAAAAAAAAABPFUUAAAAAAAABFQFE8VAAAAAABMKAAAAAAAAAAACSqAoAAAAkKAAAAAAAAAAACTIKJCgAAAAAAigACSCiQoAAAAAAAAJhQAAAAAAASO6oCgAmFAAAAAAAAAAAAAAAAAAAAAAAAAEwoAIoAACGBQTCplQGdMdGDOntJUrKOyR3XwYsxhnEmJYrlSsuhDFlEYSosNnbI/3ir5P1hrNrbM/aKvl/WEix2IDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AkyooACYUAAAAAE8FQFAAAABMgZVMKAAAAAAAAAAAAAAAACKmFBJWAAAAAAAAAAAAABJlYTCgAAAAAAAAAAJKgAAHQAAAAABMKAAAAAAAAAAAkncOwCgACAoigJCoBJEhgFAAAAAAPEAAASSJVMAoAAAAAAAEpEqmAUAAAAAAAACQBIlQAAAAAJAGML4goAAAJhQAZUyxZUiVlTOTCRGGSM1YjKSsSk92dpSGUTlFpEVtbZ/n1fL+sNWG3tsfv6vl/WCLHYANtAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXn8KAoAAAAAAAAJmVABMyCgAJhQASFAEzKgCdTMgomZUAAAAAE6gomZMyCiZlQAAAAAABOpmQUTMmZBU8VQFABJlYTCgAACdVAE6rAAACTKpgCFAAEkFEzJAKAAACeKooAAAJIKJmSAUABJVAUABCTqCidTMgokKAAAAAAAAAJJAKniqAoAAJIKIZkFEzJAKACQoAAAAAAACZk6goAAAAAJhQABOoKJ1MAqSqAYJUBMqmFABMyCiZk6grKliygKyVIUc6QuEhWECAgGcQ2dsn9/V8v6w1obO2/59Xyz9YIsdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FefmTJJgVQATKphQAAAABJUAAAAAEyAoAAAAAAACZMgZViygAAAAEyqYUEyrGWUAJkyYBYAAAAAAABJlYSe5kCZWE7qAAAAAAAAAJMkAoAAAAAAAAAAAAAAAAAAkkAoAAAAAAAAAJJAdgUSFAAAAAAABJBRMmQUSJUAAAE8QUEkCSJO5gFAAAAAAJAEiVTCyAJkiQUAAABFABM9VAAABMgoAAACQoAypYsqRKyUBmkKkLlhlcGCJMgyhtbb+Iq+T9YakNrbfxFXyfrB+1jsQG2gAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+grz+FAUABMqmFAAAABFEyCgACZMgqYUABJBQAATIKJkyBgwZUGLKEwoAAAAAAJhRMgYUAAAASZBQgASZJlABYgwBlYTCgEgCeCwh2AmSDuoAJMgYVMkAoAAAAAJMkEkAoAAAAAAAAJIAZMgokKAAACSCiZIBQSQVCFBFCQBIUASJJBRIkkFSTJkCDCLkDB4k9lABPEFRQBJJO4EEmCQUSFBPFU8VAAkATJkFEiVBJgjuqYBQAAAAJBMLKZMgZVjDIBMKACYWQTKsYZAAAMqWLKkKy6qAwAnizEWFiEhYSlZNnbPxFXyT9Ya0NvbfxFXyfrB+yOwAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAABMmQVMqxBkxZJgDKphQTBhQEyqYUBFTIKmVTAKxlkmAMGDKgxZQmFAAATKpgDKpgyBlWLKAEwoAAAAAk91TAGVhMKCYSWST3AjsqQoAAJMrCYUBMKAnYgwsAJhQEwoAAACTJAKACSQTBAKAAAAAAJMkAqEyQBgwoCKJIKJlQEUBJIJIAk7kkAdiCSAUAE7ESSQBhUkiQOxkkwBBgiFBMGFARQARQEkyspgDuYIhQSTKykwCLEouAUkASJJ7GFBiLhAFiTBHcFlIlUwCgABKRILKd1TAGDCymQMCgAAAAJhQARZQFZUpC0iVkZVMFZqoowELCQsCVk2tt/EVfJ+sNVtbb+Iq+X9YJ9kdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAmVTCgmDBlQEwoAACZVMKAAAAAmFTIGVTCgAAxllCYUAAAAAABMKAmFAAAAABJlUwCgACZUEmUXBgCFAAAEmVhMKAAAAAAAJ4kAoAJMEKAAAAAAAAAAAkwQoCTB2VJAhUhQElUkCSCSAVJUAEhQAAAAASQJIgiVBJIhQEkySYAiSSIJBQAElUkCJVI7qAkqSCRKpEKASAJhQAAAlIlUwCphQBMGVAAAABJ7IyTAGSJMGAVMKAmVTCgAAAmQUAAFiBKyhYhIUSqAIAM0FyiIM4nLb2z8RV8n6w06W5tn+fV8v6wRP27EBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAcWq/C3fkn6OVx6r8Ld+SfoK8/hQFAAAAAAAATKphQAAAAAAEwoAmVTAKACKigAAJlUwCplUwCgAAAAAkqkkdgURQAATCgAAAAAAAAAAAAAAAACTJBMEAqTKpIEKkKAioCgAAkyBMkHcgFAAAAAAABJIVJBRIUAAAAAABJUBIhQAAAAAAAAAABFAAEkFEiVAAAAATKpgFAAABMKAAAAAAAAAAAAAAACYUAAAhnEMKe8OTMeYlIgxiVjHmCUAEAISpSYFliysZUtzbfxFXyfrDUpbm2/59Xy/rB+0/bsAG2gAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABQAAAASFAAAAABMgoAAAJlUwoAAAAAAAAAAAAAJkFRUBQAJAAAAAAEyoAAAkkdgUAAAAAAAAAAAAAAAEhQAAAAASYUBOxBMEAoJMgomTuCgkAoACSSQBCgAAAAAAAAAAAkkncFBJBRIlQAAASQUSJUASSJBQAEz1VMdQUAAAAAAEyCiZPEFBJ7AZMouAMmTBgFAABMgoICgACZUEhZTsZAhn0YKDOMLlx5ZUCWMwBmixCLDO0oAgsQ29s/z6vl/WGq2ts/z6vl/WCfZPt2IDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAqZVMKAJlQSFTKgmVTCgAAAAAACZMgoAAAAYnyAAAAAAAAAAAAAAAAAAAAAAQFAAEyZBQAAAA6gAAAAAAJMkEwQCgAAn5AoAAkyQCgAAAAAAAJCpAEkEkASQoAAAAAAAAAAAJKgAAAAAkgSRJMkAqSoCRCpJgFEAUSIUASTIKJlQAAAAAQFTxUAABMKAAAAJIKJhQEUABMgYUSAUAAMSAMqGLKiBKzEVKzViAiRlkXCLlKLHVtbb/n1fLP1hrU9m1tv+fPyz9YWLPt2ADbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoADFkmFBMKAAAAAAmVBMqmFBMGFABIUASVAzPmAAAAAAAAAAAAAAAAAAmFAAAEUAABMGFAAAAAOoACZVMAQqdjIKJkgFAAAAT81AQgmDsBJEpKxAEKkEyCiQoAAAAAkmQUSFAAAAAAABJBRIUBJVJA7qAAAAACSoCYIhQAAAAAEkCTJMpAL3MEQoJhQAAAAARQBMk9iO4KAAJlQAAAAAABMmQVMKAJBlQAAMzhIVIBYZ0d2MQyo7iVVBKzViBaUZSrgwZVKi09m1tv+fPy/rDVjo2tt/wA+r5f1hcVn27ABtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AAUTJkwCiZMgoAAAAmVBMKAAmVAABIUASVEyCiZUATJkFTKsZBkEAAAAAAmVBDIYAyqYUAAAAAAEyqYOwGVTuoAAAAAACZMoC9zBBkDBBkgFAAAABJkFSYMkAkrBMEAoAAAJMmSYSQXJCLAEmCSAIUAAAAAAAElQEhUkgFAAAAABJMkmAIlUiFBJIkkgFABJIkkiAVJVJBFgmCAVJVJAyZRcAoAAAAACdlSewGTuix3AwomQUAAEnsBlWMMgTCMkwBkyYMAYUAEyssYBkkKkAyiWVHdhDOkSsse8RUqLEmUTOZZNMlykAyzbW2/wCfV8v6w1YbW2/59Xy/rBCOwAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFTCgDFcGFAAAABMKAJkyYMAYVMqAAAAAmFATBlUwCLgwoJkwYUAAEyZMGAUAEwoAmVTBAKAAAAAAAAk91TAEdlAAAEyqYUEyZMGARYgwQBBhQGMrBMEAokyZBRIUEmTuTB2BJWJO5gCCZIJgCFSFAAASYUBMHZUkDudiCQIVIUAAASSAJIJIBUlUkCSDBAKAAEACSqSBkiUhYgFEkiQJIJIgFBAJMkmAIlU7ESBKQsoC5O6LEAYUAAAAATJ3MGAUAEwYUATCgAJkFTKpgEXJgwCiZUATKgAAJhQEyqYUFhlSwhaRKzhUhRKIowhCpCwJVht7Z+Iq+T9Yara2z/AD6vl/WCEdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdACTIqgAAAAAAAAAmVTCgmFABIVIBQABMqCZVMKCZVMKAAAACZVMKCZMmDAKCZBUUAEz1UAAAAEyqYUEyqYUAAAEyCpkydwMqmFBMrCYIBQAAASYSWSTAEKkEyCpMEKCQoAAACKAAAJMkATJBMEAoAAAJJkkwB3OxBIGTJgwBBJBIEKkKAACdjJJgCJJIgkCJVIhQSSIUAABDsEgRJJBIEyQYIgCUhZIgDCgAAAmVTAGTJg7AqZMoC5MmDAKAAACT2RkmAMmTBgFABMKAJhQATKpgFAAABYWmOqR2ZUdxmrhQKgAwGFTKgybW2f59Xy/rDUjs29s/EVfL+sLEjsQGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groGMrJgVQAAAAAAAAABMmQUAAAEyqYUGK5MGAUTJkFBMgomVAAAAAAATBkyCgmQJUAAAAABMkAomVAAATBlQTCgCZVMKAJkyCiZWAAAAASZO5MEAQqTJkFEyQCiTJACgAACTBCpMgqSZJBRIUASSAUEkFEhQASQUSFAAAABJIkkiAJIkkiAUSSJBRJIkFAASVATsRJJAKkqkgonYyCiZMgoAAACd1TsBgwZMgomVAEMgoAAAJlUwoAJkFEyoAAAJkFAAhUUSjKjumCnuIzAKlAGAiFIkhSMqY6Nvbf8+r5f1hqU9m3tv8An1fL+sJPtP27ABtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK8/MKAoAAAACZBQAAAAAAAAAEyqYBQAAARUUAAAAAAAAAAAAAAAAAAAAAAAAEmFgTIKAAAAAABAAACTKpMAsCQoAAAAAAJMkEwdgUSFAAAAAAAAASVASFAAAAAAAAAAABJVJBRIUCBIUAAAAEkiFACRJBQAAAAABMk9gUSFAAAAAAATKykQCgAAAAAAAAAJhUyCoqAq5hjCgy5iKo8mK090NM4lWMMktZoBCIYZRCQyNptYbW2/wCfV8v6w1YbW3fiKvl/WEn2R2ADo0AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAACZUBMKAAAAAAAAAAmQUAAAAAAEyBhQAEyoAAAAAAAJIKmVTHUFAAAAIAAJTsCgAJMKAQAAAAABKQoAAAip4goAAAAAAACTCgJCgAAAAAAAipIKJMkAKkKACAoAAAAAAAAAIoAAAAAAAAAAAAAAAEpkyBEE9lJBI7KAAAAAAAAAAJ4goAAAAJkFAATBlQAATCgAtHdCJxKUZxPVWMd8rmUSzbIhFhGFhkxWMylRlDa27/Pq+X9YasNrbf8+r5f1gn2sdgA6NAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACpkyi4AwoAAAAAAAmJUAAATJhGQAACdVAAAEwoAADGWUMZZQAACdVAE6mVTAGVTBkFAARUkFAAABJ7mCYWAIABMqkwsAAAJ1UBMSsAAACZMkmAUSOigAAJKpMAdTsdjuBlUwQCgAAAAAAACABJJgEWCFAAASFAEDuBkMHYAO5AKAAACSQoAJlQATIKAAAAkqAkKJIGTuYIgDCQsmAMqkQoAAJ1UJBMqnYyCplZSIBQAAAE6qAJlZTAEykLgwCpkyYBIZJhQAATKpgyCgAsSuWMLlLBnErDGGUd0c6sMo6MWTNRW1tv4ir5P1hqw2tt/z5+WfrBPtY7AB0aAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFTCplQBDIKAAAAJlQTKphQBMqCQoAAmQUTKgAAmVTCgAAmFAAAAAEyqYUBMKAJlWMgyEjsoAAAAJlUmDsCgAAAAAAAmTJMGAUSFBJggyoCQoAAAmVSYA7kEGQUAAAATsoJkJggFBAJIJIBQAElQEgCQFSFBJIUASVASFAAAAABO53IgCIUSQJkgwRAKB4gJkkiAUAATKgAmQUAAAAAAACUiFAAABMqACZBUydyIBQJBMmTBgDBkyYBQTIKJlQTJgwZBQIEWI6JhlDLCU2kdGVKMoZZoQLEJWWVPZtbb/AJ8/LP1hqw2tt/z6vl/WFxWfbsAG2gAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HFq/wALd+SfoK6DJkwgouTBgCUAGQACZMmAMGVTAGVTCgmFTKgAAJEKAxZQmFAAAABMqmFAAAABMqmFAAAAATCgEAAAAmVSe5HYDJ3JhYBOypPcjsCgAAAAAmTJMIC5MmDAHcghQATIGTJ3MAZMmDAKkwQoJCgAACSQTBAGQkgFSVATBCgAgCgAkoskAQoAIqSBkMEAoAAACdySIAiFE7gZMmCIBUySRAKAACZBUlUkCDJgwB3IgiFAAATKykQCplZTAGTKLEAqZJ7EdwUkASIUAJTCpkDsZWUiAUABMrKYAwZVMAqYUBjDJMKAmFAFp6otEYErKInLIQrKrCMqWEphREqMobW2/wCfPyz9YasNrbf8+r5f1gn2s+3YAOjQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0CYUFEyqYBFwi5BUyZQFwqZUAEyCgAmFAAAAAEyqYMgoJkFAAEUAABMqmAMqmFAAAAAABMqmFgATKgk9yOxPcjsCoqSBMLAAJlUmAUTsoAACTCgJCgAAAkwoCQqZUAAEyqTBAKAAAAJlQSYIUAAAABJIUAABAkgFEUAAAAAABA7gZVOxkCSIUAA8QAAAASTsqSBkyYMAZVIUATKgAAAAEgCdjKykQCykQoAAABIJ3IgiFAEmSOwKCZBRMqAAAmVliC5VMKAABDKlIWmBKyyRBg6jNVYYLEs6Ss+vmZljlSxGUS29t/EVfL+sNOOzb2z/Pq+X9YST1Y7EBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AEyKZVMKCYMKAmDCpkDCgAmFAAAAAATIKAAmFAEwoAAAACZVMKAmTJgFAAAAAAAAABJ7kdiYOwEwsAAAAAAJlQSYWABMqkwsASkKmOoKAAAAJlQSYIUAAAAAAAABJg7KkwBkMEAoAAAAAIEkAoAJCgAAAAAACSRAZAkiFAAAAAAAAAAAElQEiFAAAAAAAAAAAEVIiVAAABMgpIAmFgAJTCnUATqoAACYMqAAAACrEpEKJWUSJESyErFYknuiIyhWMT1ZJUWOzb2z/Pq+X9YasNvbf8+r5f1hJ9kdgA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAmBRUyZRcAoACYFBMqmFAAAAAAAYskwCgAIqeIKAAAAAAJKgmFAAAAABMqkwCgACZUBJhQCAAAAAASYWBMgoAAAAAAACZVJgDuQdlAAAAAAAEgyCgAIqeIKAAJCgASAJ2MgBJAKIoAAIqSoAAAAJJEKAAAAAAAAAAAAAAAJKgJCgACZBRMqAAAABmQAAAJSIUAABMqACfmoAACKnioJhUyoAAAAEZwzpmezDwWJwDliUw4+aVzIliyJlUrKx3ZMYlklSsobe2/iKvk/WGpDa238RV8v6wn7I7EBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK8/jqoCphUyoAmVBIUAAATKgAAAAAmTKAyAAABMmVAAAAABMqAACZMqAAAAAAAmFgAAATJlQAAATKgJMKAQACZXPQAAAATIKACeKgAmVATKooAACTCpkCFAAAAAAAAAElFkgDBCgJKgAAAAAIZBRMkyCiQoAAAAAACZJIBQAAAAQFAAABJMKAkQoAJlQEyZUAAAAAEUAAAJQDKp0UBMrKYAyqYUEwoACKCZMqAAAR3ZYYx3ZZgEWEjutPdKzWUQySFSs1Ylt7Z+Iq+WfrDTjo29r/EVfJP1ghHZANNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4a78k/RyOPVfhrvyT9BXn8qkworFkmDIIyYsgAAAAAAAAEyqYBFwYUAAAAAAAAAAEwoACKAnVQBMqxkFyqYUAAAAAAAAATKgk9yOxJAKAAAAAAAAkwoCQoAAAAAmJIUAEyoCTCgJ2VJIBQAAASFTKgAAgSQCgAipCgCGQURQSUZJIIuCFBIhQAAAAABJAmSEWAUEkFAATxVMAoAAAAAAAAAAAAmTIKSAJ4LAAAAAAkQoSCZVMKAACZVMKCSdVAAAAAEXC4BaexHdYxjBCVmsoVFylZqT0bW05+01fJP1hq4y29q/E1fJP1gix2YDSgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACjFkxAZJhQAATKphQBMqCZMmDAKAAAAAAAAACZVMKAmVTAKACZVMKAACZQlcAZViygAAAAAAAAEnuR2JIAyqSQCgniCgAAAmTJPdAXKsVgDKpJAKAAAACZAkiTuYBRIUEkhQEnuoAJlUkCSDBgDKpggCSCSAUABFSQJQAWDJgwBkkwgLCpCgkhJ4gqZJQFyZRYBQSQO5BCgAAAAAncDKp2MgqZJIgFAAAATJICpJlQYrHcnskAyTIQCgACQsgmVSFkEyZMGAMmUAXKphQAAEyssQZJkykAyWEWBFjrLLEsaO7kErHCYZSM7QMDKO6JTDa2uP8Aeavk/WGthtbZ+Iq+X9YJSOxAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFEwqZAyqYUAAEyqYUEwoAAAAAmVTCgAAmVTCgAAmVYyygAAAEkFTKpgFBMgksoRQTCgACZBQAAAEVJBRIUEVJIBQARUkgFABJgwoCQoAAACeJAKAAk9SSAI6KkkAoAAAAAAkkAokkdAUSepAEkKAAAAkgSQgC5VisAqSoCQoAAAJKgJgjoqSCiQoAAAAAAJJHRUkCepBCgAACKACZBUkUEhUUEkwKCQogKAAAAgAomTILKYUAAAAAliyliC4MGVAICBKypZMKZZZErIRYYqGGcYYso7IlVtbb+Iq+T9YasNrbfxFXyfrBPsjsAHRoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AAUTCgAAAJkFTKpgDKphQAAAAAAAABMqAACYUAAAAAATIKmDKgAAAAJhQAAEVJIBQAAAAAAARUkgFAAAAAAAAABJIUAAAEnuQCgAAAAACSQCpKgJCgAIAoJIKJCgkmDKgmCFAAABJOoKJGSQMqmCAVJJMAiwQoAAAAAAJKLKAsKkKAACdIMkmAJlFwQAE9iO4ASQBCgAigAJIBIAQsiAYMKABKAoAAEghhIZSDGGTGGQAEAsMssIU2ljPwWJTwKe7NZZLHZGSaFbW2/iKvk/WGq2tt/EVfJ+sJPtI7AB0aAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CvP5VOiigAAACYUBMqmFAAAAAAAAAABMKAAAAACZVMAoAJkMKCYUAAAASQUIAAAAAAAAAElQEhQAAABPEDxUAAAAAAAAAAASe6gAkKAAAAAkkKAAAAAAAJKgJHQkkwCLBCgAAAAAAAAAAkqkkQCgAAAAAAAkkKAAAAAAAISQBPYjuSQCgACQoAAAAJIqSAQQoAEgCQoAAAmVBMLIAkKkKAR1FpjqBESziFiFhPti5IR3J7kd0sNrJTlMrSDOG1tv4ir5P1hqw2tt/EVfJ+sMz7SOwAdGgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+grz8qAqZVMKACSCgAAAAAmVTCgnxUAAAAAAAEyqYBQAAAAAAAAAAAAAAABMqAACKigAAAAniqKAAAAAAAAACSBlUwQBJCgAAAAAAAAAAAAAAAACSoCR0VJ6kAoAAAAAAAAAAkkAoAAAAAJJ4qAAAAACR3UAAAAAEBQAAAEVAUAAAASAFAAAAAAAAABMKAAAAADOjuwZUpUrkI6JTOVJHNAwLpYLTMQgzYrkzDZ238RV8n6w0ctzapzqavkn6wkhI7MBtQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABUyqYMgomVAAAAATKp+QKAAACZVMKAAAAAAAACZVjLKAAABFBMqigAAigCZVMEAYIUBFRc+4BFQFAAABJIVAUAAAAAAAAAAAAAAAAAAAASepAKAAIoAAAACSoCQoAAAJKgJ1IUAAAABJMKACSeIKACZVDxBQAAABJUBMqn5AoAAkd1BJIUAAAABDqKAIoAAJPYjuSQCgAJlU/IDKooAmVAABMqmFAAAEyoLC0x3YwuQZxODmYZMe8ZscnVCI6d2UYE0gsogmG5tP4ir5J+sNRt7V+Iq+SfrBsdmAqgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQAmRTJgwoMVyi4BQAAAAATKsVyBkyYQGQmVAAAAAEyoAAJgVMAoAAAAAAAJlUwoJlUwQCgAAAJkkwBkyYMAoigJKgJCgAAAIoAAAAJPdQAAAAABJBUkgkCFSFAAAAAAAAAAAAAAABJBRIUASSAUAAAAAAAASSAUAAAAAAEkFSSFBI6KkkAoAJJCgAICpJIAZJQFVI7qAAAAACAqSSYBFygC5MouAUAAAEMhgFEhRCO7LEsY7w5MiWqJCptCQEtDEtvaoxqKvkn6w1o7NvbPxFXyfrBKunYgNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0EsVQVkmTKAMkwoAmSAMmTBgFEyZAwYVMgqYUBMKAAJAKJKgxllCYUEyrGWUAAAAAAAmVTACpkygMggAAAAAAAEUARQSSFAAAAAEVJBJWEWAVJMqCQoAAAAkgokKAJJAKJJAKAAAACZBQABJ6kAoAAAAJIKJCgAAAAkqJkFAABMgoAAAAkkAoAAJIGTKAMhIUBMkmAUSFAABJIFABJAJSFAhRAUSSAUAEnsR3J7EdwUEkCTBhQTCiZBRMqAiyxBcKmTIEKAlWO7KWEd2XURlHZUhcIaRVwqVL4kNvbPxNXyT9Yajb2v8TV8n6wkWV2QDYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI4tX+Fu/JP0FefFwgoC4AyZMIAuTCAuTKALhFySBkwjIAAAAAABMqmAUEyCSyhFAAAAABMgqYMmQMGDKgJlUwCiQoAAAigkkBkCe5HYIBQAAABDIKJlQSTCgMVgkgFAAAAAASVATBCgJJBJAEkKAkkKAkosoCwT1PiQBHRUkgFEkgFBJBRIUAAEkjoqSBPUghQSTCgJCgCSYUBIVMqAAAAACSCiQoJJhQEhQAAAAASVASFRQSTCgMVjuSQBJCgAAAAJPYjuSR3BQSewGVYsgJYskwBhRMgssVykAuEZJgCFSGUCUiJyyWIMM7Z2YZRMIL9m1WGMd2eEy8S3aYltbX+Iq+T9Ya0NvbfxFXy/rCS+kdgA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI4tX+Fu/JV9BXQZQBVwoAmUAGSYUBiuEZAmDKsQXCgAAAAAJlQAAEwoAAAAAAAmDKgxXBKgmFTKgAAAACZUEkhQEkwoCQoAAk9gFSO6gk90We5AGCFASSFAAAElQAEkDKsVgCSFAAAAAAAAASSFASSFAAAAAElUkCFSFAAAAAAAAAAASVATBCgAAAAAAAACT1JIAhQABJBRI7KAkqAkKAAAAigAAAAJJCgmCFQFSVATBCgCZVAWWK5QAgIBkmVQCGVMdUwygSsxjEmWbGayRMrHUniLHdyONllLuhlt7ZOdRV8n6w023tf4mr5P1gkI7IBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAcWr/C3fkn6OVx6r8Ld+SfoK88MmIq5ViyBiDIAAEyrFkAACZMmDAKAAADFkAAJIKAAmVTAGVTCgAAhlUBQAToqYUAAAAGMrHYkjsCgAAAniqYUAAAAEnujIBI7KJgFAAEwoAACSoCQoAJkwYBQhMAoAAk91ASSSAIUAAQFBAUABJUBIJUBIUABAFABJIUAAAAABMAoJgFAAAAAAAABMAoAAJPYDJlAGQkd1ATuqYAwoAiphQTxUAAASeyQyTAGTJgwBlUwoJlZTACLlAFyCgAAsdhYjoglAURVhFgKpAmUrLOG1tf4ir5P1hp8zb2r8TV8k/WCEjswFaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAAAAYskhQAAAAAAAAAAAABMKAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAnioCQoAAAniKkgokKAAAAAAAAAAAACSoAAAAAAAAAAAAAAAAAAAAAAAAAAniCpPZUnsBHdUjuoAAAAAAAAAAAJPYFEjsoAn5KAAAigCKAAAJ1UBlHZKiOySBEsoYwojOFYRJkRkiZUFbm1fiavkn6w04bm1fiKvkn6wDswAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/DXfkn6CvPypLEVkxZAAAAAAAAAAAAAAAAAAAAACHVQAQFGLIASO5PcFAABOoKMWQAAAAAAAJ1BQASSOxPcjsCiT3I7AoAAGQAAAABJIBU8VASFAAEkFEzJAKAAAACeIKJCgAAAAnieKgAAAAAJIKJCgCSQCgAAAAABkAAAEkgFAAAABJBRIlQElQEhUkjuCgACQoAEgkKmSO4KCT2BRIUAAAE6goAAk9kBkIoBIAxhkkKAACx2SpY7FQMYZJCiAAgyjskKluhlEQ3Nrj/eKvkn6w06ezc2z8RV8n6wSpt2QCqAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FeflQFAAAAAAAAAAAAYjIBiyAAAAAAABBQAAAARQAAAAAGLKAAAAAAAASewKJHZQAAAAAAAASexCgAk9yAJIJIBQAAAAAAAAAAAAAASQUSFAABJIUABJBRI7KCSoAAAJKgJCgAAAAAAAkqkgQrFYBQAAAElUkCFSFAAAAAAAAASeygJCpPYgFABJ7Ed1AAAASewKIoAk9kBkAACAoAAALHYqWOyVifaQqQoAKIQpgjulKyhubX+Jq+T9YasRDa2v8TV8n6wmLLsgGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvw135J+grz8os90FZAAxZAADEBkAAAMWQAxZAAAAAAAAAAACKAAAAAAAMZCVBGUIAoAAAAAAAAkkdgUAAAASe6AyEjsoAAJPchQAAEwoACSQCgACSQCgkgokKAAAkqAkKACSoDFYUBPE8VAAAAAAAAAAAEUBMKAJKMgGIySQRYRYBQSQUYgLKLCgkKAAAAAAkKAAAAAkk9iO4Ed1AASexHcFAAEnsR3BUnsqT2BAAIZIsgEsVBAAZDGGQMqUrWEqE+khSknuAqKIsMo7sYhY7hZtk29r/E1fJ+sNSlt7Z+Iq+T9YZjM+3ZANNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAAAAAMWQAAAAAxZACQoAAAAAiMgAAAAAAAAAAERkAIoCR2UAEkI7AR2UAEkkjsBHZQAAAABJ7oyASOyieIE9yFAAAAASSFAAAElQEhQBJIUAAASSSAIUASSFAAAAABJIBQAElUkCCSFBIUAElQEhUkgCSFASUZAJBKgJCgAJCgkoyASFAASSAUAAAATxUBJ7KAkd1AAAAAASexAKJJHcCeyMgGIyAYqoAADEZAIoAigDKEqWlKhEjuzYR3ZgYIjoKAE9khKjKG5tf4mr5P1hqR2be1/iavk/WCMz7dkArQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoAAAAADFkxZAMWQDFkAAAAAAAAxUFAAAAABJUAAAAAAAASQUSCOwKAAk91Se4EdlSFAAAAAAAAAAAE8VAAAAAABJIJIBQAAAAAAAAABJIBQAAAAAAASSFAElQEhQAAAABJRkkgQrFYBRJIBQAAABJIBRJIBUlQEhQAAAlOqgAk9iO4E9iO6gAAAAAACST2I7gR3UASexHdQAAAAAAGIqAKigKAMqUqWEqESO7NhChGQiirCC+CVmsobe1/iavk/WGpHZt7X+Jq+T9YTFmOyAaaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAABiAyAAAAAAAAAABiDJFAAAAAAABjLKAAAAAAAASQUSOygAAAAk9yOygAAAAAJPcFEjsoAAAJ+QKAAACSQoAkqAkKAJPdUkBQAAAAAAAAAAkABJBRIUAAAAAAAAAAEkhUkFEgkFAAABJUAElQEhUkgFAAAATxUAAAAAAAAAAAAAEkjuCgAAAnVQAE/JQAAQWWMAqgAJHYjv2BnE9EkZTEYEqRHQQkIyJI8GQrGGQkM1jJlDb2v8TV8n6w1aW1tn4ir5P1giR2QDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Gu/JP0AV5+e6gKxZAAAAADFkAAAAAAAAAAAAAAAAAAAMZZQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJKAAACwoAAAAAAAAAAAAAAAAAAAJPYAI7qAAAAAJPZABY7qAAAAAAAAAAAEsYAGQAAAL5ACUJAIsdmYJSgDLFZUtra/xNXyfrANQjsgFaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAf/2Q==" alt="Rejuvenese" style="height:52px; width:auto; object-fit:contain; filter: drop-shadow(0 0 8px rgba(201,168,76,0.4));"></a>
  <ul class="nav-links">
    <li><a href="#incluye">Programa</a></li>
    <li><a href="#proceso">Proceso</a></li>
    <li><a href="#precio">Inversión</a></li>
    <li><a href="#premio">Premio</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <a href="https://wa.me/50684354162" class="nav-cta">Inscríbete ahora</a>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid-lines"></div>

  <div class="hero-content">
    <div class="hero-eyebrow">
      <div class="hero-eyebrow-line"></div>
      <span class="hero-eyebrow-text">Clínica Rejuvenese — Cirugía Plástica y Estética</span>
    </div>
    <h1 class="hero-title">
      <span class="line1">Reto</span>
      <span class="line2 gold-shimmer">Rejuvenese</span>
      <span class="line3">10 Semanas</span>
    </h1>
    <p class="hero-desc">
      El programa de transformación corporal más completo de Costa Rica. Ciencia médica, tecnología, nutrición, entrenamiento y seguimiento clínico semanal.
    </p>
    <div class="hero-checks">
      <div class="hero-check"><div class="check-icon">✓</div> Evaluación médica completa + laboratorios</div>
      <div class="hero-check"><div class="check-icon">✓</div> Seguimiento clínico semanal especializado</div>
      <div class="hero-check"><div class="check-icon">✓</div> Plan nutricional y entrenamiento incluidos</div>
      <div class="hero-check"><div class="check-icon">✓</div> Acompañamiento metabólico médico</div>
    </div>
    <div class="hero-actions">
      <a href="https://wa.me/50684354162" class="btn-primary"><span>Reservar cupo — USD $1,000</span></a>
      <a href="#incluye" class="btn-secondary">Ver programa</a>
    </div>
  </div>

  <div class="hero-visual">
    <div class="hero-photo-frame">
      <div class="hero-photo-placeholder">
        <svg class="silhouette" viewBox="0 0 260 480" fill="none" xmlns="http://www.w3.org/2000/svg">
          <ellipse cx="130" cy="60" rx="40" ry="46" fill="rgba(201,168,76,0.06)"/>
          <path d="M70 160 Q80 100 130 95 Q180 100 190 160 L200 280 L170 480 L130 460 L90 480 L60 280 Z" fill="rgba(201,168,76,0.04)"/>
          <path d="M75 165 L40 260 L70 270 L90 200" fill="rgba(201,168,76,0.04)"/>
          <path d="M185 165 L220 260 L190 270 L170 200" fill="rgba(201,168,76,0.04)"/>
          <text x="100" y="220" fill="rgba(201,168,76,0.15)" font-family="Montserrat" font-size="10" font-weight="700" letter-spacing="3">FOTO</text>
          <text x="93" y="235" fill="rgba(201,168,76,0.15)" font-family="Montserrat" font-size="10" font-weight="700" letter-spacing="3">HERO</text>
        </svg>
      </div>
      <div class="hero-photo-border"></div>
      <div class="hero-photo-border-b"></div>
      <div class="hero-badge">
        <div class="hero-badge-num">10</div>
        <div class="hero-badge-label">Semanas de<br>transformación</div>
      </div>
      <div class="hero-badge2">
        <div class="hero-badge2-num">$20K</div>
        <div class="hero-badge2-label">Premio<br>estético</div>
      </div>
    </div>
  </div>
</section>

<!-- COUNTDOWN -->
<div class="countdown-bar">
  <span class="countdown-label">⬤&nbsp; Próximo reto inicia en</span>
  <div class="countdown-units">
    <div class="countdown-unit">
      <span class="countdown-num" id="cd-days">18</span>
      <span class="countdown-unit-label">Días</span>
    </div>
    <span class="countdown-sep">:</span>
    <div class="countdown-unit">
      <span class="countdown-num" id="cd-hours">09</span>
      <span class="countdown-unit-label">Horas</span>
    </div>
    <span class="countdown-sep">:</span>
    <div class="countdown-unit">
      <span class="countdown-num" id="cd-mins">42</span>
      <span class="countdown-unit-label">Min</span>
    </div>
    <span class="countdown-sep">:</span>
    <div class="countdown-unit">
      <span class="countdown-num" id="cd-secs">00</span>
      <span class="countdown-unit-label">Seg</span>
    </div>
  </div>
  <span class="countdown-spots">Quedan <strong>7 cupos</strong> disponibles — inscripción cierra pronto</span>
</div>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item animate-on-scroll">
    <span class="stat-num">10</span>
    <span class="stat-label">Semanas de transformación</span>
  </div>
  <div class="stat-item animate-on-scroll">
    <span class="stat-num">$20K</span>
    <span class="stat-label">En procedimientos estéticos</span>
  </div>
  <div class="stat-item animate-on-scroll">
    <span class="stat-num">100%</span>
    <span class="stat-label">Seguimiento médico clínico</span>
  </div>
  <div class="stat-item animate-on-scroll">
    <span class="stat-num">1</span>
    <span class="stat-label">Programa. Resultados reales.</span>
  </div>
</div>

<!-- QUÉ INCLUYE -->
<section id="incluye">
  <div class="incluye-header">
    <div>
      <div class="section-eyebrow">
        <div class="section-eyebrow-line"></div>
        <span class="section-eyebrow-text">El programa</span>
      </div>
      <h2 class="section-title">No es solo<br><em>bajar de peso.</em></h2>
    </div>
    <div>
      <p class="section-sub">
        El Reto Rejuvenese es un programa médico completo diseñado para transformar tu cuerpo, optimizar tu metabolismo y cambiar tu estilo de vida — con el rigor científico de una clínica especializada.
      </p>
    </div>
  </div>

  <div class="incluye-grid">
    <!-- Card 1 -->
    <div class="incluye-card animate-on-scroll">
      <div class="incluye-card-num">01 —</div>
      <div class="incluye-card-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="6" y="4" width="28" height="32" rx="2" stroke="currentColor" stroke-width="1.5"/>
          <path d="M13 14h14M13 20h14M13 26h8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <circle cx="30" cy="30" r="7" fill="#0a0a0a" stroke="currentColor" stroke-width="1.5"/>
          <path d="M27 30l2 2 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
      </div>
      <div class="incluye-card-title">Evaluación Inicial</div>
      <div class="incluye-card-desc">Diagnóstico clínico completo al inicio del programa.</div>
      <ul class="incluye-card-items">
        <li>Historia clínica detallada</li>
        <li>Análisis corporal + bioimpedancia</li>
        <li>Laboratorios metabólicos y hormonales</li>
        <li>Fotografías evolutivas iniciales</li>
      </ul>
    </div>

    <!-- Card 2 -->
    <div class="incluye-card animate-on-scroll">
      <div class="incluye-card-num">02 —</div>
      <div class="incluye-card-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="20" cy="20" r="14" stroke="currentColor" stroke-width="1.5"/>
          <path d="M20 10v10l6 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <circle cx="20" cy="20" r="2" fill="currentColor"/>
        </svg>
      </div>
      <div class="incluye-card-title">Seguimiento Semanal</div>
      <div class="incluye-card-desc">Monitoreo médico continuo cada semana durante las 10 semanas.</div>
      <ul class="incluye-card-items">
        <li>Consulta médica semanal</li>
        <li>Revisión de métricas corporales</li>
        <li>Fotografías evolutivas comparativas</li>
      </ul>
    </div>

    <!-- Card 3 -->
    <div class="incluye-card animate-on-scroll">
      <div class="incluye-card-num">03 —</div>
      <div class="incluye-card-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M8 28c4-8 10-14 16-12s8 12 8 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <circle cx="20" cy="14" r="6" stroke="currentColor" stroke-width="1.5"/>
          <path d="M14 34h12" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
      </div>
      <div class="incluye-card-title">Acompañamiento Metabólico</div>
      <div class="incluye-card-desc">Optimización hormonal y metabólica con protocolo clínico especializado.</div>
      <ul class="incluye-card-items">
        <li>Protocolo médico clínico</li>
        <li>Optimización hormonal y metabólica</li>
        <li>Monitoreo de respuesta clínica</li>
      </ul>
    </div>

    <!-- Card 4 -->
    <div class="incluye-card animate-on-scroll">
      <div class="incluye-card-num">04 —</div>
      <div class="incluye-card-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M8 32L16 18l6 8 4-10 6 14" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M8 32h24" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
      </div>
      <div class="incluye-card-title">Plan Nutricional</div>
      <div class="incluye-card-desc">Plan alimenticio estructurado para acompañar todo el programa durante las 10 semanas.</div>
      <ul class="incluye-card-items">
        <li>Plan nutricional semanal</li>
        <li>Recetas y guías de preparación</li>
        <li>Orientación sobre macronutrientes</li>
      </ul>
    </div>

    <!-- Card 5 -->
    <div class="incluye-card animate-on-scroll">
      <div class="incluye-card-num">05 —</div>
      <div class="incluye-card-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 28V20M20 28V12M28 28V18" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M8 32h24" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <circle cx="12" cy="20" r="3" stroke="currentColor" stroke-width="1.5"/>
          <circle cx="20" cy="12" r="3" stroke="currentColor" stroke-width="1.5"/>
          <circle cx="28" cy="18" r="3" stroke="currentColor" stroke-width="1.5"/>
        </svg>
      </div>
      <div class="incluye-card-title">Plan de Entrenamiento</div>
      <div class="incluye-card-desc">Rutinas estructuradas para maximizar tu transformación corporal durante el programa.</div>
      <ul class="incluye-card-items">
        <li>Rutinas semanales estructuradas</li>
        <li>Guía de ejecución por semana</li>
        <li>Progresión controlada y segura</li>
      </ul>
    </div>

  </div>
</section>

<!-- PROCESO -->
<section id="proceso">
  <div class="proceso-header">
    <div>
      <div class="section-eyebrow">
        <div class="section-eyebrow-line"></div>
        <span class="section-eyebrow-text">Cómo funciona</span>
      </div>
      <h2 class="section-title">Tu ruta de<br><em>transformación.</em></h2>
      <p class="section-sub" style="margin-top:1rem;">10 semanas estructuradas para maximizar cada fase de tu transformación física y metabólica.</p>
    </div>
    <div class="proceso-visual">
      <div class="proceso-card-visual">
        <div class="semana-display">10</div>
        <div class="proceso-card-title">Semanas de programa</div>
        <div class="proceso-card-sub">Cada semana es una fase médicamente diseñada hacia tu mejor versión.</div>
      </div>
    </div>
  </div>

  <div class="proceso-timeline">
    <div class="proceso-line"></div>
    <div class="proceso-steps">
      <div class="proceso-step">
        <div class="proceso-dot">01</div>
        <div>
          <div class="proceso-step-label">Semana 1</div>
          <div class="proceso-step-title">Evaluación Inicial</div>
          <div class="proceso-step-desc">Historia clínica, bioimpedancia, laboratorios metabólicos y hormonales, fotografías basales. Tu punto de partida documentado.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">02</div>
        <div>
          <div class="proceso-step-label">Semanas 2–4</div>
          <div class="proceso-step-title">Activación Metabólica</div>
          <div class="proceso-step-desc">Inicio del protocolo nutricional y de entrenamiento. Primera aplicación del acompañamiento metabólico médico. Incorporación progresiva al programa.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">03</div>
        <div>
          <div class="proceso-step-label">Semanas 5–7</div>
          <div class="proceso-step-title">Fase de Aceleración</div>
          <div class="proceso-step-desc">Máxima intensidad metabólica. Seguimiento médico semanal continuo. Monitoreo de métricas: peso, composición, grasa, músculo.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">04</div>
        <div>
          <div class="proceso-step-label">Semanas 8–9</div>
          <div class="proceso-step-title">Consolidación y Definición</div>
          <div class="proceso-step-desc">Seguimiento clínico final. Fotografías evolutivas comparativas. Preparación para la evaluación final y documentación de resultados.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">05</div>
        <div>
          <div class="proceso-step-label">Semana 10</div>
          <div class="proceso-step-title">Evaluación Final y Premio</div>
          <div class="proceso-step-desc">Medición final completa. Comparación de laboratorios. Fotografías finales. El participante con la mejor transformación corporal integral gana hasta USD $20,000 en procedimientos estéticos.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PRECIO -->
<section id="precio">
  <div class="precio-inner">
    <div>
      <div class="section-eyebrow">
        <div class="section-eyebrow-line"></div>
        <span class="section-eyebrow-text">Inversión</span>
      </div>
      <h2 class="section-title">Un programa.<br><em>Resultados reales.</em></h2>
      <p class="section-sub" style="margin-top:1.5rem;">
        Tu inversión incluye 10 semanas de atención médica especializada, tecnología de análisis corporal, nutrición personalizada y seguimiento clínico continuo.
      </p>
      <p style="font-size:0.78rem; color:var(--titanium); margin-top:2rem; line-height:1.9;">
        El precio incluye todo el programa. No hay costos ocultos. La valoración médica inicial es parte del paquete. Cupos limitados por cohorte.
      </p>
    </div>

    <div class="precio-card animate-on-scroll">
      <div class="precio-label">— Programa Completo —</div>
      <div class="precio-amount"><span>USD</span> $1,000</div>
      <div class="precio-period">10 semanas · Cupo individual · Todo incluido</div>
      <div class="precio-divider"></div>
      <ul class="precio-features">
        <li>Evaluación médica completa + laboratorios</li>
        <li>Análisis corporal por bioimpedancia</li>
        <li>Perfil hormonal y metabólico</li>
        <li>10 semanas de seguimiento clínico semanal</li>
        <li>Acompañamiento metabólico médico personalizado</li>
        <li>Plan nutricional semanal adaptado</li>
        <li>Rutinas de entrenamiento personalizadas</li>
        <li>Acceso completo a la App Rejuvenese</li>
        <li>Fotografías evolutivas comparativas</li>
        <li>Participación en sorteo de USD $20,000</li>
      </ul>
      <a href="https://wa.me/50684354162" class="btn-primary" style="width:100%; justify-content:center; margin-bottom:1rem;">
        <span>Reservar mi cupo ahora</span>
      </a>
      <div class="precio-note">Aplican restricciones. Valoración médica requerida. Cupos limitados por cohorte.</div>
    </div>
  </div>
</section>

<!-- PREMIO -->
<section id="premio">
  <div class="premio-bg"></div>
  <div class="premio-content">
    <div class="premio-eyebrow">◆ &nbsp; Premio a la mejor transformación &nbsp; ◆</div>
    <h2 class="premio-title">Gana hasta</h2>
    <span class="premio-amount gold-shimmer">$20,000</span>
    <div class="premio-subtitle">En procedimientos estéticos y corporales con Clínica Rejuvenese</div>
    <div class="premio-items">
      <span class="premio-item">Cirugía estética</span>
      <span class="premio-item">Tratamientos faciales</span>
      <span class="premio-item">Procedimientos corporales</span>
      <span class="premio-item">Medicina estética preventiva</span>
    </div>
    <a href="https://wa.me/50684354162" class="btn-primary" style="font-size:0.75rem;">
      <span>Quiero participar — inscríbete aquí</span>
    </a>
    <div class="premio-fine" style="margin-top:1.5rem;">
      El premio se otorga al participante con la mayor transformación corporal integral evaluada por el equipo médico.<br>
      Aplican términos y condiciones. Valoración médica de ingreso requerida.
    </div>
  </div>
</section>

<!-- APP -->
<section id="app">
  <div class="app-inner">
    <div>
      <div class="section-eyebrow">
        <div class="section-eyebrow-line"></div>
        <span class="section-eyebrow-text">Tecnología</span>
      </div>
      <h2 class="section-title">Tu progreso<br><em>en la palma</em><br>de tu mano.</h2>
      <p class="section-sub" style="margin-top:1.5rem; margin-bottom:2.5rem;">
        La App Rejuvenese centraliza tu programa completo: métricas, nutrición, entrenamiento y seguimiento médico — todo en tiempo real.
      </p>
      <div class="app-features">
        <div class="app-feature">
          <div class="app-feature-icon">📊</div>
          <div>
            <div class="app-feature-title">Dashboard de métricas</div>
            <div class="app-feature-desc">Peso, grasa corporal, masa muscular, hidratación y progreso semanal visualizado en tiempo real.</div>
          </div>
        </div>
        <div class="app-feature">
          <div class="app-feature-icon">🥗</div>
          <div>
            <div class="app-feature-title">Nutrición personalizada</div>
            <div class="app-feature-desc">Comidas, recetas, macros y recordatorios de hidratación adaptados a tu plan semanal.</div>
          </div>
        </div>
        <div class="app-feature">
          <div class="app-feature-icon">💪</div>
          <div>
            <div class="app-feature-title">Entrenamiento diario</div>
            <div class="app-feature-desc">Rutina del día con videos, checklists y progresión semanal controlada por tu coach.</div>
          </div>
        </div>
        <div class="app-feature">
          <div class="app-feature-icon">🏆</div>
          <div>
            <div class="app-feature-title">Gamificación y ranking</div>
            <div class="app-feature-desc">Puntos, logros y ranking del reto para mantenerte motivado y en competencia sana.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- PHONE MOCKUP -->
    <div class="app-phone">
      <div class="phone-frame">
        <div class="phone-notch"></div>
        <div class="phone-screen">
          <div class="phone-status">
            <span class="phone-time">09:41</span>
            <span class="phone-logo">REJUVENESE APP</span>
            <span style="font-size:0.6rem; color:var(--titanium);">●●● 94%</span>
          </div>
          <div class="phone-greeting">Buenos días,</div>
          <div class="phone-name">María Fernanda 👋</div>

          <div class="phone-week-bar" style="width:40%"></div>
          <div class="phone-week-bar-bg" style="margin-top:12px"></div>

          <div class="phone-metrics">
            <div class="phone-metric">
              <div class="phone-metric-val">72.4<span style="font-size:0.5rem; font-weight:400">kg</span></div>
              <div class="phone-metric-lbl">Peso</div>
              <div class="phone-metric-chg">↓ 3.8 kg</div>
            </div>
            <div class="phone-metric">
              <div class="phone-metric-val">24.1<span style="font-size:0.5rem; font-weight:400">%</span></div>
              <div class="phone-metric-lbl">Grasa</div>
              <div class="phone-metric-chg">↓ 2.2%</div>
            </div>
            <div class="phone-metric">
              <div class="phone-metric-val">52.3<span style="font-size:0.5rem; font-weight:400">kg</span></div>
              <div class="phone-metric-lbl">Músculo</div>
              <div class="phone-metric-chg">↑ 0.9 kg</div>
            </div>
            <div class="phone-metric" style="border-color:rgba(77,184,153,0.3)">
              <div class="phone-metric-val" style="color:var(--green-accent)">87<span style="font-size:0.5rem; font-weight:400">%</span></div>
              <div class="phone-metric-lbl">Progreso</div>
              <div class="phone-metric-chg" style="color:var(--gold)">Semana 4</div>
            </div>
          </div>

          <div class="phone-section-title">Tareas de hoy</div>
          <div class="phone-task">
            <div class="phone-task-check done">✓</div>
            <span class="phone-task-text">Desayuno — Bowl proteico</span>
          </div>
          <div class="phone-task">
            <div class="phone-task-check done">✓</div>
            <span class="phone-task-text">Entrenamiento — Cardio HIIT 30min</span>
          </div>
          <div class="phone-task">
            <div class="phone-task-check todo"></div>
            <span class="phone-task-text" style="color:var(--titanium)">Cita médica — 3:00 PM</span>
          </div>
          <div class="phone-task">
            <div class="phone-task-check todo"></div>
            <span class="phone-task-text" style="color:var(--titanium)">Registrar cena</span>
          </div>
        </div>
        <div class="phone-nav">
          <div class="phone-nav-item active"><span class="phone-nav-icon">⊞</span>Inicio</div>
          <div class="phone-nav-item"><span class="phone-nav-icon">🥗</span>Nutrición</div>
          <div class="phone-nav-item"><span class="phone-nav-icon">💪</span>Entreno</div>
          <div class="phone-nav-item"><span class="phone-nav-icon">📈</span>Progreso</div>
          <div class="phone-nav-item"><span class="phone-nav-icon">🏥</span>Médico</div>
        </div>
      </div>
      <div class="phone-glow"></div>
    </div>
  </div>
</section>

<!-- TESTIMONIOS -->
<section id="testimonios">
  <div class="testimonios-header">
    <div class="section-eyebrow" style="justify-content:center;">
      <div class="section-eyebrow-line"></div>
      <span class="section-eyebrow-text">Resultados reales</span>
      <div class="section-eyebrow-line"></div>
    </div>
    <h2 class="section-title" style="text-align:center;">Ellos ya<br><em>transformaron</em> su vida.</h2>
  </div>

  <div class="testimonios-grid">
    <div class="testimonio-card animate-on-scroll">
      <div class="testimonio-result">−8.4 kg en 10 semanas</div>
      <div class="testimonio-quote">"</div>
      <p class="testimonio-text">
        No es solo el cambio físico — es la seguridad que siento. El equipo médico me acompañó en cada paso, ajustando el programa según cómo respondía mi cuerpo. Los resultados fueron más allá de lo que esperaba.
      </p>
      <div class="testimonio-author">
        <div class="testimonio-avatar">AM</div>
        <div>
          <div class="testimonio-name">Andrea M.</div>
          <div class="testimonio-meta">Reto Rejuvenese — Cohorte anterior</div>
        </div>
      </div>
    </div>
    <div class="testimonio-card animate-on-scroll">
      <div class="testimonio-result">−6.1 kg · −3.8% grasa</div>
      <div class="testimonio-quote">"</div>
      <p class="testimonio-text">
        Llevo años intentando perder peso con dietas. Esto fue completamente diferente: laboratorios desde el día uno, ajustes médicos semanales y una app que me mantuvo enfocado. Por fin entendí mi metabolismo.
      </p>
      <div class="testimonio-author">
        <div class="testimonio-avatar">CR</div>
        <div>
          <div class="testimonio-name">Carlos R.</div>
          <div class="testimonio-meta">Reto Rejuvenese — Cohorte anterior</div>
        </div>
      </div>
    </div>
    <div class="testimonio-card animate-on-scroll">
      <div class="testimonio-result">+2.1 kg músculo</div>
      <div class="testimonio-quote">"</div>
      <p class="testimonio-text">
        La diferencia es el seguimiento médico real. No es un gimnasio ni un nutricionista solo — es un equipo completo que diseña cada semana con base en tus resultados. Gané músculo y perdí grasa al mismo tiempo.
      </p>
      <div class="testimonio-author">
        <div class="testimonio-avatar">LP</div>
        <div>
          <div class="testimonio-name">Laura P.</div>
          <div class="testimonio-meta">Reto Rejuvenese — Cohorte anterior</div>
        </div>
      </div>
    </div>
  </div>
  <p style="text-align:center; margin-top:2rem; font-size:0.65rem; color:var(--titanium); font-style:italic;">
    * Resultados individuales varían. Todos los participantes completaron el programa con valoración médica de ingreso.
  </p>
</section>

<!-- FAQ -->
<section id="faq">
  <div class="faq-inner">
    <div>
      <div class="section-eyebrow">
        <div class="section-eyebrow-line"></div>
        <span class="section-eyebrow-text">Preguntas frecuentes</span>
      </div>
      <h2 class="section-title">Resolvemos<br><em>tus dudas.</em></h2>
      <p class="section-sub" style="margin-top:1.5rem;">¿Tienes más preguntas? Escríbenos por WhatsApp y un médico te responderá personalmente.</p>
      <a href="https://wa.me/50684354162" class="btn-primary" style="margin-top:2rem; display:inline-flex;">
        <span>📲 WhatsApp +506 8435-4162</span>
      </a>
    </div>

    <div class="faq-list">
      <div class="faq-item">
        <button class="faq-question" onclick="toggleFaq(this)">
          ¿Quién puede participar en el Reto Rejuvenese?
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Cualquier persona mayor de 18 años que desee transformar su cuerpo bajo supervisión médica. Se requiere valoración médica de ingreso para verificar que el programa sea adecuado para tu condición de salud actual. Aplican restricciones médicas.</p>
        </div>
      </div>
      <div class="faq-item">
        <button class="faq-question" onclick="toggleFaq(this)">
          ¿Qué incluye exactamente el precio de USD $1,000?
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>El precio incluye: evaluación médica inicial completa, laboratorios metabólicos y hormonales, bioimpedancia, 10 consultas de seguimiento semanal, plan nutricional personalizado, rutinas de entrenamiento, protocolo de optimización metabólica, acceso a la App Rejuvenese y participación en el reto con opción al premio de USD $20,000.</p>
        </div>
      </div>
      <div class="faq-item">
        <button class="faq-question" onclick="toggleFaq(this)">
          ¿Cómo se otorga el premio de USD $20,000?
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Al finalizar las 10 semanas, el equipo médico evalúa la transformación corporal integral de todos los participantes — considerando cambio en composición corporal, adherencia al programa y mejora en métricas clínicas. El participante con la mejor transformación gana hasta USD $20,000 en procedimientos estéticos con Clínica Rejuvenese.</p>
        </div>
      </div>
      <div class="faq-item">
        <button class="faq-question" onclick="toggleFaq(this)">
          ¿Tengo que venir a la clínica todas las semanas?
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Sí. El seguimiento semanal presencial en clínica es parte fundamental del programa. Las consultas incluyen medición corporal, revisión de progreso y ajustes al protocolo. La clínica está ubicada en San José, Costa Rica. Consulta disponibilidad de horarios al inscribirte.</p>
        </div>
      </div>
      <div class="faq-item">
        <button class="faq-question" onclick="toggleFaq(this)">
          ¿Cuántos cupos hay por cohorte?
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>Los cupos por cohorte son limitados para garantizar atención médica de calidad. Una vez que se completa el cupo de la cohorte, el siguiente grupo inicia cuando haya disponibilidad. Te recomendamos asegurar tu lugar con anticipación.</p>
        </div>
      </div>
      <div class="faq-item">
        <button class="faq-question" onclick="toggleFaq(this)">
          ¿El programa es seguro si tengo condiciones de salud?
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-answer">
          <p>La valoración médica de ingreso es precisamente para evaluar tu condición de salud y determinar si el programa es adecuado para ti. El programa es supervisado por médicos especializados y se ajusta de manera individual. Si tienes condiciones previas, comunícalo al momento de agendar tu evaluación.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA FINAL -->
<section id="cta">
  <div class="cta-inner">
    <div class="section-eyebrow" style="justify-content:center; margin-bottom:2rem;">
      <div class="section-eyebrow-line"></div>
      <span class="section-eyebrow-text">Cupos limitados</span>
      <div class="section-eyebrow-line"></div>
    </div>
    <h2 class="section-title" style="text-align:center; font-size:clamp(2.5rem,5vw,4.5rem); margin-bottom:1rem;">
      ¿Listo para tu<br><em>mejor cambio?</em>
    </h2>
    <p style="font-size:0.9rem; color:var(--titanium); max-width:500px; margin:0 auto 3rem; line-height:1.9; text-align:center;">
      Únete al próximo Reto Rejuvenese. 10 semanas de transformación integral con acompañamiento médico especializado.
    </p>
    <div style="display:flex; gap:1rem; justify-content:center; flex-wrap:wrap;">
      <a href="https://wa.me/50684354162" class="btn-primary" style="font-size:0.75rem; padding:18px 40px;">
        <span>Inscríbete ahora — USD $1,000</span>
      </a>
    </div>
    <div class="cta-restrict">Aplican restricciones. Valoración médica requerida. Cupos limitados por cohorte.</div>

    <div class="cta-contact">
      <a href="https://wa.me/50684354162" class="cta-contact-item">
        <span class="cta-contact-icon">📲</span> WhatsApp +506 8435-4162
      </a>
      <a href="https://instagram.com/rejuvenese.vanes" class="cta-contact-item">
        <span class="cta-contact-icon">📸</span> @rejuvenese.vanes
      </a>
      <a href="#" class="cta-contact-item">
        <span class="cta-contact-icon">📍</span> San José, Costa Rica
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo"><img src="data:image/png;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/4gHYSUNDX1BST0ZJTEUAAQEAAAHIAAAAAAQwAABtbnRyUkdCIFhZWiAH4AABAAEAAAAAAABhY3NwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQAA9tYAAQAAAADTLQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAlkZXNjAAAA8AAAACRyWFlaAAABFAAAABRnWFlaAAABKAAAABRiWFlaAAABPAAAABR3dHB0AAABUAAAABRyVFJDAAABZAAAAChnVFJDAAABZAAAAChiVFJDAAABZAAAAChjcHJ0AAABjAAAADxtbHVjAAAAAAAAAAEAAAAMZW5VUwAAAAgAAAAcAHMAUgBHAEJYWVogAAAAAAAAb6IAADj1AAADkFhZWiAAAAAAAABimQAAt4UAABjaWFlaIAAAAAAAACSgAAAPhAAAts9YWVogAAAAAAAA9tYAAQAAAADTLXBhcmEAAAAAAAQAAAACZmYAAPKnAAANWQAAE9AAAApbAAAAAAAAAABtbHVjAAAAAAAAAAEAAAAMZW5VUwAAACAAAAAcAEcAbwBvAGcAbABlACAASQBuAGMALgAgADIAMAAxADb/2wBDAAUDBAQEAwUEBAQFBQUGBwwIBwcHBw8LCwkMEQ8SEhEPERETFhwXExQaFRERGCEYGh0dHx8fExciJCIeJBweHx7/2wBDAQUFBQcGBw4ICA4eFBEUHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh7/wAARCAWSCrIDASIAAhEBAxEB/8QAHAABAQACAwEBAAAAAAAAAAAAAAECBAMFBgcI/8QAVhABAAEDAgQCBwUGAwQHBAUNAAECAxEEBQYSITFBUQcTImFxcrEUMjSBwQgjQlKRoRUzYhYkstEXQ1OCs+HwJ2OS8SZUVWRzdKLCJTWjw9I2RIOEk//EABkBAQEBAQEBAAAAAAAAAAAAAAABAgMEBf/EACkRAQEAAgMAAgICAgICAwAAAAABAhEDEiETMQRBIlEyMyNhFCQ0QnH/2gAMAwEAAhEDEQA/APyuAMgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAJhQAAAAAAAAAAAABPBUhQAAAAAAAAAAAASO6iZBQAAAAAAAAAAAAAAAAAAAAAATxBQAAAASQUAAACQAAAAASFAAAAAAAAAAAAAAAAAAAAAAAASFAABI7qAAACSoCeKgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACQoAAAAAEADKBKVkFhZlI7BUqwQkLDMYZRDb2v8AE1fJ+sNSG3tn4ir5P1hJ9kdkA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAACZUAAEyqYUAABMqmAUAAAEwoAAAAAAAAAAAAAJhQBI7qAAAAAAAAAAAAACeKgAAAAAAAAAAAAAAAAAAAAAAAAAAASAJCgAAAAAAAAAAAAAAAAAAAACR3UASSAUAAAAAEhQAAATJJgFEhQATxBQAAAAAAABIUAAAAAAAAAAAAAAAEyCiZUCGWGMd2YlI7B4CVKKjKGWayhtbX+Iq+T9Yaja2v8RV8k/WCEdmA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAmFAAAAAAAEyZMGAUAAAAAATKgJlUwCgAAAAAAAAAAAAAAACSQCgAAAAAAAAAAAAAAAAAAAAAAACSQCiSQCgAAAAAJKgJCiSCiQSCiQoAAAAAAAmVAAAAAAAAAAAAAEkgFAAABJPFQAAAQ8QUAAAAAAEkBUAFSFAAAAAQkgFTJJgFTJJgFABI7qJkFTJlAXKLhIBcEKQBDNDIqwuUjsJWKuVhjDKErNVtbX+Jq+T9Yarb2uP8AeKvkn6wkJ9uyAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugBMiqAAJlQAAAAAAAAAAAAAAYsgAAAEyoAAAAAAAAAAJlUlQAAAAAAAAAAAAAAAAScrAAAAAAJKgJCgAJJAKAAAAAAAAAAAAAAAAAAAAAAkkoAsEKAACSQoAAAAAkqAkKAJJCgAACSoCQoAJKgJCgAAAAAAACT2AkjuR3UAEnsAqQAqE9iO4KCAoJPYDJlFBQAGLJMghC5AVDKgAAyhFhEqso7BHYSsLCiZkZZRLb2v8AEVfJ+sNPPxbW0/iavkn6waJHaANNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXn5RZUUABiyEgFAAAAAAAAAAAAEkBQAAARQAAAAAAAAAAAAAAAEnsR2BQAAAAAAAAAAAEnuoCR2UAAAAAAAAAAAAAAAAABJIAkhUkFAAAAAAAAAAAASVAAAAASSCSAUAAAAAAAAAAAAAAAAAAAEnsR3UAAAEnsR3BQAAASexHdQAAEnsR3UAAAAAAAYsgEUARUAUAGUIsCUWOxBHYhGauVYsgg29q/E1fJP1hqNvavxFXyT9YU27MBQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AAUAAYrCgAAAAAkAoAAAAADFkAAAAmAUAAAAAAAAABI7qnmCgAAAAAAAAAAAAAAAAAAACYUAE8QUAAABJUBIUAAAAABPEgFAAAAABJUAAAAAAAAAAAAAASQJRYUEhQAAAAAAAAAAAAAAAABJPFQEnsR3UAAAAATxJ7EdgUAAAEnsR3UAABMKAAk9gFAASVliAKoIoAARHUGVKkQCWi0mCUrNqiYVk2Q3Nr/EVfJ+sNTDb2v8TV8n6wsT9uyAaaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFEhQAABIUAAAAAEwoAmFAElQAAAAAAAAAAAAEjuoAAAkd1AAAAAAAAAAAAAAAAAAAE8VAAAAAAAAAAAAAAAEhQAAAAAAAAAAAAAAAAAAAAAAAAAAAAElQASO6gAAAAAAAJgFAABAUABJ7KAkdlAAAAAAAAAAAAAAAAAAABFAAASFAAgBKsSyYxHVkJVI6osIyywAyg2tr/ABNXyfrDVbW1/iavk/WFix2YDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV5+VAUAAAAAAAAAAAAAAAAAAAABAUAAGMgyCAAAAAAAAAAQjsCgAAAAAAAAAk9iOygAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJIKJ1JBQAAAAAAAAAAAElQEhQAAAAAAAAAAAD+gAniR3UASSO4KAAAAAAAAAAAAAAAAACT2FACRJ7gKAAigAAkd2UIQDJWIDOOwkT0WO7DB1WAEqtra/xNXyfrDVy2tq/E1fJP1gix2YDagAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAMWQAAAAAAAxZAAAAAAAAAAAAAAigAAIoAAAAAAAAAAAAAAAJ4qAJPZQEjsoAAAAACT2IBQAAAAAAAAAAAAAAAAAAATxPFQAAAAAAATxPEFAABJBRIUAAAAAAAABJVJAhUhQAAAACRJAhUhQASQUSO6gk9jxUAABJ7HiT2I7goAAkkdwUAAAAAAAAAAABFAAAEUAlKVSAZCwBVVBLGFyuWLJLEo29q/E1fJP1hqx2be1x/vNXyT9YSLHZANqAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FeflUlBQZAAAAAAADFkAkKAAMQZCQoAJIKAAACKAAigAAAAxkABlDFQSRUBY7KkdlABJ7AokdlAAAAABJ7gokdlAAAAAEnugLJBCgAAAAAAJJJAIsEkAoAJCgAAAAAACSQoAAAAAAAAAACSQSQCgAAAAAJKpIEKh4gSQoAAAAAAAAAAAAAAACSBPYjuix3BUnsT2QFjuqR3UAABJ7KAkd1EnsCjEBkCAoigAASxWe6gxICAZBKQDOlZYx2M/EGUdghUtYSGUBDNqVW1tf4mr5P1hqtva/xNXyfrBCOyAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugE8VFAAAAAAAAAAYsgAAAAAAAAAAAEUAAAGMgyYgAKoDGWTEFViyAAAAAAAABJ7kdlAAABJ7oDISFBJ7os9yOwIsKAk9yCe6AskIsAoAJJBJAKACSQoAJPdQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABJUAAAAAAAQwCpKgJCgAAAACT2I7qAAAk9iO6gAAAAAJPYFSUWO4IMgGKqAAAIqAKMQURkAkKAyiOiLHZjkGcdgjtCpWaoQqVmja2v8TV8n6w1W1tf4mr5P1ghHZgNNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAAAAAMWTFkAAAAAAACSCgAAAAAAAAAIAIMmIDKGLKAYyKoAAAAIR2UBJ7oySQQFjsCDIBisKk9wUYrHYCe6LPdAAWOwIsE90BZ7kIsASQoAkqAxWCSAUAAAATxIAnuoAAAAAAAAAAAJKgJBJJAIsKAAAAAAAkkEkAoAAAAAAAAAJKLJAEKAAAAJIKJHZQSeyMgEjuT2VJ7Aix3DqCgAAAAAk9kWexHcCFSexHcFBJ7AoxZAAAAAEgDFRQCkKe4M/Biyn7rAZn0z8AjwZCCsVZqVW1tf4mr5P1hqZbe1T/vNXyT9YIR2YDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoAAAAAAAAAAJKgCYUAAAYqCMgAAAAAAAYkgAADKGLKABMGAUTCgkkdlAQhUnuBJHYhQAABMGAUAEnuiz3QBY7IsdgJ7kdie5HYFAAAASVSQQABYIUBJ7mDAKCYBRMHgCiQoAAAJgFSRQAAAAAASSFAAAAmEBRACFABJUBisEmAUTCgBMJgFBMAoAJJCgAJgFAiAElce8BI7KAAJPYFEjuoAmFAEwYBQAAAAAAAEnsYMAtLLokQAniJ4rIIIyAAkAYrHYFWnuxwtPcGbFYhI7hWUeCpHZYS1gwoJbsRubV+Jq+SfrDTw3Nq/EVfJP1gg7MBpQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABQAAAAAAAAAAAAABiyAGLIAAAAAAAABjISAMoYsoABOgKCR3BQAAAYysdlwYBPFViIZcsCbYDPkSaQ2xGURDGYFA6R3PgAB08QSe5HZfgk9gUSOygAAAAkosoACwCLCgAAAAAAAAAAAkqAJMkAoAAAAAAAAAAAAAAJIKJEqAAAAAAAAAAAJKwAAAAAACSR3UBJ7Ed1AAAAAAABJ7EgT2I7kd1AAAAATKgJC5CQCWMMgYkMgAAAAEjuR3VI7gzhFgShDKGMMoSsKIZRYzp7Nra/wARV8s/WGpS2tr/ABNXyfrCxI7MBpQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvw135J+grz/AIqk91FAYgyGLIAAAAAAAAAAAYsgAAATIKJkyCsQAZQQAxllDGWUAAAAABHckEx1XAoJjomGUR1ZYBIjouGUU9Fwzaztx+LKOzLHuWITbO2Iz5UmnEGzbBKockQTBtduLCTHVnMdTC7XbjwYcmFinMGzbiwOSYxKTDWzbAZ4SYGmKT2WYASFAElGQDEZAJCgAAASAJCpKAyEhQAAAAAABJIBQAAAAAASQUSFAAAAAAAAAEkiQUAAAAAAAEk8STIKJEqAAAJJHcCexKgJhQAAAEyoAJPYCexHcjuoAAAAAmTIELKT2QCGTGGUgDGGQAAAmVAlIVI7gzpVKVSiQyjskMkrCZTxWSCLFp7NzbPxFXyfrDUpbe1/iavk/WDFn9uyAaaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugElRQAAYsgAAAABMqAAAADFkxZAAAAAxllDGWUAAAAAER3FoAwuCO7LDLNrFHJyrFOegm3HEdWeGfq8Mop6JsrixCxTEx0hy8nuIjE4Tsk9ccUdVilzRR0XklLkunHEHLlzRR0XHKz2accW+iernu56YXlXsNfEeMLyxPaHPye5Jtx44XsacE0dU5Gx6vymITk97PZHByHLLY5I/NJp92Tsrh5OjHk9zZpoz4dVm30O6VqVUYY00dW1VbnPRIt+a9mdNaacSkw2ZtsJoa7L1a8wwqhsVUOOuhqVd6cU9IRnVSwmGmhJWY6EgxWCFAAAABJRZQAFgCFSSAUAAABJJQAABYRYBQABJIBQASSFSQJIIUAAAAAAASSAUSUBZQWAIUSQUIAAYyCyQgCyR3RY7gSR3JI7goAAAAAJPYjuT2I7gqT2J7EdwI7qAAAAAAAJPZFnskAQyAAAAACWLIBjDIIBf4Uhl4EQAyhMLDNYqgQiUhubX+Jq+T9Ya0R0bO2R/vFXyT9YIR2QDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Gu/JP0cjj1X4W78k/QV5+e6pKigxZAxZAAAAADFkAAxZAxZMQBkxZAMQAZQQAAAJhcLAJgwykiE2ztOWWdFPTqzopZ8rO1rjwsQ5IpZ0207MacWJZW4nPaXPFEdOjkponw7M5ZLI4Ip9zKKJc9NDKLeejO101+SfKVi3V5NqLfvn+jOLXZnZ1atFE4+7LKKcfwy24tde7KLcQzcmtNOKMz2Zeqp/ib0Wox2WmzTKbNNKm1GOixanyb3qIiemD1M56G2pGjNuYnssUT5N31VWV9Rk2umlyT5QRbnH/k3o0zP7P7juaddNrMdiLXhh2M2ZT1NR3TTQps9ezKbOP4W/TZqK7VWE7GnWVW48aWE0R5N+u3MRLi9XOOisWNOaPJhVROG5Nur8mNVrLW2o66u3OWE25b1drqwqow1jkmmjVRLjqpqiW5XR0y4aodJRq1ROeqYc1cdWFUN7SsJhJhnLGezSSsJWFliNLJBCgkoyAYiygAALBKLAILKAAAAALCAMhiAyEgkFSUWARYJQFlABYJRYAhRJBUlAAAAAAFgCFSUBkkoAsEoALCALKACx3ViAyGIDIYgLPYjugCz2QAAAWOysVjuCpPYnsgLHcnsgAQQyBJ7JCz2SAZAABLEFnussSACGUsQZEMYZwJVjssQQyS3SWscSsdFEtTYcwEhpealubZOdRV8v6w0m3tX4mr5J+sLo07MBVAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAYsgAABiMgBiyAYjIAGLIAAAAAMQvQEIg9lYAZUwyiGdNPRm1hKKWfJ7mVNHbLmi3DFrUjipoZ00TLkpt9XLRbnwYtNOL1eO7KimnybFFurtju5KbHWI5WLV04Io6M4tRMdfNs02evZy02fPoza01YtU9MOSm1Daps9YxLnosJtdNKmy5KLNOIb9Nn3Q5bWnmqcRESzczTr6LEeUs4sf6HaRpa8daY/Jnb0lcx92pz7tdHV02Z90MvU1O3p0NyY6U/2ZRt1zvVmPhCfLGujpos1Z6w5abMduV29G2XKqebkuY+DOnQTnERVHxPki9HUU6eGUWKfJ3NOimI60zMs40cdsf2Lm10dJ6in/1B6mn/ANQ76nQTV0pj+zKrbL8dqJlO58boIsUzHY+z0+Tv6trvRbzyxHulj/h16Y628Y69e0/BPkTo6OLEeTivWKcO8r0lcY5qJifKXBXo66ozTHRe8TTobtinPRwzY69ImXfV6OqYmeWceceDC3oK65iKYnnmJzENTkjPR0fqM/w4cdVnHTlj+r1ei2e5qrtvTaexqdVq65xGn09uq5dny9mmM4Yb3w9rtrq5dy09qxdzMTZpu0V3KJiM+3TTMzT+azMvHXkbluPGIhwXKKcO4u6eObEU9JjMNS5Z9zpMnO46dXVRS4a6Yw7Oqz29nq4blmerrKy66aOjiqpb1dqerXqt4lvszWrVHgxmGxXRnq4qobxyZjgq6SjlmmJ75YTERPi3trbFJZYgmIVrbGFMQAJKgJCgCSiygALAILKAAAsKkKCSiygAsKDEWUBYJIUEhQBJRkAxFlABYUGIsoAAAsIAsoAAAAAAAAAAsdyewIAAAACx3BBZ7IAsd0AZJPZAAAAAAAAgAZSxghlIBLGGUgxhkxhkBLGGUsYBksIsJSsqWTCGUJWFARKC4TCyoNvavxFXX+CfrDUw29rjGpq+SfrC7WOzAVoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AAUGLIGLISAUAGLJiyBiADIAAEwCgAAYBTHVYZRDLO2OOrOKWVEOWihm5JtKKHJRR3ZUUOSm3Mz0YtWJRR5OSmirPVyUWZnrMNm1Z7dHO1prU2szDYtW8Tjq2KbPWPZbFqx1joxtZNuC3Zc9FiPe3LWnx4Ni3Y6x7Lnc3SYNKjTezHSXPTpPc7C1Y6R7Mz+bstFt06irHJXTFPXMT/wCujF5NO043R29FM9olsWdDXPajxen0WxXL1fLYtXLsx0qpsU80zHnjweg2/hXUxbj1tq3pqe8/ar3PXER5U0xM/wBZhyz5nT4XhLO13a6oppomqZ8Idjpdjvz1qsTGPGaoiIfRtLw1t+mxcuXdVqacZ/d002sfCM1S7HTaHarOKrG17fX/AK66artcfH1mYz8IcLzr8b5xpthuX64ooqm7V5WY55/s7nS8FbjNOadDq5ie83Iptx/+dL3E1XcRTbquUR4U2vZp/pT2YV0ae17WruWIrn/trsRP95c7ztTB5KeDr1vP2idssx/73Vc9X9LcT9XJpOFLGcV7robMeE0aK5dn+9cPS067a7VOLV6mavGNNp6rkz8eWJj+7CvctNFXrLe162qqn+KYt2on8qqplj5K18caP+yGji3y18SX+vha2u3H96rkuGjg3aqI/ebtvVz5YsUf/oy7SrX6i7TM2tt0vb/rNR1/pEJZ1O8VYijRbfRT75rnH0yfNWphGpRwjsEe1Oo4jqn3a6xEf+Ey/wBluH4/63iSPfO5WY//AITftXNz5ut7Q0e6nRzP1rckzr5737U/DSUx/wDpSl57/bX8XWxwxsf8Gq36n5tws1f/AMNl/s5tFv8A/ut6jzx6i7/bFLfinX5+9bmPObVMfRnT9ppqn93Yrj55p/RPlpqVoUcNbXdrzY3C5TVHb7VtUY/rRd/Rw3uF6Iqm3Ou2eqYjmnM3bOP/AIqao/u7m1OqmvljRU1Z6xyaqmZj4c0Q5atZTcoqouaTWafkjMzVpc5/OiZyz8uSXjeV1XB+r9V6y3p6b9E/xaW5Re6/CJz/AGdBrdjpsz6vFymuPvU1UzTMflL3Xrdq1FURRqtFNU94nFurP54lnet1esxOorpimImKK45qf7/8pPmY+N83q2eYommbU05mJi5Pbl8XbbLwlZu51G5RfooiJ5LVrHrLseeZ+7T/AHez9Toov13atv0tN2Y6VW6Zpx7+WJ5ZkuVU0UUV2vvVTia8ZrojxmI8Z8o7L81X4tOp1dN61bnY9l+z7XTcpzq7uliaaqIx92a/vV1z4zPSHR7ttujtcL1bLte26rV625qKbsVW7M11VT1iZn+z6JtXD2i112j1V2mu3zff7zV75nz+L0248M3bOnt2ts5bV7niYoiZiaojvM+ER8WsOW2tdfH5Z3jYtXtt71e4aHU6S7PXkv2+WZjzw6XU6TH3qZirxy+u+ljV3tbvc25uVaqjS0eqpvcvSurOZxPk+caqzHNOO/j5vo8fLt48+N5y7p+vk1b1jGZ6u/u2OvZp39P3nD0TJwuDoblru1blvEu5u2e7UuWere3Pq6uuMw4aqMOwu2+WcNe5R3bxqaaVVOGEw2pocVVDuy4MYGdVLHCm2MpV2ZSkxkWMRYgw00guJ8CYnxBjKM8dGOARYIUAAAAAABJVJBAWAQWUBYJIUEhQBJRZQAAAAAFgCCVASCSSIBBZQAAAABYRYBUlQEjuT2JQAAAFjuBHdRJ7AT2I7kd1BJ7HioCT2RZ7IAAAABDJjDIAAAJYwDKWLKWIBAAyljBDIAo8RYSlZUsmNLJKwEBPZEq5MoQIyjs29s/z6vl/WGnDb2z8RV8n6wRY7IBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6ATxUViyAGLIAAAGLIBiyAAAAFwCKYZDKQyiCIZ00yzaiRDkop6LTS5aKWLk0kUeyzt0zPgzoo6tuzRHk5bTTit2un5tmm19Wdu3OW1Ys1THVm1qOCi11jo2rVqJq+65aLVXN07N3SaeZmaqaczEc2PPwcbnp0xx206LMZ7S29LYzXFNPefOHb2dtiqqaaczif6x5w7bbdkuXr/JbppvXOk8tFPN0nxnwj83LLmdpxur0u31TFXSMxEZzH3fe7PQ7TN2qmimK5uTH8FH6eMPUaPYLdi1VN67GZnHq7GMUz7656/lEfm7zS6eixYi3prdqzRy8sxRTMVVfNPeXkz5nbDB57beE71fXVae3pojvVdnET8KIiavo7rQcP7VZuR66KtVFM5imZmi3/8ADEzM/nLsaYiueSZzjtTM4iP+a+utUTNMXYuVU/wUxmr+kdvzcby12mDntVaemzFu1Yo09qO1FumLePywwmIxzYropjrzTOKWEVXKppqiZsxHl7VX9+jn02inVXImi1fvXJ7c1PNXP5dcOWWS9WFGp0k4mmrV6quf4bUZp/rOI/vJXf19WfVafR2Ixin1tU3K/wA4pxEPSbfwRvOsoiu5po09MdvXdJ/pDvtLwRpNNETuuvuXc/wW/Zo/5pta+fTat3eWnVamu5cjvzVTTTn3U0zmfzy39Jw/9rnOn2uq9XHaq1pZpj/4p7vo9rTbFtsRGj0dmK/OKYz/AFllf4hpsREaa3TXOOsT2hWHjtPwPvmqoj1lmzprcdc3q56flDsrHo0rqiK7u52o8+SifrM5bOr4ororm5euW7Me6qIdVreMdLNPLOum77oqmfoklV2lPA2x2MU6jdrnrPdTlzf7O8OWaYiddeuxHjNGHkLvFFMzM2tPernzzFMf3cFXFF6vMTYpojw5ruc/2Xqte8nbOFaI6Wa6/jmEnQ8MTRmNBzY86ngf9ob8zmLWn/OZn9WVG/6zPsxYj4Up0ZfQrG17FHt0aKzGO0TLnnQ7VV97brOPdVh87o4g18dea1OPc5aeJ9wj71Fifzlf5I+h2dt4from3XoKImqe8VZlyxwlsOooxa1WosVZ7RczEPAabirWc8RVpLdcR16VO2s8WW4iJv2btvPWeXrEMXPL9xqSu53P0d2L9NH2fXUaiJqxMaijPwiIl4LcNs0mh1+psWbsT6rpm3X7M3PHHlEePv6O+4j4omqzGj2+9X6y5THra4jE0Uz4RH80+fk8vTVM+1Ec2O0eX/z/AEZtbkKZnlirlpmczTFFMdap8IjymXDqLlVNiiNbp5tX4nFeIiqz+VUdvhL0nCu01bnqJrooqvVXc2dPTV41fxXJ+Hb+r3+v4L2udrixoqIt6miMc9c5puT4xVHk3j9Lt8c01/U6S/67Q36tNXjpVamY5v6Q7WniLfr+nq0ms1VNdqunlruRbii7MeXNHh+UuXfOGtXt1+fs1mdPenrVp5qzau++ifCfd2dDRdpqmqK4qoqpqxVRVHtUz7/L4rLpbZY19w22zcszFqiqqnt6uYjP5fzfV47c9qp9ZPJYxNPSY5YjH9XupuUTTy/0y1tXZt6iiab2avKe1Uf8/hLphyWOOWD5VrtBNFVUYpny6uqv6fETExOflfR922iKIzTTNVuZ7TGI/wDm83rdBjmjlns9nHzbcM8HitRYiM4hoXbdPXEPUajTxnGJ6uq1OmiKpjpPwevHN58sHn79uc5al2nrOXcaqzy5mGhctdHfHJzsdfNLiqo92W5XbnwcddEtzJhpzR7sMZp6NmaGFVOG+zLgqpYTS2OXMMZoa7DgiDDl5TljxOxpwzCTT4ufliOyVU5hdtxwYzC4ZzScoza4quiM6o6pMYahGICtAAAABjIkguMJBBAKAAAAAAACSjIBIUAAAAAAAElQEhUkgFAAAAEjuoAAAmFACO6z2BAgq7wAAAAAAAAAB4AAAAn5AoAAAASxgGQADKhiyoKVlHdSMGGHOgGAgBkUbe1fiavkn6w1G3tcY1NXyT9YWDswGlAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugE8VFBiyBiMgAYgMgAAACIyLR2AwuGbFlkiGUQtEM4jqM7Sily00LTT2c8W/ahytWMaKHPboz4OS3RGXPbo69KYw5tuO3b9zZtW8eDOzbnwjq3LNq5PL7PeWLk1pw2rWZbmnsTMdI6NijRTFcTyTHn1y7fb9uruziuI79p6RLlnyN4cdrr9Noa5qjNE4nydztW3Xbutpt0W67tX8NNMdfz8oej2vh+mKaatR6y1TM/u6Y61zPw/hj3z/R6XR6axpLEUaaiKLc94iOtXxnvV+bx8nO9PFxuu27arWnsRc1dFNVyKsRbt1ez+dXj8Ix+bt9NbtxE8lq1RTT1iLdMUUwwnrPWIqpj+y24jmxMROJ9n3/B48uXb2fG2MTNUVc0z7pnuxpquTVNFFPPMT1iIzj/AJOe3p713rdrroinvTR0qn4z/D+XV3GybFrtyvU2tDpJqx3qp9minzzPixcmeunSRpb1cRF25NNP8lE/WXbbDsOr116adBp6qsd/CiPjL3+38GaHbqKdTuV2L9+3HNy9PVzHlht6rfdHpKPV6K1bp5o7R0iJYnq7dZtHAFqzRGo3m9mc9LNqrEfnVLu7VWxbFZqp2/T2qbkx1x1zPxeS3ni+mieXUauLtcR/l257f0eQ3Xi3U3JmizRRapmMc0+1U748NYub6Vr+LLtEVTXct26ceeIeS3DjHRxnmvV36/Kjr/d881e413ap+0X67mO01z0/o1Lu4exNNNcVRHlGHXHh0x2ez1PF+puU4sU02486usur1m/Xb9GLmpuzPjFPTLydzWU1Vd5icebgq10RM4nMtziZt09BXq9PNXNTRVVVHfnqzDC7reaOlu3T8rzn22ies82fdLGrWT/DMunxp3d9Oq6daqsx26lGvuU/xxPxdD9rmZ61Sv2mnxqln4me70EbhXj+HPnhna1dVczz14+DztOpjP3nPa1ETPSuT4yZvQ0XvGLlX9W1Y1GO8835vPWrlVUxHP2dno5qqlzuOnSZO5096qqvmpjEz06Oyivl0/NjM5xET5+bptH0q5vLu7GbvTMTmIefkrthNrTcqiueeYqn3x1z5t7abFWu1kWIq5cU8125jpTbjvV8fCPe6u5ci3mur2oxmff7n0LgLaafs0TqKJjmmL1/p97/ALO3+rzx0s09Jw1V/hNqNZTZpoza5bVvxt0fw/n4y63U8Uzo9ZFqi5NU1ZmZq6xHvlOJ9yo09muaqo55ntE9JnPb83g7l/muV3ZrnmqqzM+fudMZZGPH1W3rtv3bS0xreSaKo79+vu8nmOLeC5vUxq9DXzdMU3KZnmx5VRH3o9/eHnNLuVVirNiuaJx92YzRP5PTbHxBcrrt+tqpprjtifZn3YLakfNbsV2rtdq5zRXRViYmOuWVNNUzNMzMT45l9E9I2zW9Xo7fEGk09NuqjFOpop7d+lX5PCVUcs58/Htlz+TTUm3BNqmaZpmiKomMTTPWKnQ7toKbdM+qpiq1M4pmekxP8svSYx08/Nw3rdu5TNNea6Z6VxMd4duPkTLB8z3PRRFVXLHxdHqbOJmOV9F3ra67eKvZrorjNqqf4vj73kNfpus1TTOe2Je/iz283Jg8pq7OaJ6OqvW+Xwek1lqevTDptVZ6y92NeTLF1dy10a1dup2ddvEYa1dEZ6ukcq0KqKoYVUVS3LlHTo4+TLcqVp1UTnqk223VbnKerlraNSLfROSW5FvxY8k+Rtpq8k47MZp8ujbqonywx9XOOq7GnVBjo2qrceLjm35L2ZrWrpmezjmmcdW3NGHFXS1MkcHLPgkxPi5sdGMxhvZtxxBMM5gwbNsMLMMopXlNm3HMJhyTBg2u3Hg5cs8LhNm3Hy4WIlngNm2OJXlmYjLKI6s4jobTbh5J8Dlqc2PImJwmzbg5Z8TDk5YSYXZtjFM+Byz4s6I6ssLs3XFyLyOXCYNm64+XCY8nLKYNm3DMVGKnJgwba248T4mHJjK8uDabcUwuOjkwYTZtxYMOWacpFODZtx4MT4OXBg2bcWJ8TE+DlwYNm3FifEmHLgwbNuOmFwzwYXZthyryMmUJam3HyzBiXJgwmzbiiJyTTMy5op6lVHU2scHJJy+5zTSmDZbWHL0YzDnmOjCuldpv+3HEGGcQsU9V2bceDDl5fcRQmzbjiCYcs0JMdOxKbccQuFF+zbGYTDOOvgkx1RdsJgVJ7rGtksYZCgAAABhlSRKiVYlcsYZDFWBFhmoJhRF2mG3tf4mr5P1hqtva/wARV8s/WFix2QDSgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQCeKigADFkxBkxGQAAJhQAWlGdHYKyWISIctDDkUx1ctNBbhzW4Zta0UUOe3RLO1azPvbVuzPi5WrI4rVuJ8G1ZsxzdOzO1ZnwhvafT561dIcrW5E0djNVOIdpptLXNVERHer+i7dpoqqjrjwj3/ABen2raK80V6iZtURPNE+M/CPJ5s+R6cONq7Zt1d2eSmIrqiMzGPu+/Pg9ZoNJY0luin1cXLsdPW46R8sfqxtURatxbot0W7ceEfxe+fOWxN7NVOZnp0h4c+Xb04cbYiKcU1ctUTV1nr1ck36ZppmmZiPHq4Ymcd8RHeU09mq/XNU0TTamOWMfer/wCUOOWW3oxxkbMXZuXPV2reYn+KetNP9O8/B6DYNri7eppotXb1+vxpp5q6v+UOXg7hjW73eijSUer09OObUVRimiP1n4Pru17ds3CO300Waqa78xM1Xa49q5Pl7octVcuTX08xt/A82Ip1e7Xoptd/s/n5Zl39/cdNoNJas6C1Rbop700dnQcTcU24tVV3bsU2p7RHWce6PF823jirV6muqmmubdrPSmmeuPfLrjxOVz29bxLxTEX7lub1dy9Hai3HSPPLw+679qNXVXFu9Ni1PT1VM4z+fd1mr19Fyj2q5ie/NEup1OqoriZqqmZ85d8OHTnc25f1U0ZxPWeuI6NDUa6uekTES0b+rjmxEtO9qJnPV6cONy23Lurq/ilq3dVnpzdGldvZ8XBXeiXXox2blWojwcVV+qfFpVXPf8HHNczPdvqlydhF7zqJveVTQytM9V0zt2NN6qe8sqbuZaES5rM9WdDepq6OaxV7bTiZiWzZ7xLlkuLs9HPNHN5S7fR1TFVMc3ecOo0UVRMUx2nu7vR0xHX8o/5/B5869GDs7c8s8vh5tjPLH3uktCmuIiImZxHdnZvzVXFFOarlXs00+czPT+7x8j04O22jR/btxo9ZFVel09VNd2nxu1T0ptx9fg+v0zG2bdyXZj1lUesvYjpzT5e6Ozz/AKP9ltWI+1XaPZ0kTNX+vUTHX/4Y6fm4+M92m3bqopnrXM2/+658fH2u2ssnnN83Gdbqrtdc5tUx7Hxy6S7qqJnOZznrhw6vUctE26Z6R0y6uvUdZiJmMPXjxvPcndRrY5ukt6xq4quUe3iY65h5e3qMznLd02omK4qmWM+Mxr6twVvmm1k3dg3Ormt6i3Pq6p/i86fi8Zvmknb9z1GimeaLVc001eceDX227EV0XaJxXbqiqmqO8fBtcT6unW6+NVTnN23E1fHxeLPisu3fGusq6eOU5mMykT7iXTpptbdpI3O5XtdcR+8pmuzVj7tcdXh+I9uuaXV3LOot8t6icV0x5vecPar7LvuivR92LsRV8J6MPS/o6P8AGLOpt049bRNNePd2ez8fP1x5I+LbjaiKp9jEum1FqevR6nd7UzXMR2y6LVUYmYfUwyeLN0N+iYlqXKZzLub1mMTOGnXajrMO0rhY6yqiWHJPm37lqZYRp5b2xpp+rjPWJn4MvVRMdIn825b01c1ZmMxDe0+31XKqYinMT2+LNzkWYWuoo09Uz2ZVaWcfde82LhHWbnZ59P6ii3HSbl2vlpmev3fPs5t04H3TRWpvTRY1FERmZ092K5iMd8d2Pmlrp8L5xXp5iezhrs47w9Tqtui3GaszHhMOs1GlxM5icQ6Y57c8sNOkqt+5hVQ7G7bxE9GtVb8sum2GjcocU0N6q3GeriqoxPRqVLGpNqfBj6vHdtzR5OOaYierW2Wvy48Ex1bE057JyT5LtHDMJy+5sepqPVzHSV7Hrgin3E09HNyT5HLP8p2PWvy9DlbMUTPeF9VjwTuarV5SKMy2vVe49XjqTM9a8UYZxT0cvKziimY65guRqteacJhs+ro85PV0ecptZP7a2IOVs+rzPQm117GzV/TXinKxRlz02p8IZermPBNrqtWaMHJDa5J/lSbefBZUsa00QnJHg2JteaerjwOzMla3KcrnijHgTR7mttTccHKcrnij3Lye7BvRq1rcjKKHPNGU9XJ2TV/bhmj8k5ceLnm3OEi1UdjTgmCIy55tecpFrqdkcXKcuHN6v3Hq/cdj1wY9yxS54t9eyxb6ndZHBFHnCzTHk2ItxnrDKLdPlLNy23pqRR7l9W2Zt9e0ysWs+Z2TTX9XOOhFE+MNvkhOSk7L9NeKKfLqk258IbPLHgcptY1JoqTkltzb6nqjsaas0SkUNz1UJNqIjonbaWNOqiISIp8m3NpJtRhqZT9saa3KU0+9z+r+Kxb90lyn6akcE0e9JtzhsTbjwTkq8yZFjX5KfGGNVEZ6NibdUdWM0z4w1Mk04OXCTHVy1Qwnuu9owqhx1R1c0wxqjsSrK4sGGcwkttbY4FKhWOFkAWO0MqWGWUBWaJHYSsLlY7pn3LCUZyxIEZG3tf4mr5P1hqNva4/3ir5P1gix2QDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cji1f4W78lX0FdCMWQrFkMQZAADEBkABCpDKBKmGcQjOiM9WWatEOaiEpjrDmt0MWjKihsWqFotexDasWs4cW9LYt9m9YsTVLGxZjo7LTWesOed03hilnT1Rb+639LpK7lMU+1E5/q29Jpq45Zpo5svQaDT29LNN6qI9ZNP3Ko6R75eTk5Xqw42ttW3W7Uesu0xcqz7NuY7e+r/k7yiv2ozEVeFUz3/JpWYpzM0zVM1TmZnxbFufzePPLb044tuLlPLiZnv4uWmaKaKrlyrkt0xma5+ke9o1XKbFHrrk4pnpHTMzPlEebsdn0N/UX7V7UURimrFqx35M+PvqcLXRz7bpruqqjVam3NNM/5VjtiPCap8/c+mcDej6/u9Nvc90rr02hmY5aZjFd3wxHlHvd16O+BLNu1Rum/wBuJpiOe3Yq/tNX/J3fF3FVqiJsaOuKKKJxNdMYiYjyhcMdudzcm87zoeH9LTtm1aai3iMU4iOWn/zfNuJ+KZqvTT631monriJzFM+TqOJeIJ1VU06e/VTETPPcz1mPKHjr+pt5nE8sR2xPd6MOPxyuTtd03CbsTcm7NXf/ANY8nQanUUTE9Z5onpjs1dVqqpzVFfbo6y9qq8zGXpw42Lm3dRrImJmYzM93X3tXE5jHRq3dRV1iIjPvlq1Xqp+9MOkwkc+7Yu6iJq8nBdvRj7ziqqmYnDgriZ8XSRNuSb0ZYzcplxco2jKqWOZyqx2BlEs6e8MaIctNLNZZ0Oe046KezntUsW6akckRmqPNu6a3NVUZa9q3Gcu10duMx0cM8nXCNzbLFUxEzGO+JdtFMRbi5FMYxy0/BxbfRi3jGZq8f9LarpiafV5xEdnjzzenDFhPNNNVOY7dHccG6W5c3D7TRp/XV0Yt6ePCb1XSn+nWZ/J1NdFVVFNFGZmJx0857PrPoy2iixXTrK4pixpLcxbrn+K/V96f+7HR58ruvRjj49JrvVbPsdG32aommzRPPc8blX8Vf5zl8n33cJv3arnnmKc+Xm9vx7udNqPslNWaq8xPuh8w3O715Yq5qXq48dRwzrqtXemasRVOIak3cs71UTX082vVExMu7g5rdzFWMtzT3fa7uropqmW1p4nMR73PNrB6TR36qOtP5tjUXormnE9oddo6Zpqpnw7Nq5P72qKe0dHi5Xownq0zmJZxlhHllzU09MvNa76ZaC1Xd3DTxTM83rIxEeLvvSZo6vsVmqZzNM9ctbhzRzOpo1tUVTy1xRbiPGqf0eh9K1mmjaOfHLXNMZjPSHp4MtuHJHwnd9Py1ZmMRPZ5zVW85ez3mzTFFPL0mYy8xes95fT468Wbo71vENWq27mu1E5y1LtqPB3jlY6uq1E94WmzEziI6t6LOfNnbsRNTVrMjh0mjrqnpGevd6fh7ardzV25v8/q8ZqimOs48Pza+0aWuqvlox36va7HtOo1Vd6bFuuatPb9ZijvMeM+/wCDzc2Wo9HHh6VU01xEUW6Y5YiIpp6U0x5RHkzieWrnnpVjFE094kirnp5qKOsd4xiY/JxXapot1VVYxHvx/wCvF4pyevV1dHxVoLN2Z1lNqKZuTMTTEdJr8/zjq8VuGm5IxPXyfbtm2CjVcD6rWaqmYu6i7623TV/DTEYjp4dIy+V7/Zim9MROevV7uLN5+bD9vG6m1ERPRq124ins7q/aiapjENOu1MZjleyZPFY6m5REeDimiJns7G9bmJ7OGqjzhvaaaNdGHHVabldrM5Y+qybZ004tzHhlYpnPaYbnqZgi3MeDWzTV5JnzPV57t2KJ8j1c+SXIafqo8k5IjwbtVufJjNuZjsnYafJlJo97b9XPhB6uryNjU5cT4yvLEx17NmbdXkeqqnwWUavJR4MuRz+pX1Mlo1+Q5G1FrHc9X5QmxrRER4MuTPg2Ytz/ACr6qrwg2aa0UY7QcktqmzV4wzi1jwNmmnFE/FJjHg3Zte7CTanyNjQmM+GGM0N6q1Pkx9X7jY0eROTq2/U+Keqqz0hqZDW5cMqIjyls0Wqs+1Dki15QlyGnNuPJfVxjs3ItT5LNqfJOw0eWI/hSY6dsN/1Mz3g9RHkdjTrZtx36pydfF2FVnyhh6mM9V7Jpp024yy9Xhtep/ljqsWqonrC9k161otkW+rc5J7xC02pnwNtNWm2s2276n3E2DayNHkOT3N71HmnqYYuS6aU0dOyRbnyb0WV9QTLadWj6uf5WUUTj7rd9R0ZRYldnVock+RNE+Ut+bMp6qoOrR5fcnL7m/wCpnyJszjs1tdNDkz0iJYzbnPZ2HqZ8j1M+SWpY67kmJYzTLfqsz1wwmz5ptNNPlieiTahuepgiysyGlNHRxzQ7D1XVhXZa2ljrqqPJxVUznq7Cu04areJWZJppTT3YVRLaqoxlxVUumyzTgmOqTHVyVQxa2jCY6sZZT3YysVBZhFjQsItJSsokBGD3sk8CAZ0ksYZT4IyYbe2f59Xy/rDVbW2f59Xy/rCxY7EBpoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAcWr/C3fkq+jlceq/C3fkn6CvPDIFGLJiAyAAAGLIAIZsaVhlms6Y6M6ISIctEdYZyIzt0Nu1R7UOK1T2btm3mqJcbWmdujMeLct0ctPRLNNPbDds2qa56w52tzA09FVVUey73Q6eqIiqac9GrorGaqYiHpdBp7dFui5P3p+7TMf3efkzenDBubfYosUUzV0rmM0x3iHJcmnmz188+9InrM+MsapqmMf0eDPN6sYyiZnw6sqq+WnmqqinHT4z/zYR7NM1VdojMz5e9t7Xo6rlyNXqLPWn/Kt1eHvn3y53LxuRs7Ztt6q5Tfv5m9923TTOYtRP8A+lL7x6MuBKNFYs7vvlETfqpzYsVTiKY/mqdR6JOEIq9Vvu6UZpnratVxiI8pqj6O/wCPOKq7tNzTaSfV028xdmqeWavz8mcZ2Zyrn404os29Je01u9HLMT6y52jGXx3iDfrmoqropuVxZ/hmO9Xx8ocfEu616qKZmZi1jpEz1q+Lyms1U5nrL1YYOOTk1uqqnMdIjyh1Oov+HNH9XHqr+fHwdderzM9XqxwcbWxfv+zPWJdddvzmYcV65PhPRwXLkxGHSMVyzc6d2FVUOGapmGNXfu2zGxz+y45q6LTiaWdNEVdP0Zt004/anGGU0zhzUaeuaomOsZw56tJVTXNMZqjHdnvDW2ly9Fppnylu06SqesRMeeWdOlrxmIzB8ka6Na3T26OaKY8I6uejTVeMw56NPPScRhLmdGrFM4bNq3MzHdz026O3RuWbMRjMMZVvHFxWLPtx0d7tuniq5T0jHj8HDpdPTVcifB3FmxRazMTGZ7/B5eTJ2xjKmjGaqYimKYxiXDVPjmXNXV093g4b1UxamqI69IiPfM4ePLJ6MHbcK6a5f3C3coom5Xz8lmnwm5PSJ+ER1fZ7tuxs+1WtFRVEU2qZ56v5p71T+c9XjvRvttOm1NWorp56dNnHT/rKv+UdG5xnuk12501NeefMTP8ARy3uumV8eR4k3C5rddcv1Timc00+6mP+cvMau5FU9J7u33brXyxnEeLo7v3p6y9vG8mf20rs4zlw8+cZhsXac9XFTT7WHW3+3LRaqzVOOzd08RVieseUOKzazV0jGXZaDRVVzzVfurcda7lU9I/83n5M3XjxbdrFvTeunrMTiiPOrwj4FqZimJqnrJeqpqqpi3GLdEexTP8AefzSimqesR8IeTLN68MNVy2+ucuSiLtV63YsxNy7cq5aKI8ZYTct2rNV29VTRRT96XuvR1w5qaojdtRZ5dVqY5dFbrj2qKZ73Jjw6dnDO11uWnccCbL6jFu9iujTRm/V4esnwh03pQvW67cWeeZrrq5pjyiPB73cIsbRtcaGzVmaY5rlc966vGXybiG/9u11y9M5irpTDr+PMsfa4ZevD7lamqO+XQ6qxRE9Yev12mma+WKYnHtT+TptXpOenpERVE5fR4+SPNnNvMXrMTM4pa1zTzHXGXpZ0eYieSI6zmfCGlXpc9Zjl69peqZuHXTpaNNEznlxDms6emJnp4OzjRZjGC3paqZ+74tXNJPTa6fV104iOs9X1r0QaTTazctdav3KqYuWKYorpnHLMTPV810OnimuOaMZnEf+vyeq4bv1aLW03rdyqmJiOaI8fF5+W7ld+L7e64h4X03ra7+s0UXaa56ai3M0zX8cdpdTouE9u1F+i1p9ti7XMxNM11zMU4nvOekvUbdxRpa9NFjUXoriYxMVdpNXxFoabHq9NVTFMR92il83rdvZqaavFWm27hzYOa//ALxeqiaapz0qmY6Yjyh+eN7ibt2a5piM/wBn0rjvdL+436Iqqq9Tbzin3vCbnYpropqmPafQ4fI8nL/TyV6xPrJzDguafp913t7T08+OrhuaWJ7U1R+T2TkeS4PO3rHualyxOekPR3NH06RVn4Na5pPdMfk6TOM3B0M2KmE2ao8Hd1aXH/ycc6bPj1a7s9HUepqz2yypse12dtTpczjPVyxoa6Ko9mfifJDo6n1HuPUe53caGqYzMMKtLNPTMTPuZ+SHR01Vn3TLH1M+Tu/sc9JrzEe6GNehmntOafNZyQ6OlizM9z7Pl2tWkmPu1RLCLNUTjEFzOjrZ0/myjTR4Q7aNNM49nMy2tPoZ5v8AKqmUvJqNTDboaNFXVmeWn+pOjmKP4vyh7La9kp1l72Ypt2YjNy7jOI8ojzb+58PaOix/udzWetpp54puRTy3KPHEx2mPKfNznPtr4tPnVzTzGOk/0SjTznrD0uo0Pxn8mv8AY8eEy6fIxcPXUUafr2Zxp5iezuKNHE94mHJGjjPuO8To6ejTc0dI/qy+xzyu+sbfM082PZ+Dknb4qnFPT4Jc43jxvMzpcMKtPMR0elq26rM0zTP9HDd2+aczNM9e3TuvyRq8bzVdirDD7PVM9nobmh5cZmMy4atJ5Ss5IxeN0f2WrPWCbFXbDufslcz4MqdFXNWIxJ3lS4OptaacZctOm84/s7q1oap6zT28GU6SmIxMTB3OrpadN7pllOmmJ+67enT0x2yv2eJ7zJ3Tq6SrTz/KxmxPk72dHFU9KpSrQTHNnPsyd4s43QTZ86Zyx+z+OHeXNFPLzTRVH5OCrSzE9zuvxup+zzErFiZ8Ha/ZZxnKxpsecLMk6Osp08/ys6bH+l21Olice1P9HJGjzOIqnHwXtCY/p1FGnmZ+6z+yz/K7ijRYjM1S5KNFNUxGPD+jNzkb+N0U6X3wkaX3u8+xTNUxFuZjzYVaWaY6U+1ntMJ8kOmnTTpe6fZndXNJconNVPsz4+9jTp6pnpTiPeszxq9PHT/ZmVOmz4O3p0vXrLlo0PNOIiZO8SYOnjSwv2WM9ne07d7MVZxkjQTPejHnMpc4vx7dDVpfKGE6fq9LG11THauYnxppy452yrOeSvPaY5ZS8uK/FXnp0yTp+nZ3tWijlzGZnOMTDhq00Z9/kfJEvFXRV6fE5xLjnTz4Q7qvTz409HF9nnP3Zw13jncHU+onxg9R7ncRpZn+GXJTo5x2iF7z9J0dFOlmYmeVhVpqvJ6KjRz4s6tqu1081EZhj5Is43kL1iuM5hp3bcxEvXanaLlNE11Zx5w6i9osVVR3n3w6Y8kS4WOgronDDkjxdre0sRPLlq3dNNucT1w795fpzuN/bQrpjPeHFXDZuU4z0hwVd25WK4ZY1eLkq6S458W9owlFnujbUFhFpSlGRIiUWCDAjKOwQsIyR2bW1/iKvk/WGs2Nr/E1fJ+sEWOzAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAAGIyATEqQC0uSIYU93PRCWs1lbhz0U9WFulsUW8uOVJHLao6Q3rFvrDWsU1c0RPZv2afahxrTY09rNeHbaPSzMw0tNaq55mHo9os+stxT2r8JceTLT0ccc216LN2ma8xREZnDt5nnjmmmYnwx4JZtzbo5afD70x/M5eseEvBy5+vbhHHyz5SyiJjrV0kmuc58Ilz6Sxe1+onT2qczHWqryp/wCbzZV1kc212PtMzXcp/cU1Yp6ffqjx+EPqvos4Lne9V/iWvt/7nZqxFHaLtff+nm83wfwzrN53azoLMclqmIm5V/DRRHefi+xbxu2n4c2u1tu3UU0xTTFNqjxpjxqn3yxJ2plWtxtvc7fTXptHXTHLGJiO0dOz4vve73tVVc5q825ntn70+fwdnxTvleqqqsesnrVm5V41e54bc9ViuYmesR4dsPbx4f04Wsdbqqq6+aqfa8Z84dRqdR3nMsdTqOaeky0NTdxnq9WOLjlkt69M49ppV3KpmeqV3Ylw11w6ue2NyqcOLmrnwWuvMrSumLfSJnGfJaYirDj6889J7t3SWIuzTEUTzT1px3mUt01IysWKpnEUz8Hc6DbqrkRTFEzd8KIjMy7PadptRXz7lRXRM4mbVuM1R76p/h+r09iuuxR6nQ10aS3Pauxbibv5zV1/o4cnK3I6TbuFNzv26uXSTTTPeq7MURH5y7CngrV0W8TuO1U+fNqqejlv6L1szc1dFWp5us136qqs/wBZ6FjQ7Z7M0ertTHhVXmPq8uXI3hh/JwXOEb1FU00bltd2Z/k1VLgr4W3O1bmYs03afO1XFf0d39itRR0tWJjzptxLjq0tmjFdNFMVedETTP8AZznNXouDy9zbrlvNNdFVNUd6Zj9HFRp7kT93pM4h7GNRdqxRcmL9MdIpuxzTHwq7wxr0mmvxTVYqjT3c9KLnWifdz9o/PDc5nO4vKxaxVEVUx/Ru27ETEd3a3tBct3OW7RVTXnPWnpP5+XvX1MUxjlxKXm2YxxaW1RnlmJxjMy2cxEYxj3S4655bUUxHWrrV8seDLOf+bjlltuEzFU+5ubTo6dXXXM0zVFrGI86p7NOcYzHeHuvRbtM3950ti7RE0UTOqvVT4RT92J/Nyy+nXGvbaTb/APBuG9PamcX5jN3Peap6z/R4Hd9ROo1VdyPuU+xT7/e91xzuNyLfq4iIrziIjznpLwGvo5KvV/w09Iw54NZV0erqrmqrMzMRDrLlOZzh22qtzM4xPVwzoK65j70R5w9Uz089jqZinM83THZlTYmesUT18cO3p2u5RE3NRTRRZp6zVd9mj+srXrtJbmKdHYm9cx7NdcYtx8sT1qO3jUjh02loptRXqZqooiO9UdavKKY8ZW/qJrpiiKIpt0/dtzPj5z73FVcuXq5uXblVy5jEzV0mPdEeDX1N6i1RPraqaafOrv8AlHi82Vd8Zpzc01TmYnPj75c1V+i3Vbt1U13r9yeW3Yo+9XP6fFjte17xuOJsUTt+kx11N+M1T8tH/N9S4D4J0+js+us6Wqqu7Ti7rNX1uVfL5R8HPKam2+7oeD+FLv261ruILEXtVFUfZtBb60W6vOr+aX121y7VpKr12aa9Vc6VVeFMeXuiGlRGj2aibeniJvzGKrlXef8AlDouId4r1FqdLZrxTV/m3I7zHlDExyyu6xlk0t+3SvUzcmjFUZnM+E/B43drVHr5m1TPLOOXHn5Q7TU6imxarq1FdNFFuM1e17NMPIb3u862Zt6PnsaeaZiu7FXLXX+XhD144z9udyc+rv6CxM06vU4ueNmzEVXI90+EOo1d7TVauPVaOqmJ7U3Ku/8ARraazb09mqvpXbp680x4eMvQbNwrrd6ptX9VTqdLprsx6mxZp/3i/wD/AMlPvb3ji5W2unnWaWi1PPorMdcTTFc5lwWrejvzMUc1q5M/duRmmr4S+oT6LtNTst6dVpNPoPVWqqrcWqpquRMRn2qvGXyHb6p1WgprmM11Rmme3Nh0wz2Xj/bmv6KYu1UzNfNT3iIcNGlnmz1w9dsG33d54Yr3Cmuab2jr9Vd866e8fq62nSzRbxjr2zLr30z0dfp9NNNMzMzGJzHT+0f1dxbjTaaInU3ZuVRGJpsdcT8fNxzTVa01VWIm5GKbcf6p7f07tO5yTVTapn2KYjGf7/3cc+S1vGadrp9ftdu7E41kVdsVUxVEO4jWWrens6j1MVae9mKKojHWHj/V13b1qzap57t27TaojzmZ/wDm+qcX7Tp9HsOl09miKYs0xER78dZcZfW7XzTiXkr1FVVuZmO7zuptVTGOWJw9brLE1RViOZ1V3RxGKqqJmc5xEvRM3HKui0e1ajXX/Vae1mvGes4iPjLuJ4X1FNERc1uz0TjtOpjLD1UV81PLM2qZ9nP8c+MyU6Gz6v1tFm1FM9apqjrnyb+Twxjg1PC/q7VVyrcdrx48uo6um3PaKtLMxzWLkTETFVurMS97wBtFrVbjXq67Vu5RYjFGI6c36tDiPQW9Pvmqs27eLcVc1Efy57tY8jWeD57Xo6p/hjv5OGrb7lU5ijq9Zd0sU1zmmcr9hqqzyU1TFUxiI7uvyuPR57aNg1Ou1cWbNiKq8ZnNWIpjzmZ7Q9FRwdXM0zTrdspqme06uOnu7uebNum1VZmimujP7yfC5V//ACwxs6LS8ubOkoxE4piYx/6hzz5ITBx1cIXreZjWbbV1641UNGjh+Lmoqt0TppqicT++iIn4S9z6OuGbW78Q41mjs3NJpaJqv25ieWqqelNOfj1/J3XpT4b0Vmxt13btBYt2dPbqt3aLduIznEx75x17uE/Ikum/jfM54R3CJ5qPs2M9I+0UT+rV13Cm6W7Fy/OnpuUURzVeruU1TMfCHbVaexERFWmtTPTHswWaPV1xXap9VXTOaaqemPjHj8HbHljFweKu7fXHWKJ6eOOmP/X0a9eljPSMS9nq9HHL62KIopqqn2c9InPWPynOPi6i5p/bn91PfxdseTbHV1FixirHi7zY9uv7jrrG2aKzVc1uqq5LUTV3nxcEaenkqmqmaO0RMPZ+jOxbtcR2tVXbmm5bp5bfuz3n44M74uM1XoOIOHdBtFM16KzNE2ZosX6J/nppxMx7p7vNXYiLmaZ9qmf7x2fZOMtro1Gkm9bzyanT9PmiOj43yU0V+1TmqauuZ7T2eOZarvrceb3HRxVqpuU0+xcjmifOfH+7Rq0U5xyvVXLXrbNFE00zFFUz/VxRoLleZtY+GHacjllj+3m6dJEd46Q27Oi6RE0REVecPR7bsly5cirkqmZ6TRMd/hHjLc3Cjbdh5bFy1Trtwp7WZqzbsZ/7SfGf9Mfm1MtubpNDtGsrs1XKbdFGnpjrduTFNEfnP6MqNNtNERFzVXL1U+FmzOJn3TPdx67VarXarn1d/wBZNMYpir7vwimOkRDc27R6vVXrdjTU3NRqKutu3atxVVEec+UfFcspHXjm3De0e1UxNVdOvpj3xHfyY6nY9NNn1k6i/pYnHLVfo6TE++Oz6LoPRxr9Tp7Go3S5XZ5J5ppoj739fq63jPY9PttizesUVUUzXNNVNVc1dXHv67ddPl+47Xc09UUzbiumY9muJzFUecS0KtJVExGMRPuetpt11U/Z5pmbFU5j/TV7vc0rmjmauszmMRyx5us5JIxY859jqjLd0m2XLk00xTVVXcnFFFNOaqp90PXcNcKaver1VFq3EWrefWaiuPZo93vl2O8xt2x1XNu2ub/2uKf3+oudK4jH3Kcfd8/M+VmYPMUcLblp4irURb00T/2t2mKo/Jw6rapouck3LddMx7NdE5pn4NvTXKaqPWTE015xPN1zny/V2em0dN21Vy2+k1xOY84iY/Vn5NVMsNV5qdqqn7sdO2YhxV7VqJq9i3mIe80mzX4iuuzamvEe3iOlLl1uh0eyaW3f3bV06eJ+7bxzXbkT/LR+s9F+Uxx28HZ2e9X09X1iMy3KeG7/ACU3NVNOlt1+N6uKZmfDET1d7c3+u9ROm2zR2tq00zmbk4uamqfOa56U/CGlFrTxVdrru1Xr096rlU1TP5z3X5Xb4dTbrbnDfLGaNx092r+Wa5j++HWbjstzS1x661NPNnlq7xV8Jeiorx/FFM++GF2JuU+ppqpm3XPtRHaJ/RmcjFxeUu6SrpNNLCNLc/ll6ejRdZiYnPjGOzkjb+ucT/Rv5dRnpt5qnSXJiPZbFnR3Jn/LmfhD01O2TXEVzHJTEd5js7rZuF72qmblMTTTFOapuTyU0R/NMz0iE+ba9NPIabba6o9q1jPaZju7S3w5XyW7l+LWjt19Iqv3Ip5vhHeXf39z23b4q0+z27OorpjNWuv0zMRV5WqJ+sulqxrNXOpvV13NRMYm5dqmqr458GO6zFrTsmmt3eWZ1NyM9KqKMRP9Zcd7QbTaq9VdjWU38/dmaJ6f1ex4X2Ded3sRqtHTXGiicTqb8TMV1fy26fH5uzsrHAv2X1lGvxXdu5mu5GObE+/wYy5ejpMZ+3znVbPp69NEabUc85/y71M01fl4Osr2+q3PJXRyT5VT1eo1+jp0e7azb7cXJq09zEVzPhiJa9VqL9+KK8xVj81+W32JcY6K1ttdf3KMw7DR7RVFOblOIny7y9Zse3zf1NNjS24rqnpOYe4+w7Nwpt0avc6rf2j73NjM5x0poifGfPwLzViR4DbuDKrulnWblVRtmjpjrdv9JmPdHjPuZanT8LaC1TO2bbc3KZxT9r1lXLbifdbj9Za3EfEWs4g1c11VVRYpr5rVrPSn/nPvZ8PaTXbrqv8AD9DRTVcqp56pn7lFOe8ufbK/tuY+uC7Xfiqu762m3bjp+6txRTH5OC5rNRRRmnXUxTM+VGfo+n7bwTZtWuW/dp1N+elVd7rTHwp7R+fVjuHD1Wlqze0Onqt9ouUWoxP9mblY7yTT5bqLWj18RGptUUXZ7X7McuZ/1U+MfB5/cdpuaWuqmq11jrmJ6T730fiTY7FufXbdRyXojM0R92qHlr1NGp001Vc1NVM45Z/hlrj5a55Y7eRnSVVVY5VjQ1/yz/R6C1oqp69fybWl2uu5dxE1x8fF6vkjzZYevL/Y68zGMkaCZ+/FVPwe2p2K5z0RbpmqasxjGer2PDno4/xCxOr325a2zb7NPNVe7VVR8JZvLP0kwfJdLt1VUREWqq5n7uIzMu90vC2v9TF6/Zp0tiO9V+uLf16y9Tu/FWx7Hb1G38G7bRYppxTRuV6YuXq8d5piYxT7njb1/wC2X6r+pm7qLtc5m5dqmqqqfzTLNqT9Gv2nRz+6t7hbimO9NFPNn4YdRrOHNFc5Y9fq+ar+KnSzMfm9hsPDu67vXEaHSclumcV1RGevlHnP0ejt8Cai5FyzrNXFiZ9nktVdafjP/Jz+bLGuvx7j4dv3DN7SWJ1GnuWNTZpnlqv2v4Z8qqZ60y8jrbNNEzHLMY8+76Vve3X9u3jWaT1szf09ybdVWeldPlPxh4rinTUWdZMURiaoz8fGP7PocPJ2eTmx148rft+1OGtXTPk7C5T7UtSqO7243TzWaadymcuKYnMtquPc4bkdXWVzcEwxmHJV4uOe7cagtCMqCqR3ZCwlc6YIhREEhUyDNs7X+Iq+T9Ya0dmztf4ir5Z+sEWOyAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAAAAFpWIWmCpstw2LcS46I6ue1DllVctqlt2ocFqOzds24nxcbRy2I7N6xT7UODT24mHYaWz7UTlit4x2O22ea5ET1jx+D0ujs02qIn3dMeTrNnsTVPsz4df1dtTFPNE0dvDPhDxcmT2cUbFqcez16M5mfOWvTViXLz5jOO7x5fb0xKuaaMUxMznGI8fJ7Lhfb7lvQU2qYom/dr5rk/xZ8Ij4PMbNa9duFFU55bf/E+1eh3Y41euq3nV24mxo6uWzTP8dzGfzw45t26e14e2ixwtwvVXqIpp1d2Oa/V51YzFEfCHzLjXefWXZu115qrzFPujz+EPW+kDfM89j1tXq7czVPXvL4/vOunVeurqrzXVGMeEUR2j4+Lpxxxrrdxv008001TmevNn+7zerv8098tvW35qmacYh02pue1PlD38ccc8nFqLsZnq0b1zv1Zai517w0b1cxnq9Dz3JncuRju4fWZlwXL09i1c+8umOzZiXJajnqxDX5pz2bOjmYuTPeIjqmV0s9rbsaWqqia4j7sxEx4x73qdn0VrSUxd1PLRqI6xVHWLXTpPzT/AGaXDtuar/rojNFPTMxn2vh49HfxnE2rEU89P3qqvu0zPaZ97ycnJ+nrw49so1Fm1dimui7z3OtFm17Vy5PnP/OXa6LSay5TNV3Uzorc9ItWqYqr+E1VdI/Jx8KbPqdbrbej0Viq9qb/AFqr/inzmqfCH2DYeGdp2iKb+7U29RcppxE4mKYmPc82WX9NzB800nD06yumnT7XqNbOek3rldeZ/KYh6nSejveq6I5dk22ime8XrVP1zl7DWcYfZaKqNLTYtUU9opoino6DW8fXeeqJvRM+UOe7WusjVvejXXRFWNDZtV461aXWTGPymZh0O6cGcSaKeaxVOpo/7K9EU1flXHSXdVcc3668zTcmfPLa0XHHLMUX6sRM/drjpJZWuz5pq67mn1s6PWU3NPqP4bV2jlmv4T2mPgvPVEfez7pjrD6pu17ZeJtHVpty0dnUWaozER96ifOmrvD5xv8Aw7qtltTqNPfua7bubFN6MTVb/wBNePqzYs05du3abNNFjWWY1ej5sTbnpVT76Z8Jj+ku4ubVodRpJ1236yzd0tPtXKp9m5bjyqifH6vH0TT/ADTLkppjM1UzVTMxieWrGfj5udnppsXqrd65Vct08lE/dj3eDjx264wwmuZqnM5nxWmqIqziZhtG5tdiNRqaabkz6qJ5rkxHhHhD736P9u0u1cNX9y1027eo1vWmKsUzRaj7sd/Pq+AaavkiaYquUxPXpOF1Wqqqqj1uquV0x535mf6T0Yym0v3H07ifW6fWbjVctajT1UWsxTVN2I5p8XmNw1Gjop9rWWMz4UTNdX9oeSo3LQRi1bv28x2iinmn+2XNRVfvVRRptDuGpmOscmnmI/rOIXDBq+u0ubhobdyP931Oo6xmOluP1n+y6nfpqt1U6PR2dFR2mqin1tX/AMVXb+jgtbLvtdPTb7WmpnrM6jURmP8Au05lnb4Y1138Ru9uj3aazMz/AFn/AJOnXSajSu1V6mqm7rtTXdpjtXdr6R8M/o16a9HN2beluXdXdntTZomt6vbeB9JXEVTo9Tr7me+prmqP6Rh7PaODb9FmJzb0tue9NFEUwzYsunzfRbFvOumKq4tbdbn+Kv27v9PB7HhTgSark3LNr19/x1GojM/92O0PbbdtOzbZTNdzGpu+XkbpxbY0Vv1VFdqxTHSKY7uettdm3t/De17dRF7X351F6nrFGIxEuLfeIfU2Zii5at0dsR1l43ceK69RzxZmqnm/jqjrLo7l25cnmu11VRPXrOWei7d9rd21GrpiabldFuJ8e9fuaeo1Vq1TzTXTRFMZmc+zTH/N1tWrmLU1c2cR2q6dHkd93qvVXIt0YixROYj+afNvHFm56djve4fbbtMxRizRV7FM9599Uebqr1y3RzXappimIxNMz2+Hn8PFq29RmrnmqmZnpPlPvl6z0bbRXvGtp1tFqmr286aKozHT71yfKI8Gr4a23ODeG9Tf1FjV7jpZm70r02iqjPLPhdux5+VPg+zbDotHtliqq9XFerrjNy9M5x8PJr7Xo9Ptummi1PPeqz627Per/wAnSbxv0VXKtLopi9emfaq/gpx5uGeW6dNO04s3fT6Dhjcdxqq5eWzVTTTPjVMYjEfnD84aPTVaXSU2uWOkZjr+cvacYbtO5RRoqL92/bor5rl2qel6uM4in/THX83RaXS6jXaqzoNJam7frxnyop86p8Ojtjn1i63HtvQzo/X7bucXYops3LlEREz1mI7z/eHR75pIs7lrLfLyxRcmIj9H0rhHZ9Ptuxckc3LTEUUV4xz9czPw7R+TwnEtqm5umpuU5nmuc0T4TPj+rWOW4zcdPJ6m5VTVEYxEdYj+zUq9XTV36+MOW9XFeprqmc080xT8I7OGcTMfn1Rn9u/9HO3VbnxjpPZmbWnibtU+U+D6D6QLldent280x7WcYdR6G9u5Nv1e5VTVNd65MUznHs0uTiG7c1W5XKZqmabcRj81mO1yeZ1ViPV1TX7Mz1iYp7Oj3G5FqmKKJmOfpFWMTMeM/o9DrbfrvYrnGJxnyjxl5XcrlNequVUz7Ha37qY7Nftzk3WvVX7EcslV29cimzZpzdr9miI8Zlx88TRjMQ9N6Ndoubhude410c9mxPLZzH8Xmutukmnpdo0lOzbHTbiqLfqqeaqcdZq8XjNbH2nUV6m7VM3LvWrye440rpptxpbdWJq61RDyE2aaaZ69IWfxTL11s6eiJ+73YXo9TRTXammLk5ptx7/Gf6Ow5aZxMdM9nT7jqIuXpqt1RVbpnkoz0nHjP5ndnRTaozFNEcs0xiInrhzU2p5sdOacRmGra1EYmYx2xEPYei3af8a4g+03redLooi5XE+NX8MOWd2R9C4L2inY+HrdquY+03cXb8z5z2j8ob+/aSP9n9Tcr5a4miZjp26ODiDVxiNJRVEc85qmO8NzTTOp4a1FqZ5/3c0xEuHX9ukfBKqaY8GMRRHXDLUxNN6umek01TTMfCcMJ7u+N2lx24+TnpudM+rqaVemzPSn3u32+3FdzVxP8NuJ+rj9XEz2enC+MXHTQ0ugm7M+xnGHptks06fX2ZozTFOM49/Rp7fREXJjwmHa6ai7TXFyinrOPyMs2Jj6+x6nS1XuE9PfmZqjMRGKfu9ofn/W00fb79uiZmablWMx736K0F/1fBVqjUVU+zRFean5x1eqmdfqrnJiiq5MxOe8Zebt66yObT2vWU4inEZxnDuNBobmYibWYnERiOufc7nZNm1F7TUWKrcUXLdum5M4ziaoicOPijX/AOy2l+z6W/zbjep5qJq76ejtNfzT2iHTHPaZY+Os4j3Wdjt1aTRVUzulUYv36JzGlif4aPOufGfB87rieaap6RMzMzzZzPv97a1V6qurPNVmY7zPX/5uLT2rl69b0tq3Vdru1RRTFPeZmekO8uo4zjdpwpsu5b7udG27Zo6tRqLvaa59i3H81XufoThLhzb+Ctt+z012LmuvxFep1NcxE3avKPKmHmtm0un4Q2WnSaW36zcb9Efabkz/ABfyx7oaNNy/rddFd2q5drqqjOZmZj4e5zy5Nu2OGn1izrdPq9NXbiLXPV06TmHx30xfubun2+JiKqapuV9fyiH0LUa/ScLcOXdx3CKeSY/d0T96uvwimHwriPd9VvG43tw1nLz3ZzVETmKIjtDnWq0KLNdy7RTREZmYnviHLb271uuos9apruxExE5x1bXCtivV6u5qYpmbNqOWJ/hmryj3vZ8K7LGo3T19y1HLRXGJ97pKxXqtHbsbHstU0U0U0UU5imqnpMxHf4vgO46y7rdbqNRemZqvXaq5macePR9h9Mm6/wCG7P8AYqIxVcp5Ok+NT4hVOJ5YnOOndP3tZG1FzrHLMTMdZz4x4vecO7VXf27S0RTXFcz6yqmY6xFXaPfMQ8bwrt9W78Q6LbqKJqi9dia4iP4Y6z/aMPoPFvGu38N03dv2eu3q9yqifWXqfuaT3Z/iqj+2OqZ22rlIz4x3zS8KaONu0Xq7253KOfknrRYjH+Zd86vKl8u0NnXb1uPr7Gov7nq9RmZmumZqiP5s9oj3eDtuAtm3bi7imdHRcmLWfX7jq71PN6ujvzTM96qo7Q+27Xw/tWzaWdPtGkiiquqJq5qY9ZdrmfvVT8PDwMtyN4TGPmlPo9u6PaKtz3azVq5iOeaKa+S3REd+3WXnN1sabS6mijT0eroqpiqKJnM05977r6RtZa0vDv2PnpprvTGYnwpp61T8Jw/PN7W16jU3NTXTjnqz18Iz0hjHK/TpllK2unXLk0tNNWppju07eopricTGXZ7NaqvaqqqmnNNv+7pr9uNjdt6bPXHj5N+1t9ybsclE1xVH3XYbNo7tzUW7Vuiarlyr2YfSdFsO3bXbt6q9b9bqMeznwq/Vy5M7ImnmNk4c02l2y7vG80027FFOaKK+1FMfxTHn7nhONuLa94ufYNLR9l2zwop6VXp/mr/SOztvSnxZXuOqnatNen7FZrmLuO125Hfr5R4PCRiaszHNHecs8W76Oe1E124oiiYmMe1NWKf/ACeq4R4fs7hNGs12f8OmrPLV7NWrqj+GnyojxnxdRwvtsbhrKqr9M06OzTz6iYnEzHhTHvl6u9NWp1VExRNMUxFFqmntTTHaIdvqj7Dw7NNWkp9VTRRRbo5aYpjEUxHhHueb4qridXNy5z0UxHSaez13Cm2Ta2e3F7MVVUxMw+eenbiHR7dbp2PScs6y5TFV2Y6xbo+PnPk8+c7VP/s+V7xqZ1O96rURy1U11zyzjriOmZXh/Q39w3ujT28TzTj4Orm7VTd9j+PEUxHbHk+o+jHYZtbhbu3Otyi1zXYx2qq7R8cO+M1G3ptr2rQ8ObR66mxE6i77NNyrrmp8j9MWsnVcR6fR0zX6vS2OWYmrOapnMy+7cVW5pt6O3yxEW8+HTMvgXH+hm3xXqq8zOcT+WO7lvVNOl08/doiKseMx3e24U3erbtoidPtsU1VTy3dRHXnpz0ifzw8rprcer6xicZhvaLVXbHNpIuTTRcmqbcf64xj+vV1l2z9Po+18Q03Jo9ZOJmrxen0t+dRYmKqomnPjPSXxynWVWaM833Zz+U/+pe54e3XRclu5rblqqiKImKZq+seaXHbW14rpsaXURFFExV4Y6w+ZfYtXGqv3rsTTF65NdNEx1xL6fxTxHoNbYt2tpseru0T/AJsW+3wz2eRt6aaqprnrVnMzMzOfezMdG2nt+lpnpVRPv6O92zZdRra+TS2Oaf5qqcU0R8Wzse2V6zUU2qMUU966seHl8XvIu6XadLRotNTTN2rpH82Z8/emds8WccydTt21bfw/Yr1utvW671ujnuXLkezREeUPmfHnG+v4hvRpac6fa6J9ixbnE1+VVXx8m9x7xF/iVdW26W7VOktVfvblE5i/XE9Yj/TH95eIvZ55mesTKyb9bskmnNTZi5ETTnt06Zy9VwHwj/i96dVqprt6K3Viuqmrrcqj+CifrU63hbQUa7URF6ZjS2/a1FUd4p8o/wBU9ofSuHblWq3LTaa1E2rFExTbsURim3THb8/NvtXGYyV7zY9n0+l263csWaNNZt0fu6KaeWKY/wDXj3l4erc7NvW6m5VMRRTcmJnzjL6Ru+rs2eFNRzXaczammmI71Ve58I4y1NnbNvq0d27V9v1cZ5InM2qJ71T+jju3L11lj55xDe+275uGqzExevVVR06RTnEfF4LiuqbmriJiIiiMZh7ncbtu1ZmaetNEYiPd5vB7vTVN25NXeZ7vqfjTTx89283fpnM4al2MOwv04y0b8d30cfp4a1rnVrXI9ptVU9O7XuR1bxrNa9cONz1w4ppdpU3piU+K4IXa7ZQufch0NMaZZ+AhAmlRUhKMobW1/iKvln6w1YhtbX+Iq+WfrBFjsgGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABRIUAAAEg8QcsLDGGdLFYrlohsW6ezhohtWuznnVx+nLap9uOjsLNHRq6enm6y37GHK1qeufR25dzorPNOIaOjpzHZ3W2W8VxDjyXx3wjtdDZ9RZmuqPaqjEY8vJyxMzHtY97k5qsR44pxEe5x0xGI6f1eDKvZhGcecuSK+XrExzY9mPe4onEdWxtduu/uNuJjFuj25n3+Dhk6x67hHZL2t1FjR6eiatRdrin4zPefyfoXWaezw1w1Y0WnoiYt08kefN41fHL5/wCg7boq3W9u1dvNnT08tNU+Nyf/ACei9Ie727lyuiJjksx1693H7K+ZcXa6q9qa7PPnl9u5Hu8IeH3S5FE5pmearrPV3W66iYpuXK/v3Z565nv7oeV3K9NUx7fWIe3hw/bhnXXau7TMz1l1Oqr74mWzqLnd12pr6S9eEcMmpfue1jLVv3Ok47M71cZaN+50qddOXYque8t3eWes9/c1pu9exFyZ8G5GHYU38zEeDsNLPtRy9qujpKKo6d3Z6K76vkmPCcsZzx0xvr6BsVqfVaexYq/eVTinEfxT3mfh+j2m07Ld1uq0+3bdRNddVcTmY61VT3mZ/v8AB4vgq/XqtXTVTGZ5eXH95/R924It6bh3QxrrsR9uvUxOKv8Aq6fKJfJ5cctvoceU09HtGx6HhDZOW1HrNTc63b0xiq9X+lMeEeLwvFnEtdjUVRczXVXGIppn2afj5OTjrjuqLeYqpqu19KKY7Uw+Ub1ulzU36prrjFXWqf5lwxv7S8kdzqd6i/VVN3U1zX5R0pmPJwWtdZuRnpTPk8xcvTnM1Qytaif5nox43K5vV0au35uSNXTVimYzHveataicR7Tds6jNVMeBcdJMnodJrKtLVzae7XRnvETGJ+L1W0cR2r9NOn1cWbfPHLPTNNce94W3XcnGPu/BtW5zTGKZjM4zPaXHOO2OTtOIuHK7Fy5rtpim/oo9q7birrY98edMvPTVTHhLtNXq9Va0NdinVXIt3IxXGZn2fJ001Yz8OkeTz5Rvbl5s9XDqJsxNqdTRXXZiuPWRRXNM4nx6MornHWISuqOTMziM9eiWbR9R4U4A2/ctH9pq0Wn6UU1UxzV3ZqpntPfGHeaf0a2LdWaNq0dHhE1aaI+ryXok4zu7FqrW36m5y2Jr/c11T0pp8bc+6Z7eUvte9Xbt3Q/ao1ETRVTzRyz28e/m5ayl9ZeMo4RvaWIimuzYiJx7FMU/Ra9is0/5+s5o+bJq93maZmLddfjnPR0ms3a9V0ijk+aXWWkd9a0OyWsetuVXJpZfadk0/WzpqOn88w8JrdwuzMzN6Y6dol0mq1tVdOb1yqqPDq6zdH07UcX6bT5p9daoiO1NFOZdJrONpr5vV0Xq5/1V4pfP7uso5cRVy/k0burjM4r5m/jNvYbjxLrdVEx671dHjFucz/V09zXzM56585nLoa9bmMY/uwjUZ6xE/wBV+JOz0Maya8RVVOWzF6Mc01THg8/p7s1Y6S7GiuKKJuXImaKI5qoz4OeeDXZd+1k02ps00xE1dauvZ5O9cqmuebGY8m9qLl6u9XcuTzTX1r8vdDrqqcV1dcZno5aNbb+2aGrX3PVe1Rb73a48KPGPjPZ+hfRfstG2bL9qv2pszqaYxT/LbjtD41wZu3DOgsRG8ajUUVU3eeq3b01Vc3YjtETHSPzey3D0x2PUTa2TaKoiIiKa9dcimKP/APHT1n85hMpb46yaj6Xv1dq1tl6u9q7emsUR7d6ueWIjy+L43xJvtnVVVaHQzdtaKqeWrEYrvfHxiPdHd026cUblxFq6ftuuv6+uJ/d2LFvMUfLRHSPjLd0HDG8bnc9XdmvbtNP+ZRZn1mprjymrtbj+suePF76u7XDt9i7uGup0WlqpuayKeaqM/u7NHbmrmP7R3l9N4L4a02j0lUUxXNuv2r16ely/Pv8AKPKHPwZwbo9t0s0WtNa0+niYmaI+9XP81dU9ap+L0eu1NuzEWrfLFFMdcT2Szd1GpXXcQa+nSaCaKZiinGKKY8HzXd7lVnbb9+mv95RTVX16xM+H93qt9uevtVXaqM1Z9mnww8NxVfj7BTZjp6+7EY90dZ/vh2k055Zb8eV9ZXHLE98dSiuqI+7nPTHn5f3YzMc0Y8nPtdv127aO1jMVXqYx+a/pzj7pwpoKdq4T01muJpu02OavHnV1/V5e9PPeu3s/fqxH5Pb7tXXo9om3NVNVcUREzju81p9Fbro5apjkxNVU57R3mW59LvbxvFFf2TSzREYuajpHXrFPjl5K9NM4oinEN/ibco1m7XbnPNVqapppifCmOjp66o+/MzPuVJHFqeaqmLVqnmvXKoot04zzTPg+4cMbfb4f4fs25o5KrVuJqj3z1l4H0P8AD9O+8RVbhejFnbYzTEx0uVz2/o+icYXps0fZeaM1+GCeetV43ddTXrdfc1FcYielMeUNSnS1VxPX2Zb3qJ58REVe9s12rdnSVXK8UxjrMz2cuW2pXlN/n7Np6LVr/NuZppnPWI8ZeUux+8zRTimY7Z7N/dtZOs11eomqqLc9LNH+jzn4uvuVdZ6R2ZkrCTM8vSfajtHfPuffeAtlp4c4X0+acavU0Re1EzPjPaPdEQ+NcDbVc3nijSaOKIm3RXFy9PlRE5l973q/RRp5or9mbnSI7Yhmzd03Pp5zWXpuam9qOnXpEfV6Lg2zN7Saqe/szMUxPeXltZNMdKOXl8OvZ6/0f9dNcjpirMS3yTWDUfAd0u0zvGuj7sxqbkTT5e1LgmqJxES4t0qmniPd6as5p1lyP/zpccXJiZ/9eKYTxf29Dw3ai9Xr5iM4t0fVx02OuZ8XNwJVFer3G3VOM6bMfHmc1NucR8HaZaZycensRFcYmId9tum9ZcotfzzENHSWqJn2o6+D0nD+mqu6i3XETimejGeXjMd36TN0r2f0aa+u3cri7coptaePKrMdnyLg3bbm/wC/bfpZiqLEz67UVxHainrMY9/Z33pg32rU75b2G3cqnTaCzFy/XTPSm5V4fGIw9n6GuHvsWzVbjqreNRraY5YmMTRbz0j8/vfn7nmyvWadJjt2Oqv2dp0Gu3rVUTGn5IqmMY6U04ppj4z0fBt63K9umvva7WTM3dRVNc+WPCPdh9H/AGhN8ppuaLh7T6mqJtfvr8R2mrHs0z78PkdFyuKaaJp6eOerv+Ljfupnds7kRE5xPXr3fQfRNtVNqm9xHqLc/u5m1pM/zY9qr8uzwERGaaZropiuqKLfN/DMzjM+5+i9Hs2k0XDWk0di5paNPp7NMeu9bTFHbMzE5x383bPLwwjzGou3NTqqbdMVXLlVWKYjxmfB62izs/A23U7nv+qp+1XY9m3THNVMz2oojvM+cvI7jxftOxUX7OzW/wDENZNOPtMx+6t+/wA6p+D5nvu9a3XblF/XauvVay7HJRjNy5V/pppjOPg883fpnLx3vG/Fet4i3SrU6nltWqfZ0+lirEWqPOPOrzl0W07Zr993GdHopqt26PxF/HsWaZ7zPnVPhS9Twp6Nd219unWcR3q9n0sxmnS0zE6i5H+rv6uP7vS16fRbRpf8K2+zZtW6Jxaot9affVVPeap856u2E17ftmNPR7bp9Jprei0dmq3YtRiiKvvTPjVOO8z3y99wvofUaObly3in72ceTz/DunjUaym3Tiapn289er6Hvcf4Zwtcm5yUzNOJ6do8Zbt0b9fnP0y7lc1u+0WY7RE3Koz28Kf1eBpzHTHaOsu04o193X75qddcmKbd67PJmf4aelMfr+br6aoxmaMTPhBPpuOSzNzETbu3bVUfdm3MxOfLMeDe4V4f3TiTdrGz7TbivV3qZm5XVn1dqiJzVcrq8ozPvmZaFNd3nt2tPYrvXq6oot2qYmZrqnpFOI69Zl9v4Q22jg/Ya9vtXLc7prcXNwu0xmMx921TP8tPb3zmUn9s16HYNl2TgzYI2/R0VVW4qmb1VcYuam5Mffq/Snwj4uw4TtXNTza67zTTMzTZntHvnH9HS0U3dfetRdnpiYpj9XrrsUbVs+KYzdmPV2qPfjvPuhMskn9vlXpv3LFyqxbiOeqfstuc9qYjNc/nPR8k56OeqMTEZzT8HfekHdP8Q4hv1U3Zrs2Jm1RPhXMT7U/1eYqrnOfJiYt7b9qKY9qYjEdXtuGNFyaS1NXSu5muYx4eDxvD+nq3Tc9PoaJ9ias3Zx2pju+2bLtUVUU8lqJi5imnpjlojwddahtv8H7Vbt53C5RHrao/dx4Ux4y6D0scVRo9DNrS3Zt6i/E27UxP3KY+9X+kPZcQXI27ba4t4tzNOKavCmPGX5x4r3a5um7X71VWKKZ5LVOe1ET0/r3eTVzyK1Z1VyuKaautEdJifH83NpIuXMUabmru1VRTRRHjM9odZRMRXHhT447vc+jDZrW5a+9ci7br1NmIizp+b2sz3qjPfD0ySMx3227f9m01na7FNdy7TVz6mqI/zLsx1n4R2h7rgrh+mvVzc1VuardGJiao6VT5MNP/ALN8K6f1+9brp6NZV0ixar9bcq92I7S8Tx16RdRuNidBtludt2+apjlon97X76qo6R8Iz8XHLK2+N19J9IXpA0fDtivbdu1NvU7pNOIimM0aePOr3/6XwLctyvarUX9VrrlVyu7M11Xbk5mr3y07UajcNV9j2udTrdVM/wCVpv3kRnxqmPZp+My9Fp+F7miv03N7rsXNTGJp0luZm3anzrq/in3dmscLj7Ua3DG1RN+jcrtP7m37dqirxnzx5Pq3AW412pvRciiar1frKpnvPlLw1E1XO9EYmcezPT+juuHtTGm3DmqzjGMNj63xDYq1my06yzMTVaqiZiI7vi3pD0tMblp9RVGIvW5onEeMdYfY9k1H2nS12oqjlqp7ZfPuMNruXab2gu0TmJ5rFXnLy7/ksnj5ZqbkUYpxjHSXW39RVNVMxOKqK4rpq8pjtP5NzXU3LdUxdmrniZprpmPuzHh+rqrtXXs9OP0zY77TairW284iiYnFdMeE+fwlsWLXtxFWe/R5jRaqvS6mm7RMxPaY8Ko8ntNBFGusU37HL8M9afdKo3dNRNOMzVVHvdzt+jru3KbcUzNVc4+DR0FHPcpiKc9fB77hHbszN6qieeekRMdY96UZ29DY2XbZu01RM0dZmr+KfJ89484ivaTT3abUxOq1tPWrOPVW/GI98vecV6iima6K65+yaSJuXMx3mPB8E4g193cd1vau5NVXPVmI7REeDGOO7t33qOKb8zjrHLERC2bNzVVU0W6aqrlVXLTTHjPk0Llc01YpiJz5vY+jTbr2u1Ver9XTdpon1dr3TPecO9xLfHqNk2iuLWl2rSUzdqzFVeI613J7z8I7Q+o8N7La4foivU2/W6u5HLRRTGavhDrdNe4f4M22nV6/U2rOpqj71c81c+6mmO0PA8Xeku/ul27o9m1Feit3omPtNXtXKqfKnH3Yn+p1/Thb69L6RuNdLs1V3TWYsa3daulVFM5taaPfPjVHl4vhe7blOp1NzVai/N25cq57l2qe+fDHn5RHRnV9r3Dco0Gjm7rL/WZs25zTTHnXVMYpj3zLQ3jT3dPX6mu/arqonvaieWmfKM9Z+K48Oqm/HW669Vdmaqvu0fdif4fKZ97zm41+smurpOfGOjttwvTTFWKfZiO0959+XRaiqZir/wBQ93FNPNndur1MdHXX/F2OpmeWfi6293l7Z9PJXBV2cFXdzVuGru3izXFcjq45clbjqdYzkwkhZ7JDZGSEpAtZAkpSMkgghKyzjs2ds/EVfJ+sNWOzb2z8RV8n6wQjsQGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+grz/gqeCigAAAJ4rHcIByU93LbpcVPXs5qOzFZc1uOzbsUxjs1bfg27MuFG1Ypnlb1ino1dPHR2FimJns510wje0UTEUxjPwen223Zpr9ZPLNMU5mJjtLoNBTHNGKXpdLTFGmzic1T/WHm5a9PHHLV7XWEXCVPA9cY9JnGcO44fpj7NVdqn27lcRHTwh012JiMxHWen9XtOC9pnWa/RaCM1TVcoifPGerGUaj75wVtf+DcC6e5yclddE37s571T2fNONdbN2qu3ze1XVip9W4t1dFjaqdLazTTERRjt0iHxDifURc3W9cnGIpxMe/zMcPEry+93M1RmZxDzOuuxFcu83i7FVVcZeY19Xtz1e/ijy5tLV1xzS6vVVt3UVx1zMup1lfXpPR3jja4L9bSvT3ct6tq3aurrpyTm95FXVxzUxiuctwbdFUYjq2tPcxP3nW01z5OW3cxPZM5tZdPofA28afQXbNF3ln1t2IqmZ6xD65xBxHYptYt3aZt0U89U58PB+bNNfmIxOIpnpOYdxo9210WI09WquV2qe1Ez4fHy9zy5cMdcc3qtz3i9rtdVeqqinmj2Y/lhp3NRVPXMOmo1NXfPWe7Ob9dXivxr2dlTfmZ64ly2rvtdodXamJnM93PROJ6QddI7m1c90N2xX2n9XS2K4mYiaZ/q7PSzETEcs/1ccm8Xc6S9VzxETPvjLt9LXRTRzVzimI9qXR6Lrc6RLd1eopt0Rp5mKp6VV9O/lDz5u2MZarUzXRVXVM81U80x5eTra78xPaqPgzruVVZme8tS9buV9aZmZnwif6ONddNqxqaaq5om5Tn+XPWPfPu97Yomqc9Y6Pp/CXANne+EKtpv1abS39Jbm/Tr4tRN63frj2aeeP4OntRPg+aajS6zQai7odfa9VrNPXNq/TV/DcpxmI93WJpx0mJTUv0m1xM09I5ffD636MeLrd7TRsO636Z5qeW3VcnpPw975DFU+Of6s9PfuWL1Fy3Viqiea3VPemfdLOUWPtfE22Xtuu4jPqKvuTPk8hrvYucs1zMvX8E8R6bi/Ya9Brpop12mpjnpmOtVPhXHn5S81v+muWb9dmuMV26sdPEwmkrz2tudZ69cOp1N2eV2Ospriqc0Yife6vUU1Ynpl6sNMNO/dqmPBq1XJmHNeirrGIa8UzmeZ00WrE9GVPWWEz0Wj4q5dt1u6WJnGOk5bmsvUxpqbfN0rrzMx4RDU0k4zPdnruTkt00xj2cy4Zz12jgu3PWW6o6xPg16qaZqpop57l6qYpot0x7Vyqe1Me9yVznr4u84EszquIbfJEestx7GZ6RNXSfzw5f9u0njuuEvR3f11dNvU0xeu1TPrIrqmmzRPjREx1qmPF7nbfRpY013ljQ7fFMUxiZomr6vWWqKNBpLNmxy26LURy4/hmGpqd2uRcqquXquvhEuF5LtuMNFw1t2gpmLk0T/oop5Yl2V2rSafTcmns27MRPajzdBe3K9XVmm3E++amvc1lyuf3lzr8S5W/a2Ox1m51WonknM1T1p7Og1Ws1ty/XVz3Ypq6cs0xiGeov266o55iqc4zM/daeu3HTaaqm3qJnnq+7ap6zMecz2pj3yzvXrDCuu/imiZquRNXLmY93aHguMLtVW5RYtVxFWmo6Ux2mqrw+OIh9e4V0VWprp3Tcoi3p6Kc6e3HSKYnpNdWfH3vjfEevs6rdtVrbfT196uuKeXHLHaP7RDeOTF+3WV0001RVEzVTmO0+fV6v0SbP/jHFkV1TFVvTRN2qM9nk7cUcsU0Z8JiX2n9nvbqNPte6bhdpiPXTFuiuaf4cdW59rjHccV189z1VuufDET5PP8b63/B+EblOaadTrJi3ajOJ5P4p/R3e7zN7WxyxOKemfOP/AFh8u9JO807nxHXprV2KtNpKYs2598fex+eXXJHk79VFdzNEYjyYV82cxTmrwiOszPhC3MVXsUVTPweg9HO0zuvGWisV2s27UzdrnPhCEfW/RtoaeGeCLH2izFN67T62506xNXg89u2pnX7hcvzVOInFMeT1nFd+5bsxY6REx4S8hZt081U1RMpWq47Nr2apn+nm6XjHXW7Wi+xW5mqbnePHl8Z/TD0lybWm0t3U3q+W1aomuqfd5fGez5duesr1mquaq7Vm5cnPLMdojtH5JjN1zrgrzmappxmenwad63EUzNNWZ8nPmrr1hIom7XTRmOeuYpp88z0ddeM4/b6l6EdqnSbRq93v24inU1+rtTPeYp7z8HdbvrLmp1lyj+C3OIdlo9Pa2jhbR6GnFEaezTERHjVjr/d0ldMzVzY9qqcy4TH3bq45xjGOj2HBVXLpLlWIiKZl5Sbc83LETM+b1Gw3reg2jU39VV6q3bt1V1V1fdiMeKcnrWE9fnjiCuK+INyrie+quf8AFLSor9qMT4ruVym5rr9+jM03rlVymZ7zE1Thr259qMecLhNRLd163gOaqtbuWPDRx/xw7i3bmauzrfRtb59Ru9zwp0lET+df/k9BYpiZ64mJmYSZOeXhp7Fc1UzTb5sd4jvh6jWazS8H8JVb1qqJvam9Pq9Hp6uk3K5jvjyjvPwaey29Na9ZrNZfosaXSU+svXKo6RGe3vmfJ844r4n3PjDiuxVpNJXXXdqjTbVo89OTxz5TMxmuZ7RGO0M30x9bHoy2DUcX8aarV6u9cv6K3X9o3Guc4qqn7sde+Z/s+/auujR2+WzRFFuza5pinERFMR/yaPo74f0vDnDlrQWrlFzU5i7q78U49ddn72I/ljtHuhp+ky7Vt/B++bhTFMXJteroienWro4ck3lNO2OXWafnXjDdqt34g1euvTiblyZmJnr7nU019Y69M+Lh1Nyar0zywU3Ip6zT0jv8H0JNTTjb69Lsm2ajda7tGm2qvWTRTmuYxRRTnzrmeju9s4F3q7XFu1On0tFXXlpueu+j23o64c2Lb+DtNf1tizd12upi9qJqrzHX7sY90PT29bb0lONL6qxT5W6Ij6OOdevDCa28rw96JaL1yL+87rqa7f8A2dNHqqf+b1+n4e2ThSKruz7forN2uMVamaM3Z/709WnrN7v1R0uVVfCHVarVXtVXzVXa4hymWnHPH1tard71VVVNNUXM9+rqMRFc3Jomaqp6tii3ExMRmfhS46pt01VUxVM1RGcY7Hy3aXHT0nAVrn3Sa8ZimM9YcXp+4lq0WwfZbNURN+Is0xE9Z5u8/lGXo+DqbOk2z1+om3RcuW5nNXsxEY8Z8HwH0wcTWuIuJ6qNJdrnRaKZoonwrq8ao9zpjbldVmx5DWV0zVyRGYxhwcvL0xM58pwyiqMe02Ns0N3c9fa0FmPau1Ymv+Snxq/KMy9ckV7X0T7PyX6eIdTTFddPNZ0MVR2rjpXdn4ZxE+eXsaZi5VXzc0Zjp0/t/Zo6GrT2rNnSaSJo0ti3FqzTMdYop7RPnPj+budJFNeIzHNNUR197jYlek4L26b92m/MexbiIxh13pm3uNDt12i1diibVqaKa6Z6zXV4Q97stnT7fsly7E0027dMzXVjrOIzL86+mrdap3DSaKMe1bnVXqP5Zqn2In4Rn+rnl/K6ZfOb9+a70809M5mY8fixiqJqmeaZ9zgiYmqfa7zlz6C1XqdRa01qJm7duRRTEecvTMUj6j6KtjqjRV7rXFPNqbkWbcTHaiOtU/nOH2TYNJFV/mmKcRHszl5Xh/QWdFo7GntTiLFuKZjHTs97w9Yxp7U1RHLjMz5R3XLGaV889N24zodp1OK6aeSiLPL51Vd5/o/P93krmmunE47vr/7QWpquafR2se1qL9d6qM/w9ofG6q5iZtxOIjy8XPiwiZXSxT480Zic/k7zZ9j3Hc7Vu7Y2mqqmZ9m7Oqi1GPy64aPC+1U7zxBptBVM02655q5jyju/QGz29s2zT2qLOg09qLdOIrmmOZOReP2vA7N6L9911rNe5bTt9Ez7XLTXdq/rOOv5PQ6f0RcM6Llvb9rtfvNWYnkiv1VqfdMU9XdbjxFRiabd6a5+HZ0Wt1uq1MTPr66PdTVMMR0sdpuGu23Y9BG2bJoLG32I+7ZsURT+cz3n83kLtdV2uq5XOapnMuaq3M11ctVUzPfPixvWq4jH3vgrNjit9K+jftV8seGfNoTTXRViqjrnvlncucsR0z7oZo9nwpvNVuvkm5MTHeM9Zev3TbbO/bZ6+xXm/THSntmfLL47otTXb1PNbqqiuJzGfGPGH0Xg7eaKrcRzYoziumpyuG7tt8w494d13rrut0Nqbt6Mxq7ER7VUx/HTHjMR0x4vntNcXqIrp6+fT34/rnv5dn6n4l2mzummqu6Wm3TVTGaK5qx+T4lx5w5XauXtz0+kim/bq/32zT054jpzR/rjP5xmXbDKfRcdvEzamqevRu7Xrbu2aym/YuYq6ZiZ9mr3S16+emYziYqjOY8ff7o9ziqxy48G2er6vwVe02/aiqdLyWr1NVPNZmesR5x5vtOls07PttzVTiZijo/MHo33S1tXG21anUXfV6au76m5VM4iIr6RM/nh+k+NLt/S7FTRXVTi7ViIpnPb3/3TL6NPkHpX3ivTbVTY5/3u43qq6oz2op/8/o+RzM1VTzT/AMnqfTDrKq+JNHppqzFrS9vKZnLyFFWacGGKVnVdojM1Y/N2m1/41VYzt2m19Fm5/wBZZvU2Ob4VTGWrw3o7Ou4i0Wmv0zVauXfbiPGI6/o+0Rc27RzE0W9NRyRy05mPZj4OujbwW2cA8V6+qL1nS6DRzX1qu6zcqrlUz74pjq7ij0ZzZomrf+Jqq7OM16fb7UWaZ903KuuPhDtt14lt+rmi1NNc4xmnph5jcNZqtZHLcvVRR3xM5yky1657dhueq23adtnZ+HNv0+j09yMV+r/i98zOaqp989Hhd608WqYimeaMd583f0TNnE80Yz1h1O8Y1HTkinE9IlqZ+rfp4rdKqoprjl6S8/qJmKO3i9PvGnmmmqrmiInz8fg8vrZxE9MTHm9fHdvLm6zV9JdffnrLe1UzU0L/AHl7Mfp5q4LnZwT3bFbgq8W8Wa4q+7jmOjkrlxVS6xm/bCSle5ENRYeIKpU7EElKMso7JCx2SEqM47NnbPxFXyfrDVjs2tr/ABFXyz9YIsdkA00AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0Fef8FSVFAABJUEhYSGQOSiHLTHk4oc9hzrLmtNu3S1LH6t233caN7Tw7PS0xjs67TOz0sZiXLJ2wdxttMxVFUR+T0E5posxFOP3eZz75dHt0TmnDvdRGb058Kaaf6PHyPVxriUxmfyZ0+BNFWZmMPI9KaaIuaq3br8aons+v+hbS273F9F6bcVxYtVV0xy569nyjaKarmtpqmnPLD7p6ArExO566IjNFEUUzjxljKrHf8a6y3OrqomcRRbnpjxfGd8uxcquXo6zcqz+T6Rxzq6qbWurz1iiY/Oej5buEzRZpo/0x4N4s5PNbnMTM9Zy6HWS7vcq+s9J/o6DW19Hs43lzddqqu+Lmfdh1GrnNU+DstVV3dVqZerFwzaVyevfLhuVe5y3ZjLguT0l1cnHVLGmWNcpRKjmplyUzlwRLltSlG1a8J8m5Z+7mZnq0rVXsT8Wxaq6RDFalb9urp3bNrrPWWharbVquGXRu28Z6S56MxLVsTmrLdt5mIZrTasRmY75dnpoq/l/u0dJFXNh3m2W4mfanMeMT4f+TzcnjpjG3pZ9Tam7X0in7tOetVXhDUuaiqqrmqnNUznPh/Rhr9TFy9NuzyVWLc4irxqnzdfXcriczPw6vO9OHnjs6buPZiXoeD9BG5bzbxaprosU+tuR4VTH3Y/q8RRduxexzRjH9H3T0KcN37mmt1XbU816Y1Gonty24+5TPx7uOf146S6fS+HNFRtWxW6L/S7fmb1c+HXpj+j5z6Y9q0Wtpq4m0lmiqvRUU29dMdIm1E+zcx4zTPSceE+573iTcItTNHPy4jpDy+qv0U28RVTXRdiab1NVMTTcomJ5qZj88OXHLCzb4pNVVuqbeYiqOswtFyJj2pc3Fe0zsO8V6S3M16WqmLmjrmOtdn+WZ8aqJ9mf+75upi5P8/8A5u9jOtO+2bdtVtO6afXaG7yXrFWaZnt1jrE+6esPqt+u1xRs1veNr/goj19uMTVbnymPH4vh9F2Y7+1R4xPi9X6POKauHd5ouXYzoNTMW9RRPbHhMe9iwju9z09NOJzicdnQ6yKsdH0ri7ZtPFFG46LluabURzRMfwxPweH12lpiZ6NYVMo81epmc5a9cYjDs9VaxloXaZxOIerFxya1UQlEZqSqKoq6s6Pg24W/ybel9nGJx1cuuzN6nPk4dNETMROPPMuTcJmK7cd5qozEuHI9ODgqmIh6v0QW6rvF8RTHNijmml5GeuZnr+juOBt9r4f4m0u6RTFVumr1d2qmek0T3jHm81vjv+n6B4giaLER2xX2h5zU1zGZjzeo1dzRbntsajSai3es34iu1c5vH9Hkdy9Zbj1c0zTc8c/o4723i17uor5usw1/WXaqsU0xmZxGfFx35jTaerV6rUWdPYo61X9RPLbp8/fM+547iXjTmor02yXqrFmqP3murjkquR5W6Z+7Hv7mievR77vWl2nOkt3Leo3GYz6qKsxa99c/p3bPBOw6jcLtrc9fFd6q/XzWrX8V+rxqq/loh0no34Or1d+1um76S5Tar9rTaaqcVXvOqufCn49ZfW5uW9JNVum5RFU0/vbsezEU09qaIjtH1Yy/pqcd/bpfShudvb+DNfa09zNyumnTxcpnliZqnEzHwjP9Hw3UerqomKJmfCJiO8PaemTeLV+vQaDT3J5aebUV05+9/DTP6vBUVRzfe5vDPm7ceOpHPk88ctMYmmImZmqYxnvnyfo3hPSUbLwfo9NNU01zbiqrEY6z1fD+BtFO5cU7doqLcV892JnNOYiKevV+jOM6vs+3W7MU00T0iMRjo6a3WNvKTf5PtOrvYmzpbdV6qZ8MROP7vzxq9VXd1Fdy5VTzVVzM1R45nu+58YaqdF6MN21cU5r1FdNiJ8YiZ6vz/dq56pjp3bituxcibk/vMYfX/QXt/qNNq9+u0Rm5PqbU+6O74tTM0xmmrHm/QfBGknb+ANrsRcn11dubvumauplRu8SX41d6qvniMR0dPpLdU3JzERRMT7U9I/r4NjV8s2aavW8sRHtTV2o+M+T5lx/x9pp0dzZtl1HNT1p1GppmqOeI/gomPqzrbNra434n02ouU7ZpdRb+z2qs3cT/AJtcdvyh0Ov2zdtJtlG56zbtXp9Fen2NVeiKKK5ntEZ6z8ezvvQxwDqdz1tjf9801+rboqirS6W5Vmq9V4ZzGYojz8Xu/wBp2u3/ALG6GKJm3EaumMU9Yjp2j3NYzV0z234+KxVT2iJj83a8Gaf7bxbttjliY9fFUxMZzEdXnovTjrVMzHaHsfRVXZ/2rs89yim5Nuqm3mI7zHmuWWiPrnEN7HqrPNme9WI8XU3LlWInxnt0dlutj1l+m5FFVcY6dXV7prdBsViNXvFXqYn/ACdNbjmu3p8uvaPe59vG3ZW67Gg0Neu3PUUabRWo5rl+5T7Me6P9U+EPnHFnG17iOPs9imvTbRTP7nTzMRcvzH8dyPHw9ns6TijiLeuMN5t6KxazTFX+76W3n1empn+KvxmX0u9wNtPDHom1utr22xc3aaYm7qr8RXcnPlj7seUR+bllVxfEdTcuVXaqtRVNNyZ6xjH9vBxUXIielffuw1NUTcmYz169YcFMzFcTHWYnOHbD2MPqnoh083tl4j1eJjNFmiJx2nNU4/vD0u06WmfXXKptUWqP3t25cnFuzTE9aqpnw93jOHF6JI0WxejG9uu/XLGksazU3LtU36+s24iKaYx3mZxL5x6SvSFTxBpo2jZ7U6HZ7M4nT55bmoq8aq+mOkdceHdmYepax9JnG/8AiVMbXs9dUbTZuc2K6cVX6on71UR3jMezHh8X0b0R8GVcNbHHEO8W5jedba/d03J/C2Z6xET/ADTHWfjh5L0H8AVa/wBXxpv9mqdttV50Gmq76m5Ha5MTH+XExHxmMvovEe8RqtX6mK4miK/bx4z4wmWDeN8eh4a3KK9ZdjmjERGKcdGr+0DqKKfRxcpoiaKrl+jMx3l1nDWqzut23mIiIiYho+nzVXtTwpXTEV8tiumuuInwc+nsLdvz1fnNyczVOPGrpLGJifp2YVVTNU1TXzZ7e1noW+tUePXrD12dWb5X3Hh7WWp2fR01U5q9RRGce52lu9bx1jLxPCGvnUbLboojluaePV3OvXHhPven0t2KqOWZiZ7uOb0YZbb9Vynm9iMfFjzUzVmqqKffju1qvbnlpiqqfc7zh3ZadVNd/W3oqt0RzVRM8lFFPnVV4Q5TG5eGWTg0Vuq5MVx1iJxEYxzOp4y4m2zYYrszetXNfTRz8s45LEedX+rypaXHnpG2zT2bm1cITRVNmmabu61UexRHjFqP4p/1T0PRH6O/8Qv08R71YqjTUV+u0+l1EZrvVz/1tyJ8PKJW8Ux9yYyy3Hkd2434o3LSVaHU7jqrOgvU8lVM2qbdddPh75iXj666pu1UzFMeGY7z8cPpHpy1umucRU6SKfWX7Fr2qqZ9mjPaP6PmWIirMROc+b0cM365bqzROZz4vccGaCvTbXXuE8vrNRE0UxjrFEd/6y8dZsXdTcosWpxduVRFMzGYfQrFduxZs2rdUTboiKaY7dun6OlXs7qxVPrYzTFPaIjPh0eh4XtVandKLMUZiKsPJ2bvNfpmnGM9YiXvvRxRTd10V09avW57dnO/RfY9txNVRa2zT7b6zlt3pim78sdavo/IPG283d44n3PW1x+7vaiqaIielNETimPhiH6e9K2unQ7buN6bkT6jRXaqev8AFy9Pzy/I92c3Z5u+Ov1Tjnu0ymoROMdYjyek9GWnjV8WU114inTx6yJjznpDzN2iZzMTMzjpEQ9n6KNPdop1OpqpmJrvxTbmY/hpjw/Of7PR20j7rs9qmq1V7c1ez7Uz4Pd6KzTRw3OojpHqpjD5fsNG7am7VRY1Ecs/5t2afZpjy+L0/pF450XC+x29BoKbeq3Wq3mzp659m1GP8y7jriO8RHdyzz34mtV8g9Pdyad/01qeaaLeliKXy3PLGeuanb8T7pqt23OvWazW167UV9a7tXb4REdKY9zpq68VRE+DeM1C3buuEtT9m3em7FNUVVW6qImJ7Ze9saq7y05u3Ksx/FU+XaG/9n1FF7OZpnMx7n0LbbvrKbdWM019pz4JnPNtYXTuKLkdKsRls0XIrjEzFEOCxainrV1h3G07JVraqaq6Kot56RM4z8Xm7euu3HoNHcv3c26Zqpx1qxmF1W3X4uRRRa5uacYx1h9U4d2rZti2G9q91qtW9NbpzdvX45aYj3eb496QeO6t919PDvBm33eTXXfVW5mZ9fqvfEx/l248fGfFvW3O5/p0mv3nSf4pVtel/fXKKee7cp6x06Ypnxj3+fRhXXM0c01RnvEeL1U8J7dwZwrVa1Op0d7WXMXd01l2J5M46UURHWcdoiO8vme98QTqJu2dpsV2rUdJu1x+9r9+I6UfLEZ98mpb4m3o7ExVczMTOIz0h2+162dNqee32x1h4fh/R8S6qijVW92vbfRVETRn26qo+WemOnj/AEeu01q/Fmn7Tdpv6iI9q7FuKJq/KOn9DLHrNukfVOGd1pvWqaefMYjNOerW442yiIjV24mqcxTVER96nz/LLzvBt6Y1+KcTVMRHWX0LeZqq2eqLtm3imiYzli2Rvb818T7ZG1a/1dNObF3NVvz79nn7849mPZxL6B6TNNy6XR3p7zduRTExjo+d6qYprnM0uuPv0lmnDr7kRpLlOaeXkn6P09eu3p4E2Cu7druT/h9mZqrnMzM0R1mZfla9bu6yunR6a1Fd/UVRatxHeaqpxH95fqbiq1Oj4V0FumJiixp6LEZj+WOWfocnkcssnwH0qXfWca3ZpiJpizTEYebt1xHszLvePuu/evx7Ny30/Lo81FUTMT2mGsfo347zh2rk3rS101THLM9c+6Xrb/JERVMTXNUznmnLwWgvVWbtF2jvTOfi9zbrov6e1qLdcVW7lPSI/hnyn3t78YsZ0zTcxTXFNNNPbEd1opo7TiI8MrYszX2ifJ2u3bHqNbqIotx7MdZrmOlMOFq4x12j22/uGoi1Ys1VxNWMxHRubjwfes1esuV2dTM9Jt0zMVUVeXv/ACe52nR6fQaSbOmqxNr72fvT75eH4149sWJvaLYr+b8zi5q4qjFuO002/f8A6u0eHVnG3K6jpnPHguPbWm26attmmxqNZTMRcqpjNGnjv6unwmv+afDs+ba+qPa656+PeHod7u5rqiKeWrrOKsz17zOZ7zP/AK6vNauYzPWJnzfU4pZPXz+Suv1MtG+3L/dp33rjz724K8Y7terGZ6uW7OIlr1S6xKwrcUs6/Bx1OsShlCkVkrEEq+KopWasdkhciIsdm1tf4ir5Z+sNWOza2v8AEVfLP1gix2QDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4a78k/QV5+VSe6igAAJ3BVpRlEg5KO7mtd3BQ57PdzyYc+n7S27Xh8Grp/Ft2ezjm03bEz5+DtdHPR1Nifo7XSeEOWTri9BtH+bRHhl21Vc1V11TPeqXUbRP76n3S7G1PPj35n+7w8329fG36YSrPNMRMs6ZjBR1qnpDy13b/DlGdX3/hfd/QXTycN7pVEd78R/Z8O4ao/3uav9M9H3P0KTEcI7hVHT/eP0cc8lef46qmdLqqcdaq4j+757vmIq7Q99xpc/d3une5H1eB37EXJnLvx/Rfp5PcO8uh1rvtxnEy6DW93t43jydTqu0ut1PaXZ6qIw6zU9ZmHpxccmjca93u2bkYlr3I6tuTiq7JTDKqEpjq2LEOSjomFpiUquejs5rff8nBbjpDntx7X5MK2LMznu3LMdKZ82nZjq3rEZx7ma3i3LEdYb9imcw0rHeOkO10Nqa5joxcnSRvaW37UdZ/o7bVVxp9P6qOWa7lOO3WKf1y4NLZp09urU3MclEdczj4RHxaF/VTqbs3Kp6zPh2eXPLbrhFqqx0iP6SxqqicRPLHxcczzT2/uVVU0RmqIq8o7zlyd/p2vBmn0uv4ksWNTZm7Ypibl2InwjtE+6ZfrDgmzRtHDdWouxTOo1cRXNOOkU+EPjXoX4Np1N2J1NqYqiPX6654Ux/Bbj3+Mvo/HW/UaHQzYs4jkjloiJ8Z6OWWO8kue46HiPdZv66umKulNU+PZ0tev6xM1Y69XR6jcJjOZ5qp+9PnLXp1011TTTVjDpeKLjn47HijQTv21RptPMRqtNc9dpauXrXVPSu3mfCqnMfNEPmc1UV3KqrNOLc9aaZn7n+iffEdJ98S+i2NTTOJmZirpPNnrmPH4PL8c6Omzus7lptPV9n1sTVXVTHSnURE83/wAVOKo85iomPjTpKZxP3o6dnJRcmbkTzROOvVrU104jrzRjpV5+/wDNZxVGP6MaZ2+teiXiezqrM8J7pdiLWonGlu1drdX8sz5S2eI9pvaDXXNPdxMUzOJjxh8it36rMR6qOSaZzTMd4qjrl914R1Gl444Nqu2/3e7aKiKb9NdWZqiO1UfGHOyytz2Pn+ssRGZmJdPdpxVMRHR6zX6SqZrpzmqO8Yxh53U2Zj+DHWXpwrjm6m9RNNWe7GIx3bl2icT0alWY6zHi7T1x6tnTUxVTOJ9rwjzdze2jUbpw1Vc22jm3DRV+si3VP+bb8aY/5uktdMTE9YnMO84W3mvat4o1dPWjOLkT15o8YZym28bp5S3qaqpmMVU1ROJpqpxNM+U+9n62mKqYieWrx8H1bceGdt4rmdXtdjN2uMzbt3It3Y+GekvEbzwBu+33Z9ZuF+316U6vQ5n86qZ6/wBHny4nomTS2rijeNmtVabQ6uaLNXe3V1p/o3J423u9GKdTZtT/ADRZpmf79mjZ4T365VEWNdoIjPeLFeZ/KXoNm9E+4bjfpq3G7r9TRjrTTHqqPzx1wz8WMTu8nqN4ubjr7dvUanVbtrP4LdObmP6dKX0H0e8B67Ua23r9ZZpuX6J5qIr/AMqx75n+Kfg+gcK+j/Y9j09NM2LNMTGZt0xy5n3z4u+3Ld9LpNPRp4oot2afu0UR0hxzsnkjWOfrGxpLG3WK6Ldc3r1ynN29XGOaY8I8o9zzm5X/AFt6qzmKbXjmO7DeOIqbtPLbjrHaYh5XiTf6tJsWp1lc9bdueT31T2j+rGPHuu15Hzji7c6dbxRrr9OK7UVxZtzEfw09I/vEy4aJ5p74nDqa59XFNM1zmOtUz4zPWf7uajV02tPmuvMT1qqx4eT1ddOOX8vX2T0A7Rev7zc3SYjltU8tPlMy+n8WVzf1GblyaaKInPjjDpfQ5ttex8CaS9eiftGqpi/VTPSaebrEflGGW8bnTeov1xOZqqmnCxjHPfjquPK6J9Detu0Uetot3fbmI605nETh+c6aouVdKsY979K7NqtLd2bVbZdqibOooqouUVRmJzD4PxTwlq+H9xqt0zVf08zmi5HbCYxZXURETE0zPszHWfD83rdp9LGs2rZrW26zbrOunT0+rt1+tmieXwicd3jpir1nJHrJn/TTVP0hw0cO7vrav920tVuiqJibupmLVFOfj1n8oauG6WtjjD0ib1vPNpdXqrWi0tXSdLp6ZjMf6pzMy9R6IvR7e3DW6fX7vpa7lVeLmn0NXs000/8AaXfKnyie7c9G3oy02k1FrW6iq3c1dGKo1Got+xR77dE9ap984fX724abY9urt6OmPO5XXOark+cz3dvjmMc7XsdJqdt2iKaK64uXZpimq5ERERHlHlHueD/aV0f2/gKxqLHWi1q6LkzEdMe95HcOItffvVV1aiKKapzFHJ3/ADfQtj3/AGviThm7sm66eiaLlvkr5qus++PfDHVj9vzRRbmIxHSZnv4y5rN6vS3qLlFc0XKJ5qKqZ65en4u4D1+x7hdt6W5Gq0sTm1PNEVY8MvNXdu19NfLOjuRPj0Yy43Sf29Db9IW7fZ5ondKdLV2quV0RNX5ZdNoq9y4t3mrT7ZVqdVcvTi7rL/XEe6f0bvDHA2q4h1eNVbrs6Wn78zGJmH1XR7dtvDW3xpttpot0UU/epiPqxeJqWOx4E4b2/hfQW7dmm3e1VUfvb1URMzPxek4pt/b/AEe7tpc80zZmYfMNbvV+7en1d+aaafKXsOGN7tazZb+lqqmuq7aqox5zhyvD7trvP0/OOqzF2YmMTHRr114iemYxiYd3xXtuq0W63aa7UxTM+XZ0d2nwtfvbkzimiiJqmZ8ujvMdRmfTS1uoibUxVfmmaYxRzTzY90Q936FuAv8Aai9Rvm/WZjh/TT0pqiYnW1Rnp8me8+OcebZ4S9E9eoqtbvxXTNjTYiv7HFWJq8uefL3Pd77xLRoLMaPR027du1HJaoojFNuIjp0jw6ukx3HOPR8XcTW7dinR6Wii3i3FFNNEYpt0x0iMeHbpHueJo1ntZ6VTMzMznvPm87qNxu3K666rsV13J5qqp65a0a7lriYq6+7ozcHSZPomy62mxulm5npc9mXoeP8ARRr+H5uV1Zs37U2bk/y57T/V8p0264iiYzmmcxMeb6Fw7xDpd02m5t2snms3Y5LtMT7VM+Ew55YfWm9+Pzrq7VzTX67FdM01WqpoqjHlPf8ANhbqxVE9Jj3PovHXBd+NTe1NN+miZ7X4pmbd6PCZmO0vB17frtP9/TXMR2qpiKs++MOlx3GLW9s286ratVTet4qjHLVRPaqnxiXutm4s4drjF/VanQ1RH3Llr1kflMY6PmdMXKKZzbuRnvVVTLPkru04s6e5cq/0U9Wfi2Y5ar67qOP+E9tszcs2dbul6J6UxTTZomffVOZw8XxBxpu/GWvp2nV13LWkrqj7Ps210T+9q8Mz/F75q6NLhngLiXf70UUWKtDZntduxmI/q+vcGcJcO+jrb7mrnUW7+71xi7q6piqrHjEeUfB04+KYsZ8jV9EvorjTb1Z3fi+/Zu6mmrOk2yJ5rdj31z2qq93aH2Hdb2j0FFWb0ZnrM8uJxHaHzjhjiGddvFVdExRZoq9iqZ7svShxHejb7lvT089dVM0xMT5uP5HFllZWe9fDuMdw/wAQ4i3LVzOfX6irHXPSJxDprUzPSJiqYbFWi1lNUzVauxNNU5xRM5y2to2XW67WRY0mluXLkz7U1UzTTEeMzM9odMZY6t3himZ3Ca5t5izRzf8AenpH6z/R6Gm5MY8nV2NLXtsTp/XU11xVm5ct5xVV5fCI7JOrqjpzdm9Jt6LbL/8AvHtdsPp/o5qpixTcpmImqJmOvi+K6XWTF2iaqvZmcf1fS/Rxr7U6Omj10U12Lk0VfpMOeUaxrrfTVqtZTs2vpu5qoqqo5p/05/8Ak+ETVFV+qZ7zPTq/RnpT2m/uOiv1zei/Yu2fVXop/gz2r9+Jw/OWt2/X7Zqpta+3VROcU3eX2a6fCfdnGcGGKZ31szM0xE1Yjt1mej3XAO+bFprFOl3TVfZYt9eem3NduYmesdOuXg4i5Va5qaYrpjty1dzRXbtWqosWLNV6/Vmmm1ao9ZVP/dpb+PbO33Hc/SZsWg2i5Y4fs3bmpoq5afW08lNMfz+95vgLhbifjrVajiTcdXOi0lVebV67RmrW1x2xE9qI83V8IcE26Ine+MsWdJb62Nrir97fq8PWx4U+59X4c41q1WljS6jT2rHq55aaKI5aaI8IpiPCIS8cxlWevknpJ0c6Dlu3tNTTds1+qv8AJ2iPCXiblUTMzVyxGcc0dYnyfoLjnhzTcQ2K9dtvLXqZpxqdJmIjU0edOekVQ+IbrsOr2ya509VzUaPm6TFGbtr/AE10+E+9MPorrYnE82IzHjM5ei4f3z7JFGnv0U1aeP45qnmo/Lx+DztuqJnNM5/09p/u2tPR6yJpxy598NZEun2bhHdeDr9dNe48RaOxFMZi3dpqpmPj0ei3j0j8FbPVasbRfndNTVMU0xanktRPvuVRH9ol+dNbXGniI5qIrjpTjrXPux3eo4G4A3riCaNTummvbTtkzn1tyM3rkf6ae1PxlnHi21a9Nx3xHxPxdvtrZtLTRuW4xPNa2/RzP2bR0/z3a+0z75/o+i+jr0f6fhDZtTumq1lGu3/U0T9p1OPZoj/s6PKPq6Gxq9g4M0VO1cP2PVRFX7+uI9u5PnVX3ql3u08QWdbpqY54ojtzefuXkkuPXFjb516Z9Xqb2itWoiZtTdiqfi+bWcVRFfNy9enm+38fbVpdftdVnVaW7XZqqzF2zHNNqfCrHjD5Lq+Htz0XNVZt/b9N/Dc0tPN/8UZzTPucsePTUu2/w9xFa0dNrR6+aptxGLdyimZmmPfEeHve7263b1drn0mr02opq7TRdjt8O/0fJaYot3v31u5b+aiYxPvy2tLVp5zy3uSqZznOJaywtjW9Pv8Awbs1VFyrVVxV7PSKaKYnL0HFu+bZoNr5Nbq7eloiPam7VmufhT+j852N3v2Ij1e76u1FPTFu9VGff0lo3K7ut1k3aKtTuN6uc9Oauqfzl5bxZVZk9HxrxNb33caZsUV2tFYj1eloufemPGur3z9Hjtwqoot13L1XLTHarOf7PTaThPiDVaadVqNJa2zTR09bq7nLMe6I7y17m17bpb0equ16m9T3v3IxGf8ATT2p+Pd6uPDRc9tz0KbLNfGNvd9xtTb9VRNWitV9Jz/2lXlOO0fm++8SW51fD02Is04iJ7d3wvZ9xr0Wps3LVdOKJ88T17vruwb7avxRNyuaqZjrHNEs829M18O9IG3amKa79NqJq0k55cd6Z+9/TpP9XhbVUXMXKOtFXWJ836b4x2PTa+atTopomZ6zRjpPxfF+IeFPs2tmrScmj1NUTVOmvVRFu7Oe9FXhPuleO7jLylFVVNHv8HZ7JvN/QXPVTHrdPXVmu3EdvfTntLq9XTXpL9en19qvSX/K7HT8pjpMOLn6U8tdNXTvFUTn+7rcbfpa+sbBunDup1FM17lRpLUVe1Gpp5cfGYzGXtN2444A2nRUxoNdc1d2mMVWtNb6Vz766sY+PV+fbeotUUxF6/btxV061Y/P3t7a9k3jeqpjbNDX9mjPPq79E2rER55nv+TPwZWky1HecZ8Z7rv1VVqm3Tte282PUWp9q58a+9U+6Hj9Vcm3E1TXHPR05I6xR8cfxO51Om2/bomzpNbVuOopiabusq6W6I8abVPh8esvN7jXRNNfLiIjtMO+HDMa558njqNffi5VVVMzMzPWYdXfmiKZ5euW1q645ZxPV1t6qesZezGPFlduC/OZy0rs9JbV2ejSuz3h2jm4a583BXMOStw1ukGFTjllVPVjLpBFpSZ6rSFUAYZAFSqIQiMo7NrbPxFXyfrDUbe2T/vFXyT9YWLHZANNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQCSooAAAAQEA5aezntd3BQ57XdisOfTN213aNjs3LblWm7Z6uz0k+1DrdN3dlpe8ONdY7/ap/fRh2mmpmMZ8p+rpNsuTTczDv7faifOHj5np423TnyZWqZ55WjtS5Lf3svFk9LtuGqIq1Xv5Zfb/AENUR/sjr6ZnFX2nM/DD4nwjirdoo86JfZfRFeiNu3LSR9/1kVTEvPm3p5vjankpuUzOf3v6vCb9HtvoHH1vHrqevS5l4Deus/k9PD9MZPJbl9+r4Oh1sPQ7hT7cuh1tL3YPLm6nUx7LrNRHWXb6in2XWX6esu+Ljk6+7TMuGuhuV09XFXb692tsaalVDDlnPZs1USx5Zy1tnTjpirLkpo9zKmmcua3QlrTGijt0bFujqUUdXPat5qS0kWzR7TsNPbifc4bVuO7e01ia6oxEw52tyNrR6fmmHodo0czcp9icVdMz0x73DtOhprmmO9Wfu+Mufer32C1OisXYrrq/zoiPux4Rl5uS216McWtuuqpuVeqt11eppmeTp1qmO8/Fp019I6zPm16q+eZ5vH3s7M4ntLm7Y4tq3MT/AAxme3un9XquB+Hb2vuUblcsVVxFyKNLRj/Nuds48odbwdsV3ftypsUZp09HW/c/lpnwj3y/SnBmy6HY9PTrtVZtxXaoi3pLeMRbj/n72MrrxcsW9o9uscJcGxopqn7TVTN3UVzPWu5Pj8I7PjfE24XNZrbl/nqmimJpojw+L1/pI4lrmurT27ma6utXXtH/ADfK9010zTVETMe12hcMXFx39XiZnnqz49XDb1ftz7VXbzdbe1GKpj3uO3qI5pnL0dGtvTafUziPaj83b4s7ht1zbtbTM6bURFNc09Zp6zy1x76Z6x+ceLx1jVZuxHg7zbNVHN36x1hzyx01Mnk9bZu6bU3dNqa4+0WLk273q+0zHaY91UYmJ97jqriK5nmjGe0eD1HF2h+1ae3u2ls8t/S2p9fyxmbtqnx+ajMfGmZ8njsRTXMeEduuYcxs+tpjx8Xe8D8RajhniWzr7Fyr1Nc003aM9KqfHo81mc9ZW37V7FWYpjrlnKLv1+kN90Ol11i3ve28ldrUU81cRHSMw+e7lp55pjER18Hd/s/cS2bs3uFN0nnpuxM6eqZ7T5NnjXaLm17lcs1TmJqnln3M4X+zKPCaizVTE4mcOsuZ6xPm7/VUTyzHm6TVUzTMzh6MHNhNWI6Sz092uivNE4nwlq80zHVYrx4tj0+yb3qdvuU3oqqqrpnpFNWJfTdq4/0eqs02tTesXcRiqjUW4nH5vhsXJ7ZlsaXUV04zVmI8J8HPPFqV9/0/EmyUVRds6Pb6au+aaWzqeOLU255blNOIxEUdHxDTblNPL7Udm7Z3KK8fvIj4uHS2+rX0DX8X365mLFFEzPjV3dRVrL1+uLl3UVV5nt4Q85Tqqp8ImPNs6a9mevRdaMXb1TM3cRMTnpjDxfpKv+r2vTaSZppi9d9ZNPjint+Wfo9PTemaoxTVNWe0eHvfNuNdfG4b3du01c1q3+5t+6mmcTP5zmUbt8dDXXNUZrmZ65nLtuE9ujet/wBv2yqc27+po9ZGP4Kfaq/tDqaoiZ5fCemPN9W9B3D1F+1f3eiaIv1RNFq5VTMxboj71XxqmYp/KWpdxzt2+ubtuMWNkmLdynFNOIiOnWejweo3GLcRFNyqrwq+LPifdPU3503PFUW4zn+bHSHkNZraZq5qa+tUZmM+KY4syadzOuqs189NyevhLbjdNBr9H6rXW4uTT0zE9YeNva3pHtf3dbqNZTTXnNUfCXWYNb09zZ0Gx2bsXbd/U1W5pmJoivlxPxhvabd9k2+zE6bbLXr4j/MvVc0/HMvllzctRRVVFF+umiZ7Zal/V1Xc+tuXKon3tzE7vpG68b6m5fmjS1zdq7TFMYpj82lf3mvUe3drpicdqezwVrVU0RiiaqYjt1c3+JzHerLVxtYub0mp11U1c0V56ubbN/nb9XTNUzyT3l5KrccznLir1/WOuZ95jjpJn6+008WW7uktVxTptTbmOWbd2mKo/v2a08X8NUV/vOF9HTcifC5Pd8Zu66aaoiiaqfhU17mqrqmeeuqqPikwde80+ybn6QNPVb9Tp9Pb01uP4LUYy8ruHEl3W1/emm3n7mfvPDRrIx2KdX174b6OeWcr2VrcZ/m5Y5usZ8HZbLvlelvert3piiKuaiY8Pc+fxq6v5pcsa6YxMVzzeceDNwYmWn1rcdbtu6Rbq3Cb1qqOvrLUxEz+U925s9rhjb6Y1lmrV6q7HtRN3FNMT59O747G56icZ1F3p/qSd11MRiL92mIn7tNWIhPjamb6TxdxXqdTem1annq7xE/ww8fqdwuTVVXVVz3J7zVLz9e4VRFUUTV7U5qqmfaq/Nw1anww6TDw7u5uayM+z0hxVavEd3S3dTj3OKdYdE7u/o18x0it2G2btf09+m9ZuzRcjtMPJ0a2P5XJb1s5+70T42pm+vbNxlT6qbetxamYxNNcc1qv348GzqrWw623F2vRxarn+LT14if6PkVGurmnGJn3TLe0u510xm1crt+6KsJ0q7n2+i29n4dmYmbusrjxoqudG/Z1GwbbTE6Xa6c0/wAVdfd83/xnUcuPtl2J9yUbnVVM1V3Jrq98p1rXaafR9y44mNP6vT6emjy5ejyOu3K9rLnPermZznGezob2vqrnM1R7sOL7Znx/usxycrHteHN6p0dyqLtymKZdxO66bW3eeeW5TTPWmau75dVrYmcRMSn263RFU4mc94iTrf2s8fYrG47DZomJps83lVMOl4v4t0UaSrQ7Tbj2/v1R4z7pfML+rsd5pmcx5uCdXRTVGKZj816Olz8eku6yJtU01VRNWOs+UtKvUURP3on3uluayqqrpUwjUT5r0cuzv7Wspt1RVTVGXdbNxLXodVReorjlmfbpjy83hp1GIz0lnb1c80ZiMJePbUyj7ztHFOl1dqifX0zE94mezir0ezbjXXXVXRTNczMxFWI/o+MbfrfVV1Tbqqpqj3/3d1a3vVU0Z9dT+cMzDS9n0KNg4eouTN2LNcRH3ZiPac9rijZNi0len2natNpbuPvWLcZmffL5nc3S7ezN7UVVfLOIa0aymMxTciM+c5WQ29Tq98ua7WVanU4pqnynLWo3C5TXFVN3kqjtMfq87Oq8eb8yNT483VLjtZlp9L4e36iZpprrxX4xPj8HeXbm366efUaej1nablPs1fn5vj1nW003Imqr+7f02+6u10p1M48p6ufVe8fQdx4X2DcZzVp9N80uPTcD8H6ajm1VnS1+6In/AJvFRxBq56ezP5JVvWouUzFV3l90QnWr2j6NYjhTYo9bt+0aG3dpj2a4txNX9XVbpxVr9dFVumuixb/09Zl4SvcKvWc01zV8XDd3GrM5q6S31pbHd6zXTMRETEzzZnm8XJt2/XdNXy81HqZnrGOryd/WTVHdx0auae84ydGJp9d2jiD95F21qaa6cYmmqXeam1sO4UU37mjt0Xpj2rlrNM/nh8Ss621TjPNGZ70y7XTb5qLMctrUTiO2Zc7jf06yx9LnhThXW49Zdpj2us1VS56/R7wbNqLtuvT3MeFVUPnNniTW45apt1R36w5auI9X6uqmLlFEz5Us5Y5aLY+h0cM8E6OzN2rSaeq5EdIiuMf0dPqt62PbZr/w7Q26a+0TGHz7U7tqruYvXOaJ8ujr7uvoimZpomZ8ereOP9pvx3vEXEeq3LU8+ouZop7W4npT+Tpa9Zzz4Osvarrntlq1ar23eYOe3eW78esz079Xptg4gq0lyImavUz0mn+V4CnUZ8cNixrJpj7/APZjPBqZafcdn4l0dWeSuiume0TPXLb3f/Z7d6KY12kprp7c0Ty1R8Hw23raomJpqjPnnDes8Qay1b5adROPCJ6uWPHY12fRNXwpw5fr9Xa19dNqI9iLkc00x5dXV3eAeC7UTc1dMazxxT7Ef2eOucUa7lmPXxGHW6ne9Zdpnm1c1Z8KJw7442pcnuLuo4J4Ymats4b0FV/+GapzVH51PJ8U8U7lvNE0anUU2tLnNOns+zTHx83nNXrKsTz0zP5ur1WqiYxE8vuy7TFwubZ1e4zETTmJiP4Y7Om1WpnGM/Fx39RFUT1aF+5E5bmOnLLJNRXE0zGWhVV3cly53alyuOrpI5WsbtXVqXqurkuVw1btWW8YzaxrlxVyymrDjmcw7SM7cdXdKln7yT3/ADbjSYWlPFlT2KlUFwiVFMEiELCQsFSq2tr/ABNXyfrDVbe1x/vFXX+CfrBCOyAaaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAASO7JjEssgztuaiZw4aHNQxWXPa6NnTzMz1lq256tmzmJ8HKjsLOcRMTLs9POMOrs55Ydjan2qYcq7YO40FURXT18er0ViYqi3M1ZjrHR5bST1+L0G31RVa6/wy83Ni7ceTuqI6M6Z6fFhbicROJxMM6Yz4dnz749cdxwtct2t80kzT7NczTVOe2Yfa/RBas29019q5Ec923mM+OHwSxeqszFVEe1ExVE+Ux1fV+D93ot7rte50Vcti5MU3J+PSY/q5O+L0vpH22zVXemimIiq3mPi+P7vRM2aK4jEzT1h+iONtLTqNHFdFEVTT3mI7w+EcQ6abWrvWeSYiicx8JdOPJjPF4XXUZqnMS6TX0S9TuFvly6HW2pl7uOvLnHQaiieXs6+9bmc9Hd3rU4no0rtucy7xwsdNXb9px12nZVWuvZx12vdhrbPV1s24809XDcqs9emUizOcYNs6a0Wow5LdptUWJ7YctFjHgbacFu3TFLns2oqnMY6S5LVmOflw7LS6TMR7GWLWpGvZ08zVE8vi7zatJXNVVddP7unrOejk0W3zVy9MdesT/6/u7i/TY2rS82ojOonrYsz1/79UeEeUeLjnnt1mGnBuGotbfo6OTpq7sZop/7On+aff5Q81FVdVWZmYmJz3cl+9XcvV3aqprrrq5q6p680uPm65nDlt1ckRExGWzodLe1evs6DS0U1378+xmelMeM1eUQ1rcXLlyizp7VV7UXZxbtU/eq9/w977N6JPRxXqtRTe11WLcxE669HevytUe7znxMpMfXTD/t6n0T8NWdDt1Nym3P2KzmqL1UYnUV+M/DybvHXFNvSaT1djFV+eluiJ6z7/ydtxlvFjadFVZtVUW6LUclFuOn5Phu+brc1d+5fu1z6yqfLtHk5THtdmVce8bhd1EzPNNyqqeaZmevM6PUX65j2p6+Lj1Wqqrqmqa+3Tp4ut1F/wAImf6vThHDKuS5dmbkxMwTdopmOrr670c0rTdy7aY7O3tXaYxMVTl2W3aqYqzMxEvN0Xpiejbs6ifGesM54Ljm93t+txVRVVXTTy5nM9Yjp16fCcPI8RbZXtm5VW7dM/Yr01V6auf4fO18aZ6fCW1turqqriYmOnTDvpt6Tc9Bc23WVVU2rluOSuOtVm5E5puR8M4mPGMvPrq69tvFRTGO05WIxJqdLqdBqLml1MTTeszyXYienNHeY84mMTEsKa8z0zn3sUdlsutu7dr7WssTXF61XFdMxOMY7vvWq11rjDhqzudmnmv2qIm55++H50iqrPNE9InOPN7b0a8Xf4JucabVVTOi1UxRXTn7sz0z8GLPW/t3u5aPkriqjPLjxef1lEdc9X0PizQW9NM3rExXZux08cPE67S1RRnGW5dM3F0VdERHSlxTGPBvXqKqektS78HWZMOKGducVMZjpnEuOmr2uuYUb9u5htWLvtRDQpmIw2bPWYZo7fT3Mz3b+nrxXEZ79nVabPg7rbo5uk+PZxrUbe4XqNBsWo13NFN2I9Xa5p71VdHyfWzRNfsxERTiPm83sePdzi5qLO2Wqo9Xpo5rlMfz1R+kfV46uZnmmInm5sxOO0+TLUNBoruu1tnR6WOa5fri3bn+WZ8/hnL75pLFjhvhm1p6cUR6rkjHTNFPj8ZnMvNehPhX7RX/AI1q6IiKomm1XMfdtx9+78f4Ydj6St2iq9Vpoqi3TGKp6dKaY+5T/RrHHa143ftynUamu92mqfDydBqNZOZ6+Ka/VVZq5o5ZznE+DqdTqYmO8RL0Y4OOVbl3W+EtK/qszLRv6iM9+rWq1Edcy6dXLLNvVarzcV7VZp6NGb9Diq1FE5zLUxZ7N37TKTqPHLra71MR0lxVamfB06m3a1amfCWPr5mO7qK9XFPjhPtkY+8nVNu1qv1Z82M6ifN1U6ufCU+057p1HbRqZjxJ1LqJvzPacJN6rH3mpidtO5jU9O59qr9zp4vzjuyjUxjqddnZ2/2que0xC06icxNUw6j7T5ZX7RMnTRt286jHZhVf6d3Vzqao7Q46tTVg0dnZV3/OXDN+PBofaJnvhjOomJ6YOqdnZU3Zc1u/VDqKdRPjLONT/qXR2d5TqZiXJGqx1y6CNVPnllGpz4prZ2egjV5/iWNTHfLoY1HvZxqJ8JWYnau9nUz4Sk6mXTU6mYWdVPmnVqZu1nUT5JOpx17S6idVVljVqJ8ZOp2dvVfirrOMuKq/Ge+XVVaj3sJ1GDqdnaTqKY6zKTqM9YqjDqJ1NXmxjU1RJ1Ts7inUTXGJnszi54ZdPGpqz4OSnVVdsmk7O7ov0xGa6sz5tmjVRyxiejzfr6s5y5qNX0OqzN386r3wfaPg6KjVuT7V0zlnq12d39pmY7n2ie8S6WNWfa5Opt3P2iqe8wzjVY71Q6SNXMdp/qy+2TjrMJcFmTvqNZ1jNUsp1lXNMROXQxq56YnrCzqqu8TKdEuTvZ1dXi47mrmYjq6SdXVjxT7VUvVOzt51Uz4pGp85dTOoz3ki/H8x1JXe2dTOe7YjU9HQW9RFPXmy5Y1nRm4NTJ3Xr+ufFy/afZxl0NOqqz3ZVaqrHdOqzN2t7VY8Wvd1cxHR1tWoqmc5hw3dRVjwaxxW5t25qq/FxVamfFo1X8x3cc3J82rix2dnRqeuHNRqJiHS+umJ+8yjUzCdTbu/tOIzC/a58odL9r8Mn2vp3WYnZ2tzVdJ6Q0r2oqz7MYj3NSvVZiergr1SyaOznv36sdZlpXb85x3YX9VE5y0L2pxPSG9OVrmu1zmZ6Q1rtyJz1cVd7m8JiZa92536tSM2s7tdPL07taupjVW4qq4dJGdpclwVyyuVOGaurrJpnKlTCvpHRlMuOqcqzITJDFYht0Se60J4sqAqnXzWAY2guDDAsKi5Eqtra/xFXyz9YamW3tc51NXyfrCwjsgGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABQABJ6HgoAkqDkoclMzhxR2ckSxWdue22bfZq0T0y2Lc9HPOLPXYaer2Iz3b1qqXW2KoieretVOdbldtpKpzGZd1t9dURNPhPZ53T3OsdXcaa/ERDjl66YvV6WuarUUzE9O0ufpmY64dXoL/WmYq8ImY8vc7TnpnE0z0ns8GeD14ZsubETicPVcF66KvWbVdiI5o9baz39+Hk4jE+/wAnPau127tuqzVNu9annoq/9eDz3Dbvjk/T/Bu7Ub1wz6q5VTN6zT6qvxn3S+Z+kXQzbv8ArOXE83JOI7x5uv4L4js6XWU7hR62miaoo1VuJxETP8UPe8VaLT7lopv2qpuUTHWe/SY6S447xpcq+Iblp5mMYzl0es08xnvh7vdNHNFdVmKMV0efjHm8/uOk/dTy49724cjnnNvHai1OJ6uvvW8eL0t/S9ZjDrr+m6z0emZvNp0Fdv2nHctfF29eniJ7OG7ajydJWdOq9VV5ynqsT3dnFiPcldjr0j+y7TTSotz06w5abU+Dao09cziIbmm0We8zli5LMWjYsZqjNM5eh2rb+frVR0856RGOvVnodviqYppiekxnFOZnPhEebstx1VvZ4nT26qLut8aO9Fjy5vOryjw8XLLPbpMTWXtPtVizcqnOorjms2JjtGfv1+7yjxeY3HUVX7tVd6aq665zVM1ZnKXr925fru3LlV2u5PNXVV3mXHNGczM0zzd47y57dXBM9Zme3k5NLRcu6mjT2bVVy/c6UW8d/fPlDc0mg1Orv0afS2fWX6ozVnpTTT51eUQ+zein0b267M7jq64t2Zn29VcjFV2fGKI/lWaiXx1Poc9H1eq1VzXamKuS1P8AvGoxjM/yUe59V4p37RcO7LTa0vJbimPZinu4eJ9427hzZ40u3VclqiJxRTOJqn/m+IcS7xqtz1Nd+/dmObrFGelLPXvfU7OTiPiLVbrfm9dq545ulM9o+PveX1+un1lVNH95YajUzRM805mXU6nUc12Zno9GOH9M3JzX9VmcNK7dmeuXDduxOWtcudPvOvXTltsVXeqU3erSquf6mMXsT3XTO3a0Xfe2rVfV09u/0blu/wBjSyu9267FN6Jej0N+JxNNXXP9v+bx2nv4xOcS73a9RTiImrE+DlnjtqZPSb7obe67HGtsU/79orfaO9+xT3j5qO/weHrmjpNMxPj8Ye62bWfZ9XZ1FiKZrt1xMRPafOPhjOXS8b7Rp9Fqqdw2ymv/AAvW3Z+zxHbT19eezVPunrTPjEx5OMxdZlt0EVR4xH5LbxNc4iMzHj4OCrpMz72VEzGMTjrnLEjUuq+wcDb5/jWw17Lfqoq1enpxbz3rp/5uHU2K6Iqt1RMTE4xMdXzPbddq9u3CzrdJXVTdtTmMeL7PparPEOw29303JOomea/bp70++XK+V13uPF6zT1Zno6y9anM+D1+s0s5nMRnxdPqdJPWeWHSZOenRTbnOM5cdVERW7SvTzEx0cc2c19sN7YyjTiicx1ht6enrGZcsaaapzDkt2KubGGbUkbWkiM4b2v3Kxs22Vau7Vbqrqnk09HjcrmO/wp7y4dLbsaPR3ddrb0WtPajNVcRnP+mI8ap8Hz/jDd53Pc4v1c9mmKeSxb7xap8pnznxZ67dJGeovzdvV3apm5VXMzNXnPjLs+ENnu7zu9Omo5otRGbtWOlNPi6XYNNqtdqPsumoruX6sRFNPk/QXAWw6PhzYaNdqsTRTOZpq+9qr0dqfkpnuswavjv9wv6HhjhijSUVU0VTapqvRT/Lj2aY/X4vim+7jN+7duXq4ruXapqrx290flGHc8eb/c3DcK/3vNRTM1VTHaurx/KHg9yv5zOYy644sXJpa/URnGcun1GomKphya69mc5dVfvzzS9GOLhlk5NRe8pa1Wqz0cN2937NWu5E5b6uVrcm9ER3cNy9HeGrVexDgruzPeV6s9m5VfjHZwXL84x1a1VzHi46rnTu1InZzzdn3yetnylpzemPFPX+bXU7N6L8+Sxdjxho+uhxzdnP3jqdnZTd8uiTenHd18Xav5l9bPjK6S1u+u6d5T10z4y1Ju9OjCb1Xgmkb9N6af4mUX5n+N13rapPWzHkaa27OL+f4kq1GHXes+DCq7V2OqWuyqvZ8WFV33ut9ZVPjgi5Vn7y9Edl67C+u6Q66K/eziuPM6jsKb0Qy9dloRdilfWxPinUdhF7Hmypv58cOt9dMdpyRfnxNLt2nrYmOtR62I8XWxez4k3vJLF27Gb+P4mFWonPd183uqTdysiWt2rUTjux+0Z82jN2ISbseUnVG76/3kX+veGl6yY7U/mtNyc/dNG296+Z8mdN6qHXzdnyKb1Ro3t2PrZ82X2iYh1vrmVN46rK7Gi/OesuSL7rfWxHY9dPmlxXs7WL8T2PtE9uWHWU3MdqmfP45NHZ2E6iqI7R/UjUVTHWcOv58dcr633ppLk7GL/+rLL7ViMZdbF/qk3zSzJ2f2nqy+0e51dN7MsvWT5pYsydj6+PIi/Hk6/nnzWK+vdNL2dnN+cdEjUV+brpuzHjk9cshcnafaZx1qPtE+bq5uZWL80x2Lind2fr58ZlhVe+LR+0dEm+kx0vZtVXZnLjqvTHTq15vdO7CbvXuaTbZ9fiesyzjUZjDQrude7Cq5MT0qWQ27Cq/MsY1GO7Qm/jxYzfWYm3YVX4lxV3ons0pvzMYYV3Zp7S1MS1s3rs+TXrude0OOq7mHBcrnPdZGa5bl2PJrXK5laq4lxV1eTUxZSuucuOqrDGquc4YzMusjNqVVTLHxWZYzPdqRPtKu7GVmWNXgsjcmhcomFVcTLKmOq0x7K0iUUBkAYBMrACdW3tOftNXyT9Yarb2r8RV8k/WFhHZgNKAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAAACeKgziYZQ46WWfezpixzUT1bVqWlTLnt1ueUXGN63V1hvWpdbbq9qJbdu5Oe7m07TT1dYdlYudO7prNWIhu2LkuNjpjXotHdxFPfLvNFdzMRNXxjy97ymkv4mInrDutHfzVGZxE9vi4Z4+O2GWnoaacx0mJn3OSmnt1/Nq6WZ6TR7WenTw9+G/RaqntTNUe7s8lx1XpxybWjvzYmKrecZiLlH80Pq/o936zqdF/h2oiu5p59mmumnNVqfKqPL3vj8zMVdZx4dG/s+46zbtVb1Oiv12L9M5pqonv7pjxhwzxdJX1jizhaa4qu2LlM1U9YqjvHu9755uOiuU3avWWqqasYqox1j3/B9F4Z9I+36+3b0e/WY0l6YxN6in93VPvjwb++8O2dy0s6rQ3Ld6jvTXbnOHOZ2VbNvid/RVZno6/UaTr2e73XZNXppqqqtTVRH8dMdHRajSTMTVy5j3PVx8srhcXkb2k69nBXo4nu9Rd0NVVWIpcNegqxM8k9Pc9PaM9Xm40Oe0M7ejimc1W5nw6O/t6KuZzGMR3jxb2n2q5MTeuclizR967enlo/KfFi5nV56ztvNyzFHecZ8vfLe0+z509eqruU2rFE+3du4pt0/n4z7odrf3badJamjb7E627HSq5ciabX5R3q/s85umo1WtvRe1l6apzPJTMYoo+WntDHyVroz1W60aan1O11V0UxmKtRVHLcrj/R/LHv7uiuTTV1iZnPu/u5tZTNdMU00z07z4R+bj0Vi7raqbGisV6q/OYmaMxbpj31doPtWpVnPtximfOejveGuH9bu1U3LERp9JmKfXV0zmrziinvMvYcDejDX7pft112atZVTOZzHLp7X5/xS+ybZtWwcKxF65jVa23Tnmqj2KPhBqfpO0jqOBPRhpdDt9q9udH2XRRi5VRcnN2/76p8vc2uP+MNt2uiLOjmmuaaeW1ap6RR8HlOOuPtXqKq7Ggv9apmPWc3s0fDzfK911tyu9NdzUV3blXWquqe644bZuW3Z73vut3HUV39VcpnrmKaZ7PM63XRP8WZmXBq9RzT0nt/d1Wpv81XNDvhixcnLf1M1TM1dWjfvzVOfFw3b/SWpcuS7Yxzyyct69MT0a9d6rDiuXJa9yurHSYbkcrk55uzM94T1mJzlqTcnxPWZ8GtM9nY27vTLctXY9nMumt1zju2rVU9OucJcWpk72zd9qPJ2Wk1M0VxPV56xd6Q7Cxd97ncW5XsNv1sxXmJqjt4vVbZd0es0N/bNxuTTt2riKbtUd7NURPJdj30z/WJmHznR3piend3236iuiqKontiYp8M57uGU9dca0d42zVbZuFzQ66iIvxMclVP3LlHhcpnxif7NKaeuOWY8X0jb42zftro2fc7vqZtVVTodXFOatNVV4T50TPePDvDx/EOza7YtxnRbhaii5V1oqjrRep/npq8Yc8pr6dI6umZp7VY6d5dzwnxJq+HNyp11ufWWao5NRamfZu0eP5ulvRyRnMTns4+aeSI5cw41rt7p98nTaPddot73tdybukvRnEd6J8qvKXRanTTEzE94nq8NwVxbreHrtz1UzVpbnS/Zq60Vx+k+99B23dto36iK9BqKKLkz1tXKoiY90T4larqbulmZcf2TE5l6i5su4c3s6G/X16TTTmGN3ZdVbp9ZqKaNJbjvVfrimI/uzckkecjTxHtRn4RDYo0dGm0le4bhdp02io+9cnvXPhTRHjV7jdOI+G9jt1Tau/4zro+7aszizTP+urx+EPAb/wAQ7lvOujVa69Fc0dLduiMUWY8qaf17szJrTc4n3W5rbvrL0xp9NR002liczR/qqx3qn+zylmi7rtbTbs2Zm7dq5YtUe18G9pNv1+8bhTZ0Vmuu9c/hjt8Znwh9i9HvBOh2HRV63WXLMXaYzf1df3LX+mjzn4O2Oe11px+jLhGxs+ku6rVXIp1PL/vd7wsUf9nT511ds+DPjTiqvU4sW6KbUUU+rt247W6Y/XzXjLiixFH+H7Ti3prf+XEx1mfGqrzmXzfctVVNybk1zMz4zPX83TH2sZZeGu1VXLM1YqnMxl0Ot1M4mGer1PTv4un1eonM9XbHFwubi1Vyaqu7r9RPiuouVc3dpX7k5xl3kcssmF+ufNrV3ZjPVjeuTmYiWrduYju6SOVctd2Z8XDXcnHdxes6d3HVV7116jkquzHjLGq517uCuphNUy31LdNma58JYTXVnu4ZqnxljNU+ErpnbZ5p8ZYzd6tfmqJqnxXqbc/rcSyi5EtXmhec6rtszcjzT1nva3PMk1SnU22PW9e6zd6d2rzSsVL1NtiL+PDuy9bHdq85Nf5HVNuequJlIra8VLzfFdG2zz+89ZPm1uafNlFRpZWzF3Ed19ZGPe1czlYqnPdNLa2vWREJF73tfOfFjM48Tqxtt03ZntK88xnq0ornPSViurzNLK2/WecsfWe9rTVPmnNPmdTs2puT4VJ6+qejWzPmZnMdTr6XJsRcqWK583BmfMyvRjbYi5V5rNyprxPuWOqdWpWxFyqfJnTciI692nM1fzLzdPvJcV23ouUk3KfNo83vXM+E4Tqu25E+9Yrx3qakVT3momqe81ZOo3aLmf4mUV+9oU1zE92XrKvODRtvc0z/ABHPHjLR9ZX5r62rPVNDeiuJ6ZZRVHm6+bs+/wDoeumPM6q7HnjzT1kebR9bOO5FyfNOo3aruO0sJvVZ+9LV5s+KTVjxOo2vW1fzSzi9PbLS9ZC8/TOTQ3ZuzjuRdnzaU3M+KRWdRvTc97Cb0w1Kq2M1z4SdRuTe+LiqvS1+efNjVVPmvU25/WZnuk3fe1ZqnPdJqnzWRjs2pu9O7H1rWmZx3TPvamKdmzNyZcdVUuPPRJqg6t72ymr3saqvewqqY83fq31RZnqxmWMymVkNLM9WMkyixZFyVIZVQADM+bKiWMMqe4lZgDBAQMVFgIWAMR5Nra/xFXyz9YazZ2v8RV8s/WCNR2QDagAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAAkKAkKAZI7hHcGdM9XNRLgp+85qcMVG3aqhsUVYnu0bdceTnt1Q5WDsrVyejbs3Il1dqrs27FWJc7G3b6W5irrLt9JqYmYp7R73QWauuW5YvctUREueeLeF19vW6HcLlqqmaK485x4PSbXqtPf5KblzkmZ+/HSYn3x5Pn1nVYqh3W26uM57uGeDvhm9rqNNVapi7m3etVR9+3VzUTPw70yxtW4qjNOJnPfPZobXu1zTxHq8U0x1mfP4vW7FHC+64o19yds1dfSi9ZqxTVPvifZ+jy5cbrMnUXYiImKa4bmy79u+1XJnQ6+5YzHSInNPwmHqL3o93e57e07pt24U4zFNcerq/r2dBuXCHFeimftHD2qn/Xp8Vw43idZlHe2vSZqIiijetn0msqmOtyzPJV/Ro7jxHwprrs3rm1blp6qu8WppxLyup2jfKc1Xdk3KaafH1MzhoXI1FMctWm1lGPCbUxhzw47Ftxegu7vw7FeaNJukx/qmIYRv+zxzTZ2e9cnHszdv4j+kOitUXruKbek1Vc++mWdjbt3u3eW3tl2mfOaZenHDKudsdjf4i1tdMRpdLodLiOk0W+aqPzl1Gr1Op1Nym5fu1Xa4j2qq6sxH5dneaLg3ibW1xFrS8kz06W5ql6LQ+iHfdVNudXZ1Exnr62uLdEtXCxnvHzG9qtNaxnU0zXPTERmqZ+DZ0W37tuOZ0mguRan/rtTPJR8evWX3bZvRbsG36abm4bho9Nf8bentxcqj/vT4vQaTQcBbTYru1U0aiuI+9qK84n3QTG6a7x8Z4S9FGt327Hro+1TmJzXV6qxEefnU+qbVwXw3w1RRTulydZdtz0sWqOSxR+Ud/zdZv8A6RNh0VEU6S56y5R0t0WPo+d8T+kDeN0uVUU50lGZ7TmufixMcsvtnb6vxH6Q9Htukr0tmLVFER+7tWcRMe7EPkXE3Fut3WaqaqvVWp7UUz1n4y8ld13Ncmar0zVPeqesz+bR1mtiZmOeXbDi0xlpua3XzNGJuRPTvh0t/VRNU5nMy4NTq5nLr71+Inmz2h3xxcrk2r+pomJiOjrb12c4iqHDXfmqJme7Tu3urrji53JzXLsxExlq3LtXXq467vectW5cmZzzNzFjs2K7kuC5PWfalxzcnHdx1XIdNMuXm96xXnpzNea4Y01xlWa36K5iMZc9m51zl19NxyU3PeNYu4s3YzGJb1i9GO7oLV2Yx1blq7iY9pyyjcek097pmJdppdVOY9qXmdPqMRiHYaa/VGHGz10lex27VTTXFdFcxy9cPfcNbntnEGkq2PiKxF7S1RPqqpn95aq86Ku9M/2l8j0Wqqjm/J2un11VF3Hv6dXPLF1xyd9xpwFvWzxXrNJP+KbXTHs6i3T7VqPKunz98dHjqeszERn6vpnC3H2u265RTqLvrbEezNyunm5afGKo/ih6rWcNcCcZUfbLdNO26q5Tzev01WLVc+ePB589x1klfELFuYp5o5omZxMua3Rat0RzWusTnNPSZl9M13oh3eixTXtuv0+vopnMzRVHNHXxjxdPf9G/FlFyaaturq98UyzvbVdBpt+3rT0zTp911duiP4KL1XT+7p903DVaq5z6q9rblU/9pmqJe4s+jriarEfYbtE+OKJd9tHog3K7NN7X1TYo/wDeXP0WYMzJ8k0s6m/TV6nTTmPLpn8nqeH+Dtw3GKK79i7Tz9opp6z8Z8H13RcEcN7Viu/q7Vdyn+GmMtTirinb9u0FWi0tyiqqYxTRbmIq/rBcGu7S2PbNs4b01Vu9FE3MdbVE9/ml0nFXFlWsmNPauW6ot9KYpjFu3Hujz97y247vrNXTi5VFu1HemJ9qXUanU00xmIxGOmG8MNM3Ntay/M81UXKpme/NPV0G4aqf5smr1k45s1Tl1GsvZnmxLvji4ZZLe1HNEw6/UXs9C7exM9Wlfvw6zFyq3rseUtG7djMzPRNRfzPScNG9czMxno64xzZXbvWZhrXa89pK6v6OCuqOrpIi+siIwwquOGqevdjMukxZtclVeY7sYrywnCZamLNrOqrqx5pYVSkTBpdOXmJlx80HNBo05IqXmcXN5JNRo05Zqg5ocOViV0ack1eSczjmTJo05YqYzVnxYZMml6s4lZqnzYRJk0mmcVSc0+bDJk0OSK5815/e4oxK9fA0OWap80zLj9oiZ8TSWOTJlhlJqTSacmUmWEVpNUeRpdOSJXLiiqPgsTnxNL1cs3IhOfLjwT2U05aa+vSVmufNwxOFz7yw05OefNJqnPdx595MpoZzXMMouVT4uLOIXm6GhzxXPaZXna8VdSapNLK2OY5ujXiqcrzSliObmSbnXvLi5kqq6khuuaLn+qV9b/qlwc3UirzXS7rY558JWK5x3a/P4ZXn6d0uLTY5+ndJq85cPP5STVKdUtrmiuMrNXlLXmUmrp3OqW1zc8/zHrMeLgykysxJWx6ye+T1kuCmrouTSub1k+bGa/e48pKzFmuTnTLDOJSajTOtuSaky48+8iffBpZi5Jq6MObr3MsavFZFJmcmWKT3WNsplAUAAEVJAhUhQZR2KSMYWnxSpVjsdSFGABKVlSsJSqIuGztn4ir5f1hreDZ2z/Pq+X9YIsdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAAAmVTCgLShkGdOMs6ZcUMss1muamXPbqhqxLltywztu0T5Nm1XMd2jRW56a8x06M1vbsrd2qI7uexdxOZl1dqrr1bdFcRDlY3HcWrtPSYdppb0REYnDzmnude7sdPfinHXLnY6Y16nTanrDuNDqqeSYnlqz3ie0vH27/AGmHY6HU8vtTLjcHSZPZ6Lc9TpcRpdfq9JEfw27k4/o9RsnpB4n0GItbjOotx3i5PX+75pb1sT1z+Tnta7EY5oZvHtvs+77b6Y4pm3TuG31xVPeeSOWf6NjUek3hjUXJ9fpNJTnwn/5Pg1Otpp7XMe6HLG4RPTFFXxYvE12fedDx7wnNymbek0cT5xMT+ja1HpG2SxTm1OktT50xEz9HwCnXU46U0ZYVa+Y/hpj8oXGWMvs+u9LWks5qtauKqonpFqzMy6HdPSlrdZTzRZ1dc46TX7MPlt7cq47Rlq16uuZ9qqcd8Zb1az9Pc6/jHd9ZifXUaarzjrM/m6PU6/UamqftF+7XMeNVcvP1ayYiZie09nDe19XPM9pyswXs7W9copqxHaIaeo1FMZimrDrbuqmrrzdZ97Wr1ER1rrg6M9m1fvdc5al6/Ez1lwXdTRMTiqJaF+97XSW+rNrn1N7vhoXLsVd3Hdvd/NrXLvR0kc7XNcuREzHVq13I65cdd2evVr11z8W9ObOurPi4q6oYV1uGuv3tSDkquRHRxzXHg4a6urGamtM2ufMGYy4YqnHcmpZGd7bEVxDkory04qlyUVYXquPjft19urbtVxmMust19nPRdxLnlG9u4s3YzEOwtXZ6dXQ2b2Jjzbtm9VzR1c7G5Xf6W/y9Kp8XYW9RnOZdBau5iJy2rV+evVzuLpK9FpdVVmPbxDt9JrZ0eoo1Fm9VamfvTbnGZ98eLyFrUYmOrdt6yZjHSZ83LLDbeOdj6Nt3HO7WL0RVVbqp7c1uqaKsO9p9I+ts0+zrdxo+FyZfJbepiY9ucy5betqomO0x72Pia77fU6/SbufJMRrdyufGqYaGq9IG736fZmqMf9tVl8/q1nPMz5terUzTPSZw10Ts9RuHEm6auZ9ZrKuWe9NHSHUzqLcZqnPNPefGXT16zE4mqYcNespxPtTMtdDu7a/qKZ7S63VarvHM1K9XMR0aF/VZmctddJcm1e1Ez07w6/WX5xj3uK5fnPsz0aequTMZy3jHO5MtRdiIy0rl2Jju4797mzT2atdzEd3SYudrO9XDVrqjK3K8x3a9dTpIxtnVV0cFc9Uqr97jmp0mKWkzDGZSZYz3b0mtrzEzDGCZaWRKpQBoAAiQSQUSFAI7gDLEZXEeTDPmsyCziGOQAyZAFiZg5pYyoMsz5pFU+aALMzKAC9EzGQBTOPFiYBlzT5mZ80AMz5mZ8wAzPmZnzAFzPmmZAFiejLLGOyTIaZZJliBplljMznuAGZMz5gBmfNZlAFiZyy5mADkiYx1Y1+5jmTIGZMyALmfM5p80AZc3ROZANLkmUAXMLmPBiAuUyAAAAAAAAAAAM6YjlEiehE5SiwBhGGQLEFSkMmK5RFbW2f59Xy/rDUy29s/EVfJP1gn2sdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAmVYsgAABJUF6L+TEBnEuSiXDlnRVDNjNjYpnq5qKp82nRX7Tmpr692LEbdNc+Eue1cq8WnRXGXPbrjDnY237VzE9JbVq9Ed5dZRW5qLnvYsald1b1M+EtzS6nHSZdHZue9t2r0UxjOXOxuZO8o1HXLmp1XTpDpI1MRDkt6mE007unUzHerDkjU5/i/s6anU0uSnU0+9n0ldzGpj+aUq1ET/FLq6dVTjxSdTBpezfqvRGZy469RGO7r69T0nq4Lt+fCWupcnZVajpPtQ4q9R73W1X5w4q9TCs7djXqYjxj+jXu34mc5aVWo6OKu/jqG21cvTjwat27MTnLguXs/m4a68zjLWmK5bt3m6NWq51xMsbtXWergqqx1y3Im2ddeY6y4qq/ewm5Hg4q6ustyMuSqvo4qq89GMz0cdVTUiVnM9e6TLDPRMt9WGeTmcc1e8io0mnLTLOJcUVRheaEGzbr6Q5qa4jwy06Koc1uuM4Suk+m5ROZictyzcxPd19FcR8HLTchysXbtrd6nEYnDZtXo8JdPavREREtmi95SxY1K7i3e97Yt35/mdLRqIjxbFF+PNjTUyd1Rfqx0qZ036/GXUW9REQ5ftUGm9uynUT5ld3MZmuXWTqGNWpnGE0bdhXejzmXBXqIju0Jv5qzM4cV2/Ge6yM2t2vVYy07l+Zmcz0at2/Ez3cNV2Z7TC9Wbk2bt6PCWtdu5ju4qrnnLhrrjDcxY+2N2vEuCuvotyvplwV1dHSRCuvDiqqyVVQwmYb6sX7SphM4nDKZYTPVuEmyZTuxqRp0Z497EAAAAAAAAABJIBQAAAAAAAAAAAAASFAAAAAAAAAAAAAAAAAASQCSFAAAAAAAAAAAAAAAAAAARQAAAAAZUMWVBUrLEE91RhlYVDIlZRhEzCwIYbm2R/vFXX+CfrDTbe1/iavk/WFix2QDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoACYMqmAMqmFAABJViyAI6B0BlDkpmcuPLKKoZ0zfXNTVhzW6+jWiWdNWGE7Nymr3uaipo0V+9z0VMWNRu0V48Wxauzh19NbkpuzHZz0rf8AX+Dkt3583Xes692dN6Y7QdWuzsPtXXGf7OWjUVT4uuovdXLTdWxduxi9OO7Gb8+bS9bP5MZuR5ufptuVX569XDcvT5tabkz2cVdyc+TUTs2ar3vYV3fe1aq583HVXPm11TbYqvT5sJuz5teapYzUdTbYquzj7ziqrmfFxVVcssKrkzPdqYM9mddyfNw1VTPixqq97jmvq6dUtZVVMJqY1SxmWtJtlNU47se6RiUzjsujS1Mckz0RprSrHdjlYlFZLDDmWKuiaZ05InEuSmfFwxOZyziU0srnprnzc1FbUpmcw5YlmxW3RXDmpudOktGmZ83JTVjxc9DeouY8XLF7r4uui7EMqb/U6Dtabs4zEr66fN1fr581i9nxTqvZ2nr6vNhVqKv5nXxcmfFlzTjuzpdtuq/73DdvTHWOrXqrnLHnx1n+hIlclV+ZnMsKruXFXXEuOqvPi3pHLVc97Ca+jhqq97Cap82pE25a6pw4ap80qqlx1VS3In7WqWPMkywz1a0WM5lhKzMI01BJUBPAhQAAAAAAAAAAAAAAAAAAAAASVAAAAAAASVAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAASO6gAAAAAAAyoYrbSlZ5TK+DHKMMwCgsIsd0Sja2v8TV8n6w1W1tf4mr5P1hYR2YDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoAAkqAAACZUEwoAAALgXKIyiplTLiZIlxckVOaivHeWvHmsVQnUjbi5BFz3tf8zmiGOrVbdNzPi5Yr97Sor7ORnrU226Lk57uSLnvaNNcxLkivodTba9bOMZY1XOvdrc3vSa00dmz6z3pXcz4taa+vdeeDqrkmqc92NVU5cc19UqqyuhyTU46q8T3Y1VOK5X1akZcldeZYVVx4OOauiZbSs5qY5Y5JkNLOMMFmejBVkJnEiK00CSQAonUFE6r1BaZ8GUSwhlCMs6apclNXm4oMou3Pz9WXP07tbmZRUlxTbnirz7M6a6Ya3N1XLK7bXPThYrp8OjU5vOViqPNNG25Fz3r6yY6ZakTELNZ0TbnruTnuxi7iXDNSc0L1WVnXdnyYTWwmphMrMVck1MZn3sIkjqumbF5ssJlZYy3CGQSe40oAAAAYAAAAABYhJAAAAAEhQAABJUAAAAAAAAAAAAAAAAAAASV6gBgAAAAAAAE8VAEkjIKAAB4AHgYURE8WUpMYkUAAE6nUFAAABPioAAAAALbRlRAVZ7JDKYSlGYs9lRWUpC+KR3WO4lG3tf4mr5P1hqNravxNXyfrCwjswGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groBJUUAAAAABMKAAAAAGQAWGURVPaDkmJmIx0d9wfwxuvEmv+xbbpa7tU4zXnlot++qZZtkm6sm3R+GMJEdO2fg+9WPRPwpw1oLet424km1VVHSzp+kVe6Ok1VfHo665qfQbT/utGh36qI6evouTmffia/0YnJL9RZhp8W68+M4g6xVjr17Th9kvejbhTiKxN3gbiy3qLuczotdRy3Y92YjP1dV6SuArHCXC2z3rkzXuF27XTqblFUzR2zEREnyTfVel1t83imqIjM9Y7xhzU265p5p6R7/Pye29G/DvC+86qzHEXEVemqu3Yop01u1M1VT76+1MS+v+kng/hbZfRjuUbdsumsV2qKcXpp5rueaO9Xdzz58cbMdJOK2bfmSaqs91zXjpPT3wuopxcq8IzPR7P0McNaTiXi+3pNw00X9FatVXb9PNNMzERiOse/DdymM2xMd3TxXNX7OZ79esYWKuk5mMx732f0y7ZwBwvtn2Hbdkt07xqKMRPra59RRn70xM9Znw/q+J3Kp5ulXRcL2m1yx1XJ1nrllTPTq4Ir6suacNdWNuScZ6MJrxVjwY83QoiJqz4M6VyVRFUfe5ejgnPi+//s/8N8Ma/hq/rNdpdJr9dN6qm7buxFc27eI5ek9o75l8y9Me37NtnHGr0mx+rjRxFNUU25zTRVMe1TE+6WcOSXLq6dJJt4uJMsWURMu7JlJlJ7nUAMLFMggswkxMAigARGWVNM1RmG7tO163c9bb0eh09y/fuTim3RHWff8AA3JN01a04omf/mvJMU/dmX2/h/0Q7ftu0/b+NN+t6C30mbdqYjGevWqYmZn3RDkv6z0GaOJ09vTbzreT2artN2qnPv8AvR9HL5Zfpvrr7fDYtTPWekFVE0xnHT4vt9jhL0V8W6n1HDnEOr2zXXIiLVnVxzRVV5de8/CphvPoqscPcAb5uW6129RrrNVurTVWqpimm3FdEVdJ/imJnpPZLyyXVJhubfE4pln6uIomua4xHhPj8HLVRTF2qMTGJxHXyfpngnhDgm9wBpLt3Rbfd09/SU3NVq68VVU1THt+33pmJzGOnZcuSY/pMcZX5dqjlqx5MZnq293tWbO56i1p6pqs03Ji3V5056S1J7uku4zrSxLOJcU9smZNDkmoz4pTEzPUq6QjJzT5nNPmxmRo0s1SnNPmixGSmljJMMqYYzMeTLSfBacz0iMp37NrQaeb2potxTzTVOMFups04JommcVRMThjNPXExh+lt39HvAHC/C1G479tnNXprFHr6vXVxXdvTEezTGcZmcxiO3d+c9zv2L+vv3dPpqdNZruTVbtUzM8lOekZnv8AFnjz7rlh1adeM9EWoxl0RAmMABHeIHY8Oxtk7tZ/xiNRVouvrIsVRTXPScYmenfBvQ0IxjtKxTEz4vuHAvBHo74s0ldW363e7V21Ga7N2qjmiPPMRiYdrvPot9HWy2rd3dt73HS03JxTNU5z/Shwy/IwmWnWcWWU2/PcWpntEpVRjvMPvu2ejj0a7zVOn2jinU3L9WYpomqKapx5RVTGXluO/RDu2z6a9rNquxueltZmumKOS7REeOPH8lnPjvV8T46+VzTC0UZpmqIzicY82zo9PTdvUW7t+izTVXFNVdUTMUR5z7n3j0Z8AcC6rT1arT6yN9v2YiLk3bc0UU1T4xRPh8V5eWcc7VMcez8/V0csR26sKol9J9P+36PbuMKbGh0tnTWqdLbnktURTHWZ8IfN+/SO7WGXabjNmrpjEOW3YqrmmImOvvZ2LFVyqKYxMzMRGfN+jNh4H4F2PgLSbrxTtNNd6nTRe1Fdd2uJmqrrTTEROM4mIZ5OXppZja/NtdM0TiYxLF23Fuo0Oq3y/e23RUaLS1VfurFNU1RRT4Rmes/83UukZAwRCh4GJXlmezOmmZ6cspscePNyU2805cut0mo0d+bGps12rlP3qa4xMeP6rpYiq7TRMzETPXHkW6g4ZtzMefux1YTHTo/UFvg3gSrgS5VTotJVpY0VV2NfGJriuKJmJ5vCc+D806+iijU1+qiYtTPs5xnDHHyXP9NWaagswkw6MgJIKJGVwAAABiQATqCiKAB4wDKKfdM/AmPc2tumzGpojUVV02uaIqmjvjMZx+WX17gPhX0Z8WXvsmn1e/afWzFU027ldHLXjviYju58nJMJutY43K6fF+n/AKk6S/Q+/eingDZNFOt3Ldt209iKop55qies+GIp9zz8cO+h2J68T7tPX+Sf/wCRnH8jHKeRu8Vj4xFOfA5er7louFfQ5qLtNqjindaaqpxE10zTT+czR0dH6ZuAtl4U0W3azaNTqtRZ1M1RXN2umqOkZiYmPOFnLu60xcLHymunlYs62DqyAsUzMZBBlRbrqqimKczPZzavSXtNcm3ftV2q4iJmmqMTiYzE/wBJBrsqMeLHDktR1jEZnPYEmnriYnr5JVRMT2mPjD7h6HPR9sW7cLXt54g0tV+Kr1VNr97VRTFFERzVTiY6Zmf6PnvpJ1HDFzfJ03DGhp02h08TRF2blVc36vGrrPSPL/z6c8eTtdRrWo8f1WI6MoonOZ6tnTaLUaii5VZs1XItUTcr5fCmJiJmfd1x8Zb2y1Y7sppnOPGe0E04r5Zjt3e89Ce0bHu3FtqzvVVFdEUVVWbNc4puVxMYpmfhMz+SZZTGbJN14OaYiO8f1YVYz3fa/wBobh/hvbLW3Xdq0djR627NVNdizEU5ojGKqqfDrn4vityPax2mPAxy7Ta2aYhgiOrSAY95j3gAYkATqoAAAAAALEdGVPZKeyx4pUrJIjCiVkAQEiZyqAyht7X+Jq+SfrDUjs29rnOoq+SfrCwdkA0oAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AkqKAAAAAAAAAAAAGBcg7jhjZtXvu9aXbdJb5r2oucke6PGfg/UO1aLavR3wXemm37Glo9ZduTHW9XjpzfGXzj9mPa7dzW6/d7tOZ01qm1bnHaa+s/2iHof2kNfXp+E9Loaa5/3u/VVVEeNNEdp/OXzuXO580wn6enDDrh2fEOMuKNy4h3W/uGuv1VVXKsRTnpTHhEe556qZn/5sevL7kp7vfjNfTz27dpsG66zatzsa7S36rV21XE01ROPyn3PtXpU3qzxP6Ktl3qmimq5TrJt36aZ6U18k5jP93wSmZpmO3R6HTcTa+nhK7w1NVuNBc1NOp+7HNFyIxnPftLGXHMr2Wclk04eH7tdvdtLy1Yj1tH1fqP00R/7Lt1qjPW3Rn/4oflLabk/4ppsf9tR9X6n9NFc/9FG6TE9fV0f8UPLzz+eLrxZfwr8n3apm9VnMxEy+leiTijZ+DuH963O7M6jeNRTRa0WniieWKc55qqvLOOnueA2zQXNx3Wxord6xZr1FXLTXer5aKffVPg+48A+iLZKtHTrd03Sxu81VY5NLX+5pn3zHWrHR6OTLDHH+Tnx423b4VxBuut3fc72u1t6q7qLlXNXXVPef0jHTDrcTMZjr9Xu/TBtWh23jzXaLQaajT2KJpim1T0pjNumc/wB3qvRt6LNo3q3b1Gu33Tai9FNNdWi0lWaqObt6yqe3eInHbzavLjjhsmNt0+OU9I/Vs6e1cuRV6umZiIzOPB9z9JPo00l7VbJt3DW16fT1V1Xq9TfmcU02qIozXXVM9usuw4T4c9FG310bXqty0G77jVXNNV6/NUUTV16R05Yhi8+Nm4vw21+eK4qiOuPcxpjp4PvXpm9Fm2aLZtVv3D+nqsTpoidVpY7RT0zVT5Ymese+PKXxradru63X2NHF3T2KrtyaIrv1ctFOIzMzPg1hyTObZyw63TU0mr1WniadLeu26qoxPJVMTMd2neruV1zVcqmavGZ7v0XwN6IeHKdHa1+57jRu9UZzGmrxZ5u+Mx1l8j9Me2aDaePty0O3WbdnTWr000UUdogw5Mcs7Itwsm3jMMqaZnpES39m2rV7xuFjQ6GzVe1N2rloojvU+txwjwVwHord3i2qd13S5TzRpbU4pp/8vfLeWcl0zMbfXxiqzVFEzy9ae/WGGMxjHV+geDLfo141uXtso4Wo27U8nPTEV9aojvMVR5eTxPpb9Hl3hS9a1eluVX9uvzNNNdUYqoqj+GfyYnNLl1rXx3ruPm1NPWPJzxYrm3z025xPTL1Ho84N1/Fm9xt+mxat0Rz37tUZiin9Z9z6PxbpPR/6PabW36jYP8Y19y3FdU36+lNM+M+XwhcuWS9WZjbN18MrtXKes0TDinMzGYfonhXYPR56Qdgv16HZadr1lmIi7RbnFVGekVxPaYz5vjvpB4X1PCu917bfqi7RjmtXYjHPR4T8Vx5ZcrjWrx3W3l5hOjKucRhhDow29FRNdcUxTNUz0iI7zPg/Ufou4N0vCXDn2vXWqKNyv2Yu6i9VHW1TjPJE+ERHWXxL0FbTTuvHOipvW6a7Gn5tTczHeKIzEf1x/V+g/S9r69F6Ot71FuvkquWabEVR/wC8qimf7TL535XJfknHHp4sf42vzv6VOMNXxLxDfu03Jp0VvNGmtZ6RR5zHnPf83iaoqqxzVZxHmz1EzVduVeE1OB7sJMZqPNld1t6K7csXqK6a5pxOYmJ6w++7RxZe4r9DXEG26u9z67bdHFdVeetyzFVOJ/LGJ/LzfnuicUx8cOz2re9dtNnXW9HeminW6arS34xnmt1TEzH9aYY5OPtdtYclk00L9UzfrrieWJqno5rWu1tFivTW712LVUdaIqnEy7jhHYbe+am7Tqd10G22LfJz3tTX1zVM45aY7y+7bX6J+E9s2W/fu2690u+orqpvXKvZzyTMVU0x4dI6nJy48etrjjcpt+Za6pmqZnutFFVc9KZmceDsre306zebWiouWtPF67TRFdyrFFOZ7zPk+3+j70VcMTTTqtZulre6qZ9qmxXizExHafGfBeTlxwm6Y4XK6fn/ANXVnFUTEx4MqrNdNMVVU1RE+L73unAOwVekTX6zc6bO18PaKbNFVEezFy5NMexH6z4PV8XcB8FWeFtXuM7Dp7VvS2/XU12rk0c8R2p5o75cv/Jl/TV4tPy1RRPNhK6J5ez9F+jrhn0c8YbXXqbPDuo016xVFF2irV11d+sTE5fLvTFsW1cP8YavbtqtV2tPRFE0UVVTVjMZnrPVrDmmWWmLx2evATROeh1l9F9GdXBGrnTbVv8AsWov6q9e5I1VvU1UxGZ6RNL23pi4A4V2Hgy5uG1aGvT6im9RTFU3aqukz16TK5c8xymNWYWzcfBIhlboqrq5aYzPk5abfNXinrHZ9g9Gvox0N7aZ4j4qzb0FFE3KbGcVV0x/FV5R5ebefJMftnHC5PkNOmvdf3fb3sJt098TMPrd3jHgKnVzop9H+hnQxVERd559dNPhMz2z4vX6j0T8I8RaWxuuya69pNPqKOaim3Gafzirt4uV55j9x0x4uz85VU4ntL0fo7ubTb4v227vd+rT6G1ei5drijmzFPWKcR5zEQ9tx56PeGtj2C7rtBxTa1motzT+4iqiqqqJnE4iGPo49Ge37zcsXNz4k00euoi7To9JXFd+qnvOfCnDV5MbjtOl7ajrPTBx9quMd4mbdNyztliqqnTWp7zE966vOqcf0fOZiqqcvt/pv4Q2Hh7hLbq9n0EW71Wqqt13qqpqruRFuqesz74fINp0d7Wa2zptPaqu3btdNFu3HeuqZiIpj39V4ssem59GcvbVdfTRM9IiZlyepriJmaMREdcy+92/RzwvwdwvXvnF9udw1NMxHqLdfLbi5M9KI8/HMz5NLg3ePRpxJvNraNRwdpttq1E8li7zc0VVTHSJnwz2z54Sc8vsT49X18NmjliJmGMx17vrfpo9Glnhaindtnmurb7lXJVbqnPqap7Rnxievd8jq7uuGczm4mWPW6JhlRMxPScMYhlTHVay+0/syRM79uMz1/3OJ/8Aznc/tLVTRpdommZpz6zrDqP2Y5j/AB7cY/8AuUf8btf2nKojSbPEf+9/R87L/wCRI9eP+p8Q024aizeovW71dNyirmiqKp5o+D9VejPfq+IuDtNuGpiJvxmze8qpjpn84fkq1FVdfLTMRGcTM9ofqT0KbZqdt4D0lrVUTRVqLtV2Invie0497X5skw3+2eG33b4v6btg0+wcb340VuLdjUU036aIjpTM94j83uP2bK6q53Sias5tW5//ADnm/wBpDcLOr42+zWq4mdJZotV4/m7zHxd5+zNVi9uvX/qbf/EvLLeD0wsnJqOk/aVoxxtMx/8AVLX1l8op+8+r/tJz/wDTb/8A1Lf1l4bgzh7XcTb9Z2rQURNy5Oaqp7UUx1mqfdD0cV1xzblyTeTk4ItbbXvukr3bU/Z9HTepqvVTTM+xHWf+X5vU+lzj2/xRr402imu1tWnnFmjxuTHTmqj6R4f1ey4o4f4F9Hm0aWjdNqr3vcb0Tj1lzkp6d5x5dYw5eEND6OOPdLc0Vvh2jatbbt88UW68TMfzU1R3xPhLGWWN1lWsZfqPz9dqmurMx7ujGInPaZe19KnBt7g7eKdLF2dRpL9M1WL004mrE4mJ98dP6w6rgjh3V8R8Q6TadJTTNy9ciJmrtTHeZn3RES7/ACSztHLrd6dFTbrq+7TM474ZeqriPaoqjPZ9z4ksejvgLG1VcPTv24W8evvai5y0xM05xy/CYn3dG3wJoPRbxvuHqf8AAK9s3C3+8jTU35m3epiOuPPHfDn83m9N9HwKKcVTHl4vf+iPgu7xPvVv11FcaKzMV6q5jpEZ6URPnV0+EOHjbb9o230ja/RTbr0m2Wtxu259TTmqi3TVjERPu8/N969GO58M6vh25pOGbF+xpdLVTRcm/ERXXVMZmqqY7y5/kc1mO41xYS5ar4X6erU/9JG6cluIp9ZRiIjt+7ofPs10T09mX3z0k3fRpTxZrI4g0+53NxxT62bNcxR9yMY6+WHzfa+Gdk4i4o1lOg3nTbTtNF6PVV62v25pnMxER4ziO+XTjz3jusZY6yeUjW62bH2f19yLPTNHNPL/AEa1U5nx/N+lP+izhTZ+Fdwv1WK9dqKNHcu0371WfaimZjFMdIfnDU0RGoqt09KYqXi5Mc/8TPGz7cGMRlyU6e9XEVU25xPXu9t6OfR/uHGGqqp09cWbFrE370xMxR7vfMvZ7rR6MOEtTG1/4RVvWoonlu3arsRGY7x1zH9MF5p9RJh4+J3LVyiImqiYy4474mH6W2zgzgLjnh37btO3VbVciZomaP8AqqvfHaXw7jPhnWcNb9e23W0RzUzmirwrp8Ko+JhzY5XTWXH1jzkUxnpLkizcmMxT/d9Z9E3oxtcQ6GN33u5XY0HNMW6KOlV3Hec+FLn1u++jTad5uaC1wdTqtNbr5Kr9yuJqnHSZiJ6nzzeoz1s+3xu5RVTHWJYQ/Ru9ejLhbibYKd14Vo+x3b1ua7FMT7Fc/wAsxPafDo/Put01Wn1V2xcpmm5bqmmqPKYnEw1x8sz+jLHq1WcRVPRhVDZ0tMVTETGfzdN6Zrj9VX4QVWq4pmZfe/RxsPo44u0FVFradRZ1untUzdt16qqeaO01x7s/0zDg9KPDnAnCu00eq2PUXdVrKLtNir7VVEW6qYiMz54mY6OE5/5dW+l1t8GjrHZlTT0y5IppoudfajOJx4vtfol4e4D4o2GunU7Jfp12itW/tN6dTV6u5NWfajE4p7dnTPPrEk2+HzEx3R7P0pVcIxr7VjhPSXrVm1NVN27cuzV62emMRPaI6/F4xrG7m2ayiqcdH0f9n+5X/wBIm2+1OJquU/8A7up82h9H9AFWPSFtef8AtLn/AIVTl+R/qydOG6zj63+0LNX/AEdVTzTP+9W4/wCJ+ZZqu1dYmcePV+nfT97fo7qjOP8AereP/wA5+aPst6MxmjrP8zz/AIV/43Xn3tx27tyivPNVOI7Ze73rifSbj6Mds2a/eu3Nw0OquY5o6RZqiOXq1fRRwtd3rjbb7V/TRqNFbuxXqenNRyR1mJ+Lz/Flq3p991tu1TFFqNRciimO1NPNOIenctcNWfbp/vT4yyos11xmmmZ+Dt+D9j1W/wC+abbNJRNV2/ViPKmPGqfdD6vvljgDgSadsu8PTv8AuNOI1F3UXOWimryppXLk1dEx36+JeouR15cr6mvPaZjGcw/QHBGi9F/GetjTRw/XtmvpjnixTqJmi7Ed4jHTp5PnfHWi2rQcfa3b6rX2Xb6NVy8tmmJmmjEdo/qxjy3emrhpwei3g7UcS8Q6e1NNdGkt1Rd1F7Hs00R4fGe2HP6e7UWfSHuFFu3FFMRaimmPCPV09P7Punoq1/DGs2G5puGLGotafS1U+sqv0xFdyqYn2pw8f6S/+jG3xdq/9pNNutevxRN2qxM8lXsxjHXycePnyy5LK658eMx3H54nM9HLpYiLlNUz2ns7febW16jiHU0bPTct7fVexp/W/eij3+99B2T0d7Nsmw2uIOONXcs03ZibOhtR7dzxxP5dfc9eWeMnrzyVjxzx1pNJwJtvB3DGoquWadNRGu1MUzTzTPWqimJ645pnM+PZ8pmJz1/v0fceHd09EW7a21tl3h77FN2eSi7epzGZnEZqjrDU9Knomp2nS3d34fi5d0luOa/pqvaqtU/zUz4xHjHeHHHkxxunS4W/T5Bp7M13aaeXOZ833HhLg+rafRNxHu+qsVUazXaH1dmiqjFVFmK6Z5p8uaeuPKIeP9GWq4M2zUTrOIrGq1Ort3Y+z2qbcVWYjEe1V5zE56dn6H4lq2yeF9zr3Ka69vnTZvRTPtTbny/s48/NlMpI3hxyx+N9XRVTqK5qpnpVPg47Ny7buRVZqqoqjtNPSYfUeKavRXXseoo2PSbpTuM8vqartc8sdfamevlluejj0X7Tvv77X8QWLsxEVVaPSV5uRExH3qpjEd47eL0fLMcd5OXT3UfJ9ZqtVq7s3NVeuXKvOurMtOr7z696feFtk4c0m1RtOip003OemuYmZmrlxjMz3nq+S2LdV2uKaeszOGsOSZY7iXGy6Y0xzTEUxMy5KbF2r/q5fW+FfRptm3bF/tHxper0+k5Yqt6aJxXXM+fjn3N3ZN69Fmp3OjQTwjNu1XVFFOouVRXMZ6dY8P6peaL0fEptzFWJiYSaeXv1fePSj6J9Fp9uvbvw1TVbi1Tz3dJNWYmnxmmXxza9q1O5bla0WktzXdu1xRTR4zMymHNjnjuGWGrp11FqqcTET7mVVi9HtVUTEeL77/sDwdwPw1/i3FMXt01EzFHqrc8tE1z2piPrMtXhTV+jXi3cY2q9wrRtuornls3KK5xXPlmO0pOeWbh0fBp7yxnL6l6ZPR1b4Vm3uW2V1XNvv1TTNNf3rNflPnE+D5hXGOk+TrhlMpuM2WMMqkd1aQAAABaZZR4sIZ0FSsgGWQBUqwniyx0YwlRlERhtbX+Iq+T9YauW1tn4ir5P1gjUdkA0oAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Gu/JP0cjj1X4a78k/QV5+e6pKigJIKAAAAAAAAAABGPEH6N/Zmn/wCjO6UxiZ+00Z6f6Iw0f2nZqjS7RiMU8l3r78w0P2ZN3otbjuG2XL0URes03bdM/wAVVPSf7Yeo/aF22rceCY1tFuqu7or+Ymn+SrpMz/SHytdPyt39vbvfF4/NdWeTu447sq4mIwxxL6rxOTvHUzCYmY6Mrdmuumqqmiuqmj70xHSP+R4ja2mqf8U0v/4tH1h+p/THVM+indP/AMOj60vyttFMxu2lp/8Ae0/WH6n9MUVR6LNzjp1tUfWl4/yP88Xfin8a/KFVyqi/zUziYnMPvv7Mmou3tv3e3crmqiiu1VTR4RMxOen5Q+AXo/e1fF95/Zdj/c96z52vpU1+V/rTh+3ivTzVP/SRuk5/joj/APdUNj0C6q7T6QdHRRVNNNym7FcROIq/dz3/AD6tb08x/wC0fdP/AMSj/wAOhn6BY/8AaHt/vi7/AOHKZf6ln+x9L/aI3jXbbw1o9Do71Vm1r5u03+XvXTTFMxTny69Y8X5/sau/maaq55eWrpHujL7h+01Gdr2PP82o/wCGh8H0/wDmT8tX/DJwe8ZyX+b9b6O7O5+i6bmun1039jmq7NXeqZsdZl+S9fqrn2u5VTXjM/WH6t2Sf/ZRZx/9hR/4D8k6v/Pqz5/oz+J95N88+n6K/Z0v118ObnbnM00ayjljy/d0vlXpxmJ9JO8VeP2ifpD6d+zbV/8AqPdY/wDvVH/hQ+Y+nCP/AGj7vH/3mfpBxec1TO/8ce+/Zt4ft00arf7tETVVV9ms1eNMYzXMf1x+T5v6WN6v7xxruOprmcReqt289OWinpTHwiIfbvQBXZngHT8nWaNTc5/dPN/yw+J+lTaq9t433PT10Yj7RVXT0701dYleLPtzWVM8dYTTX9HvEP8As3xHo90m366mzMxVRzY5omMTD6D6WvSXtXEvC9vadBpL9Fc3qbtdd2I6REdofHqaJz07NijQ6vUWL96xYuXLWnpiu7VTGYoie0y7XjxuXZzmdk0+hehzjzauFr2vtbnbvcmqpp5a7cRVMTTLovStxJa4s4rr1+is3IsRbptW4mPaqiPGYafo/wCD9z4t3WNHo8WrNM5v6iqPZtx+s+59K4h1vB3owinbNo2ujdd+5M3tTqo5ot593bPug1j33F3evrk/Z52fiLb9zv6vWbXqdPt97S1W/WXaeWO+Yjr1aH7T1MU7ttVWMf7vVif+9DtPQrxbvvE3HNyNy3K9fsU6a5VTamcUU47YiPJo/tT043Haq4zP7iuP7w80387tfeJ8Oq61dTCxTVPVYe95X179mCObivW04iZ+w18uZ/1Uy+p+m6ibno01luZj2r+niPd+8j/m+G+g7drW0cdbfcv3PVWb1U2K6pnpEVxiM/nh+hPSdpKdx4K3bQUxM3KtPNdqPGa6PaiI/wDhfK57cfyJk9fH/rr8hVxMU1R07uCejkvZ9ZXERjrnEuPEzHZ9OPJYRVMRj35JqmfFJicZc2j013VXabOnt1Xb1XammMz5/pLQy0Vdfr6IzmJqjo/WfAtdVXol0NdyublX+GV+1P8A+HV0flHRWp+2W4x/FH6v1dwJGPRBoMf/AGZc/wCCt4PzL/j/APr0cH7flLV1VUa6qqjp1w+6fsx3qqtJu1FdU4mq1OPKZiXw3coxq6/i+3/svY9Ru2Y65tfSXT8n/Wzw3+bpv2i+INRPE/8Ahdiuq3a0lNMTH81dURM1f3iHzS5xNvdzb5227uepq0s97XrJ5enueu/aFmZ9JG4T5+r/AOCl83q6OnBhLhKnJldv0F+y7fqq0278059q3P8AZ4b9oSr/ANpGu7fct/8AC9j+y5ONLvE9Ok2/o8V+0FTMekbWzM/w2/8Ahefjn/sZN5X/AI3luCa+Xifbqqe8am3j/wCJ+if2gomfRxcrme+pt9Pzfnfgin/6Tbf5fabf1h+jv2gKM+jm5j/6xb+q8/8Auxicf+NfmzhrT/at70tmvl5Kr9MVZ8pqfqf0qWq9J6Ndyt2It0+r08WoijvFETHT4YflDSXatNq4u0zy1UTMxPl1fp/gfifaeP8AhW5s+qriNfXppt6ixOcziMc8fVPycbcpV4rLLH5jv3J+01+14/q/RnoB1c3eA4t3YmqLeqrojr5xExH1fLN89FnFmm3y5pdPs2q1Vmqr93et0+zMZ7+59T0N3bPRlwJRp9w1Nm5uMU1XZ01Fcc9dyekU48I7dfic+88ZIcV6b2+G+lO19h453fR2oiizRqaoppp8In2sf3/s3fQ3qb3/AEhbLbpq5aZ1VETEdMx5PKb9r725bxqdffqmq5qLk3a5nxmZzL0vobn/ANomyz4/bKP1ejOa4tOcv89vr37SMVU8IbV/+WV/+FW+JcC7ta2LijbN3v25u29FqKb1VEd5iJ64fc/2l8RwhtEf/fKv/CrfnbbdLqtfr7Oj0lubt69cpooojvVM9Ihy/G94/Wufffx9o9L/AKRNi4j4Zo2ra/X3q7l2Llddy1yzbimJp5ffMzV/R864H4e33cd50up27bb+pii7TXzU0TyxirOeaenTH9n03RcC8N8BcP1cRcZV/wCKauKpp0+jonFuao8PfiIzOXmd19KPEO8avT6PR3be16H1lNMabR0RRTy80YifPos1MbMV1/L19W9OcZ9G+51T1nntT18+eH5Qq+9L9b+m+1z+jTdJ7e1a/wCOH5LqonPgn4V/hV5vtjC5wdmMzEy9ded9l/Zlrn/aDcf/AMij/je79MWm4W1ul0NPEu5avQzFVcWKrFvn+OXgf2Zv/wBv7jEf/Uo/4ndftK80bftHxu/o+dnjv8mPXj/qaHDWweifb9VRrdZxXXuFNNUVUWa7M0xMx54jq9Bxp6YNn0m33NJw1bqv36qOS3ero5KLcds0x44fnv1lVMZzV/VwzX8cPTl+Pjld2uHyamo2901V7XauvVX7ldyu5VzVVVTmapnvMvsP7MvXUbpGP+po/wCJ8Upqie77l+zFREarc/fZo/4j8n/VV4bvN5/9pCrHG8RP/wBVt/WXWehfinb+FOKbm4blRenT3LFdqardMTVTmO+PF237SkRHHXWIn/dLf1l4jgnhjdOKN7tbbttGa6varrmfZt0eNUmGrxepl/l49X6a+L9Fxbu+hjaouzp9NZ5Ka66cVVzM5l2PoG2DiCxxdpN0ubZqregopriu9XTNMYmmqMYnv3d7v2n4O9FmmtWqNJRvW/XLfNTVej93bj4eHuju1vRjxzxBxR6Rdt0+v1lX2aZr/cW45beOSZ7R+TGV/wCPWP03h5lutz9p6iidv2SuaJ5vW3o+HSmcf2h5n9nDUaexx/FN6Y9Ze0t2mz5zc5ekR75jMPZftPW4na9orznF69M5+Wl8M2nW6vQa+3qdFVXRetVRXTXT3ox15vyTjly49Gd1nt9p9N/AW77zvNzibZ7f2uK7dNF/T0/foqojlmYj+LpEPk3Duu1vDXE+i19dq9YvaPUU3JomiaZmImMxifOImPzfZ+DvS/tuvi3peILVWkvxGPtFqP3dXvmnvH/m97u2wcM8XbbF7V2dPrLVVOadTaxz0+Gaao6590uePLlxzrlPG7jM/Y/L/Hu9Wd64s3LdNNRXbs6rV3b1FFfeKapzET78YfVf2cLk1bHvOZzPr7f/AIcvmHpU4X1XCvEVegu3PX2eSK7F6Yxz0dv6xOYn4PpX7NkxO0bxH/v7X/BLpz6vFuMce5n68B6cq6qvSFucTP8A1tMf/uqHjdJVVTeoiJ71Yl7P04Uz/wBIW5//AI1P/h0PHaWmfXUZ/mejG/wjjlb2fqfQXq7vohi7ermuurZp5qp7zPq35ZqpmvcZpiMzMv09tmZ9DluPPZp/8N+Z9JTy7tFVXhMT/eHn4POztn7p+otLYjg70RVzo7dPrtPoeeqqOkzXVERNXvnq/LW5am5d11yuqqeaapmZ8/N+tuLdNVr/AEa7jp7Ec1VWgzTjxxES/IWuoqi/V4dT8W73V5vNafTPRF6QbPC1vVabcbV6/pb+K49VMZoqjpnE+50vpW4vscWcRUa3SWLlqxbs02qIufen3y8RRFUZ/s569LqKLNu7cs10U3ImaJqiYiuPHE+L0fFjjduPa6fa+CfSZse2cDWNv1FOqt6nS2arcW6LfNTc749rw7vjlNjW7ruUxotNdv3Lteabdumapzn3Po3or9F9zftFG875qa9FtUe1TRTOK7sR3n3U+9vb96Q9t2GuraOBNq0+36eirl+2csVXbkx05oy543HDL+H23d3W3070M7duO2cF2NJumlr01+L9VVFFc9eWYjE+7xfnH0g2qbXF2800RFNMa27iP+8/RXoP3HV7rwrd1mv1F3UX6tbXmu5OZxEQ/O/pK/8A6z3n/wDLbv8AxOX4+++W2+bXWPLzgprmmek4SWMd3ued6r0a8Q3+H+LNLuFNVU26Z5btvwron70fr8YffvSxsFviTgW/d0VM3LmmojWaSqmOtdExmqmn5qevxiH5c00zF2JpnE+b9P8A7P3EMbzwj/h2puc2o2+Yooieszaqn2fyiY5fhh4/yJ0szj08P8pqvzP6ir1nLnOJnr4fF9otWZ4G9B9VdfsbhvdXWJ6VRbqp7f8A/Pp8a3Buno+pp9L9rYrVnO3ay9Grpx2p08Tz1U/lMTT+cOl/aF4ijcuMZ2rT1R9k22n1NMU9ueetc/1iKf8Aut9vkskZuPR8xvXKq5jmmZxHi44ZVzGOjHMPS4Lh9C9AkT/0g7XMf9pc/wDCqfPo6vovoEon/pA2v/8AFuf+FU5c/wDrrpx/5R9z9JG/UcP8LVa6vb9Nr8XaKItainNGZz1/s+UVelrSTnm4L4dqqjw9XL3Xp/p5eAKv/wAqt/8A6T8zdas9Xk/B45eKWuvPlrJ+nPRf6TNp3rco2WnZ9Htt3UUz6qdL0pqqjryzE+L8+8Y4/wAf1mfDUXO/zS1+Ht21Wy7rY3PRV006nTVxXaqqjMRJqPte762u7Taru6i9XNU026czVM9ZxEPVjhMbtxyy7R7v9nXV6bT+kCinUTTzXdNcotZnHtzHSHsfTL6Pty3PdLnEe0Wp1Vd6mPX6en2ZpmIxzU+b4dt1zWaHc7eo0s3bd+xVzRNMdaZie77xwL6YNBq7VvS8R2K7N+mMfardOaZ99UeHxcefHPHLvi68XXrqvkvD2o1/C/Euk1ersX9Pe0t6m5NuqmaZmM9Y6+5w+kPeLO88XbhuejouWrGovTXbpr6VUxMR3979P73snDnF+z01aiixrbF2P3eptTE1RPnEx9H5m9JXCmr4W4jr2+5c9dZqj1mnuz/HTP6+a8HLjnf+2eTj6zy+Pq/7L1VVW17zEzn97a+lTwP7QU/+0ncpiOubX/BD3X7L1X/6u3iJ6fvLWf6VPCen/MekjcvOZtf8EOfF/vrWf+uVq+hLZbO88caSjU26blixFV+5TV2q5YzET+eH0z0s8G8Q8T79Td0+4bXa0lmxFFm3qNVFFUTPWurE+c4j4PJ/s14nifWRMU806G5FMT4+1Q2f2itv1el4m0+4UUzTZ1Okp9rPTnomYqj/AIWssr82kk/ht12n9EnENm7TXG5bFMx5a6n4P0Fw7Xp7Wy6HSbprtvvXaNLRa1MRqqKoqnlimrrnrmI6vxp9rv8AhX4NnS3dbqK7dqxE3K66opoppiZmqqZxERHnMunJwfJ7azjya8dtxRpLG18S6/Rae9Rds6e9fs0VUVZiaaaqoiY90xiX6P47rx6Lt2mnpP8Ah1P1pflW7Z1FjVXLWooqt3aIrprpqjE0zicxPwnMP1FxtM1ejDdIj/7Pp/8A0XH8jHVxb4ruV+W7tyv7RXPNOcy976B9Veo9IWgiLlURc9ZFcRPSqOSZ6/m+e3av31c+97b0GVxHpE2343P/AA5enln8K5YW9nvf2oIpnS7LPb/Nmff1peK9A+x29143083aIqt6Wmq/XExmOmIj+85ey/aanm0eyzPb97/+i6v9mWqn/abcc4ir7JGPyq6vPjlrgdbN8jd/aW3W79q2/a6Ziimi1N6qP5pmcR/SI/u+MaTU3LN2mqmuYmJ6T5Ps37T+310bhtmt5fZu2Joz5TTV2/pMPiVMVTVh2/Hsy44xy7mT77/0ybZXwtNi/tuqr1/2X1UzNVM0TVNOMz49XzDgbfNNsvFWj3XUWprt2b3NXTT3xjrj+rzuk02ov3KbFqzXdu1TiKKYzM/CHNt23azcNytaDSWaqtRdriiinxzlZx4YyxiZWvqPpp482niTadJt20zqK4t3PWXKrlHLjpiIx+rxvo22nf8AVcQaLVbbt2pv0UXqa+eKZiiMT1mZ7Po9jg/hbgHh+je+Lo/xjce1nS82LfN5R5485eYu+krfN93XS6PTVW9q0EaiiKdNpKeSJiZ8Zju5zUwsxnjpJ7NvqH7QNFu56PNRXNEc0Xrcx7vafl691uVZ8Oj9TenWjm9GusmIxi5b+r8sXf8AMqz5r+NlvE5/8nH4qTCQ9TioAAADOnxYM47FSshFYZABKyieiBAg29r/ABNXyfrDUht7X+Jq+T9YIsdkA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FefUBQAAEyCgAJ4qgKABImFAAB3PDG66jZt50m46arlu2K4rpz2nzifd4P1bwnvOz8c8N13aYorpu0er1WmzGbee8T+kvx3FWI6O54W4i3Ph7WRq9s1l3TXY71UT3jymPGHn5uCZ+z7dOPkuPj2HpN9F258Nay5qtJbuana7lU1Wr1FM1cseFNWO0vntenriZ6RmPDL7rs3p7vRpLVjedko1ETHt3LFcU8+PGaZ6ODVekz0c6nU3L97gibtyrrmbduPoYZck+41lMb9PlHDfDm6b9uFrR7dormouVzETyRmKffM9oh7Hji5tfCPDM8F7X6jVbhqK6bu6aunExmPu2qZ8onu5eKPS3q7+iu7fwzoNNsGjrjlqjT0R625Hvqjs+X371y7dquV1VTVXOapme7rJb7XK6/Ts9gtzd3fS0RRE1V36e0eOX6j9MVrn9Gu526e9NunP5TGX554B4o23h2/Rq9Xw9pdxvW64qtXL1yY5JiPKO73mt9O1Wqs12NRw1oblu5E03Kar1UxVE94no8/LhllnK6ceUk0+J3qZ9fVE4zFWH3r9mGzXGh3mrE8s1Wo/PEzh8p4j3fatw3uzrdLw7pNv0sRTz6ezcqmm516+1PWMve7B6YtFsWgq0O08J7dpbHNzTEX65mqfOZ8W+fG54aiceUxy26P0+W5j0jbjE9M1W57eE2qMT/aXL6BLVVXpE2/ljMYvT08P3c/83Jxh6QNr4ri5VquFNBGuqpii1qKb1fNHlnzwz4B9I23cI6CmnTcLaKvW1TMV6uu7VFdVMz5eER2ZuN+PS7nfb2P7Tdqr/CdlqiM4r1ET5Z5aHwW1TMV5jtMVf8AC+u8QemTb990U6HduENv1Vias001X6s0zMd4nweB2Dftj0G4ai9ruGtNr6Ll3mtW671VNNmPKMd4+K8WNxw0Z2ZZ7fpDYqZ/6LbNM0z/APsOOkd/8h+TddZqp1dVOM9emPHo+2WPTx6umKKeGtBRREcsURfq5YjGOXGO3g+d8TcR7Jum+aXXaXhnSaO1bq59TYt3quW/n3/w/kz+Phlhva8ufZ9X/Zts1xw9ud2qmYpnVURn4W4z+j5z6cLMx6Rd3qmO9/PXxiaYem2P0zaPZtvo0G18JaHSaamJn1dOoq61eMz0dDx9x3tvFtqq5e4Z0VjcJiI+1271U18secdpTHDLHluS3OXDT1H7OW/aaxq72w37/JOomLtmKpxzVx0mI/KI/pL2npe9HtfFlNrcdvuU0a6xRyTbq6Rdpjt18JfmjRau/o9Xb1Fi5Nq5bqiqiqmetMx4w+zcKem6uxofU7/oK9XXRGPXWaoiqqPOYnpMscvFlMu2LXHyTrrJ4ix6NOMbmtq08bHfpxMxzVVRFP8AV6TjfQ6b0ecARw3Vft3t33iqm5rKqZz6u3T2pd5vXp10/wBlqp2baLkX5jFNeqriaaZ88R3fE+Jd51u+bnc124X672ouTM1V1d5/8nbinJf8vpzz6/p9+/Z6taeODdXctcvrKtZPrPOYx0h859MPDe66XjXWaivT3Lmn1VfrLV2KZmJifDPm6f0c8c6/hLUzVaopv6a5H7yxVPSrHjHlL6lf9Ou2/wCGx6rYKq9Tn2ftFcTbpn3+LHTkx5blPpuZTLHVcf7PnCe87buNW+a3R1afTXbFdu16yOWquZ8YieuPeftDbRuu87/s2m0Ogu35u0VW6ZojPtZjMfk8no/S1vNPGVG+a+/XrKOWbVdiZ5bdNE+FMeGHbcc+ma/ue21aDYdNVoJriYuX6q4qucs96aZjsz8fJeSZaXtjMNPkGr09Wl1N/TVzTNdquqiqaZzGYnE4anaWzfuTXzVTHWZzMtWcPdHmbOjv1WqomJ7VRMfGH6W9EvG1nibaY0OtuUzummtxRMT3vUR05vjEd35fbm1bhqtv1dGp0l+5YvUTmmuirExLhzcM5HTDO4vrPpc9Fupsbjf3jh7S1XtLennu2bfWbNXjMR4xPf3ZfJLli5RX6uaZpqjvE9JfXuFfTbuOjs0Wt80Ma+iMRN63PJc6eM+Ey7nVelb0e6y9N3V8HzqK5jvXat5mfjCYXkx8rVmNfENs2jW7hqbdjR6a5qLtyrlpot080zL6rY2/S+i7h7VXddRp73F+46aqi1anExt1mqJiaqv9dUTMRHh3Z7x6YtHpLFy1wZw5o9luXKOSb80Uzcpjzpx2fJ923LV7jrbmq1uouX79yrmruV1ZqqnzmXWXK31yuoy0Mz9st4j+OJfqzgezdp9FO2aeqnF27t9yKKfPmoq5Y/vD8w8L7ttu2a2dRue0WtztxR7Nqu5NEZ5o69PdEx+b6rHp7uWbVFqxwzt9u1apii3RTeqiKaY6Rjo835HFeTWnTiz6x8a3Gmr7ZcpqjFUT1j3vuX7Mti7Z0u711U+zFVumZj4S+bcTcU7Fve42txs8LaLQ1Vaibupps3qsXY6ZjH8Md+z2Ww+mbQ7Dt0aLaOEtu0tqZ5piL9czM+cz4t82Fzw1DCyXboP2hrM0+kPWV1RiKqbVXuxNEf8AJ8yuT1fU+NPSXtXFNuqdw4R26u/Tbmi1ei/XzUZz19+Hy2uOsz5u3FOuOmMru7fbv2XtXYp1G8aWq5i9ctUVUUecR3lo/tCcO7hVxPTu9nT3Lml1VumOemmZimuIxMTh864L4h13DW82ty0NyKblGYmJjMVUz3ifc+17b6ctqnQZ12y6ib0R2tzTNFU+fXs82XHnjy946Y5S46rw/ox4D3LV6/T7trcbbtti9RVVqdR7PPOelNMT3mez7V6Z9Df3H0fay1prVy7ctVU3IpojMzET16Pi/EfpN1e/b1or2qt+q0Gkvxct6S193pPefOXpeKfThq/ss2+H9FGj5uk3b0xVX+Udmc+PkzymTcyxmOnyLU7VrNJr7dnV2Lti5ciKqablE0zMT2nEv0HVwdu3C/o7q0/CtHNvOqpt/ab8Y55pqiJmmmfCMS+B6/ddz4i3adVrL97Vaq5VEc9fWrPhD7nqOPNdwLwrtej4konX7ndtRVTZo9mq1ZiMRzz5t80z80zxam7XgtdsPpTiuqOTdqaJiImmi9Vj6vOblwpxnVXXe122bjXVMe1VVRNcy+mR6d9Fnrsl2PPF+HZbZ6ctmu3qIvbRqqIj+Km7TOPPp4sduXH3TXXDL9vzxrNNc0+oqt3aKqa6fvU1RjD1Xocpqj0h7NiM41lMz8Iicvpvpx0fDu+8IaHjXZabVNVV+LNzloima85zmPOJw8HwXxvtXCkU3rPDWj1W40UzE6u5fq5szM9o8HbveTDWvXLrMcn0/wDaV56uEtop6c32yr4f5VT5p6AKNPX6SNHbv0xNdNF2u1mOvPFucfrP9Hc756ZrO97fOg3ThbbtVp5nm5Kr1WMx7/B89je50vEH+L7PZjbardyK7Fu3XNXq8eETPf8ANji48px9a1lnLlt9y/aB2jW7rsG16zS26rlvS3blOopopmZp54jFf9pj83yfgHhDfd73WzTotJXVbtVxVdvV5pt0REx3qn4PpGz+nXQRoqf8T2O7XqMTFc2a4i3XPwns8rxx6Wt03q1RpNBbt7Vt8XOf1GnpxNdUTmma5jvjyY48OTHHq1lljb2fZ/TJTXqfR9uum09FV27NNuqKaKZqxiuMvy7xFsWv2OuxRuOnnT3dRai9Tar+9TTMzjMeGcZ+Ew+xf9O2njaqb9vaKqt05MTzXI9TzeM474z1w+LcT7zr993W9uW46u5qdTenNdyues+UfCI6N/jYZYeZM82Uy+nVVz1lKI65xlJbmz3rGn3Gze1Omo1VmmrNdmuuaaa48pmOz1VxfXf2X9PXXvu43YieWNLFM/Gapx9HoP2lNLdq2fbL8U5po9ZTMx5zh5nhb0u6Dh7TzY2fg/bNFRX1rxeqmqqffLa3v006feNDc0O5cK7ZqtPX3prvVdPh5PHlxZ3mmUemZz49PjF2rE4cU/F2nFGv0G47lGo27arW2WeSI9TbrmqM+M5l1Uva8zltR7n3j9me3VFe6X+X2abNEZ8s1PhWluRRMTXTzUxVnl8/c+rcL+lzTcO7fVpNs4X0FimvE3aov1TNdUR4zh5/yMMs8OuLfFeuW6x/aXoqnjfmmOk6W31x75ej/Zhp00aLdrmIi/zWoqnxin2v1w8pxd6Ttv4mszTuXC233btNE0273r6uen4PLcB8Xa3hTevt2n5btFVPJds1fdrp8vy8GMuPLLh6fVdJlO23svT5sG6Rxrc3GLFdzS6y3RVZrimZimYjExPlPT+7sfQVwnvOl4n0W/arS1abR24qiK7scs3Kppqj2Y8Xd1em/avsOY2S9cvTHSiu7TNvP1eFv+ljfL/Fuj3rUTE2tLM00aSmcWopqjFUR75jxYxx5Lh10tuPbs+h/tHaXX6/btps6TT3L+b1yIi3RNUxmIxnDxPof4fnTelDV7Fulu3NVGh1Fq/TMxMU81rE/nHN/WHacUemyLu3V6fZNBd0uquRib9yuKpt/LEePveF9HnGH+zfFNe937FWurqs3LcxXVjNVUd5n4t8XHyY4VnPKZXbr+KeH9x4d3u5tmrt1UX7EzR0jpVHWYqifKYxP5ve+gHeN1scX6fbaa669Fqort3rcz7PS3VPNjwmJjv75dlr/Svw3v8Ap7VrifhGzqq6YxFyzdjNPwmevfLRp9JXDHD1m9VwfwrTpNdcomj7TqrnPNMeUf0TPHLPHrYS9buVsftQ6zS17ltGhorpr1ensV+ujxiK5iac/wBJn83Yfs0xFe2bzH/vrM4/7kx/zfFN+3TV73u17ctdqLl/U3p5rldfeZ/5PS+jTjTUcH7hVeooi9Yu0xTeszOIqx2n4x1/qvJxX4ukTHPee3femvZ9Zc9IWp5NHeuzqpt1WOSmZ555KYxGPfEw8RxDs+v4e327teupt06qxia6aa4nlmaYnHxjL6vv3pxt1aGadp2qizq8T6u/emK5tz50+98p2jfbFnerm5bzttG713KprmL9yaeavOczMd2+OZddVM9W7fpDYdPdr9FFuxj2/wDB5jE9P+ry/MuopmjXzNUYxOOnk+tWPTldotzajYNBFmmnkiiLtWOXyx5PnPGe97ZvGp+06DY9PtlX/WU2bk1U1T5xnsxxcdlu2s8pdafpD0Rb/pOIOELFqaqatTprcafUW5nPSI7/AAmHzD0leiPcrO439w2Cz9r0t6ua5sU9K7cz4fB864N4r3XhndKNZtt6aaojFduetNynymH2LR+nTaa9NTOv2TV0X6ae9muJon+vZxvFycWW8G/kxymsnzzhv0VcT7jrqaNTobmg00T+8vaiccseLD0p7lt2q4i0uz7ZMf4dtGnjS2aoj71Ufeq/q7zjj0y63d9DXt+06KrQae5GLlya83Jjy9z5PVcn1tVcVTM5zn3vXhM7P5OWXXfj9dabSUa3gG1otBNNMXttiizVHbM0f88vzRXw3vMbpOjq0OpnUxXy+ri1Oc57PZ+jb0sXeHdvo27X6WdXprX+VMVxTVRE94694d7xP6bvtGlqo2XbqNJqKonGpu1RXXT8MPPx48mGVkdMsscpH0D0TbNuHDfCNGk3C3RTqKr1V2qiKs8sTjpOPHo+C+kDYd11HEHEm4fYrlGm0uoqu3btcctMRVV7MR5zOXpOAPS1Vs2339Fu2nva3nuVXKbkXIirNXeJz5vOekz0i63i239kt0xo9vpnmjT0TnnmO01T4yvDx54521OTLG46jwFcRHiwjuyqnPdjjye1wZ2qppr5o8HvPRFxT/sxxXotTcuTTpblXqdTGcfu6+kz+U4n8nhLURn2uza0dqvU36LFmmqq5XVFNEY7zPSI/u58mMyllawtl8fsPivcdLsO0a3iO9Zteu0Omqos3I71TViKaInymqKf6Px/vGquavWXdRdrmq7crmquqfGqZmZ+r7H6e901O18M7Dwfc1c3dRZsUXdXV/NNMclEe/rFc/lD4dVVMz1cvxuLp66cufbxjKYWR6XFlbxE9er6b6AKKrvpB22immc01XK56eHq5jP94fNtJVFFzNURNPjl9T4V9KO08OUTXtfB+32L9dMRXdnUVzXP546ZcuXG5Y2R04tTLdfTv2gNPXd9H171dNVUUaiiqcRnEYn/AJvzB6qqmZiJpzPTu+23vTvXes1W7vDuhuUVRiqiu9VVEx74w6mr0s7ZM9eCtj/pP/Jx/Hwy48etdOWzK7fLdPpb1y5FFEU11T0iInMy+zcA8KXeEOD9w423ez9n1UWpt7fZr6VRVXGOfHn3aOh9MGg0d6L9jg/ZbVyP4qc5+jrfSN6VNVxbs9rbatFY01um5zzVRcqqmqffns3l2rP8ZHN6D9Da3jjXV2NVFNdOp0V+iZmM9Zju8Pxfsmu4d3/U7VqaK7VdquYicTHNHhMe53Po14xp4S3qdxjR0amYs124pqr5Y6vZbp6VuHuJrNFPFHBun1FdMYpuWbuKoj3TKy5TJmasdX6At73TT8X2dri5cq0mroq9ZbmfZjEdKojwdn+0prtLe37a9LTVT6+xYqqve6Kp6R8ektO16SOFuH7FyrhDhSjR6y5Ty/adTciuqn4RD5pvu56ndd0v67U37l+7dr5q6656yzOLfJ3W5/x6vtP7MlzGj3qiJjm57dcR7vaeb9Oe0a7UekC9Xb0d27Ospt1WeSmZz05cRjxy8n6POMtXwlvE6vT26b1q5RyXbVc4iqPj5w+l7v6b7FWhn/C9ni1ruWeW9eriuLXvp97HxZ48vaNTKZYaeP4LuXuAfSJpqNzimmbFcWtXTTOeWK6YiqJ98RMZ98P0DxpwzoOMOG69v1FcR2uabUUdeWqYxEx5xPTPufkjXbhqL2tuaqu5XXerqmquuuczVVPWZn+r6L6OfSzuXDu307ZrrMa/RUf5dNVWK7fuiry9yc3Dnb2x+zjzk8rV3n0P8X6DWTb0+2Va61mOS7ZriYqj3x4PV8B8Ff7C27nG3F1Fq1G3U+t0ekirM13v4M/96Okd/Hwd9qPTlw9a0HrNPs+uuX6v4a64iI/PyfI/SDx/uvFuoirVV02NNRVNVrTWp9iJmMc0+c48V47yX/IymE+nmd311zXblqNXeq5r+ou13LtUeNVWZq/vVL9Q8QWL+u9Hmt0+mo57t7bc0Ux1mfZiqMefSJflGzcijUU3Mdp7PrnA3pgjadk0227poK9VOlp5LV63cxVyZ6ROe+O35Q1z8WWeuv6Z48pNvAaLhbddfpNy1tnTVUWdBbm7qblz2aaYziKYmfGfJ33oMs1V+kLbZojpT6yavd7Eub0j+k7W8T2v8P0di3t22RVzTYpxm7V4TXMd/gw4C4+0fClqbmn4d0V7W1U8lWpqvVRVNPljwdM5lljYzNTLb337SmmuTtez3OWOSJu05/8AhfOfRJv1HDnFun1d+YjT1ZtX/D2Ku8/l0n8nqOI/S5pd+0MaHdOGNv1Vj71MVX6s0VecT4PlOsv0zqq67NFNujmmaaYnMR5dXPDit4+tbuU7bfrrj3hfR8ZcNVaO9cppqnF3TX468szHT8ph+d9z9GHFeg1tenr2i/eiJxTcsxzU1++Jdz6PPS7uOwaGjb9dp53HS0dKKZr5a7ceUT4x7ns9X6ddlp08zptl1s3sfcruUxTE++XDjx5eO9Z9N3LHL2uk4Y4Y/wBgNi1nF/ENNFrV27FVrb9NVMTV62qMc0+/q6L0BV2L3HtN2/yzenT3a7ef5/P493mPSBxxufF+rm9rIi1ao6WbFufYtx+sz5uj4c3bU7NudrX6O7Nu/aqiqirw/N67hlcLK5dpK+4ftC7Pr9w2/b9do7Vd2zY56L1NEZ5M/wAUvnvo34N3vdN7013T6SumxavUV3b12OSiIifOe73e2emzQV6SI1uy3atRMYqi3cj1dU/CXleL/Snum8amzRpaKNBo7F2LlGns9qpiek1T4vPxY8vS4OtuNu32T00aXUX/AEca+ii3NcxVTVNNEZnEVdX5h4l2fWbRfsU63TTp69RZi/RRVPXlnOJmPDs+z6j05WZ2qaqdo59bVRiee7E2+b3x37+D4xxVvOt3/eL26bhqKr+ovfeqnw90R4REOn43HljPWOXKZXx1Mwh4EPU4wTJJgFEnuoGWUMMMqJSlZwrGJnLJK50JWElEWCCDxBY7Nna/xNXyfrDXiOjY2v8AE1fJ+sEWOzAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugTKpgVUyqYBUwoAAAAAAACZBQADM4wALzSc8+aJAMuafM5p80AZTcqiMZTmnzQBl6yrGMnrK/P+zEBnFyqZic9YZTcqnv16YcRkHJXcqnvOWEV1ROYnqk9UgGfPV7v6JzT7kAWKpiXJF2rHfDhUHJNc4SblXLjLABfWVYxkzMxGWOFBcyRVMIAsV1ZzlfWVTMTOP6MQGU1TMdfFiABE4AF56ojETOPIpqqjrEoRMR0BlFU9/EykTkyIyiqYjpLCapXPRifSs6JnHc5pifBiAy5p7GWCgy5pjpCc1XmgDOLtcdpSa6p8WIGn0z9nextt/jm1VuNduKqKKqtNTcn2arsdvz8nv/TX6Od54g3T/GNmiNTc9XEXLE1Yq6Z60579+z8+aLU3NLdouW6q6ZpqiqJpnExMdpiX0zhv01cUbVao09+5Y3G1TGP95pnniPmh5uTjz7dsHXDOa1Xm9R6P+L7MzN3Ydwp8/wBxLteFvRdxhueopztV3R2Y61X9THq6KI8Z6vZT+0LucW5i3sOioueFU6mqY/ph47jT0tcV8T2Z02q18aXTT3saSmaIn4z3lZeXLzKM24Ruek3edBodq0XBWzainUaPba667+pp+7qb05zMe6M4fNL1VVWaswl29zV80zMy4ZqzGPB1xx6sW7Myy56pqmZnMyxGxnzzExMdyblXTr2YALNUzGOiTMyAC0zhAGXPMT0SquZnwYwoLnPdJAFiqYImUAWJmJIqnvnqgDOblXhLGapnugCzVM9+rKmuYhhADk9bM9ZYc85mWMKf9DLnk9ZV7mIBzTPeVmqZnqxUGdNcwVVzjEdI8mBILzz5r6yrtnow7mAZTXPY5pz4McKDKKpx1X1lX5MJAZc8pzT1QAclijmn2ukeMuNnRXMYiJwEfVvRz6KKuJeH/wDGdTr69Jbu11UWKKaOaauXpMz7svZcEejDb+Fd7vb/AL7uWn1Gj2+Ju2p5cRExH3qs+MeEeeHzzgD0pbpwrorm3U2LOs0nNzUWrszHLM4ziY88NTjn0k7zxRamxfqo0+jz+Hs5iiffMz3l5enLcv8Ap2mWMjq/SPv1fEnFOt3aqJpov3ZqtUTOZt2+1FM++IiP6vLT3cly5zT0/u4/F6McdTTlld0AaRaapp7GZQBlFU9iJx4QxzgyDKKp8cHPV5sQGVNdUT0lfWTjw/owAXmk5pxEeSAE1T3ZU11dfexAZTcq7Z7lNUwwXJoZ1Xa6oxVVMsZqmUAZc8+5OaYjogBFUrFUwxwoMuefcvPOMMAGUVzGMTjCc083NOJlAF5pTMxAAyouVR2nC+snp1cagyqrqmcpmcYQAMgCKAIoALRCLRKUrKO7JjC+KVhcgSgZAErKJ6NnavxNXyT9Yarb2v8AE1fJ+sEI7IBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6ASZUUEyZAyqYUAAAAAABMGVAAABIBUUAAAAAAAAATsYAUSDIKJlQATIKAAAAmFASFgAAAEJlYAAAAAJACAAAAAADM5yAMuefNMznugBPWcgAAAAAAAAAAAAkyCiZIACSAUCQAgBFAAAAEkFEhQAAAAASQUABOygLFUwc0ygAACSqd1AAABJBQAAAAAAlIkFAAAAAAAAAACUyCkplQSFAAAAEz1Az1VDIKBIJDKljHZlEdCpWVPVlgpjomZYZXxGOOrKBKCpgQy3Nr/E1fJ+sNPDb2qJ+0VZ/kn6wsajswGlAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CvPqAqYMKAAAAAJlUwCiZUGLJMKCZVMKAigJlUwoAAAAJKgAAAACGFAYsoTCgmTBgBQAAAAAAABJlYBMKAAAAAAAAAAAAAAAAAAAJMkGFAAAAAAAAASVTAIsGAAUAAAEhQAAAASTuACgAAACSCpJEqCQqYUAAAJxgABPEFSVSQIlUhQAAAABJWAAAEwoASAJEqmFAAAAAAASYUBjDJMKAJCgAAIoBLGGUsQZCZUBlT2YQzpKlZx0hIVIZjB4rCRDIqCwkLEoK2ts/z6vl/WGq2ts/EVfJ+sEWOxAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAEkyAoAJlUwoJhQBMqmFAAAAAAAAAABPFUUAAAAAAAABFQFE8VAAAAAABMKAAAAAAAAAAACSqAoAAAAkKAAAAAAAAAAACTIKJCgAAAAAAigACSCiQoAAAAAAAAJhQAAAAAAASO6oCgAmFAAAAAAAAAAAAAAAAAAAAAAAAAEwoAIoAACGBQTCplQGdMdGDOntJUrKOyR3XwYsxhnEmJYrlSsuhDFlEYSosNnbI/3ir5P1hrNrbM/aKvl/WEix2IDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AkyooACYUAAAAAE8FQFAAAABMgZVMKAAAAAAAAAAAAAAAACKmFBJWAAAAAAAAAAAAABJlYTCgAAAAAAAAAAJKgAAHQAAAAABMKAAAAAAAAAAAkncOwCgACAoigJCoBJEhgFAAAAAAPEAAASSJVMAoAAAAAAAEpEqmAUAAAAAAAACQBIlQAAAAAJAGML4goAAAJhQAZUyxZUiVlTOTCRGGSM1YjKSsSk92dpSGUTlFpEVtbZ/n1fL+sNWG3tsfv6vl/WCLHYANtAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXn8KAoAAAAAAAAJmVABMyCgAJhQASFAEzKgCdTMgomZUAAAAAE6gomZMyCiZlQAAAAAABOpmQUTMmZBU8VQFABJlYTCgAACdVAE6rAAACTKpgCFAAEkFEzJAKAAACeKooAAAJIKJmSAUABJVAUABCTqCidTMgokKAAAAAAAAAJJAKniqAoAAJIKIZkFEzJAKACQoAAAAAAACZk6goAAAAAJhQABOoKJ1MAqSqAYJUBMqmFABMyCiZk6grKliygKyVIUc6QuEhWECAgGcQ2dsn9/V8v6w1obO2/59Xyz9YIsdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FefmTJJgVQATKphQAAAABJUAAAAAEyAoAAAAAAACZMgZViygAAAAEyqYUEyrGWUAJkyYBYAAAAAAABJlYSe5kCZWE7qAAAAAAAAAJMkAoAAAAAAAAAAAAAAAAAAkkAoAAAAAAAAAJJAdgUSFAAAAAAABJBRMmQUSJUAAAE8QUEkCSJO5gFAAAAAAJAEiVTCyAJkiQUAAABFABM9VAAABMgoAAACQoAypYsqRKyUBmkKkLlhlcGCJMgyhtbb+Iq+T9YakNrbfxFXyfrB+1jsQG2gAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+grz+FAUABMqmFAAAABFEyCgACZMgqYUABJBQAATIKJkyBgwZUGLKEwoAAAAAAJhRMgYUAAAASZBQgASZJlABYgwBlYTCgEgCeCwh2AmSDuoAJMgYVMkAoAAAAAJMkEkAoAAAAAAAAJIAZMgokKAAACSCiZIBQSQVCFBFCQBIUASJJBRIkkFSTJkCDCLkDB4k9lABPEFRQBJJO4EEmCQUSFBPFU8VAAkATJkFEiVBJgjuqYBQAAAAJBMLKZMgZVjDIBMKACYWQTKsYZAAAMqWLKkKy6qAwAnizEWFiEhYSlZNnbPxFXyT9Ya0NvbfxFXyfrB+yOwAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAABMmQVMqxBkxZJgDKphQTBhQEyqYUBFTIKmVTAKxlkmAMGDKgxZQmFAAATKpgDKpgyBlWLKAEwoAAAAAk91TAGVhMKCYSWST3AjsqQoAAJMrCYUBMKAnYgwsAJhQEwoAAACTJAKACSQTBAKAAAAAAJMkAqEyQBgwoCKJIKJlQEUBJIJIAk7kkAdiCSAUAE7ESSQBhUkiQOxkkwBBgiFBMGFARQARQEkyspgDuYIhQSTKykwCLEouAUkASJJ7GFBiLhAFiTBHcFlIlUwCgABKRILKd1TAGDCymQMCgAAAAJhQARZQFZUpC0iVkZVMFZqoowELCQsCVk2tt/EVfJ+sNVtbb+Iq+X9YJ9kdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAAmVTCgmDBlQEwoAACZVMKAAAAAmFTIGVTCgAAxllCYUAAAAAABMKAmFAAAAABJlUwCgACZUEmUXBgCFAAAEmVhMKAAAAAAAJ4kAoAJMEKAAAAAAAAAAAkwQoCTB2VJAhUhQElUkCSCSAVJUAEhQAAAAASQJIgiVBJIhQEkySYAiSSIJBQAElUkCJVI7qAkqSCRKpEKASAJhQAAAlIlUwCphQBMGVAAAABJ7IyTAGSJMGAVMKAmVTCgAAAmQUAAFiBKyhYhIUSqAIAM0FyiIM4nLb2z8RV8n6w06W5tn+fV8v6wRP27EBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAcWq/C3fkn6OVx6r8Ld+SfoK8/hQFAAAAAAAATKphQAAAAAAEwoAmVTAKACKigAAJlUwCplUwCgAAAAAkqkkdgURQAATCgAAAAAAAAAAAAAAAACTJBMEAqTKpIEKkKAioCgAAkyBMkHcgFAAAAAAABJIVJBRIUAAAAAABJUBIhQAAAAAAAAAABFAAEkFEiVAAAAATKpgFAAABMKAAAAAAAAAAAAAAACYUAAAhnEMKe8OTMeYlIgxiVjHmCUAEAISpSYFliysZUtzbfxFXyfrDUpbm2/59Xy/rB+0/bsAG2gAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABQAAAASFAAAAABMgoAAAJlUwoAAAAAAAAAAAAAJkFRUBQAJAAAAAAEyoAAAkkdgUAAAAAAAAAAAAAAAEhQAAAAASYUBOxBMEAoJMgomTuCgkAoACSSQBCgAAAAAAAAAAAkkncFBJBRIlQAAASQUSJUASSJBQAEz1VMdQUAAAAAAEyCiZPEFBJ7AZMouAMmTBgFAABMgoICgACZUEhZTsZAhn0YKDOMLlx5ZUCWMwBmixCLDO0oAgsQ29s/z6vl/WGq2ts/z6vl/WCfZPt2IDbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAqZVMKAJlQSFTKgmVTCgAAAAAACZMgoAAAAYnyAAAAAAAAAAAAAAAAAAAAAAQFAAEyZBQAAAA6gAAAAAAJMkEwQCgAAn5AoAAkyQCgAAAAAAAJCpAEkEkASQoAAAAAAAAAAAJKgAAAAAkgSRJMkAqSoCRCpJgFEAUSIUASTIKJlQAAAAAQFTxUAABMKAAAAJIKJhQEUABMgYUSAUAAMSAMqGLKiBKzEVKzViAiRlkXCLlKLHVtbb/n1fLP1hrU9m1tv+fPyz9YWLPt2ADbQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoADFkmFBMKAAAAAAmVBMqmFBMGFABIUASVAzPmAAAAAAAAAAAAAAAAAAmFAAAEUAABMGFAAAAAOoACZVMAQqdjIKJkgFAAAAT81AQgmDsBJEpKxAEKkEyCiQoAAAAAkmQUSFAAAAAAABJBRIUBJVJA7qAAAAACSoCYIhQAAAAAEkCTJMpAL3MEQoJhQAAAAARQBMk9iO4KAAJlQAAAAAABMmQVMKAJBlQAAMzhIVIBYZ0d2MQyo7iVVBKzViBaUZSrgwZVKi09m1tv+fPy/rDVjo2tt/wA+r5f1hcVn27ABtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AAUTJkwCiZMgoAAAAmVBMKAAmVAABIUASVEyCiZUATJkFTKsZBkEAAAAAAmVBDIYAyqYUAAAAAAEyqYOwGVTuoAAAAAACZMoC9zBBkDBBkgFAAAABJkFSYMkAkrBMEAoAAAJMmSYSQXJCLAEmCSAIUAAAAAAAElQEhUkgFAAAAABJMkmAIlUiFBJIkkgFABJIkkiAVJVJBFgmCAVJVJAyZRcAoAAAAACdlSewGTuix3AwomQUAAEnsBlWMMgTCMkwBkyYMAYUAEyssYBkkKkAyiWVHdhDOkSsse8RUqLEmUTOZZNMlykAyzbW2/wCfV8v6w1YbW2/59Xy/rBCOwAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFTCgDFcGFAAAABMKAJkyYMAYVMqAAAAAmFATBlUwCLgwoJkwYUAAEyZMGAUAEwoAmVTBAKAAAAAAAAk91TAEdlAAAEyqYUEyZMGARYgwQBBhQGMrBMEAokyZBRIUEmTuTB2BJWJO5gCCZIJgCFSFAAASYUBMHZUkDudiCQIVIUAAASSAJIJIBUlUkCSDBAKAAEACSqSBkiUhYgFEkiQJIJIgFBAJMkmAIlU7ESBKQsoC5O6LEAYUAAAAATJ3MGAUAEwYUATCgAJkFTKpgEXJgwCiZUATKgAAJhQEyqYUFhlSwhaRKzhUhRKIowhCpCwJVht7Z+Iq+T9Yara2z/AD6vl/WCEdiA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdACTIqgAAAAAAAAAmVTCgmFABIVIBQABMqCZVMKCZVMKAAAACZVMKCZMmDAKCZBUUAEz1UAAAAEyqYUEyqYUAAAEyCpkydwMqmFBMrCYIBQAAASYSWSTAEKkEyCpMEKCQoAAACKAAAJMkATJBMEAoAAAJJkkwB3OxBIGTJgwBBJBIEKkKAACdjJJgCJJIgkCJVIhQSSIUAABDsEgRJJBIEyQYIgCUhZIgDCgAAAmVTAGTJg7AqZMoC5MmDAKAAACT2RkmAMmTBgFABMKAJhQATKpgFAAABYWmOqR2ZUdxmrhQKgAwGFTKgybW2f59Xy/rDUjs29s/EVfL+sLEjsQGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groGMrJgVQAAAAAAAAABMmQUAAAEyqYUGK5MGAUTJkFBMgomVAAAAAAATBkyCgmQJUAAAAABMkAomVAAATBlQTCgCZVMKAJkyCiZWAAAAASZO5MEAQqTJkFEyQCiTJACgAACTBCpMgqSZJBRIUASSAUEkFEhQASQUSFAAAABJIkkiAJIkkiAUSSJBRJIkFAASVATsRJJAKkqkgonYyCiZMgoAAACd1TsBgwZMgomVAEMgoAAAJlUwoAJkFEyoAAAJkFAAhUUSjKjumCnuIzAKlAGAiFIkhSMqY6Nvbf8+r5f1hqU9m3tv8An1fL+sJPtP27ABtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK8/MKAoAAAACZBQAAAAAAAAAEyqYBQAAARUUAAAAAAAAAAAAAAAAAAAAAAAAEmFgTIKAAAAAABAAACTKpMAsCQoAAAAAAJMkEwdgUSFAAAAAAAAASVASFAAAAAAAAAAABJVJBRIUCBIUAAAAEkiFACRJBQAAAAABMk9gUSFAAAAAAATKykQCgAAAAAAAAAJhUyCoqAq5hjCgy5iKo8mK090NM4lWMMktZoBCIYZRCQyNptYbW2/wCfV8v6w1YbW3fiKvl/WEn2R2ADo0AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAAKAACZUBMKAAAAAAAAAAmQUAAAAAAEyBhQAEyoAAAAAAAJIKmVTHUFAAAAIAAJTsCgAJMKAQAAAAABKQoAAAip4goAAAAAAACTCgJCgAAAAAAAipIKJMkAKkKACAoAAAAAAAAAIoAAAAAAAAAAAAAAAEpkyBEE9lJBI7KAAAAAAAAAAJ4goAAAAJkFAATBlQAATCgAtHdCJxKUZxPVWMd8rmUSzbIhFhGFhkxWMylRlDa27/Pq+X9YasNrbf8+r5f1gn2sdgA6NAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACpkyi4AwoAAAAAAAmJUAAATJhGQAACdVAAAEwoAADGWUMZZQAACdVAE6mVTAGVTBkFAARUkFAAABJ7mCYWAIABMqkwsAAAJ1UBMSsAAACZMkmAUSOigAAJKpMAdTsdjuBlUwQCgAAAAAAACABJJgEWCFAAASFAEDuBkMHYAO5AKAAACSQoAJlQATIKAAAAkqAkKJIGTuYIgDCQsmAMqkQoAAJ1UJBMqnYyCplZSIBQAAAE6qAJlZTAEykLgwCpkyYBIZJhQAATKpgyCgAsSuWMLlLBnErDGGUd0c6sMo6MWTNRW1tv4ir5P1hqw2tt/z5+WfrBPtY7AB0aAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFTCplQBDIKAAAAJlQTKphQBMqCQoAAmQUTKgAAmVTCgAAmFAAAAAEyqYUBMKAJlWMgyEjsoAAAAJlUmDsCgAAAAAAAmTJMGAUSFBJggyoCQoAAAmVSYA7kEGQUAAAATsoJkJggFBAJIJIBQAElQEgCQFSFBJIUASVASFAAAAABO53IgCIUSQJkgwRAKB4gJkkiAUAATKgAmQUAAAAAAACUiFAAABMqACZBUydyIBQJBMmTBgDBkyYBQTIKJlQTJgwZBQIEWI6JhlDLCU2kdGVKMoZZoQLEJWWVPZtbb/AJ8/LP1hqw2tt/z6vl/WFxWfbsAG2gAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HFq/wALd+SfoK6DJkwgouTBgCUAGQACZMmAMGVTAGVTCgmFTKgAAJEKAxZQmFAAAABMqmFAAAABMqmFAAAAATCgEAAAAmVSe5HYDJ3JhYBOypPcjsCgAAAAAmTJMIC5MmDAHcghQATIGTJ3MAZMmDAKkwQoJCgAACSQTBAGQkgFSVATBCgAgCgAkoskAQoAIqSBkMEAoAAACdySIAiFE7gZMmCIBUySRAKAACZBUlUkCDJgwB3IgiFAAATKykQCplZTAGTKLEAqZJ7EdwUkASIUAJTCpkDsZWUiAUABMrKYAwZVMAqYUBjDJMKAmFAFp6otEYErKInLIQrKrCMqWEphREqMobW2/wCfPyz9YasNrbf8+r5f1gn2s+3YAOjQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0CYUFEyqYBFwi5BUyZQFwqZUAEyCgAmFAAAAAEyqYMgoJkFAAEUAABMqmAMqmFAAAAAABMqmFgATKgk9yOxPcjsCoqSBMLAAJlUmAUTsoAACTCgJCgAAAkwoCQqZUAAEyqTBAKAAAAJlQSYIUAAAABJIUAABAkgFEUAAAAAABA7gZVOxkCSIUAA8QAAAASTsqSBkyYMAZVIUATKgAAAAEgCdjKykQCykQoAAABIJ3IgiFAEmSOwKCZBRMqAAAmVliC5VMKAABDKlIWmBKyyRBg6jNVYYLEs6Ss+vmZljlSxGUS29t/EVfL+sNOOzb2z/Pq+X9YST1Y7EBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AEyKZVMKCYMKAmDCpkDCgAmFAAAAAATIKAAmFAEwoAAAACZVMKAmTJgFAAAAAAAAABJ7kdiYOwEwsAAAAAAJlQSYWABMqkwsASkKmOoKAAAAJlQSYIUAAAAAAAABJg7KkwBkMEAoAAAAAIEkAoAJCgAAAAAACSRAZAkiFAAAAAAAAAAAElQEiFAAAAAAAAAAAEVIiVAAABMgpIAmFgAJTCnUATqoAACYMqAAAACrEpEKJWUSJESyErFYknuiIyhWMT1ZJUWOzb2z/Pq+X9YasNvbf8+r5f1hJ9kdgA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FdAmBRUyZRcAoACYFBMqmFAAAAAAAYskwCgAIqeIKAAAAAAJKgmFAAAAABMqkwCgACZUBJhQCAAAAAASYWBMgoAAAAAAACZVJgDuQdlAAAAAAAEgyCgAIqeIKAAJCgASAJ2MgBJAKIoAAIqSoAAAAJJEKAAAAAAAAAAAAAAAJKgJCgACZBRMqAAAABmQAAAJSIUAABMqACfmoAACKnioJhUyoAAAAEZwzpmezDwWJwDliUw4+aVzIliyJlUrKx3ZMYlklSsobe2/iKvk/WGpDa238RV8v6wn7I7EBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK8/jqoCphUyoAmVBIUAAATKgAAAAAmTKAyAAABMmVAAAAABMqAACZMqAAAAAAAmFgAAATJlQAAATKgJMKAQACZXPQAAAATIKACeKgAmVATKooAACTCpkCFAAAAAAAAAElFkgDBCgJKgAAAAAIZBRMkyCiQoAAAAAACZJIBQAAAAQFAAABJMKAkQoAJlQEyZUAAAAAEUAAAJQDKp0UBMrKYAyqYUEwoACKCZMqAAAR3ZYYx3ZZgEWEjutPdKzWUQySFSs1Ylt7Z+Iq+WfrDTjo29r/EVfJP1ghHZANNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4a78k/RyOPVfhrvyT9BXn8qkworFkmDIIyYsgAAAAAAAAEyqYBFwYUAAAAAAAAAAEwoACKAnVQBMqxkFyqYUAAAAAAAAATKgk9yOxJAKAAAAAAAAkwoCQoAAAAAmJIUAEyoCTCgJ2VJIBQAAASFTKgAAgSQCgAipCgCGQURQSUZJIIuCFBIhQAAAAABJAmSEWAUEkFAATxVMAoAAAAAAAAAAAAmTIKSAJ4LAAAAAAkQoSCZVMKAACZVMKCSdVAAAAAEXC4BaexHdYxjBCVmsoVFylZqT0bW05+01fJP1hq4y29q/E1fJP1gix2YDSgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACjFkxAZJhQAATKphQBMqCZMmDAKAAAAAAAAACZVMKAmVTAKACZVMKAACZQlcAZViygAAAAAAAAEnuR2JIAyqSQCgniCgAAAmTJPdAXKsVgDKpJAKAAAACZAkiTuYBRIUEkhQEnuoAJlUkCSDBgDKpggCSCSAUABFSQJQAWDJgwBkkwgLCpCgkhJ4gqZJQFyZRYBQSQO5BCgAAAAAncDKp2MgqZJIgFAAAATJICpJlQYrHcnskAyTIQCgACQsgmVSFkEyZMGAMmUAXKphQAAEyssQZJkykAyWEWBFjrLLEsaO7kErHCYZSM7QMDKO6JTDa2uP8Aeavk/WGthtbZ+Iq+X9YJSOxAbaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFEwqZAyqYUAAEyqYUEwoAAAAAmVTCgAAmVTCgAAmVYyygAAAEkFTKpgFBMgksoRQTCgACZBQAAAEVJBRIUEVJIBQARUkgFABJgwoCQoAAACeJAKAAk9SSAI6KkkAoAAAAAAkkAokkdAUSepAEkKAAAAkgSQgC5VisAqSoCQoAAAJKgJgjoqSCiQoAAAAAAJJHRUkCepBCgAACKACZBUkUEhUUEkwKCQogKAAAAgAomTILKYUAAAAAliyliC4MGVAICBKypZMKZZZErIRYYqGGcYYso7IlVtbb+Iq+T9YasNrbfxFXyfrBPsjsAHRoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAceq/C3fkn6ORx6r8Ld+SfoK6AAUTCgAAAJkFTKpgDKphQAAAAAAAABMqAACYUAAAAAATIKmDKgAAAAJhQAAEVJIBQAAAAAAARUkgFAAAAAAAAABJIUAAAEnuQCgAAAAACSQCpKgJCgAIAoJIKJCgkmDKgmCFAAABJOoKJGSQMqmCAVJJMAiwQoAAAAAAJKLKAsKkKAACdIMkmAJlFwQAE9iO4ASQBCgAigAJIBIAQsiAYMKABKAoAAEghhIZSDGGTGGQAEAsMssIU2ljPwWJTwKe7NZZLHZGSaFbW2/iKvk/WGq2tt/EVfJ+sJPtI7AB0aAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CvP5VOiigAAACYUBMqmFAAAAAAAAAABMKAAAAACZVMAoAJkMKCYUAAAASQUIAAAAAAAAAElQEhQAAABPEDxUAAAAAAAAAAASe6gAkKAAAAAkkKAAAAAAAJKgJHQkkwCLBCgAAAAAAAAAAkqkkQCgAAAAAAAkkKAAAAAAAISQBPYjuSQCgACQoAAAAJIqSAQQoAEgCQoAAAmVBMLIAkKkKAR1FpjqBESziFiFhPti5IR3J7kd0sNrJTlMrSDOG1tv4ir5P1hqw2tt/EVfJ+sMz7SOwAdGgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+grz8qAqZVMKACSCgAAAAAmVTCgnxUAAAAAAAEyqYBQAAAAAAAAAAAAAAABMqAACKigAAAAniqKAAAAAAAAACSBlUwQBJCgAAAAAAAAAAAAAAAACSoCR0VJ6kAoAAAAAAAAAAkkAoAAAAAJJ4qAAAAACR3UAAAAAEBQAAAEVAUAAAASAFAAAAAAAAABMKAAAAADOjuwZUpUrkI6JTOVJHNAwLpYLTMQgzYrkzDZ238RV8n6w0ctzapzqavkn6wkhI7MBtQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvwt35J+groABUyqYMgomVAAAAATKp+QKAAACZVMKAAAAAAAACZVjLKAAABFBMqigAAigCZVMEAYIUBFRc+4BFQFAAABJIVAUAAAAAAAAAAAAAAAAAAAASepAKAAIoAAAACSoCQoAAAJKgJ1IUAAAABJMKACSeIKACZVDxBQAAABJUBMqn5AoAAkd1BJIUAAAABDqKAIoAAJPYjuSQCgAJlU/IDKooAmVAABMqmFAAAEyoLC0x3YwuQZxODmYZMe8ZscnVCI6d2UYE0gsogmG5tP4ir5J+sNRt7V+Iq+SfrBsdmAqgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQAmRTJgwoMVyi4BQAAAAATKsVyBkyYQGQmVAAAAAEyoAAJgVMAoAAAAAAAJlUwoJlUwQCgAAAJkkwBkyYMAoigJKgJCgAAAIoAAAAJPdQAAAAABJBUkgkCFSFAAAAAAAAAAAAAAABJBRIUASSAUAAAAAAAASSAUAAAAAAEkFSSFBI6KkkAoAJJCgAICpJIAZJQFVI7qAAAAACAqSSYBFygC5MouAUAAAEMhgFEhRCO7LEsY7w5MiWqJCptCQEtDEtvaoxqKvkn6w1o7NvbPxFXyfrBKunYgNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0EsVQVkmTKAMkwoAmSAMmTBgFEyZAwYVMgqYUBMKAAJAKJKgxllCYUEyrGWUAAAAAAAmVTACpkygMggAAAAAAAEUARQSSFAAAAAEVJBJWEWAVJMqCQoAAAAkgokKAJJAKJJAKAAAACZBQABJ6kAoAAAAJIKJCgAAAAkqJkFAABMgoAAAAkkAoAAJIGTKAMhIUBMkmAUSFAABJIFABJAJSFAhRAUSSAUAEnsR3J7EdwUEkCTBhQTCiZBRMqAiyxBcKmTIEKAlWO7KWEd2XURlHZUhcIaRVwqVL4kNvbPxNXyT9Yajb2v8TV8n6wkWV2QDYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI4tX+Fu/JP0FefFwgoC4AyZMIAuTCAuTKALhFySBkwjIAAAAAABMqmAUEyCSyhFAAAAABMgqYMmQMGDKgJlUwCiQoAAAigkkBkCe5HYIBQAAABDIKJlQSTCgMVgkgFAAAAAASVATBCgJJBJAEkKAkkKAkosoCwT1PiQBHRUkgFEkgFBJBRIUAAEkjoqSBPUghQSTCgJCgCSYUBIVMqAAAAACSCiQoJJhQEhQAAAAASVASFRQSTCgMVjuSQBJCgAAAAJPYjuSR3BQSewGVYsgJYskwBhRMgssVykAuEZJgCFSGUCUiJyyWIMM7Z2YZRMIL9m1WGMd2eEy8S3aYltbX+Iq+T9Ya0NvbfxFXy/rCS+kdgA20AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI4tX+Fu/JV9BXQZQBVwoAmUAGSYUBiuEZAmDKsQXCgAAAAAJlQAAEwoAAAAAAAmDKgxXBKgmFTKgAAAACZUEkhQEkwoCQoAAk9gFSO6gk90We5AGCFASSFAAAElQAEkDKsVgCSFAAAAAAAAASSFASSFAAAAAElUkCFSFAAAAAAAAAAASVATBCgAAAAAAAACT1JIAhQABJBRI7KAkqAkKAAAAigAAAAJJCgmCFQFSVATBCgCZVAWWK5QAgIBkmVQCGVMdUwygSsxjEmWbGayRMrHUniLHdyONllLuhlt7ZOdRV8n6w023tf4mr5P1gkI7IBtoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAcWr/C3fkn6OVx6r8Ld+SfoK88MmIq5ViyBiDIAAEyrFkAACZMmDAKAAADFkAAJIKAAmVTAGVTCgAAhlUBQAToqYUAAAAGMrHYkjsCgAAAniqYUAAAAEnujIBI7KJgFAAEwoAACSoCQoAJkwYBQhMAoAAk91ASSSAIUAAQFBAUABJUBIJUBIUABAFABJIUAAAAABMAoJgFAAAAAAAABMAoAAJPYDJlAGQkd1ATuqYAwoAiphQTxUAAASeyQyTAGTJgwBlUwoJlZTACLlAFyCgAAsdhYjoglAURVhFgKpAmUrLOG1tf4ir5P1hp8zb2r8TV8k/WCEjswFaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAAAAYskhQAAAAAAAAAAAABMKAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAnioCQoAAAniKkgokKAAAAAAAAAAAACSoAAAAAAAAAAAAAAAAAAAAAAAAAAniCpPZUnsBHdUjuoAAAAAAAAAAAJPYFEjsoAn5KAAAigCKAAAJ1UBlHZKiOySBEsoYwojOFYRJkRkiZUFbm1fiavkn6w04bm1fiKvkn6wDswAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/DXfkn6CvPypLEVkxZAAAAAAAAAAAAAAAAAAAAACHVQAQFGLIASO5PcFAABOoKMWQAAAAAAAJ1BQASSOxPcjsCiT3I7AoAAGQAAAABJIBU8VASFAAEkFEzJAKAAAACeIKJCgAAAAnieKgAAAAAJIKJCgCSQCgAAAAABkAAAEkgFAAAABJBRIlQElQEhUkjuCgACQoAEgkKmSO4KCT2BRIUAAAE6goAAk9kBkIoBIAxhkkKAACx2SpY7FQMYZJCiAAgyjskKluhlEQ3Nrj/eKvkn6w06ezc2z8RV8n6wSpt2QCqAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOPVfhbvyT9HI49V+Fu/JP0FeflQFAAAAAAAAAAAAYjIBiyAAAAAAABBQAAAARQAAAAAGLKAAAAAAAASewKJHZQAAAAAAAASexCgAk9yAJIJIBQAAAAAAAAAAAAAASQUSFAABJIUABJBRI7KCSoAAAJKgJCgAAAAAAAkqkgQrFYBQAAAElUkCFSFAAAAAAAAASeygJCpPYgFABJ7Ed1AAAASewKIoAk9kBkAACAoAAALHYqWOyVifaQqQoAKIQpgjulKyhubX+Jq+T9YasRDa2v8TV8n6wmLLsgGmgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABx6r8Ld+Sfo5HHqvw135J+grz8os90FZAAxZAADEBkAAAMWQAxZAAAAAAAAAAACKAAAAAAAMZCVBGUIAoAAAAAAAAkkdgUAAAASe6AyEjsoAAJPchQAAEwoACSQCgACSQCgkgokKAAAkqAkKACSoDFYUBPE8VAAAAAAAAAAAEUBMKAJKMgGIySQRYRYBQSQUYgLKLCgkKAAAAAAkKAAAAAkk9iO4Ed1AASexHcFAAEnsR3BUnsqT2BAAIZIsgEsVBAAZDGGQMqUrWEqE+khSknuAqKIsMo7sYhY7hZtk29r/E1fJ+sNSlt7Z+Iq+T9YZjM+3ZANNAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADj1X4W78k/RyOPVfhbvyT9BXQACgAAAAAMWQAAAAAxZACQoAAAAAiMgAAAAAAAAAAERkAIoCR2UAEkI7AR2UAEkkjsBHZQAAAABJ7oyASOyieIE9yFAAAAASSFAAAElQEhQBJIUAAASSSAIUASSFAAAAABJIBQAElUkCCSFBIUAElQEhUkgCSFASUZAJBKgJCgAJCgkoyASFAASSAUAAAATxUBJ7KAkd1AAAAAASexAKJJHcCeyMgGIyAYqoAADEZAIoAigDKEqWlKhEjuzYR3ZgYIjoKAE9khKjKG5tf4mr5P1hqR2be1/iavk/WCMz7dkArQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Fu/JP0cjj1X4W78k/QV0AAoAAAAADFkxZAMWQDFkAAAAAAAAxUFAAAAABJUAAAAAAAASQUSCOwKAAk91Se4EdlSFAAAAAAAAAAAE8VAAAAAABJIJIBQAAAAAAAAABJIBQAAAAAAASSFAElQEhQAAAABJRkkgQrFYBRJIBQAAABJIBRJIBUlQEhQAAAlOqgAk9iO4E9iO6gAAAAAACST2I7gR3UASexHdQAAAAAAGIqAKigKAMqUqWEqESO7NhChGQiirCC+CVmsobe1/iavk/WGpHZt7X+Jq+T9YTFmOyAaaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHHqvwt35J+jkceq/C3fkn6CugAFAAAABiAyAAAAAAAAAABiDJFAAAAAAABjLKAAAAAAAASQUSOygAAAAk9yOygAAAAAJPcFEjsoAAAJ+QKAAACSQoAkqAkKAJPdUkBQAAAAAAAAAAkABJBRIUAAAAAAAAAAEkhUkFEgkFAAABJUAElQEhUkgFAAAATxUAAAAAAAAAAAAAEkjuCgAAAnVQAE/JQAAQWWMAqgAJHYjv2BnE9EkZTEYEqRHQQkIyJI8GQrGGQkM1jJlDb2v8TV8n6w1aW1tn4ir5P1giR2QDTQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA49V+Gu/JP0AV5+e6gKxZAAAAADFkAAAAAAAAAAAAAAAAAAAMZZQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJKAAACwoAAAAAAAAAAAAAAAAAAAJPYAI7qAAAAAJPZABY7qAAAAAAAAAAAEsYAGQAAAL5ACUJAIsdmYJSgDLFZUtra/xNXyfrANQjsgFaAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAf/2Q==" alt="Rejuvenese" style="height:48px; width:auto; object-fit:contain; filter: drop-shadow(0 0 6px rgba(201,168,76,0.3));"></div>
  <div class="footer-legal">Aplican restricciones. Valoración médica requerida. Cupos limitados.</div>
  <div class="footer-links">
    <a href="#">Términos</a>
    <a href="#">Privacidad</a>
    <a href="https://wa.me/50684354162">Contacto</a>
  </div>
</footer>

<!-- WA FLOAT -->
<a href="https://wa.me/50684354162" class="wa-float" title="WhatsApp">💬</a>

<script>
  // CURSOR
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });
  (function animateRing() {
    rx += (mx - rx) * 0.15;
    ry += (my - ry) * 0.15;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  })();

  // NAV SCROLL
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 50);
    const prog = (window.scrollY / (document.body.scrollHeight - window.innerHeight)) * 100;
    document.getElementById('progressBar').style.width = prog + '%';
  });

  // SCROLL ANIMATIONS
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.15 });
  document.querySelectorAll('.animate-on-scroll, .proceso-step').forEach(el => obs.observe(el));

  // STAGGER DELAY
  document.querySelectorAll('.incluye-card').forEach((el, i) => {
    el.style.transitionDelay = (i * 0.08) + 's';
  });

  // FAQ
  function toggleFaq(btn) {
    const answer = btn.nextElementSibling;
    const isOpen = btn.classList.contains('open');
    document.querySelectorAll('.faq-question.open').forEach(q => {
      q.classList.remove('open');
      q.nextElementSibling.classList.remove('open');
    });
    if (!isOpen) {
      btn.classList.add('open');
      answer.classList.add('open');
    }
  }

  // COUNTDOWN — set your target date here
  const targetDate = new Date();
  targetDate.setDate(targetDate.getDate() + 18);
  targetDate.setHours(9, 0, 0, 0);

  function updateCountdown() {
    const now = new Date();
    const diff = targetDate - now;
    if (diff <= 0) return;
    const d = Math.floor(diff / 86400000);
    const h = Math.floor((diff % 86400000) / 3600000);
    const m = Math.floor((diff % 3600000) / 60000);
    const s = Math.floor((diff % 60000) / 1000);
    document.getElementById('cd-days').textContent = String(d).padStart(2,'0');
    document.getElementById('cd-hours').textContent = String(h).padStart(2,'0');
    document.getElementById('cd-mins').textContent = String(m).padStart(2,'0');
    document.getElementById('cd-secs').textContent = String(s).padStart(2,'0');
  }
  setInterval(updateCountdown, 1000);
  updateCountdown();
</script>
</body>
</html>
