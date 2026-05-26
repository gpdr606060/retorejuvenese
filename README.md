


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
  .nav-logo {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 1.1rem;
    letter-spacing: 0.15em;
    color: var(--white);
    text-decoration: none;
  }
  .nav-logo span { color: var(--gold); }
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
    grid-template-columns: repeat(3, 1fr);
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
  <a href="#" class="nav-logo">REJUVENESE<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#incluye">Programa</a></li>
    <li><a href="#proceso">Proceso</a></li>
    <li><a href="#precio">Inversión</a></li>
    <li><a href="#premio">Premio</a></li>
    <li><a href="#app">App</a></li>
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
      <span class="hero-eyebrow-text">Clínica Rejuvenese — Programa Médico Integral</span>
    </div>
    <h1 class="hero-title">
      <span class="line1">Reto</span>
      <span class="line2 gold-shimmer">Rejuvenese</span>
      <span class="line3">10 Semanas</span>
    </h1>
    <p class="hero-desc">
      El programa de transformación corporal más completo de Costa Rica. Ciencia médica, tecnología, nutrición personalizada y seguimiento clínico semanal.
    </p>
    <div class="hero-checks">
      <div class="hero-check"><div class="check-icon">✓</div> Evaluación médica completa + laboratorios</div>
      <div class="hero-check"><div class="check-icon">✓</div> Seguimiento clínico semanal especializado</div>
      <div class="hero-check"><div class="check-icon">✓</div> Nutrición + entrenamiento personalizados</div>
      <div class="hero-check"><div class="check-icon">✓</div> App de progreso con gamificación</div>
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
      <div class="incluye-card-desc">Diagnóstico clínico completo para diseñar tu plan personalizado.</div>
      <ul class="incluye-card-items">
        <li>Historia clínica detallada</li>
        <li>Análisis corporal + bioimpedancia</li>
        <li>Laboratorios metabólicos y hormonales</li>
        <li>Valoración nutricional</li>
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
        <li>Ajuste de plan nutricional</li>
        <li>Revisión de métricas corporales</li>
        <li>Optimización del programa</li>
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
        <li>Protocolo médico individualizado</li>
        <li>Optimización hormonal y metabólica</li>
        <li>Ajustes basados en laboratorios</li>
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
      <div class="incluye-card-title">Nutrición Personalizada</div>
      <div class="incluye-card-desc">Plan alimenticio diseñado para tu metabolismo, objetivos y estilo de vida.</div>
      <ul class="incluye-card-items">
        <li>Plan nutricional semanal</li>
        <li>Recetas y guías de preparación</li>
        <li>Control de macros en la app</li>
        <li>Ajuste según progreso y laboratorios</li>
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
      <div class="incluye-card-title">Entrenamiento Guiado</div>
      <div class="incluye-card-desc">Rutinas diseñadas para maximizar tu transformación corporal con guía experta.</div>
      <ul class="incluye-card-items">
        <li>Rutinas personalizadas por semana</li>
        <li>Videos explicativos en la app</li>
        <li>Progresión controlada y segura</li>
        <li>Adaptación a condición física</li>
      </ul>
    </div>

    <!-- Card 6 -->
    <div class="incluye-card animate-on-scroll">
      <div class="incluye-card-num">06 —</div>
      <div class="incluye-card-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="10" y="6" width="20" height="28" rx="4" stroke="currentColor" stroke-width="1.5"/>
          <path d="M16 16h8M16 22h6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <circle cx="20" cy="30" r="2" fill="currentColor"/>
        </svg>
      </div>
      <div class="incluye-card-title">App Rejuvenese</div>
      <div class="incluye-card-desc">Tu transformación en tiempo real, en la palma de tu mano.</div>
      <ul class="incluye-card-items">
        <li>Dashboard de métricas corporales</li>
        <li>Registro de comidas y rutinas</li>
        <li>Progreso visual con fotos</li>
        <li>Gamificación y ranking de reto</li>
        <li>Recordatorios y citas médicas</li>
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
          <div class="proceso-step-title">Evaluación Integral</div>
          <div class="proceso-step-desc">Historia clínica, bioimpedancia, laboratorios metabólicos y hormonales, valoración nutricional, fotografías basales. Tu punto de partida documentado.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">02</div>
        <div>
          <div class="proceso-step-label">Semanas 2–4</div>
          <div class="proceso-step-title">Activación Metabólica</div>
          <div class="proceso-step-desc">Inicio del protocolo nutricional y de entrenamiento. Primera aplicación del acompañamiento metabólico médico. Adaptación progresiva controlada.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">03</div>
        <div>
          <div class="proceso-step-label">Semanas 5–7</div>
          <div class="proceso-step-title">Fase de Aceleración</div>
          <div class="proceso-step-desc">Máxima intensidad metabólica. Seguimiento médico semanal con ajustes precisos. Monitoreo de métricas: peso, composición, grasa, músculo.</div>
        </div>
      </div>
      <div class="proceso-step">
        <div class="proceso-dot">04</div>
        <div>
          <div class="proceso-step-label">Semanas 8–9</div>
          <div class="proceso-step-title">Consolidación y Definición</div>
          <div class="proceso-step-desc">Ajuste final del protocolo. Fotografías evolutivas comparativas. Preparación para la evaluación final y documentación de resultados.</div>
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
  <div class="footer-logo">REJUVENESE<span>.</span> <span style="font-weight:300; font-size:0.7rem; color:var(--titanium); margin-left:8px; letter-spacing:0.1em;">Clínica · Wellness · Estética</span></div>
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
