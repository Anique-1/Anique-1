<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Muhammad Anique — AI Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0a0a0f;
    --paper: #f5f3ee;
    --accent: #ff3d3d;
    --gold: #f5c842;
    --cyan: #00e5c8;
    --muted: #8a8a9a;
    --border: #1a1a2a;
    --card: #0f0f1a;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--ink);
    color: var(--paper);
    font-family: 'DM Mono', monospace;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    width: 40px; height: 40px;
    border: 1px solid rgba(255,61,61,0.4);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: all 0.15s ease;
  }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 9990; opacity: 0.4;
  }

  /* ── HERO ──────────────────────────────── */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: relative;
    border-bottom: 1px solid #1a1a2a;
  }

  .hero-left {
    padding: 80px 60px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    border-right: 1px solid #1a1a2a;
    position: relative;
    overflow: hidden;
  }

  .hero-left::before {
    content: '';
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(255,61,61,0.07) 0%, transparent 70%);
    top: -100px; left: -200px;
    pointer-events: none;
  }

  .status-pill {
    display: inline-flex; align-items: center; gap: 8px;
    border: 1px solid #2a2a3a;
    padding: 6px 14px;
    border-radius: 2px;
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 40px;
    width: fit-content;
  }
  .status-dot {
    width: 6px; height: 6px;
    background: var(--cyan);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(0.7); }
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 7vw, 96px);
    font-weight: 800;
    line-height: 0.92;
    letter-spacing: -0.03em;
    margin-bottom: 6px;
  }
  .hero-name span { color: var(--accent); }

  .hero-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(14px, 1.8vw, 20px);
    font-weight: 600;
    color: var(--gold);
    letter-spacing: 0.18em;
    text-transform: uppercase;
    margin-bottom: 36px;
  }

  .hero-desc {
    font-size: 13px;
    line-height: 1.9;
    color: #9090a8;
    max-width: 420px;
    margin-bottom: 48px;
  }

  .hero-links {
    display: flex; gap: 12px; flex-wrap: wrap;
  }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 11px 22px;
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    text-decoration: none;
    border-radius: 2px;
    transition: all 0.2s;
    cursor: none;
  }
  .btn-primary {
    background: var(--accent);
    color: #fff;
    border: 1px solid var(--accent);
  }
  .btn-primary:hover { background: #ff6060; transform: translateY(-1px); }
  .btn-ghost {
    background: transparent;
    color: var(--paper);
    border: 1px solid #2a2a3a;
  }
  .btn-ghost:hover { border-color: var(--paper); transform: translateY(-1px); }

  .hero-right {
    padding: 80px 60px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 24px;
    position: relative;
  }

  .stat-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  .stat-card {
    border: 1px solid #1a1a2a;
    padding: 28px 24px;
    background: #080810;
    position: relative;
    overflow: hidden;
    transition: border-color 0.2s;
  }
  .stat-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--accent);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.3s;
  }
  .stat-card:hover::before { transform: scaleX(1); }
  .stat-card:hover { border-color: #2a2a3a; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 42px;
    font-weight: 800;
    line-height: 1;
    color: var(--paper);
    margin-bottom: 6px;
  }
  .stat-num sup { font-size: 20px; color: var(--accent); }
  .stat-label { font-size: 10px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted); }

  /* Corner decoration */
  .hero-right::before {
    content: 'v2.0 // 2025';
    position: absolute;
    top: 30px; right: 60px;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: #2a2a3a;
  }

  /* ── TICKER ───────────────────────────── */
  .ticker {
    border-top: 1px solid #1a1a2a;
    border-bottom: 1px solid #1a1a2a;
    padding: 14px 0;
    overflow: hidden;
    background: #06060e;
  }
  .ticker-inner {
    display: flex;
    gap: 0;
    animation: ticker 30s linear infinite;
    white-space: nowrap;
  }
  .ticker-item {
    padding: 0 40px;
    font-size: 11px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: #3a3a5a;
    display: flex; align-items: center; gap: 16px;
  }
  .ticker-item b { color: var(--gold); }
  .ticker-sep { color: var(--accent); }
  @keyframes ticker {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  /* ── STACK SECTION ────────────────────── */
  .section {
    padding: 100px 60px;
    border-bottom: 1px solid #1a1a2a;
    position: relative;
  }

  .section-label {
    display: flex; align-items: center; gap: 16px;
    margin-bottom: 64px;
  }
  .section-num {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(32px, 4vw, 52px);
    font-weight: 800;
    letter-spacing: -0.03em;
  }

  /* Stack grid */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background: #1a1a2a;
    border: 1px solid #1a1a2a;
  }
  .stack-col {
    background: var(--ink);
    padding: 40px 32px;
  }
  .stack-col-title {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 28px;
    padding-bottom: 14px;
    border-bottom: 1px solid #1a1a2a;
  }
  .stack-tag {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 0;
    font-size: 12px;
    color: #c0c0d8;
    border-bottom: 1px solid #0f0f1a;
    transition: color 0.15s;
    cursor: none;
  }
  .stack-tag:hover { color: var(--paper); }
  .stack-tag::before {
    content: '';
    width: 3px; height: 3px;
    background: var(--muted);
    border-radius: 50%;
    flex-shrink: 0;
    transition: background 0.15s;
  }
  .stack-tag:hover::before { background: var(--cyan); }

  /* ── PROJECTS ─────────────────────────── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: #1a1a2a;
    border: 1px solid #1a1a2a;
  }
  .project-card {
    background: var(--ink);
    padding: 40px 36px;
    position: relative;
    overflow: hidden;
    transition: background 0.2s;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 220px;
  }
  .project-card:hover { background: #0a0a14; }
  .project-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, var(--accent), transparent);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s;
  }
  .project-card:hover::after { transform: scaleX(1); }

  .project-icon {
    font-size: 28px;
    margin-bottom: 20px;
    display: block;
  }
  .project-name {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 10px;
    letter-spacing: -0.01em;
  }
  .project-desc {
    font-size: 11px;
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 24px;
    flex-grow: 1;
  }
  .project-tags {
    display: flex; flex-wrap: wrap; gap: 6px;
  }
  .tag {
    font-size: 9px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 4px 10px;
    border: 1px solid #2a2a3a;
    color: var(--muted);
    border-radius: 2px;
  }

  /* Featured card */
  .project-card.featured {
    background: #0d0d1e;
    border-top: 2px solid var(--gold);
  }
  .project-card.featured .project-name { color: var(--gold); }

  /* ── AWARDS ───────────────────────────── */
  .awards-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: #1a1a2a;
    border: 1px solid #1a1a2a;
  }
  .award-card {
    background: var(--ink);
    padding: 60px;
    display: flex;
    gap: 40px;
    align-items: flex-start;
  }
  .award-rank {
    font-family: 'Syne', sans-serif;
    font-size: 80px;
    font-weight: 800;
    line-height: 1;
    color: #1a1a2a;
    flex-shrink: 0;
  }
  .award-card:first-child .award-rank { color: rgba(245,200,66,0.15); }
  .award-title {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 700;
    margin-bottom: 10px;
  }
  .award-sub { font-size: 11px; color: var(--muted); line-height: 1.8; }
  .award-badge {
    display: inline-block;
    margin-top: 16px;
    padding: 5px 14px;
    font-size: 10px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    border-radius: 2px;
  }
  .award-badge.gold { background: rgba(245,200,66,0.12); color: var(--gold); border: 1px solid rgba(245,200,66,0.3); }
  .award-badge.bronze { background: rgba(205,127,50,0.12); color: #cd7f32; border: 1px solid rgba(205,127,50,0.3); }

  /* ── GITHUB STATS ─────────────────────── */
  .stats-section {
    padding: 100px 60px;
    border-bottom: 1px solid #1a1a2a;
  }
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: #1a1a2a;
    border: 1px solid #1a1a2a;
    margin-top: 64px;
  }
  .stat-block {
    background: var(--ink);
    padding: 48px 40px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .stat-block::before {
    content: '';
    position: absolute; top: 0; left: 50%; transform: translateX(-50%);
    width: 40px; height: 2px;
    background: var(--cyan);
  }
  .stat-big {
    font-family: 'Syne', sans-serif;
    font-size: 64px;
    font-weight: 800;
    line-height: 1;
    margin-bottom: 12px;
  }
  .stat-big.red { color: var(--accent); }
  .stat-big.gold { color: var(--gold); }
  .stat-big.cyan { color: var(--cyan); }
  .stat-desc { font-size: 11px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted); }

  /* Contribution bar chart */
  .contrib-chart {
    margin-top: 64px;
    border: 1px solid #1a1a2a;
    padding: 48px;
    background: #06060e;
  }
  .contrib-title {
    font-size: 11px; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--muted); margin-bottom: 36px;
  }
  .bars {
    display: flex;
    gap: 3px;
    align-items: flex-end;
    height: 80px;
  }
  .bar {
    flex: 1;
    background: #1a1a2a;
    border-radius: 1px;
    position: relative;
    transition: background 0.2s;
  }
  .bar:hover { background: var(--accent); }
  .bar.active { background: var(--cyan); }
  .bar.medium { background: rgba(0,229,200,0.4); }
  .bar.low { background: rgba(0,229,200,0.15); }
  .bar.empty { background: #111120; }
  .contrib-labels {
    display: flex;
    justify-content: space-between;
    margin-top: 12px;
    font-size: 9px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: #3a3a5a;
  }

  /* ── FOOTER ───────────────────────────── */
  footer {
    padding: 80px 60px;
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: end;
    gap: 40px;
  }
  .footer-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(40px, 6vw, 80px);
    font-weight: 800;
    letter-spacing: -0.04em;
    line-height: 1;
    color: #1a1a2a;
  }
  .footer-name span { color: var(--accent); }
  .footer-links {
    display: flex; flex-direction: column; gap: 8px; text-align: right;
  }
  .footer-link {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.15s;
  }
  .footer-link:hover { color: var(--paper); }
  .footer-copy {
    grid-column: 1/-1;
    border-top: 1px solid #1a1a2a;
    padding-top: 30px;
    display: flex;
    justify-content: space-between;
    font-size: 10px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: #2a2a3a;
  }

  /* ── LANG BAR ─────────────────────────── */
  .lang-section {
    padding: 0 60px 0;
  }
  .lang-row {
    display: flex;
    height: 8px;
    border-radius: 0;
    overflow: hidden;
    border: 1px solid #1a1a2a;
    margin-bottom: 20px;
  }
  .lang-seg { height: 100%; transition: opacity 0.2s; }
  .lang-seg:hover { opacity: 0.7; }
  .lang-legend {
    display: flex; flex-wrap: wrap; gap: 20px;
    font-size: 10px; letter-spacing: 0.12em; text-transform: uppercase;
  }
  .lang-item { display: flex; align-items: center; gap: 8px; color: var(--muted); }
  .lang-dot { width: 8px; height: 8px; border-radius: 50%; }

  /* ── RESPONSIVE ───────────────────────── */
  @media (max-width: 900px) {
    .hero, .awards-row { grid-template-columns: 1fr; }
    .hero-left { border-right: none; border-bottom: 1px solid #1a1a2a; }
    .stack-grid, .projects-grid, .stats-grid { grid-template-columns: 1fr 1fr; }
    .section, .stats-section { padding: 60px 24px; }
    footer { grid-template-columns: 1fr; }
    .lang-section { padding: 0 24px; }
  }

  /* entrance animations */
  .fade-in {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .fade-in.visible { opacity: 1; transform: translateY(0); }

</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- ═══ HERO ══════════════════════════════════════════════ -->
<section class="hero">
  <div class="hero-left">
    <div class="status-pill">
      <span class="status-dot"></span>
      Available for collaboration
    </div>
    <h1 class="hero-name">
      Muhammad<br><span>Anique</span>
    </h1>
    <p class="hero-title">AI Engineer &amp; Full-Stack Developer</p>
    <p class="hero-desc">
      Building intelligent systems from Pakistan 🇵🇰 — specializing in
      LLMs, Computer Vision, and production-grade AI agents. Hackathon
      winner. Open-source contributor. Algorithm-to-product pipeline.
    </p>
    <div class="hero-links">
      <a href="https://muhammad-anique-frontend.vercel.app/" class="btn btn-primary" target="_blank">↗ Portfolio</a>
      <a href="https://github.com/Anique-1" class="btn btn-ghost" target="_blank">⌥ GitHub</a>
      <a href="mailto:muhammadanique81@gmail.com" class="btn btn-ghost">✉ Email</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="stat-row fade-in">
      <div class="stat-card">
        <div class="stat-num">20<sup>+</sup></div>
        <div class="stat-label">AI Projects Shipped</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">2<sup>×</sup></div>
        <div class="stat-label">Hackathon Wins</div>
      </div>
    </div>
    <div class="stat-row fade-in" style="transition-delay:0.1s">
      <div class="stat-card">
        <div class="stat-num">8<sup>+</sup></div>
        <div class="stat-label">AI Agents Built</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">5<sup>+</sup></div>
        <div class="stat-label">CV Models Deployed</div>
      </div>
    </div>
    <div class="stat-row fade-in" style="transition-delay:0.2s">
      <div class="stat-card">
        <div class="stat-num">∞</div>
        <div class="stat-label">Coffee → Code</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">1<sup>st</sup></div>
        <div class="stat-label">MediVision Place</div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ TICKER ════════════════════════════════════════════ -->
<div class="ticker">
  <div class="ticker-inner" id="tickerInner"></div>
</div>

<!-- ═══ TECH STACK ════════════════════════════════════════ -->
<section class="section fade-in">
  <div class="section-label">
    <span class="section-num">01 //</span>
    <h2 class="section-title">Tech Stack</h2>
  </div>

  <div class="stack-grid">
    <div class="stack-col">
      <div class="stack-col-title">AI &amp; ML</div>
      <div class="stack-tag">PyTorch</div>
      <div class="stack-tag">TensorFlow</div>
      <div class="stack-tag">Scikit-Learn</div>
      <div class="stack-tag">Keras</div>
      <div class="stack-tag">Hugging Face</div>
      <div class="stack-tag">Pandas / NumPy</div>
      <div class="stack-tag">Matplotlib</div>
    </div>
    <div class="stack-col">
      <div class="stack-col-title">LLM &amp; Agents</div>
      <div class="stack-tag">LangChain</div>
      <div class="stack-tag">LangGraph</div>
      <div class="stack-tag">OpenAI API</div>
      <div class="stack-tag">Claude AI</div>
      <div class="stack-tag">RAG Pipelines</div>
      <div class="stack-tag">MCP Servers</div>
      <div class="stack-tag">Vector DBs</div>
    </div>
    <div class="stack-col">
      <div class="stack-col-title">Computer Vision</div>
      <div class="stack-tag">YOLOv11 / YOLO</div>
      <div class="stack-tag">Ultralytics</div>
      <div class="stack-tag">OpenCV</div>
      <div class="stack-tag">Roboflow</div>
      <div class="stack-tag">NVIDIA GPU</div>
      <div class="stack-tag">Instance Seg.</div>
      <div class="stack-tag">Object Tracking</div>
    </div>
    <div class="stack-col">
      <div class="stack-col-title">Full-Stack</div>
      <div class="stack-tag">Next.js / React</div>
      <div class="stack-tag">FastAPI / Flask</div>
      <div class="stack-tag">Node.js</div>
      <div class="stack-tag">TypeScript</div>
      <div class="stack-tag">React Native</div>
      <div class="stack-tag">MongoDB / Postgres</div>
      <div class="stack-tag">Docker / AWS / Azure</div>
    </div>
  </div>

  <!-- Language distribution bar -->
  <div class="lang-section" style="padding: 40px 0 0;">
    <div class="lang-row">
      <div class="lang-seg" style="width:38%; background:#3776AB;" title="Python 38%"></div>
      <div class="lang-seg" style="width:22%; background:#3178C6;" title="TypeScript 22%"></div>
      <div class="lang-seg" style="width:18%; background:#F7DF1E;" title="JavaScript 18%"></div>
      <div class="lang-seg" style="width:12%; background:#009688;" title="FastAPI/Python 12%"></div>
      <div class="lang-seg" style="width:10%; background:#ff3d3d;" title="Other 10%"></div>
    </div>
    <div class="lang-legend">
      <div class="lang-item"><div class="lang-dot" style="background:#3776AB;"></div>Python 38%</div>
      <div class="lang-item"><div class="lang-dot" style="background:#3178C6;"></div>TypeScript 22%</div>
      <div class="lang-item"><div class="lang-dot" style="background:#F7DF1E;"></div>JavaScript 18%</div>
      <div class="lang-item"><div class="lang-dot" style="background:#009688;"></div>FastAPI 12%</div>
      <div class="lang-item"><div class="lang-dot" style="background:#ff3d3d;"></div>Other 10%</div>
    </div>
  </div>
</section>

<!-- ═══ PROJECTS ══════════════════════════════════════════ -->
<section class="section fade-in" style="padding-top:0;">
  <div class="section-label">
    <span class="section-num">02 //</span>
    <h2 class="section-title">Featured Projects</h2>
  </div>

  <div class="projects-grid">

    <div class="project-card featured">
      <div>
        <span class="project-icon">🏥</span>
        <div class="project-name">MediVision AI</div>
        <p class="project-desc">Hackathon-winning medical diagnostics platform combining AI agents with YOLO for multi-disease detection from medical imagery.</p>
      </div>
      <div class="project-tags">
        <span class="tag">YOLO</span>
        <span class="tag">FastAPI</span>
        <span class="tag">Next.js</span>
        <span class="tag" style="color:var(--gold); border-color:rgba(245,200,66,0.3);">🏆 1st Place</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">🚗</span>
        <div class="project-name">Autonomous Driving</div>
        <p class="project-desc">Fine-tuned YOLOv11-seg for precision road boundary and lane marking detection for self-driving pipelines.</p>
      </div>
      <div class="project-tags">
        <span class="tag">YOLOv11-seg</span>
        <span class="tag">Ultralytics</span>
        <span class="tag">NVIDIA</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">🎓</span>
        <div class="project-name">AI FYP Guider</div>
        <p class="project-desc">LangGraph agent for final year project guidance — resume analysis, academic mentoring, topic suggestions.</p>
      </div>
      <div class="project-tags">
        <span class="tag">LangGraph</span>
        <span class="tag">Azure</span>
        <span class="tag">Next.js</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">🔬</span>
        <div class="project-name">Parasitic Diagnosis</div>
        <p class="project-desc">AI microscopy system detecting 8 parasitic infections from microscope slides with high diagnostic accuracy.</p>
      </div>
      <div class="project-tags">
        <span class="tag">YOLO</span>
        <span class="tag">NVIDIA GPU</span>
        <span class="tag">CV</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">💹</span>
        <div class="project-name">Financial Agent</div>
        <p class="project-desc">Portfolio analysis, risk assessment and comprehensive automated financial reports using LangGraph agents.</p>
      </div>
      <div class="project-tags">
        <span class="tag">LangGraph</span>
        <span class="tag">FastAPI</span>
        <span class="tag">Next.js</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">⚽</span>
        <div class="project-name">Football Analytics</div>
        <p class="project-desc">Real-time player and ball tracking with match analytics — built on YOLOv11 and custom tracking logic.</p>
      </div>
      <div class="project-tags">
        <span class="tag">YOLOv11</span>
        <span class="tag">Tracking</span>
        <span class="tag">CV</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">🇵🇰</span>
        <div class="project-name">Pakistan AI Chronicle</div>
        <p class="project-desc">Digital chronicle of Pakistan's history — AI-powered cultural preservation platform with intelligent Q&amp;A.</p>
      </div>
      <div class="project-tags">
        <span class="tag">LangGraph</span>
        <span class="tag">Azure</span>
        <span class="tag">RAG</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">🦷</span>
        <div class="project-name">Dental AI Agent</div>
        <p class="project-desc">YOLO + LLM fusion for comprehensive oral health analysis — detecting dental conditions from images.</p>
      </div>
      <div class="project-tags">
        <span class="tag">YOLO</span>
        <span class="tag">OpenAI</span>
        <span class="tag">FastAPI</span>
      </div>
    </div>

    <div class="project-card">
      <div>
        <span class="project-icon">🎵</span>
        <div class="project-name">Music Composer Agent</div>
        <p class="project-desc">AI-powered melody, harmony, lyrics, and MIDI generation using multi-agent composition pipeline.</p>
      </div>
      <div class="project-tags">
        <span class="tag">LangGraph</span>
        <span class="tag">OpenAI</span>
        <span class="tag">MIDI</span>
      </div>
    </div>

  </div>
</section>

<!-- ═══ AWARDS ════════════════════════════════════════════ -->
<section class="section fade-in" style="padding-top:0;">
  <div class="section-label">
    <span class="section-num">03 //</span>
    <h2 class="section-title">Achievements</h2>
  </div>
  <div class="awards-row">
    <div class="award-card">
      <div class="award-rank">01</div>
      <div>
        <div class="award-title">MediVision AI Platform</div>
        <p class="award-sub">Built an innovative medical diagnostics platform combining AI agents with YOLO computer vision models for automated disease detection. Competed against teams from top universities.</p>
        <span class="award-badge gold">🏆 Hackathon Winner — 1st Place</span>
      </div>
    </div>
    <div class="award-card">
      <div class="award-rank">03</div>
      <div>
        <div class="award-title">ManuBot — Voice Factory</div>
        <p class="award-sub">Designed a voice-controlled factory automation system enabling smart manufacturing workflows through natural language commands and IoT integration.</p>
        <span class="award-badge bronze">🥉 UAF Idea Competition — 3rd Place</span>
      </div>
    </div>
  </div>
</section>

<!-- ═══ GITHUB STATS ══════════════════════════════════════ -->
<section class="stats-section fade-in">
  <div class="section-label">
    <span class="section-num">04 //</span>
    <h2 class="section-title">GitHub Stats</h2>
  </div>

  <div class="stats-grid">
    <div class="stat-block">
      <div class="stat-big red">20+</div>
      <div class="stat-desc">Repositories</div>
    </div>
    <div class="stat-block">
      <div class="stat-big gold">∞</div>
      <div class="stat-desc">Commits (ongoing)</div>
    </div>
    <div class="stat-block">
      <div class="stat-big cyan">PKT+5</div>
      <div class="stat-desc">Timezone — Faisalabad</div>
    </div>
  </div>

  <div class="contrib-chart">
    <div class="contrib-title">Contribution Activity — 2024/2025</div>
    <div class="bars" id="contribBars"></div>
    <div class="contrib-labels">
      <span>Jan</span><span>Mar</span><span>May</span>
      <span>Jul</span><span>Sep</span><span>Nov</span><span>Now</span>
    </div>
  </div>

  <!-- Live GitHub stats image embeds -->
  <div style="display:grid; grid-template-columns:1fr 1fr; gap:1px; background:#1a1a2a; border:1px solid #1a1a2a; margin-top:1px;">
    <div style="background:var(--ink); padding:24px; display:flex; justify-content:center;">
      <img src="https://github-readme-stats.vercel.app/api?username=anique-1&show_icons=true&theme=radical&hide_border=true&bg_color=0a0a0f&title_color=ff3d3d&icon_color=00e5c8&text_color=c0c0d8&count_private=true" alt="GitHub Stats" style="max-width:100%; height:auto;" loading="lazy" />
    </div>
    <div style="background:var(--ink); padding:24px; display:flex; justify-content:center;">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=anique-1&theme=radical&hide_border=true&background=0a0a0f&stroke=ff3d3d&ring=ff3d3d&fire=f5c842&currStreakLabel=00e5c8" alt="GitHub Streak" style="max-width:100%; height:auto;" loading="lazy" />
    </div>
  </div>
</section>

<!-- ═══ FOOTER ════════════════════════════════════════════ -->
<footer>
  <div class="footer-name">
    Muhammad<br><span>Anique.</span>
  </div>
  <div class="footer-links">
    <a href="https://github.com/Anique-1" class="footer-link" target="_blank">GitHub ↗</a>
    <a href="https://www.linkedin.com/in/muhammad-anique-300828266" class="footer-link" target="_blank">LinkedIn ↗</a>
    <a href="https://muhammad-anique-frontend.vercel.app/" class="footer-link" target="_blank">Portfolio ↗</a>
    <a href="mailto:muhammadanique81@gmail.com" class="footer-link">Email ↗</a>
    <a href="https://www.instagram.com/anique_ibn_shakoor" class="footer-link" target="_blank">Instagram ↗</a>
  </div>
  <div class="footer-copy">
    <span>Muhammad Anique — AI Engineer, Pakistan 🇵🇰</span>
    <span>Built with intent. Algorithms into innovations.</span>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; cursor.style.left = mx+'px'; cursor.style.top = my+'px'; });
  function animRing() {
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx+'px'; ring.style.top = ry+'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  // Ticker
  const tickerItems = [
    'Python', 'PyTorch', 'LangChain', 'LangGraph', 'YOLO', 'FastAPI',
    'Next.js', 'Computer Vision', 'RAG', 'MCP', 'OpenAI', 'Azure',
    'LLM Agents', 'Docker', 'OpenCV', 'TypeScript', 'React', 'MongoDB'
  ];
  const inner = document.getElementById('tickerInner');
  const build = () => tickerItems.map((t,i) =>
    `<span class="ticker-item">${t} <span class="ticker-sep">✦</span></span>`
  ).join('');
  inner.innerHTML = build() + build(); // duplicate for seamless loop

  // Contribution chart
  const bars = document.getElementById('contribBars');
  const levels = [
    'empty','low','low','medium','active','active','medium','low','empty','low',
    'medium','active','active','active','medium','active','low','empty','low','medium',
    'active','active','medium','low','empty','empty','low','medium','active','active',
    'active','active','medium','active','medium','low','empty','low','active','active',
    'active','medium','low','empty','low','medium','active','active','medium','low',
    'empty','low','medium','active','active','active','medium','low','empty','low',
    'medium','active','active','active','medium','active','low','empty','active','active',
    'active','active','medium','active','active','medium','active','active','active','low'
  ];
  bars.innerHTML = levels.map(l => `<div class="bar ${l}" style="height:${
    l==='active'?80:l==='medium'?52:l==='low'?28:12
  }px"></div>`).join('');

  // Fade in observer
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.fade-in').forEach(el => obs.observe(el));
</script>
</body>
</html>
