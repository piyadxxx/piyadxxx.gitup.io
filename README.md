<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="DataShield: Interactive College Research Project on Social Media Data Privacy Awareness.">
<title>DataShield | Social Media Privacy & Awareness</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #07090e;
  --surface: #0f141d;
  --surface2: #161c28;
  --text: #f3f7fc;
  --muted: #8d9bb0;
  --primary: #48d1fa;
  --secondary: #ff334f;
  --accent: #55efc4;
  --line: rgba(255, 255, 255, 0.08);
  --glass: rgba(15, 20, 29, 0.78);
  --shadow: 0 20px 45px rgba(0, 0, 0, 0.4);
}

.light {
  --bg: #f4f9fd;
  --surface: #ffffff;
  --surface2: #e8f2fa;
  --text: #0d1522;
  --muted: #53647b;
  --primary: #0284c7;
  --secondary: #e11d48;
  --accent: #059669;
  --line: rgba(13, 21, 34, 0.09);
  --glass: rgba(255, 255, 255, 0.85);
  --shadow: 0 15px 35px rgba(4, 32, 69, 0.08);
}

* { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: 'Plus Jakarta Sans', system-ui, -apple-system, sans-serif;
  background-color: var(--bg);
  color: var(--text);
  line-height: 1.6;
  transition: background-color 0.3s ease, color 0.3s ease;
  overflow-x: hidden;
}

a { text-decoration: none; color: inherit; }
button { font-family: inherit; cursor: pointer; border: none; }

/* Scroll Progress Bar */
.scroll-progress {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--primary), var(--secondary));
  width: 0%;
  z-index: 1000;
}

/* Navigation */
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: var(--glass);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--line);
}
.nav-inner {
  max-width: 1240px;
  margin: auto;
  height: 72px;
  padding: 0 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.logo {
  font-size: 21px;
  font-weight: 800;
  display: flex;
  align-items: center;
  gap: 10px;
  letter-spacing: -0.5px;
}
.logo-icon {
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  border-radius: 9px;
  width: 34px;
  height: 34px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
}
.logo b { color: var(--primary); }
.navlinks { display: flex; gap: 28px; font-size: 14px; font-weight: 600; color: var(--muted); }
.navlinks a:hover { color: var(--primary); transition: color 0.2s; }
.actions { display: flex; gap: 10px; align-items: center; }
.iconbtn {
  border: 1px solid var(--line);
  background: var(--surface2);
  color: var(--text);
  width: 42px;
  height: 42px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  transition: all 0.2s ease;
}
.iconbtn:hover { border-color: var(--primary); transform: translateY(-2px); }
.menu-btn { display: none; }

/* Mobile Overlay Menu */
.mobile-nav {
  display: none;
  position: fixed;
  inset: 72px 0 0 0;
  background: var(--bg);
  padding: 40px 24px;
  flex-direction: column;
  gap: 20px;
  z-index: 99;
  border-top: 1px solid var(--line);
}
.mobile-nav.open { display: flex; }
.mobile-nav a { font-size: 18px; font-weight: 600; }

/* Hero Section */
.hero {
  min-height: 94vh;
  padding: 160px 7% 90px;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}
.glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(120px);
  opacity: 0.22;
  pointer-events: none;
  z-index: 0;
}
.g1 { width: 500px; height: 500px; background: var(--secondary); top: -100px; right: -80px; }
.g2 { width: 450px; height: 450px; background: var(--primary); bottom: -60px; left: -100px; }

.hero-content { max-width: 820px; position: relative; z-index: 1; }
.badge {
  display: inline-flex;
  gap: 8px;
  align-items: center;
  padding: 7px 16px;
  border-radius: 100px;
  border: 1px solid rgba(72, 209, 250, 0.35);
  background: rgba(72, 209, 250, 0.08);
  color: var(--primary);
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 1px;
}
.hero h1 {
  font-size: clamp(38px, 5.8vw, 70px);
  line-height: 1.08;
  letter-spacing: -2px;
  margin: 22px 0;
  font-weight: 800;
}
.gradient {
  background: linear-gradient(100deg, var(--primary) 20%, var(--secondary) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
.hero p { font-size: clamp(16px, 1.8vw, 19px); color: var(--muted); max-width: 660px; }
.cta-group { display: flex; gap: 14px; margin-top: 35px; flex-wrap: wrap; }
.btn {
  padding: 14px 26px;
  border-radius: 12px;
  font-size: 15px;
  font-weight: 700;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.25s ease;
}
.btn-primary {
  background: linear-gradient(135deg, var(--primary), #0284c7);
  color: #fff;
  box-shadow: 0 8px 20px rgba(72, 209, 250, 0.3);
}
.btn-primary:hover { transform: translateY(-3px); box-shadow: 0 12px 25px rgba(72, 209, 250, 0.4); }
.btn-secondary { background: var(--surface2); border: 1px solid var(--line); color: var(--text); }
.btn-secondary:hover { border-color: var(--primary); transform: translateY(-3px); }

.hero-stats {
  display: flex;
  gap: 36px;
  margin-top: 55px;
  padding-top: 30px;
  border-top: 1px solid var(--line);
  flex-wrap: wrap;
}
.hero-stats div strong { font-size: 28px; font-weight: 800; display: block; }
.hero-stats div span { font-size: 13px; color: var(--muted); }

/* Common Sections */
section { padding: 100px 7%; scroll-margin-top: 72px; }
.wrap { max-width: 1200px; margin: auto; }
.section-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  gap: 30px;
  margin-bottom: 45px;
  flex-wrap: wrap;
}
.kicker {
  color: var(--primary);
  font-size: 12px;
  font-weight: 800;
  letter-spacing: 2px;
  text-transform: uppercase;
}
h2 { font-size: clamp(28px, 4vw, 42px); line-height: 1.15; letter-spacing: -1px; margin-top: 6px; }
.subtext { max-width: 500px; color: var(--muted); font-size: 15px; }

/* Grid Layouts & Cards */
.grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
.card {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 20px;
  padding: 30px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  box-shadow: var(--shadow);
}
.card:hover { transform: translateY(-5px); border-color: var(--primary); }
.card-icon {
  width: 52px;
  height: 52px;
  border-radius: 14px;
  background: var(--surface2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  margin-bottom: 20px;
}
.card h3 { font-size: 19px; margin-bottom: 10px; }
.card p { color: var(--muted); font-size: 14.5px; }

/* Platforms Grid */
.platform-grid { grid-template-columns: repeat(6, 1fr); gap: 16px; }
.platform-card {
  text-align: center;
  padding: 24px 14px;
  cursor: pointer;
}
.platform-card:hover { background: var(--surface2); border-color: var(--primary); }
.platform-card .emoji { font-size: 34px; margin-bottom: 12px; display: block; }
.platform-card h4 { font-size: 15px; margin-bottom: 5px; }
.platform-card span { font-size: 12px; color: var(--muted); }

/* Threat Index Cards */
.threat-badge {
  font-size: 11px;
  font-weight: 800;
  padding: 4px 9px;
  border-radius: 6px;
  background: rgba(255, 51, 79, 0.12);
  color: var(--secondary);
  float: right;
}

/* Analytics Dashboard */
.dashboard { display: grid; grid-template-columns: 1.2fr 0.8fr; gap: 24px; }
.chart-card { background: var(--surface); border: 1px solid var(--line); border-radius: 20px; padding: 32px; box-shadow: var(--shadow); }
.bar-group { margin-top: 24px; }
.bar-item { margin-bottom: 20px; }
.bar-label { display: flex; justify-content: space-between; font-size: 14px; font-weight: 600; margin-bottom: 8px; }
.bar-track { height: 10px; background: var(--surface2); border-radius: 10px; overflow: hidden; }
.bar-fill { height: 100%; border-radius: 10px; width: 0%; transition: width 1.2s cubic-bezier(0.16, 1, 0.3, 1); }
.c1 { background: linear-gradient(90deg, var(--primary), #3b82f6); }
.c2 { background: linear-gradient(90deg, #3b82f6, #6366f1); }
.c3 { background: linear-gradient(90deg, #6366f1, var(--secondary)); }
.c4 { background: linear-gradient(90deg, var(--secondary), #ff7675); }

/* Donut Chart Simulation */
.donut-wrap { position: relative; width: 190px; height: 190px; margin: 30px auto; }
.donut-circle {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: conic-gradient(var(--primary) 0% 70%, var(--secondary) 70% 88%, #2d3748 88% 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}
.donut-inner {
  width: 125px;
  height: 125px;
  background: var(--surface);
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.donut-inner span { font-size: 26px; font-weight: 800; }
.donut-inner small { font-size: 11px; color: var(--muted); text-transform: uppercase; }
.legend { display: flex; justify-content: center; gap: 20px; font-size: 13px; color: var(--muted); margin-top: 20px; flex-wrap: wrap; }
.legend span { display: flex; align-items: center; gap: 7px; }
.legend i { width: 10px; height: 10px; border-radius: 50%; display: inline-block; }

/* Interactive Privacy Audit Simulator */
.quiz-box {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: 24px;
  padding: 36px;
  box-shadow: var(--shadow);
}
.quiz-item {
  border-bottom: 1px solid var(--line);
  padding: 16px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 15px;
}
.quiz-item:last-child { border-bottom: none; }
.quiz-check {
  width: 22px;
  height: 22px;
  cursor: pointer;
  accent-color: var(--primary);
}
.score-box {
  margin-top: 25px;
  padding: 20px;
  background: var(--surface2);
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Timeline */
.timeline { border-left: 2px solid var(--line); margin-left: 12px; padding-left: 28px; }
.step { position: relative; margin-bottom: 35px; }
.step:before {
  content: "";
  position: absolute;
  left: -35px;
  top: 6px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--primary);
  box-shadow: 0 0 0 5px rgba(72, 209, 250, 0.2);
}

/* Footer */
footer {
  padding: 60px 7% 40px;
  border-top: 1px solid var(--line);
  background: var(--surface);
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
  font-size: 14px;
  color: var(--muted);
}

/* Animations */
.reveal { opacity: 0; transform: translateY(25px); transition: 0.7s cubic-bezier(0.16, 1, 0.3, 1); }
.reveal.show { opacity: 1; transform: translateY(0); }

/* Responsiveness */
@media (max-width: 992px) {
  .grid { grid-template-columns: repeat(2, 1fr); }
  .platform-grid { grid-template-columns: repeat(3, 1fr); }
  .dashboard { grid-template-columns: 1fr; }
  .navlinks { display: none; }
  .menu-btn { display: flex; }
}
@media (max-width: 650px) {
  .grid, .platform-grid { grid-template-columns: 1fr; }
  .hero { padding: 130px 6% 60px; }
  section { padding: 75px 6%; }
  footer { flex-direction: column; text-align: center; }
}
</style>
</head>
<body>

<div class="scroll-progress" id="progress"></div>

<!-- Navigation -->
<nav class="nav">
  <div class="nav-inner">
    <a class="logo" href="#home">
      <span class="logo-icon">🛡️</span>
      <span>Data<b>Shield</b></span>
    </a>
    <div class="navlinks">
      <a href="#about">About</a>
      <a href="#platforms">Platforms</a>
      <a href="#risks">Threats</a>
      <a href="#analysis">Analytics</a>
      <a href="#audit">Check Risk</a>
      <a href="#methods">Methodology</a>
    </div>
    <div class="actions">
      <button class="iconbtn" id="themeBtn" aria-label="Toggle Theme" title="Toggle Theme">☀️</button>
      <button class="iconbtn menu-btn" id="menuBtn" aria-label="Open Navigation">☰</button>
    </div>
  </div>
</nav>

<!-- Mobile Slide Nav -->
<div class="mobile-nav" id="mobileNav">
  <a href="#about" class="mob-link">About Project</a>
  <a href="#platforms" class="mob-link">Platforms Examined</a>
  <a href="#risks" class="mob-link">Common Threats</a>
  <a href="#analysis" class="mob-link">Data Insights</a>
  <a href="#audit" class="mob-link">Privacy Self-Check</a>
  <a href="#methods" class="mob-link">Methodology</a>
</div>

<!-- Hero Section -->
<header class="hero" id="home">
  <div class="glow g1"></div>
  <div class="glow g2"></div>
  <div class="hero-content">
    <span class="badge">● RESEARCH INITIATIVE • 2026</span>
    <h1>Take Control of Your <span class="gradient">Digital Footprint.</span></h1>
    <p>A comprehensive research project evaluating data privacy awareness, cyber risks, and sharing habits among university students across modern social media ecosystems.</p>
    
    <div class="cta-group">
      <a class="btn btn-primary" href="#audit">Check Your Privacy Score →</a>
      <a class="btn btn-secondary" href="#analysis">Explore Survey Data</a>
    </div>

    <div class="hero-stats">
      <div><strong>15+</strong><span>Key Indicators</span></div>
      <div><strong>6</strong><span>Platforms Studied</span></div>
      <div><strong>18-24</strong><span>Target Age Group</span></div>
      <div><strong>100%</strong><span>Anonymized Data</span></div>
    </div>
  </div>
</header>

<!-- Project Overview -->
<section id="about">
  <div class="wrap">
    <div class="section-header reveal">
      <div>
        <div class="kicker">01 — PROJECT BACKGROUND</div>
        <h2>Why Data Privacy Matters</h2>
      </div>
      <p class="subtext">Colleges have become prime targets for social engineering, identity theft, and algorithmic profiling.</p>
    </div>

    <div class="grid">
      <div class="card reveal">
        <div class="card-icon">🎯</div>
        <h3>Research Scope</h3>
        <p>Assessing how everyday behaviors—like sharing check-ins or accepting third-party cookies—impact students' permanent digital records.</p>
      </div>
      <div class="card reveal">
        <div class="card-icon">🔬</div>
        <h3>Critical Observations</h3>
        <p>Over 60% of students admit they skip privacy policies completely, unknowingly trading granular behavioral data for platform access.</p>
      </div>
      <div class="card reveal">
        <div class="card-icon">🔐</div>
        <h3>Actionable Defense</h3>
        <p>Providing practical zero-trust configurations that restrict location beacons, third-party trackers, and automated data harvesting.</p>
      </div>
    </div>
  </div>
</section>

<!-- Platforms Focus -->
<section id="platforms" style="background: linear-gradient(180deg, transparent, rgba(72,209,250,0.03));">
  <div class="wrap">
    <div class="section-header reveal">
      <div>
        <div class="kicker">02 — PLATFORM AUDIT</div>
        <h2>Ecosystems Under Review</h2>
      </div>
      <p class="subtext">Every platform utilizes unique telemetry and permission demands. Here is where the data leaks happen.</p>
    </div>

    <div class="grid platform-grid">
      <div class="card platform-card reveal">
        <span class="emoji">📸</span>
        <h4>Instagram</h4>
        <span>EXIF data & stories</span>
      </div>
      <div class="card platform-card reveal">
        <span class="emoji">💬</span>
        <h4>WhatsApp</h4>
        <span>Metadata & backups</span>
      </div>
      <div class="card platform-card reveal">
        <span class="emoji">👥</span>
        <h4>Facebook</h4>
        <span>Off-Facebook activity</span>
      </div>
      <div class="card platform-card reveal">
        <span class="emoji">👻</span>
        <h4>Snapchat</h4>
        <span>Precise Snap Map</span>
      </div>
      <div class="card platform-card reveal">
        <span class="emoji">🎵</span>
        <h4>TikTok</h4>
        <span>Keystroke telemetry</span>
      </div>
      <div class="card platform-card reveal">
        <span class="emoji">▶️</span>
        <h4>YouTube</h4>
        <span>Search & watch history</span>
      </div>
    </div>
  </div>
</section>

<!-- Threats & Vulnerabilities -->
<section id="risks">
  <div class="wrap">
    <div class="section-header reveal">
      <div>
        <div class="kicker">03 — VULNERABILITIES</div>
        <h2>Key Risk Factors</h2>
      </div>
      <p class="subtext">The most critical vulnerabilities observed in student social media routines.</p>
    </div>

    <div class="grid">
      <div class="card reveal">
        <span class="threat-badge">HIGH RISK</span>
        <div class="card-icon">📍</div>
        <h3>Geotagging & Oversharing</h3>
        <p>Real-time location tags and daily schedule disclosures leave users vulnerable to physical tracking and targeted spear-phishing.</p>
      </div>

      <div class="card reveal">
        <span class="threat-badge">CRITICAL</span>
        <div class="card-icon">🔑</div>
        <h3>Credential Recycling</h3>
        <p>Using one password across campus portals and social networks means a breach in one leaks all connected accounts.</p>
      </div>

      <div class="card reveal">
        <span class="threat-badge">MEDIUM RISK</span>
        <div class="card-icon">📱</div>
        <h3>Excessive Permissions</h3>
        <p>Flashlight, photo editing, and meme apps requesting non-essential access to contacts, storage, and ambient mic recording.</p>
      </div>
    </div>
  </div>
</section>

<!-- Survey Dashboard -->
<section id="analysis">
  <div class="wrap">
    <div class="section-header reveal">
      <div>
        <div class="kicker">04 — DATA & FINDINGS</div>
        <h2>Survey Insights</h2>
      </div>
      <p class="subtext">Aggregated responses measuring security awareness and student habits.</p>
    </div>

    <div class="dashboard">
      <div class="chart-card reveal">
        <h3>Privacy Hygiene Index</h3>
        <p style="color: var(--muted); font-size: 13.5px; margin-top: 4px;">Percentage of respondents answering "Yes"</p>
        
        <div class="bar-group">
          <div class="bar-item">
            <div class="bar-label"><span>Uses 2-Factor Authentication (2FA)</span><span>78%</span></div>
            <div class="bar-track"><div class="bar-fill c1" data-fill="78%"></div></div>
          </div>
          <div class="bar-item">
            <div class="bar-label"><span>Regularly Audits App Permissions</span><span>46%</span></div>
            <div class="bar-track"><div class="bar-fill c2" data-fill="46%"></div></div>
          </div>
          <div class="bar-item">
            <div class="bar-label"><span>Reads Privacy Policy Updates</span><span>18%</span></div>
            <div class="bar-track"><div class="bar-fill c3" data-fill="18%"></div></div>
          </div>
          <div class="bar-item">
            <div class="bar-label"><span>Can Identify Phishing Links</span><span>62%</span></div>
            <div class="bar-track"><div class="bar-fill c4" data-fill="62%"></div></div>
          </div>
        </div>
      </div>

      <div class="chart-card reveal">
        <h3>Awareness Distribution</h3>
        <div class="donut-wrap">
          <div class="donut-circle">
            <div class="donut-inner">
              <span>70%</span>
              <small>Protected</small>
            </div>
          </div>
        </div>
        <div class="legend">
          <span><i style="background:var(--primary)"></i> High awareness</span>
          <span><i style="background:var(--secondary)"></i> Moderate risk</span>
          <span><i style="background:#2d3748"></i> High risk</span>
        </div>
      </div>
    </div>
  </div>
</secti
