<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>bellion — README</title>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #fafaf9;
    --white: #ffffff;
    --text: #111111;
    --muted: #888888;
    --light: #f0f0ef;
    --border: #e5e5e3;
    --accent: #111111;
    --accent2: #555555;
    --hover-bg: #111111;
    --hover-text: #ffffff;
    --tag-bg: #f4f4f3;
    --tag-hover: #111111;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Montserrat', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: none;
  }

  /* ── CUSTOM CURSOR ── */
  .cursor {
    position: fixed;
    width: 10px; height: 10px;
    background: var(--text);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform .1s, width .2s, height .2s, opacity .2s;
  }

  .cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1.5px solid var(--text);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform .08s, width .3s, height .3s, border-color .2s;
    opacity: .4;
  }

  .cursor.expand { width: 20px; height: 20px; opacity: .5; }
  .cursor-ring.expand { width: 56px; height: 56px; border-color: var(--text); opacity: .2; }

  /* ── TOPBAR ── */
  .topbar {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 40px;
    background: rgba(250,250,249,.9);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }

  .topbar-logo {
    font-size: 14px;
    font-weight: 700;
    letter-spacing: -.02em;
    color: var(--text);
  }

  .topbar-logo span { color: var(--muted); font-weight: 400; }

  .topbar-nav {
    display: flex;
    gap: 32px;
  }

  .topbar-nav a {
    text-decoration: none;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: .12em;
    text-transform: uppercase;
    color: var(--muted);
    transition: color .2s;
  }

  .topbar-nav a:hover { color: var(--text); }

  /* ── WRAP ── */
  .wrap {
    max-width: 860px;
    margin: 0 auto;
    padding: 120px 32px 100px;
  }

  /* ── HERO ── */
  .hero {
    padding: 80px 0 72px;
    border-bottom: 1px solid var(--border);
  }

  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: .18em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 28px;
  }

  .dot-live {
    width: 7px; height: 7px;
    background: #22c55e;
    border-radius: 50%;
    animation: livePulse 2s infinite;
  }

  @keyframes livePulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(34,197,94,.4); }
    50%       { box-shadow: 0 0 0 5px rgba(34,197,94,0); }
  }

  .hero-name {
    font-size: clamp(2.6rem, 6vw, 4.4rem);
    font-weight: 900;
    line-height: 1;
    letter-spacing: -.04em;
    color: var(--text);
    margin-bottom: 6px;
  }

  .hero-handle {
    font-size: 14px;
    font-weight: 400;
    color: var(--muted);
    letter-spacing: .04em;
    margin-bottom: 32px;
  }

  /* typing */
  .typing-wrap {
    font-size: 15px;
    font-weight: 500;
    color: var(--text);
    min-height: 1.5em;
    margin-bottom: 36px;
  }

  .typed-text { border-right: 2px solid var(--text); padding-right: 3px; animation: blink .7s step-end infinite; }
  @keyframes blink { 50% { border-color: transparent; } }

  .hero-sub {
    font-size: 13px;
    font-weight: 400;
    color: var(--muted);
    line-height: 1.8;
    max-width: 480px;
    margin-bottom: 40px;
  }

  .hero-cta {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
  }

  .btn {
    display: inline-block;
    font-family: 'Montserrat', sans-serif;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: .1em;
    text-transform: uppercase;
    padding: 13px 28px;
    border-radius: 2px;
    cursor: none;
    text-decoration: none;
    transition: all .25s;
  }

  .btn-dark {
    background: var(--text);
    color: #fff;
    border: 1.5px solid var(--text);
  }

  .btn-dark:hover {
    background: transparent;
    color: var(--text);
  }

  .btn-outline {
    background: transparent;
    color: var(--text);
    border: 1.5px solid var(--border);
  }

  .btn-outline:hover {
    border-color: var(--text);
    background: var(--text);
    color: #fff;
  }

  /* ── SECTION ── */
  .section {
    padding: 64px 0;
    border-bottom: 1px solid var(--border);
    opacity: 0;
    transform: translateY(24px);
    transition: opacity .6s ease, transform .6s ease;
  }

  .section.visible { opacity: 1; transform: translateY(0); }

  .section-header {
    display: flex;
    align-items: baseline;
    gap: 16px;
    margin-bottom: 40px;
  }

  .section-num {
    font-size: 11px;
    font-weight: 600;
    color: var(--muted);
    letter-spacing: .12em;
  }

  .section-title {
    font-size: 22px;
    font-weight: 800;
    letter-spacing: -.03em;
    color: var(--text);
  }

  /* ── STACK ── */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 10px;
  }

  .stack-item {
    display: flex;
    flex-direction: column;
    gap: 6px;
    padding: 18px 20px;
    border: 1.5px solid var(--border);
    border-radius: 4px;
    background: var(--white);
    cursor: none;
    transition: all .25s;
    position: relative;
    overflow: hidden;
  }

  .stack-item::after {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--text);
    transform: scaleY(0);
    transform-origin: bottom;
    transition: transform .25s ease;
    z-index: 0;
  }

  .stack-item:hover::after { transform: scaleY(1); }

  .stack-item:hover .stack-label,
  .stack-item:hover .stack-sub { color: #fff; }

  .stack-label {
    font-size: 13px;
    font-weight: 700;
    color: var(--text);
    position: relative;
    z-index: 1;
    transition: color .25s;
  }

  .stack-sub {
    font-size: 10px;
    font-weight: 500;
    letter-spacing: .08em;
    text-transform: uppercase;
    color: var(--muted);
    position: relative;
    z-index: 1;
    transition: color .25s;
  }

  .stack-item.primary { border-color: var(--text); }
  .stack-item.primary .stack-sub { color: var(--accent2); }

  /* ── PROJECT ── */
  .project-card {
    border: 1.5px solid var(--border);
    border-radius: 4px;
    padding: 36px 40px;
    background: var(--white);
    cursor: none;
    transition: all .3s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    background: var(--text);
    transform: scaleY(0);
    transform-origin: top;
    transition: transform .3s ease;
  }

  .project-card:hover {
    border-color: var(--text);
    transform: translateY(-4px);
    box-shadow: 0 16px 48px rgba(0,0,0,.07);
  }

  .project-card:hover::before { transform: scaleY(1); }

  .project-tag {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: .16em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
  }

  .project-name {
    font-size: 1.6rem;
    font-weight: 900;
    letter-spacing: -.04em;
    color: var(--text);
    margin-bottom: 10px;
  }

  .project-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.8;
    margin-bottom: 24px;
    max-width: 500px;
  }

  .tech-row {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }

  .tech-chip {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: .06em;
    padding: 5px 14px;
    border: 1.5px solid var(--border);
    border-radius: 2px;
    color: var(--text);
    background: var(--tag-bg);
    transition: all .2s;
  }

  .project-card:hover .tech-chip {
    border-color: var(--text);
    background: var(--text);
    color: #fff;
  }

  /* ── LEARNING ── */
  .learn-list {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .learn-item {
    display: grid;
    grid-template-columns: 120px 1fr 40px;
    align-items: center;
    gap: 20px;
    padding: 14px 0;
    border-bottom: 1px solid var(--border);
    cursor: none;
    transition: all .2s;
  }

  .learn-item:hover { padding-left: 8px; }

  .learn-name {
    font-size: 13px;
    font-weight: 700;
    color: var(--text);
  }

  .bar-track {
    height: 3px;
    background: var(--light);
    border-radius: 2px;
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    background: var(--text);
    border-radius: 2px;
    width: 0;
    transition: width 1.2s cubic-bezier(.16,1,.3,1);
  }

  .bar-pct {
    font-size: 11px;
    font-weight: 600;
    color: var(--muted);
    text-align: right;
  }

  /* ── GOAL ── */
  .goal-block {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .goal-card {
    padding: 28px 30px;
    border: 1.5px solid var(--border);
    border-radius: 4px;
    background: var(--white);
    cursor: none;
    transition: all .3s;
  }

  .goal-card:hover {
    border-color: var(--text);
    background: var(--text);
    transform: translateY(-3px);
  }

  .goal-card:hover .goal-card-label,
  .goal-card:hover .goal-card-text { color: #fff; }
  .goal-card:hover .goal-card-icon { filter: invert(1); }

  .goal-card-icon { font-size: 22px; margin-bottom: 14px; }

  .goal-card-label {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: .16em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 8px;
    transition: color .3s;
  }

  .goal-card-text {
    font-size: 14px;
    font-weight: 700;
    color: var(--text);
    line-height: 1.4;
    transition: color .3s;
  }

  /* ── OPEN FOR ── */
  .open-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .open-pill {
    font-size: 12px;
    font-weight: 600;
    letter-spacing: .04em;
    padding: 12px 24px;
    border: 1.5px solid var(--border);
    border-radius: 100px;
    color: var(--text);
    background: var(--white);
    cursor: none;
    transition: all .25s;
  }

  .open-pill:hover {
    background: var(--text);
    border-color: var(--text);
    color: #fff;
    transform: scale(1.03);
  }

  /* ── FOOTER ── */
  .footer {
    padding: 48px 0 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-left {
    font-size: 18px;
    font-weight: 800;
    letter-spacing: -.03em;
  }

  .footer-right {
    font-size: 11px;
    color: var(--muted);
    font-weight: 500;
    letter-spacing: .08em;
  }

  /* animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .hero { animation: fadeUp .6s ease both; }

  @media (max-width: 600px) {
    .topbar { padding: 16px 20px; }
    .topbar-nav { display: none; }
    .wrap { padding: 100px 20px 60px; }
    .stack-grid { grid-template-columns: repeat(2, 1fr); }
    .goal-block { grid-template-columns: 1fr; }
    .learn-item { grid-template-columns: 90px 1fr 36px; gap: 12px; }
    .project-card { padding: 24px; }
    .hero-name { font-size: 2.2rem; }
  }
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Topbar -->
<nav class="topbar">
  <div class="topbar-logo">bellion <span>/ readme.md</span></div>
  <div class="topbar-nav">
    <a href="#stack">Stack</a>
    <a href="#learning">Learning</a>
    <a href="#goals">Goals</a>
  </div>
</nav>

<div class="wrap">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-eyebrow">
      <span class="dot-live"></span>
      Actively Building & Learning
    </div>
    <h1 class="hero-name">M. Dava Arya<br>Nada Putra</h1>
    <p class="hero-handle">@bellion</p>
    <div class="typing-wrap">
      <span class="typed-text" id="typed"></span>
    </div>
    <p class="hero-sub">
      Pemula yang serius. Fokus membangun fondasi yang kuat sebelum terbang lebih tinggi.
      Bergerak dari 0 menuju Junior Developer — satu commit setiap hari.
    </p>

  </section>

  <!-- STACK -->
  <section class="section" id="stack">
    <div class="section-header">
      <span class="section-num">01</span>
      <h2 class="section-title">Tech Stack</h2>
    </div>
    <div class="stack-grid">
      <div class="stack-item primary">
        <span class="stack-label">JavaScript</span>
        <span class="stack-sub">Core</span>
      </div>
      <div class="stack-item primary">
        <span class="stack-label">HTML</span>
        <span class="stack-sub">Core</span>
      </div>
      <div class="stack-item primary">
        <span class="stack-label">CSS</span>
        <span class="stack-sub">Core</span>
      </div>
      <div class="stack-item primary">
        <span class="stack-label">MySQL</span>
        <span class="stack-sub">Database</span>
      </div>
      <div class="stack-item">
        <span class="stack-label">Tailwind</span>
        <span class="stack-sub">Styling</span>
      </div>
      <div class="stack-item">
        <span class="stack-label">Laravel</span>
        <span class="stack-sub">Framework</span>
      </div>
    </div>
  </section>

  <!-- PROJECT -->
  <section class="section" id="project">
    <div class="section-header">
      <span class="section-num">02</span>
      <h2 class="section-title">Featured Project</h2>
    </div>
    <div class="project-card">
      <p class="project-tag">Main Project · 2024</p>
      <h3 class="project-name">Management Kecap</h3>
      <p class="project-desc">
        Aplikasi manajemen produk untuk mitra UMKM. Dibangun untuk membantu pelaku usaha kecil
        mengelola produk mereka secara digital — lebih rapi, lebih cepat, lebih mudah.
      </p>
      <div class="tech-row">
        <span class="tech-chip">Dart</span>
        <span class="tech-chip">Flutter</span>
        <span class="tech-chip">Supabase</span>
      </div>
    </div>
  </section>

  <!-- LEARNING -->
  <section class="section" id="learning">
    <div class="section-header">
      <span class="section-num">03</span>
      <h2 class="section-title">Currently Learning</h2>
    </div>
    <div class="learn-list">
      <div class="learn-item" data-pct="75">
        <span class="learn-name">JavaScript</span>
        <div class="bar-track"><div class="bar-fill"></div></div>
        <span class="bar-pct">75%</span>
      </div>
      <div class="learn-item" data-pct="40">
        <span class="learn-name">React</span>
        <div class="bar-track"><div class="bar-fill"></div></div>
        <span class="bar-pct">40%</span>
      </div>
      <div class="learn-item" data-pct="30">
        <span class="learn-name">Node.js</span>
        <div class="bar-track"><div class="bar-fill"></div></div>
        <span class="bar-pct">30%</span>
      </div>
    </div>
  </section>

  <!-- GOALS -->
  <section class="section" id="goals">
    <div class="section-header">
      <span class="section-num">04</span>
      <h2 class="section-title">Goals & Focus</h2>
    </div>
    <div class="goal-block">
      <div class="goal-card">
        <div class="goal-card-icon">🎯</div>
        <p class="goal-card-label">Current Focus</p>
        <p class="goal-card-text">Memperdalam fundamental sebelum melangkah lebih jauh</p>
      </div>
      <div class="goal-card">
        <div class="goal-card-icon">🚀</div>
        <p class="goal-card-label">Future Goal</p>
        <p class="goal-card-text">Mencapai level Junior Developer dengan skill yang solid</p>
      </div>
      <div class="goal-card">
        <div class="goal-card-icon">🧭</div>
        <p class="goal-card-label">Direction</p>
        <p class="goal-card-text">Frontend · Fullstack · Backend · Mobile</p>
      </div>
      <div class="goal-card">
        <div class="goal-card-icon">💡</div>
        <p class="goal-card-label">Style</p>
        <p class="goal-card-text">Minimal · Builder · Startup · Futuristic</p>
      </div>
    </div>
  </section>

  <!-- OPEN FOR -->
  <section class="section" id="open">
    <div class="section-header">
      <span class="section-num">05</span>
      <h2 class="section-title">Open For</h2>
    </div>
    <div class="open-row">
      <span class="open-pill">🤝 Collaboration</span>
      <span class="open-pill">💼 Internship</span>
      <span class="open-pill">👥 Project Team</span>
      <span class="open-pill">🌐 Open Source</span>
    </div>
  </section>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-left">bellion</div>
    <div class="footer-right">Build. Learn. Repeat. — 2025</div>
  </div>

</div>

<script>
  // ── CURSOR ──
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top  = my + 'px';
  });

  function animRing() {
    rx += (mx - rx) * .12;
    ry += (my - ry) * .12;
    ring.style.left = rx + 'px';
    ring.style.top  = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, button, .stack-item, .project-card, .goal-card, .open-pill, .btn, .learn-item').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.classList.add('expand'); ring.classList.add('expand'); });
    el.addEventListener('mouseleave', () => { cursor.classList.remove('expand'); ring.classList.remove('expand'); });
  });

  // ── TYPING ANIMATION ──
  const phrases = [
    'Frontend Developer in progress...',
    'Building Management Kecap 📦',
    'Learning React & Node.js ⚡',
    'Open for collaboration 🤝',
    'Pemula yang serius. 💪',
  ];

  let pi = 0, ci = 0, deleting = false;
  const el = document.getElementById('typed');

  function type() {
    const phrase = phrases[pi];
    if (!deleting) {
      el.textContent = phrase.slice(0, ci + 1);
      ci++;
      if (ci === phrase.length) {
        setTimeout(() => { deleting = true; tick(); }, 2000);
        return;
      }
    } else {
      el.textContent = phrase.slice(0, ci - 1);
      ci--;
      if (ci === 0) {
        deleting = false;
        pi = (pi + 1) % phrases.length;
      }
    }
    tick();
  }

  function tick() {
    const speed = deleting ? 40 : 70;
    setTimeout(type, speed);
  }

  tick();

  // ── SCROLL REVEAL ──
  const sections = document.querySelectorAll('.section');

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');

        // animate bars if learning section
        entry.target.querySelectorAll('.learn-item').forEach((item, i) => {
          const pct = item.dataset.pct;
          setTimeout(() => {
            item.querySelector('.bar-fill').style.width = pct + '%';
          }, i * 150);
        });
      }
    });
  }, { threshold: 0.15 });

  sections.forEach(s => observer.observe(s));
</script>
</body>
</html>
