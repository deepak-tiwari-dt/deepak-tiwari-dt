<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Deepak Tiwari — Full Stack Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent: #00ff88;
    --accent2: #ff6b35;
    --accent3: #7c6eff;
    --text: #e8e8f0;
    --muted: #6b6b80;
    --card: #13131c;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Mono', monospace;
    background: var(--bg);
    color: var(--text);
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
    transition: transform 0.1s ease, background 0.2s;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: transform 0.15s ease, left 0.08s ease, top 0.08s ease;
    mix-blend-mode: screen;
    opacity: 0.5;
  }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9997;
    opacity: 0.3;
  }

  /* Grid lines background */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: 
      linear-gradient(rgba(0,255,136,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,136,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 48px;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 18px;
    letter-spacing: -0.5px;
    color: var(--accent);
  }

  .nav-links {
    display: flex;
    gap: 36px;
    list-style: none;
  }

  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 12px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    transition: color 0.2s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -4px; left: 0;
    width: 0; height: 1px;
    background: var(--accent);
    transition: width 0.3s ease;
  }
  .nav-links a:hover { color: var(--accent); }
  .nav-links a:hover::after { width: 100%; }

  .nav-status {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    color: var(--muted);
  }
  .status-dot {
    width: 8px; height: 8px;
    background: var(--accent);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(0,255,136,0.4); }
    50% { opacity: 0.8; box-shadow: 0 0 0 6px rgba(0,255,136,0); }
  }

  /* HERO */
  #hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 48px 80px;
    position: relative;
    z-index: 1;
  }

  .hero-inner {
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 400px;
    gap: 80px;
    align-items: center;
  }

  .hero-tag {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 32px; height: 1px;
    background: var(--accent);
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 7vw, 88px);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -3px;
    margin-bottom: 32px;
  }

  h1 .line1 { display: block; color: var(--text); }
  h1 .line2 {
    display: block;
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent3) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-desc {
    font-size: 15px;
    line-height: 1.8;
    color: var(--muted);
    max-width: 520px;
    margin-bottom: 48px;
  }

  .hero-desc strong { color: var(--text); font-weight: 400; }

  .hero-actions {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 14px 28px;
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    text-decoration: none;
    border: none;
    cursor: none;
    transition: all 0.2s ease;
    position: relative;
    overflow: hidden;
  }

  .btn-primary {
    background: var(--accent);
    color: #000;
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 0 100%);
  }
  .btn-primary:hover {
    background: #00ffaa;
    transform: translate(-2px, -2px);
    box-shadow: 4px 4px 0 rgba(0,255,136,0.3);
  }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 0 100%);
  }
  .btn-ghost:hover {
    border-color: var(--accent);
    color: var(--accent);
    transform: translate(-2px, -2px);
    box-shadow: 4px 4px 0 rgba(0,255,136,0.1);
  }

  /* Profile card */
  .hero-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 32px;
    position: relative;
    animation: float 6s ease-in-out infinite;
  }

  .hero-card::before {
    content: '';
    position: absolute;
    top: -1px; left: 32px; right: 32px;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent3));
  }

  @keyframes float {
    0%, 100% { transform: translateY(0px); }
    50% { transform: translateY(-12px); }
  }

  .card-avatar {
    width: 80px; height: 80px;
    border-radius: 50%;
    border: 2px solid var(--accent);
    margin-bottom: 20px;
    background: var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 28px;
    font-weight: 800;
    color: var(--accent);
  }

  .card-name {
    font-family: 'Syne', sans-serif;
    font-size: 20px;
    font-weight: 700;
    margin-bottom: 4px;
  }

  .card-role {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .card-info {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 24px;
  }

  .card-info-item {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 12px;
    color: var(--muted);
  }

  .card-info-item svg { flex-shrink: 0; }

  .card-socials {
    display: flex;
    gap: 12px;
  }

  .social-link {
    width: 36px; height: 36px;
    background: var(--border);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--muted);
    text-decoration: none;
    transition: all 0.2s;
    font-size: 14px;
  }
  .social-link:hover {
    background: var(--accent);
    border-color: var(--accent);
    color: #000;
    transform: translateY(-3px);
  }

  /* SECTIONS */
  section {
    padding: 100px 48px;
    position: relative;
    z-index: 1;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-label {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-label::before {
    content: '';
    display: inline-block;
    width: 32px; height: 1px;
    background: var(--accent);
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(32px, 4vw, 52px);
    font-weight: 800;
    letter-spacing: -2px;
    margin-bottom: 60px;
    line-height: 1;
  }

  /* SKILLS */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2px;
  }

  .skill-category {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 28px;
    position: relative;
    transition: border-color 0.2s;
  }
  .skill-category:hover { border-color: rgba(0,255,136,0.3); }

  .skill-category-title {
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
    padding-bottom: 12px;
    border-bottom: 1px solid var(--border);
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    font-size: 11px;
    padding: 5px 10px;
    background: var(--bg);
    border: 1px solid var(--border);
    color: var(--muted);
    letter-spacing: 0.05em;
    transition: all 0.2s;
  }
  .skill-tag:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0,255,136,0.05);
  }

  /* EXPERIENCE */
  .timeline {
    position: relative;
    padding-left: 32px;
  }
  .timeline::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, var(--accent), transparent);
  }

  .timeline-item {
    position: relative;
    margin-bottom: 48px;
    padding-bottom: 48px;
    border-bottom: 1px solid var(--border);
  }
  .timeline-item:last-child { border-bottom: none; }

  .timeline-item::before {
    content: '';
    position: absolute;
    left: -38px; top: 6px;
    width: 12px; height: 12px;
    border: 2px solid var(--accent);
    background: var(--bg);
    transform: rotate(45deg);
  }

  .timeline-meta {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 12px;
    flex-wrap: wrap;
  }

  .timeline-date {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    background: rgba(0,255,136,0.08);
    padding: 4px 10px;
    border: 1px solid rgba(0,255,136,0.2);
  }

  .timeline-company {
    font-size: 12px;
    color: var(--muted);
  }

  .timeline-title {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 700;
    margin-bottom: 12px;
    letter-spacing: -0.5px;
  }

  .timeline-desc {
    font-size: 13px;
    line-height: 1.8;
    color: var(--muted);
  }

  /* PROJECTS */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
    gap: 2px;
  }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 32px;
    position: relative;
    transition: all 0.3s ease;
    cursor: none;
  }
  .project-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(0,255,136,0.03), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .project-card:hover { border-color: rgba(0,255,136,0.3); transform: translate(-4px, -4px); }
  .project-card:hover::after { opacity: 1; }
  .project-card:hover { box-shadow: 4px 4px 0 rgba(0,255,136,0.1); }

  .project-number {
    font-size: 48px;
    font-weight: 800;
    font-family: 'Syne', sans-serif;
    color: var(--border);
    line-height: 1;
    margin-bottom: 16px;
    letter-spacing: -3px;
  }

  .project-title {
    font-family: 'Syne', sans-serif;
    font-size: 20px;
    font-weight: 700;
    margin-bottom: 12px;
    letter-spacing: -0.5px;
  }

  .project-desc {
    font-size: 12px;
    line-height: 1.8;
    color: var(--muted);
    margin-bottom: 20px;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .stack-pill {
    font-size: 10px;
    padding: 3px 8px;
    border: 1px solid var(--border);
    color: var(--muted);
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  /* CONTACT */
  #contact-section {
    border-top: 1px solid var(--border);
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
  }

  .contact-copy {
    font-size: 14px;
    line-height: 1.9;
    color: var(--muted);
    margin-bottom: 32px;
  }

  .contact-links {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 13px;
    color: var(--muted);
    text-decoration: none;
    padding: 12px 16px;
    border: 1px solid var(--border);
    transition: all 0.2s;
  }
  .contact-link:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0,255,136,0.04);
    transform: translateX(6px);
  }

  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .form-field {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .form-field label {
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .form-field input,
  .form-field textarea {
    background: var(--card);
    border: 1px solid var(--border);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    padding: 12px 16px;
    outline: none;
    transition: border-color 0.2s;
    resize: none;
  }
  .form-field input:focus,
  .form-field textarea:focus {
    border-color: var(--accent);
    background: rgba(0,255,136,0.02);
  }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 32px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
    z-index: 1;
  }

  footer p {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  .footer-badge {
    font-size: 11px;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .footer-badge span { color: var(--accent); }

  /* STATS */
  .stats-row {
    display: flex;
    gap: 0;
    margin-bottom: 80px;
    border: 1px solid var(--border);
    overflow: hidden;
  }

  .stat-item {
    flex: 1;
    padding: 32px;
    border-right: 1px solid var(--border);
    text-align: center;
  }
  .stat-item:last-child { border-right: none; }

  .stat-value {
    font-family: 'Syne', sans-serif;
    font-size: 48px;
    font-weight: 800;
    letter-spacing: -3px;
    background: linear-gradient(135deg, var(--accent), var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-label {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); }
  ::-webkit-scrollbar-thumb:hover { background: var(--accent); }

  /* HERO GLOW */
  .hero-glow {
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(0,255,136,0.06) 0%, transparent 70%);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    pointer-events: none;
  }

  @media (max-width: 768px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    .hero-inner { grid-template-columns: 1fr; }
    .hero-card { display: none; }
    section { padding: 60px 24px; }
    footer { padding: 24px; flex-direction: column; gap: 12px; }
    .contact-grid { grid-template-columns: 1fr; gap: 40px; }
    #hero { padding: 100px 24px 60px; }
    .stats-row { flex-wrap: wrap; }
    .stat-item { flex: 0 0 50%; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <div class="nav-logo">DT<span style="color:var(--muted)">.</span></div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="nav-status">
    <div class="status-dot"></div>
    Available for work
  </div>
</nav>

<!-- HERO -->
<div id="hero">
  <div class="hero-glow"></div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="hero-tag">Full Stack Engineer</div>
      <h1>
        <span class="line1">Deepak</span>
        <span class="line2">Tiwari.</span>
      </h1>
      <p class="hero-desc">
        Building <strong>scalable, cloud-native</strong> web applications with React, Node.js, Python and TypeScript. High-performance frontends, robust backend APIs, and production-grade architectures on <strong>AWS & Retrieval-Augmented Generation (RAG)</strong>.
        <br><br>Currently building <strong>agentic AI–powered SaaS platforms</strong> at AriveGuru.
      </p>
      <div class="hero-actions">
        <a href="https://www.linkedin.com/in/dtiwari21/" target="_blank" class="btn btn-primary">View LinkedIn ↗</a>
        <a href="mailto:deepak.tiwari.d21@gmail.com" class="btn btn-ghost">Get in touch</a>
      </div>
    </div>

    <div class="hero-card">
      <div class="card-avatar">DT</div>
      <div class="card-name">Deepak Tiwari</div>
      <div class="card-role">Full Stack Engineer</div>
      <div class="card-info">
        <div class="card-info-item">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
          Bangalore, KA, India
        </div>
        <div class="card-info-item">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 8.63 19.79 19.79 0 01.01 2 2 2 0 012 .18h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.91 7.91a16 16 0 006.29 6.29l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
          +916371230821
        </div>
        <div class="card-info-item">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
          AriveGuru — Current
        </div>
      </div>
      <div class="card-socials">
        <a href="https://www.github.com/deepak-tiwari-dt" target="_blank" class="social-link" title="GitHub">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 00-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0020 4.77 5.07 5.07 0 0019.91 1S18.73.65 16 2.48a13.38 13.38 0 00-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 005 4.77a5.44 5.44 0 00-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 009 18.13V22"/></svg>
        </a>
        <a href="https://www.linkedin.com/in/dtiwari21" target="_blank" class="social-link" title="LinkedIn">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
        <a href="https://www.x.com/dtiwari_25" target="_blank" class="social-link" title="Twitter/X">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.748l7.73-8.835L1.254 2.25H8.08l4.26 5.632zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        </a>
        <a href="https://codepen.io/d-tiwari" target="_blank" class="social-link" title="CodePen">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12 2 22 8.5 22 15.5 12 22 2 15.5 2 8.5 12 2"/><line x1="12" y1="22" x2="12" y2="15.5"/><polyline points="22 8.5 12 15.5 2 8.5"/><polyline points="2 15.5 12 8.5 22 15.5"/><line x1="12" y1="2" x2="12" y2="8.5"/></svg>
        </a>
      </div>
    </div>
  </div>
</div>

<!-- ABOUT / STATS -->
<section id="about">
  <div class="stats-row reveal">
    <div class="stat-item">
      <div class="stat-value">2.2+</div>
      <div class="stat-label">Years Experience</div>
    </div>
    <div class="stat-item">
      <div class="stat-value">116+</div>
      <div class="stat-label">Projects Built</div>
    </div>
    <div class="stat-item">
      <div class="stat-value">3+</div>
      <div class="stat-label">Cloud Platforms</div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label">Toolkit</div>
  <h2 class="section-title">Skills &<br>Technologies</h2>

  <div class="skills-grid reveal">
    <div class="skill-category">
      <div class="skill-category-title">Frontend</div>
      <div class="skill-tags">
        <span class="skill-tag">React</span>
        <span class="skill-tag">TypeScript</span>
        <span class="skill-tag">JavaScript</span>
        <span class="skill-tag">HTML5</span>
        <span class="skill-tag">CSS3</span>
        <span class="skill-tag">Tailwind</span>
        <span class="skill-tag">Sass</span>
        <span class="skill-tag">Bootstrap</span>
        <span class="skill-tag">Material UI</span>
        <span class="skill-tag">Redux</span>
        <span class="skill-tag">Zustand</span>
        <span class="skill-tag">Redux Saga</span>
      </div>
    </div>
    <div class="skill-category">
      <div class="skill-category-title">Backend</div>
      <div class="skill-tags">
        <span class="skill-tag">Node.js</span>
        <span class="skill-tag">Python</span>
        <span class="skill-tag">Mastra</span>
        <span class="skill-tag">Express</span>
        <span class="skill-tag">MongoDB</span>
        <span class="skill-tag">Databricks</span>
        <span class="skill-tag">REST APIs</span>
        <span class="skill-tag">GraphQL</span>
        <span class="skill-tag">PostgreSQL</span>
        <span class="skill-tag">MySQL</span>
        <span class="skill-tag">Firebase</span>
        <span class="skill-tag">Supabase</span>
      </div>
    </div>
    <div class="skill-category">
      <div class="skill-category-title">Cloud & DevOps</div>
      <div class="skill-tags">
        <span class="skill-tag">AWS</span>
        <span class="skill-tag">Azure</span>
        <span class="skill-tag">Firebase</span>
        <span class="skill-tag">Heroku</span>
        <span class="skill-tag">Git</span>
        <span class="skill-tag">Linux</span>
        <span class="skill-tag">Bash</span>
        <span class="skill-tag">Vite</span>
        <span class="skill-tag">Webpack</span>
        <span class="skill-tag">Babel</span>
      </div>
    </div>
    <div class="skill-category">
      <div class="skill-category-title">Tools & Design</div>
      <div class="skill-tags">
        <span class="skill-tag">Figma</span>
        <span class="skill-tag">VS Code</span>
        <span class="skill-tag">XCode</span>
        <span class="skill-tag">MacOS</span>
        <span class="skill-tag">Agile</span>
        <span class="skill-tag">AI/ML</span>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-label">Career</div>
  <h2 class="section-title">Experience</h2>

  <div class="timeline reveal">
    <div class="timeline-item">
      <div class="timeline-meta">
        <span class="timeline-date">2025 — Present</span>
        <span class="timeline-company">AriveGuru</span>
      </div>
      <div class="timeline-title">Software Engineer</div>
      <div class="timeline-desc">Building agentic AI–powered SaaS platforms. Delivering high-performance frontends and robust backend APIs with React, Node.js, and TypeScript. Architecting production-grade solutions on AWS & Retrieval-Augmented Generation (RAG).</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-meta">
        <span class="timeline-date">2024 — 2025</span>
        <span class="timeline-company">klickEdu</span>
      </div>
      <div class="timeline-title">Frontend Developer</div>
      <div class="timeline-desc">Developed scalable web applications with React and TypeScript. Built component libraries and design systems, optimized performance, and collaborated closely with product and design teams.</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-meta">
        <span class="timeline-date">2022 — 2022</span>
        <span class="timeline-company">TCR Innovation</span>
      </div>
      <div class="timeline-title">Frontend Developer Intern</div>
      <div class="timeline-desc">Started building web applications using JavaScript, HTML/CSS, and Node.js. Gained experience with databases, RESTful API design, and cloud deployment workflows.</div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label">Work</div>
  <h2 class="section-title">Featured<br>Projects</h2>

  <div class="projects-grid reveal">
    <div class="project-card">
      <div class="project-number">01</div>
      <div class="project-title">Agentic AI SaaS Platform</div>
      <div class="project-desc">End-to-end AI-powered SaaS application with agentic workflows, real-time data processing, and scalable cloud architecture deployed on AWS.</div>
      <div class="project-stack">
        <span class="stack-pill">React</span>
        <span class="stack-pill">TypeScript</span>
        <span class="stack-pill">Node.js</span>
        <span class="stack-pill">AWS</span>
        <span class="stack-pill">AI/ML</span>
      </div>
    </div>
    <div class="project-card">
      <div class="project-number">02</div>
      <div class="project-title">Cloud-Native Web App</div>
      <div class="project-desc">Scalable full-stack application with Firebase backend, real-time updates, authentication, and a polished React frontend with custom design system.</div>
      <div class="project-stack">
        <span class="stack-pill">React</span>
        <span class="stack-pill">Firebase</span>
        <span class="stack-pill">Redux</span>
        <span class="stack-pill">Tailwind</span>
      </div>
    </div>
    <div class="project-card">
      <div class="project-number">03</div>
      <div class="project-title">RESTful API Platform</div>
      <div class="project-desc">High-performance backend API with Express and PostgreSQL, featuring rate limiting, JWT auth, comprehensive testing, and Docker containerization.</div>
      <div class="project-stack">
        <span class="stack-pill">Node.js</span>
        <span class="stack-pill">Express</span>
        <span class="stack-pill">PostgreSQL</span>
        <span class="stack-pill">Docker</span>
      </div>
    </div>
    <div class="project-card">
      <div class="project-number">04</div>
      <div class="project-title">E-Commerce Dashboard</div>
      <div class="project-desc">Feature-rich admin dashboard with real-time analytics, inventory management, order tracking, and a fully responsive Material UI interface.</div>
      <div class="project-stack">
        <span class="stack-pill">React</span>
        <span class="stack-pill">Material UI</span>
        <span class="stack-pill">MongoDB</span>
        <span class="stack-pill">Recharts</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div id="contact-section">
    <div class="section-label">Reach Out</div>
    <h2 class="section-title">Let's Build<br>Something.</h2>

    <div class="contact-grid reveal">
      <div>
        <p class="contact-copy">
          I'm always open to new opportunities, collaborations, and interesting problems. Whether it's a full-time role, freelance project, or just a conversation — reach out.
        </p>
        <div class="contact-links">
          <a href="mailto:deepak.tiwari.d21@gmail.com" class="contact-link">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            deepak.tiwari.d21@gmail.com
          </a>
          <a href="https://www.linkedin.com/in/dtiwari21" target="_blank" class="contact-link">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
            linkedin.com/in/dtiwari21
          </a>
          <a href="https://www.github.com/deepak-tiwari-dt" target="_blank" class="contact-link">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 00-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0020 4.77 5.07 5.07 0 0019.91 1S18.73.65 16 2.48a13.38 13.38 0 00-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 005 4.77a5.44 5.44 0 00-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 009 18.13V22"/></svg>
            github.com/deepak-tiwari-dt
          </a>
          <a href="https://www.x.com/dtiwari_25" target="_blank" class="contact-link">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.748l7.73-8.835L1.254 2.25H8.08l4.26 5.632zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
            x.com/dtiwari_25
          </a>
        </div>
      </div>
      <div class="contact-form">
        <div class="form-field">
          <label>Your Name</label>
          <input type="text" placeholder="Deepak Tiwari">
        </div>
        <div class="form-field">
          <label>Email</label>
          <input type="email" placeholder="deepak.tiwari.d21@gmail.com">
        </div>
        <div class="form-field">
          <label>Message</label>
          <textarea rows="5" placeholder="Tell me about your project..."></textarea>
        </div>
        <a href="mailto:deepak.tiwari.d21@gmail.com" class="btn btn-primary" style="align-self:flex-start">Send Message →</a>
      </div>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 Deepak Tiwari. All Rights Reserved.</p>
  <div class="footer-badge">
    Built With <span>♥</span> By Deepak Tiwari
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mouseX = 0, mouseY = 0;
  let ringX = 0, ringY = 0;

  document.addEventListener('mousemove', e => {
    mouseX = e.clientX;
    mouseY = e.clientY;
    cursor.style.left = mouseX - 6 + 'px';
    cursor.style.top = mouseY - 6 + 'px';
  });

  function animateRing() {
    ringX += (mouseX - ringX - 18) * 0.12;
    ringY += (mouseY - ringY - 18) * 0.12;
    ring.style.left = ringX + 'px';
    ring.style.top = ringY + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  document.querySelectorAll('a, button, .project-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'scale(2)';
      ring.style.transform = 'scale(1.5)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'scale(1)';
      ring.style.transform = 'scale(1)';
    });
  });

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Typing effect for hero tag
  const tag = document.querySelector('.hero-tag');
  const originalText = tag.textContent;
  tag.textContent = '';
  let i = 0;
  setTimeout(() => {
    const type = () => {
      if (i < originalText.length) {
        tag.textContent = originalText.slice(0, ++i);
        setTimeout(type, 60);
      }
    };
    type();
  }, 400);
</script>
</body>
</html>
