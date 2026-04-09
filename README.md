<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Adela — Website PM / Website Planner</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC:wght@300;400;600&family=Noto+Sans+TC:wght@300;400;500&display=swap" rel="stylesheet">
<style>
/* =====================
   RESET & ROOT
===================== */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --white: #ffffff;
  --bg: #f9f8f6;
  --bg-card: #ffffff;
  --sage: #7a9e84;
  --sage-light: #c8dccb;
  --sage-pale: #eef5ef;
  --blush: #e0cfc9;
  --blush-pale: #f7f2f0;
  --text: #2a2a28;
  --text-mid: #5a5a56;
  --text-muted: #9a9a94;
  --border: rgba(122,158,132,0.2);
  --shadow-sm: 0 2px 12px rgba(0,0,0,0.06);
  --shadow-md: 0 6px 28px rgba(0,0,0,0.09);
  --shadow-hover: 0 16px 48px rgba(122,158,132,0.18);
  --radius: 16px;
  --radius-sm: 10px;
  --transition: 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

html { scroll-behavior: smooth; }

body {
  font-family: 'Noto Sans TC', sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 15px;
  line-height: 1.8;
  -webkit-font-smoothing: antialiased;
}

img { max-width: 100%; display: block; }
a { color: inherit; text-decoration: none; }

/* =====================
   SCROLL ANIMATION
===================== */
.fade-in {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}
.fade-in-delay-1 { transition-delay: 0.1s; }
.fade-in-delay-2 { transition-delay: 0.2s; }
.fade-in-delay-3 { transition-delay: 0.3s; }
.fade-in-delay-4 { transition-delay: 0.4s; }

/* =====================
   NAV
===================== */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  height: 64px;
  display: flex; justify-content: space-between; align-items: center;
  padding: 0 2.5rem;
  background: rgba(249,248,246,0.9);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border);
  z-index: 999;
}
.nav-logo {
  font-family: 'Noto Serif TC', serif;
  font-size: 1.15rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  color: var(--text);
}
.nav-logo span { color: var(--sage); }
.nav-links {
  display: flex; gap: 2rem;
  list-style: none;
}
.nav-links a {
  font-size: 0.82rem;
  font-weight: 400;
  letter-spacing: 0.06em;
  color: var(--text-mid);
  transition: color var(--transition);
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute; bottom: -3px; left: 0; right: 0;
  height: 1px;
  background: var(--sage);
  transform: scaleX(0);
  transition: transform var(--transition);
}
.nav-links a:hover { color: var(--sage); }
.nav-links a:hover::after { transform: scaleX(1); }

.nav-hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 4px; }
.nav-hamburger span { display: block; width: 22px; height: 1.5px; background: var(--text); transition: var(--transition); }

/* =====================
   HERO
===================== */
.hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding: 8rem 2.5rem 5rem;
  position: relative; overflow: hidden;
}
.hero-bg {
  position: absolute; inset: 0; pointer-events: none;
  background:
    radial-gradient(ellipse 55% 60% at 90% 15%, rgba(200,220,203,0.32) 0%, transparent 65%),
    radial-gradient(ellipse 40% 45% at 10% 90%, rgba(224,207,201,0.28) 0%, transparent 60%),
    radial-gradient(ellipse 30% 35% at 50% 50%, rgba(238,245,239,0.4) 0%, transparent 70%);
}
.hero-deco {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
}
.hero-deco-1 {
  width: 480px; height: 480px;
  border: 1px solid rgba(122,158,132,0.12);
  top: -120px; right: -80px;
  animation: rotate 30s linear infinite;
}
.hero-deco-2 {
  width: 300px; height: 300px;
  border: 1px solid rgba(224,207,201,0.25);
  bottom: 80px; right: 160px;
  animation: rotate 22s linear infinite reverse;
}
@keyframes rotate { to { transform: rotate(360deg); } }

.hero-content { position: relative; max-width: 640px; }
.hero-eyebrow {
  display: flex; align-items: center; gap: 0.75rem;
  font-size: 0.75rem; font-weight: 500;
  letter-spacing: 0.14em; text-transform: uppercase;
  color: var(--sage); margin-bottom: 1.5rem;
  animation: fadeUp 0.9s ease both;
}
.hero-eyebrow::before {
  content: '';
  display: block; width: 28px; height: 1px;
  background: var(--sage);
}
.hero h1 {
  font-family: 'Noto Serif TC', serif;
  font-size: clamp(2.6rem, 5.5vw, 4.2rem);
  font-weight: 300;
  line-height: 1.2;
  letter-spacing: -0.01em;
  margin-bottom: 1.4rem;
  animation: fadeUp 0.9s ease 0.1s both;
}
.hero h1 strong {
  font-weight: 600;
  color: var(--sage);
  display: block;
}
.hero-desc {
  font-size: 1rem;
  color: var(--text-mid);
  line-height: 1.85;
  max-width: 460px;
  margin-bottom: 2.5rem;
  animation: fadeUp 0.9s ease 0.2s both;
}
.hero-cta {
  display: flex; gap: 1rem; flex-wrap: wrap;
  animation: fadeUp 0.9s ease 0.3s both;
}
.btn {
  display: inline-flex; align-items: center; gap: 0.4rem;
  padding: 0.75rem 1.8rem;
  font-size: 0.85rem; font-weight: 500;
  letter-spacing: 0.04em;
  border-radius: 100px;
  transition: var(--transition);
  cursor: pointer;
  border: none; font-family: inherit;
}
.btn-primary {
  background: var(--sage); color: #fff;
}
.btn-primary:hover { background: #5f8068; transform: translateY(-2px); box-shadow: var(--shadow-md); }
.btn-outline {
  background: transparent; color: var(--text);
  border: 1.5px solid var(--blush);
}
.btn-outline:hover { border-color: var(--sage); color: var(--sage); transform: translateY(-2px); }

.hero-stats {
  display: flex; gap: 3rem; flex-wrap: wrap;
  margin-top: 4rem;
  padding-top: 2rem;
  border-top: 1px solid var(--border);
  animation: fadeUp 0.9s ease 0.4s both;
}
.stat-num {
  font-family: 'Noto Serif TC', serif;
  font-size: 2.2rem; font-weight: 300;
  color: var(--sage); line-height: 1;
}
.stat-label {
  font-size: 0.75rem; color: var(--text-muted);
  letter-spacing: 0.06em; margin-top: 0.3rem;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}

/* =====================
   SECTION COMMON
===================== */
section { padding: 6rem 2.5rem; }
.section-inner { max-width: 1100px; margin: 0 auto; }

.section-label {
  display: flex; align-items: center; gap: 0.75rem;
  font-size: 0.72rem; font-weight: 500;
  letter-spacing: 0.14em; text-transform: uppercase;
  color: var(--sage); margin-bottom: 1rem;
}
.section-label::before {
  content: '';
  display: block; width: 20px; height: 1px;
  background: var(--sage);
}
.section-title {
  font-family: 'Noto Serif TC', serif;
  font-size: clamp(1.6rem, 3vw, 2.4rem);
  font-weight: 300; line-height: 1.3;
  margin-bottom: 3rem;
}

/* =====================
   ABOUT
===================== */
#about { background: var(--white); }
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1.6fr;
  gap: 5rem; align-items: center;
}
.about-photo-wrap {
  aspect-ratio: 4/5;
  border-radius: 2rem;
  background: linear-gradient(135deg, var(--sage-pale) 0%, var(--blush-pale) 100%);
  display: flex; align-items: center; justify-content: center;
  position: relative; overflow: hidden;
  border: 1px solid var(--border);
}
.about-photo-placeholder {
  font-size: 4rem; opacity: 0.4;
}
.about-photo-label {
  position: absolute; bottom: 1.5rem; left: 0; right: 0;
  text-align: center;
  font-size: 0.75rem; color: var(--text-muted);
  letter-spacing: 0.08em;
}
.about-text p {
  font-size: 0.95rem; color: var(--text-mid);
  line-height: 1.9; margin-bottom: 1.2rem;
}
.about-text p strong { color: var(--text); font-weight: 500; }
.about-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1.5rem; }
.about-tag {
  font-size: 0.75rem; padding: 0.3rem 0.85rem;
  border-radius: 100px;
  background: var(--sage-pale); color: var(--sage);
  border: 1px solid var(--sage-light);
}

/* =====================
   SKILLS
===================== */
#skills { background: var(--bg); }
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}
.skill-card {
  background: var(--white);
  border-radius: var(--radius-sm);
  border: 1px solid var(--border);
  padding: 1.4rem 1.5rem;
  display: flex; align-items: flex-start; gap: 1rem;
  box-shadow: var(--shadow-sm);
  transition: var(--transition);
}
.skill-card:hover {
  transform: translateY(-3px);
  box-shadow: var(--shadow-md);
  border-color: var(--sage-light);
}
.skill-icon {
  width: 36px; height: 36px; flex-shrink: 0;
  border-radius: 8px;
  background: var(--sage-pale);
  display: flex; align-items: center; justify-content: center;
  font-size: 1rem;
}
.skill-name { font-size: 0.85rem; font-weight: 500; color: var(--text); margin-bottom: 0.2rem; }
.skill-desc { font-size: 0.75rem; color: var(--text-muted); line-height: 1.5; }

/* =====================
   FEATURED PROJECTS
===================== */
#featured { background: var(--white); }
.featured-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}
.featured-card {
  background: var(--bg-card);
  border-radius: var(--radius);
  border: 1px solid var(--border);
  box-shadow: var(--shadow-sm);
  overflow: hidden;
  transition: var(--transition);
  cursor: pointer;
  position: relative;
}
.featured-card:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-hover);
  border-color: var(--sage-light);
}
.featured-card-thumb {
  height: 180px;
  display: flex; align-items: center; justify-content: center;
  position: relative; overflow: hidden;
  font-size: 2.8rem;
}
.featured-card-body { padding: 1.5rem 1.6rem 1.8rem; }
.featured-card-cat {
  font-size: 0.68rem; font-weight: 500;
  letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--sage); margin-bottom: 0.5rem;
}
.featured-card-name {
  font-family: 'Noto Serif TC', serif;
  font-size: 1.15rem; font-weight: 600;
  margin-bottom: 0.6rem; color: var(--text);
}
.featured-card-intro {
  font-size: 0.82rem; color: var(--text-mid);
  line-height: 1.7; margin-bottom: 1.1rem;
}
.featured-card-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 1.2rem; }
.tag {
  font-size: 0.68rem; padding: 0.2rem 0.65rem;
  border-radius: 100px;
  background: var(--sage-pale); color: var(--sage);
  border: 1px solid var(--sage-light);
}
.featured-card-footer {
  display: flex; justify-content: space-between; align-items: center;
  padding-top: 1rem;
  border-top: 1px solid var(--border);
}
.featured-card-link {
  display: inline-flex; align-items: center; gap: 0.35rem;
  font-size: 0.78rem; color: var(--sage); font-weight: 500;
  transition: gap var(--transition);
}
.featured-card-link:hover { gap: 0.55rem; }
.featured-card-link svg { width: 12px; height: 12px; }
.featured-card-role {
  font-size: 0.7rem; color: var(--text-muted);
}

/* Modal */
.modal-overlay {
  position: fixed; inset: 0;
  background: rgba(42,42,40,0.55);
  backdrop-filter: blur(6px);
  z-index: 1000;
  display: flex; align-items: center; justify-content: center;
  padding: 2rem;
  opacity: 0; pointer-events: none;
  transition: opacity 0.3s ease;
}
.modal-overlay.open { opacity: 1; pointer-events: all; }

.modal {
  background: var(--white);
  border-radius: 1.5rem;
  width: 100%; max-width: 700px;
  max-height: 85vh; overflow-y: auto;
  box-shadow: 0 32px 80px rgba(0,0,0,0.18);
  transform: translateY(20px);
  transition: transform 0.3s ease;
}
.modal-overlay.open .modal { transform: translateY(0); }

.modal-header {
  padding: 2rem 2rem 1.2rem;
  border-bottom: 1px solid var(--border);
  display: flex; justify-content: space-between; align-items: flex-start;
}
.modal-cat {
  font-size: 0.7rem; font-weight: 500;
  letter-spacing: 0.12em; text-transform: uppercase;
  color: var(--sage); margin-bottom: 0.4rem;
}
.modal-title {
  font-family: 'Noto Serif TC', serif;
  font-size: 1.5rem; font-weight: 600; color: var(--text);
}
.modal-close {
  width: 32px; height: 32px; flex-shrink: 0;
  border-radius: 50%; border: 1px solid var(--border);
  background: none; cursor: pointer; font-size: 1rem;
  display: flex; align-items: center; justify-content: center;
  color: var(--text-muted); transition: var(--transition);
  margin-left: 1rem;
}
.modal-close:hover { background: var(--bg); color: var(--text); }

.modal-body { padding: 1.8rem 2rem 2rem; }
.modal-section { margin-bottom: 1.6rem; }
.modal-section-title {
  font-size: 0.72rem; font-weight: 500;
  letter-spacing: 0.1em; text-transform: uppercase;
  color: var(--sage); margin-bottom: 0.6rem;
  display: flex; align-items: center; gap: 0.5rem;
}
.modal-section-title::before {
  content: ''; display: block;
  width: 14px; height: 1px; background: var(--sage);
}
.modal-section p {
  font-size: 0.88rem; color: var(--text-mid); line-height: 1.8;
}
.modal-section ul {
  list-style: none; padding: 0;
}
.modal-section ul li {
  font-size: 0.88rem; color: var(--text-mid);
  padding: 0.3rem 0; padding-left: 1.1rem;
  position: relative; line-height: 1.7;
}
.modal-section ul li::before {
  content: '·';
  position: absolute; left: 0;
  color: var(--sage); font-weight: 700;
}
.modal-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
.modal-result {
  background: var(--sage-pale);
  border-radius: var(--radius-sm);
  border: 1px solid var(--sage-light);
  padding: 1rem 1.2rem;
  font-size: 0.88rem; color: var(--text-mid); line-height: 1.8;
}
.modal-link-btn {
  display: inline-flex; align-items: center; gap: 0.5rem;
  padding: 0.7rem 1.5rem;
  background: var(--sage); color: #fff;
  border-radius: 100px;
  font-size: 0.82rem; font-weight: 500;
  margin-top: 1rem;
  transition: var(--transition);
}
.modal-link-btn:hover { background: #5f8068; transform: translateY(-2px); }
.modal-link-btn svg { width: 13px; height: 13px; }

/* =====================
   OTHER PROJECTS
===================== */
#other { background: var(--bg); }
.other-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}
.other-card {
  background: var(--white);
  border-radius: var(--radius-sm);
  border: 1px solid var(--border);
  padding: 1.2rem 1.4rem;
  display: flex; align-items: center; gap: 1rem;
  box-shadow: var(--shadow-sm);
  transition: var(--transition);
}
.other-card:hover {
  transform: translateY(-3px);
  box-shadow: var(--shadow-md);
  border-color: var(--sage-light);
}
.other-card-emoji {
  font-size: 1.4rem; flex-shrink: 0;
  width: 40px; height: 40px;
  display: flex; align-items: center; justify-content: center;
  background: var(--sage-pale);
  border-radius: 10px;
}
.other-card-name {
  font-size: 0.9rem; font-weight: 500; color: var(--text);
  margin-bottom: 0.2rem;
}
.other-card-link {
  font-size: 0.72rem; color: var(--sage);
  display: flex; align-items: center; gap: 0.25rem;
  transition: gap var(--transition);
}
.other-card:hover .other-card-link { gap: 0.4rem; }

/* =====================
   CONTACT
===================== */
#contact { background: var(--white); }
.contact-inner {
  max-width: 620px; margin: 0 auto; text-align: center;
}
.contact-inner .section-label { justify-content: center; }
.contact-inner .section-label::before { display: none; }
.contact-title {
  font-family: 'Noto Serif TC', serif;
  font-size: clamp(1.8rem, 3.5vw, 2.6rem);
  font-weight: 300; line-height: 1.3;
  margin-bottom: 1.2rem;
}
.contact-desc {
  font-size: 0.95rem; color: var(--text-mid);
  line-height: 1.85; margin-bottom: 2.5rem;
}
.contact-links { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
.contact-item {
  display: flex; align-items: center; gap: 0.6rem;
  padding: 0.9rem 1.8rem;
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 100px;
  font-size: 0.85rem; color: var(--text-mid);
  transition: var(--transition);
}
.contact-item:hover {
  background: var(--sage-pale);
  border-color: var(--sage-light);
  color: var(--sage);
  transform: translateY(-2px);
}
.contact-item svg { width: 16px; height: 16px; }

/* =====================
   FOOTER
===================== */
footer {
  background: var(--bg);
  border-top: 1px solid var(--border);
  padding: 2rem 2.5rem;
  display: flex; justify-content: space-between; align-items: center;
  flex-wrap: wrap; gap: 1rem;
}
.footer-name {
  font-family: 'Noto Serif TC', serif;
  font-size: 1rem; font-weight: 600;
}
.footer-name span { color: var(--sage); }
.footer-copy { font-size: 0.78rem; color: var(--text-muted); }

/* =====================
   THUMB GRADIENTS
===================== */
.th-sage { background: linear-gradient(135deg, #ddeadf 0%, #eef5ef 100%); }
.th-blush { background: linear-gradient(135deg, #f5ebe8 0%, #fde8d8 100%); }
.th-lavender { background: linear-gradient(135deg, #e8e0f5 0%, #ddeadf 100%); }
.th-sky { background: linear-gradient(135deg, #daeaf5 0%, #e8f5ee 100%); }
.th-peach { background: linear-gradient(135deg, #fde8d0 0%, #f5ebe8 100%); }
.th-mint { background: linear-gradient(135deg, #d8f0e8 0%, #ddeadf 100%); }
.th-rose { background: linear-gradient(135deg, #f5d8e0 0%, #f5ebe8 100%); }
.th-warm { background: linear-gradient(135deg, #f5ead8 0%, #fde8d0 100%); }

/* =====================
   RWD
===================== */
@media (max-width: 900px) {
  .featured-grid { grid-template-columns: repeat(2, 1fr); }
  .other-grid { grid-template-columns: repeat(2, 1fr); }
  .about-grid { grid-template-columns: 1fr; gap: 2.5rem; }
  .about-photo-wrap { aspect-ratio: 3/2; max-width: 380px; }
}

@media (max-width: 640px) {
  nav { padding: 0 1.4rem; }
  .nav-links { display: none; }
  .nav-hamburger { display: flex; }
  .nav-links.open {
    display: flex; flex-direction: column;
    position: fixed; top: 64px; left: 0; right: 0;
    background: rgba(249,248,246,0.97);
    padding: 1.5rem 2rem 2rem;
    gap: 1.2rem;
    border-bottom: 1px solid var(--border);
  }
  section { padding: 4rem 1.4rem; }
  .hero { padding: 7rem 1.4rem 4rem; }
  .hero h1 { font-size: 2.2rem; }
  .hero-stats { gap: 2rem; }
  .featured-grid { grid-template-columns: 1fr; }
  .other-grid { grid-template-columns: 1fr; }
  .skills-grid { grid-template-columns: 1fr 1fr; }
  footer { flex-direction: column; text-align: center; }
  .modal { border-radius: 1rem; }
  .modal-header, .modal-body { padding: 1.4rem 1.4rem; }
}
</style>
</head>
<body>

<!-- ===================== NAV ===================== -->
<nav>
  <div class="nav-logo">Adela<span>.</span></div>
  <ul class="nav-links" id="navLinks">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#featured">Projects</a></li>

  </ul>
  <div class="nav-hamburger" id="hamburger" onclick="toggleMenu()">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- ===================== HERO ===================== -->
<section class="hero" id="home">
  <div class="hero-bg"></div>
  <div class="hero-deco hero-deco-1"></div>
  <div class="hero-deco hero-deco-2"></div>
  <div class="hero-content">
    <div class="hero-eyebrow">Website PM · Website Planner</div>
   <h1>
  嗨，我是 Adela<br>
  <strong>專注於網站規劃與專案管理。</strong>
</h1>
<p class="hero-desc">
  負責網站專案的前期規劃、需求整理與跨部門溝通，
  協助團隊從零建立網站架構並順利上線。
  累積多個醫療、法律、美容、餐飲與工程產業的網站專案經驗。
</p>
    <div class="hero-cta">
      <a href="#featured" class="btn btn-primary">查看作品集</a>
      <a href="#contact" class="btn btn-outline">與我聯絡</a>
    </div>
    <div class="hero-stats">
      <div>
        <div class="stat-num">25+</div>
        <div class="stat-label">完成網站專案</div>
      </div>
      <div>
        <div class="stat-num">10+</div>
        <div class="stat-label">產業類別</div>
      </div>
      <div>
        <div class="stat-num">100%</div>
        <div class="stat-label">全程參與把關</div>
      </div>
    </div>
  </div>
</section>

<!-- ===================== ABOUT ===================== -->
<section id="about">
  <div class="section-inner">
    <div class="about-grid">
      <div class="about-photo-wrap fade-in">
        <div class="about-photo-placeholder">🌿</div>
        <img src="https://i.meee.com.tw/ABWdMKq.jpg" alt="Adela — Website PM" class="about-photo">
      </div>
     <div class="about-text fade-in fade-in-delay-1">
  <div class="section-label">About Me</div>
  <h2 class="section-title">用規劃與溝通，<br>讓網站真正發揮作用</h2>

  <p>
    我是 Adela，一位專注於網站規劃的 <strong>Website PM / Planner</strong>。
    從需求訪談、資訊架構設計到內容溝通與網站上線前的品質確認，
    我參與網站專案的每個重要環節。
  </p>

  <p>
    我相信好的網站不只是外觀漂亮，
    更需要<strong>清晰的架構邏輯</strong>、<strong>順暢的使用動線</strong>，
    以及能真正傳遞品牌價值的內容。
  </p>

  <p>
    至今已協助 <strong>25+</strong> 個品牌建立網站，
    產業橫跨診所、法律顧問、美容美髮、寵物、音響等不同領域，
    陪伴品牌一步步建立清晰且具信任感的數位形象。
  </p>
</div>
        <div class="about-tags">
          <span class="about-tag">網站規劃</span>
          <span class="about-tag">文案溝通</span>
          <span class="about-tag">專案管理</span>
          <span class="about-tag">跨部門協作</span>
          <span class="about-tag">SEO 基礎</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===================== SKILLS ===================== -->
<section id="skills">
  <div class="section-inner">
    <div class="section-label fade-in">Skills</div>
    <h2 class="section-title fade-in">核心技能</h2>
    <div class="skills-grid">
      <div class="skill-card fade-in fade-in-delay-1">
        <div class="skill-icon">📋</div>
        <div>
          <div class="skill-name">專案管理</div>
          <div class="skill-desc">時程規劃、需求追蹤、跨團隊協作</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-2">
        <div class="skill-icon">🗺️</div>
        <div>
          <div class="skill-name">網站架構規劃</div>
          <div class="skill-desc">資訊架構、Sitemap、內容分層設計</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-3">
        <div class="skill-icon">👤</div>
        <div>
          <div class="skill-name">使用者流程規劃</div>
          <div class="skill-desc">User Flow、動線設計、轉換路徑優化</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-1">
        <div class="skill-icon">✍️</div>
        <div>
          <div class="skill-name">文案溝通優化</div>
          <div class="skill-desc">品牌文案確認、SEO 文字優化建議</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-3">
        <div class="skill-icon">🔍</div>
        <div>
          <div class="skill-name">SEO 基本概念</div>
          <div class="skill-desc">關鍵字規劃、Meta 設定、內容結構建議</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-1">
        <div class="skill-icon">💻</div>
        <div>
          <div class="skill-name">HTML 基礎調整</div>
          <div class="skill-desc">基本語法閱讀、前端溝通橋接</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-2">
        <div class="skill-icon">🤝</div>
        <div>
          <div class="skill-name">跨部門協作</div>
          <div class="skill-desc">設計、工程、客戶三方溝通整合</div>
        </div>
      </div>
      <div class="skill-card fade-in fade-in-delay-3">
        <div class="skill-icon">🗂️</div>
        <div>
          <div class="skill-name">工具使用</div>
          <div class="skill-desc">Notion、Figma（閱讀）、Google Analytics</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===================== FEATURED PROJECTS ===================== -->
<section id="featured">
  <div class="section-inner">
    <div class="section-label fade-in">Featured Projects</div>
    <h2 class="section-title fade-in">精選專案</h2>
    <div class="featured-grid" id="featuredGrid"></div>
  </div>
</section>

<!-- ===================== OTHER PROJECTS ===================== -->
<section id="other">
  <div class="section-inner">
    <div class="section-label fade-in">Other Projects</div>
    <h2 class="section-title fade-in">更多專案</h2>
    <div class="other-grid" id="otherGrid"></div>
  </div>
</section>

<!-- ===================== FOOTER ===================== -->
<footer>
  <div class="footer-name">Adela<span>.</span></div>
  <div class="footer-copy">© 2025 Adela · Website PM / Website Planner</div>
</footer>

<!-- ===================== MODAL ===================== -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal" id="modal">
    <div class="modal-header">
      <div>
        <div class="modal-cat" id="mCat"></div>
        <div class="modal-title" id="mTitle"></div>
      </div>
      <button class="modal-close" onclick="closeModalDirect()">✕</button>
    </div>
    <div class="modal-body">
      <div class="modal-section">
        <div class="modal-section-title">專案簡介</div>
        <p id="mIntro"></p>
      </div>
      <div class="modal-section">
        <div class="modal-section-title">專案背景</div>
        <p id="mBg"></p>
      </div>
      <div class="modal-section">
        <div class="modal-section-title">專案目標</div>
        <p id="mGoal"></p>
      </div>
      <div class="modal-section">
        <div class="modal-section-title">我的角色</div>
        <p id="mRole"></p>
      </div>
      <div class="modal-section">
        <div class="modal-section-title">工作內容</div>
        <ul id="mWork"></ul>
      </div>
      <div class="modal-section">
        <div class="modal-section-title">使用工具 / 技能</div>
        <div class="modal-tags" id="mTools"></div>
      </div>
      <div class="modal-section">
        <div class="modal-section-title">專案成果與亮點</div>
        <div class="modal-result" id="mResult"></div>
      </div>
      <a class="modal-link-btn" id="mLink" href="#" target="_blank">
        查看網站
        <svg viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 10L10 2M10 2H5M10 2v5"/></svg>
      </a>
    </div>
  </div>
</div>

<script>
/* =====================
   DATA
===================== */
const featured = [
  {
    name: '富海中醫',
    url: 'https://www.fuhaiclinic.com.tw/',
    cat: '醫療診所',
    intro: '中醫診所品牌形象網站，從零建立數位門面，打造專業溫馨的醫療形象。',
    bg: '🌿', thumb: 'th-sage',
    background: '業主為中醫師創業開設診所，缺乏任何數位呈現，需要從零規劃一個完整的形象網站。',
    goal: '建立品牌信任感、清楚呈現診療項目與醫師背景，吸引潛在患者預約就診。',
    role: 'Website PM / Website Planner，全程主導網站架構設計到上線。',
    work: ['釐清診所定位與目標客群','規劃 Sitemap 與頁面架構（首頁、關於、診療項目、醫師介紹、預約）','撰寫並優化各頁文案，確認醫師用語與品牌調性一致','協調設計師與工程師，確保視覺與架構符合需求','上線前品質把關，測試各頁功能與 RWD'],
    tools: ['Notion','Google Analytics','SEO 規劃','文案撰寫','跨部門溝通'],
    result: '網站上線後成功建立診所數位形象，Google 搜尋曝光度提升，診所詢問量明顯增加。網站架構清晰，患者能快速找到所需資訊。'
  },
  {
    name: '台灣勞基顧問(股)公司',
    url: 'https://lawki.com.tw/',
    cat: '企業品牌',
    intro: '勞資法律顧問公司官網，強化專業可信賴形象，完整展示服務項目架構。',
    bg: '⚖️', thumb: 'th-lavender',
    background: '勞資法律顧問公司希望重新建立官方網站，讓企業主快速了解服務內容並主動聯繫。',
    goal: '建立專業可信賴的品牌形象，清楚呈現服務項目，促進企業客戶詢問轉換。',
    role: 'Website PM / Website Planner，負責整體架構規劃與文案方向確認。',
    work: ['了解服務項目與目標客群（企業主、HR）','規劃服務頁面分類架構（勞資爭議、教育訓練、顧問方案）','協助文案方向，使法律術語更易讀易懂','確認 CTA 按鈕動線設計，引導訪客主動詢問','SEO 基本關鍵字建議（勞基法顧問、勞資爭議處理）'],
    tools: ['Notion','SEO 規劃','文案優化','Google Analytics','跨部門溝通'],
    result: '網站架構清晰，訪客能快速理解服務範圍。專業感提升明顯，官網成為重要業務詢問管道之一。'
  },
  {
    name: '萬華醫院精準醫療中心',
    url: 'https://www.pmc.taipei/',
    cat: '醫療機構',
    intro: '醫院精準醫療中心專屬網站，規劃複雜醫療資訊架構，兼顧專業度與易讀性。',
    bg: '🏥', thumb: 'th-sky',
    background: '醫院新設精準醫療中心，需要獨立官網完整介紹精準醫療概念、醫師團隊及檢測項目。',
    goal: '讓民眾了解精準醫療概念，建立專業醫療形象，促進民眾預約精準健康檢查。',
    role: 'Website PM / Website Planner，主導資訊架構設計與文案確認流程。',
    work: ['深入了解精準醫療專業內容，整理可對外溝通的語言','規劃複雜頁面架構（概念說明、團隊、流程）','多次文案確認會議，確保醫療正確性與易讀性兼顧','協調醫院行政、醫師、設計師三方意見','上線前進行多裝置測試與內容校稿'],
    tools: ['Notion','文案撰寫','跨部門溝通','SEO','GA4'],
    result: '成功將複雜的精準醫療資訊整理為清晰可讀的網頁架構，網站上線後成為院方重要的對外宣傳窗口。'
  },
  {
    name: '中信勝牙醫診所',
    url: 'https://winningsmile.com.tw/',
    cat: '醫療診所',
    intro: '牙醫診所品牌網站，規劃療程項目清楚分類，提升患者信任感與預約意願。',
    bg: '🦷', thumb: 'th-blush',
    background: '診所希望建立專業形象網站，清楚呈現各項牙科療程，吸引更多新患者預約。',
    goal: '提升品牌可信度，讓潛在患者快速了解療程內容，並主動預約諮詢。',
    role: 'Website PM / Website Planner，全程負責架構規劃到上線品管。',
    work: ['了解診所定位與主力療程（植牙、矯正、美白）','規劃療程分類架構，設計清晰的資訊層級','協助文案優化，讓醫療術語更平易近人','設計預約諮詢 CTA 動線','確認品牌色調與視覺風格方向'],
    tools: ['Notion','文案優化','SEO 關鍵字','跨部門溝通','GA4'],
    result: '網站療程分類清晰，患者反映容易找到所需資訊。上線後自然搜尋流量穩定成長，預約詢問率提升。'
  },
  {
    name: '捷伊沙龍',
    url: 'https://www.faithsalon.com.tw/',
    cat: '美容美髮',
    intro: '美髮沙龍品牌網站，完整規劃設計師介紹、服務項目與線上預約動線。',
    bg: '💇', thumb: 'th-rose',
    background: '美髮沙龍希望建立官方網站，讓顧客可以線上了解設計師風格並預約。',
    goal: '打造品牌質感形象，讓顧客透過網站信任沙龍，提升預約轉換率。',
    role: 'Website PM / Website Planner，負責需求規劃到文案確認。',
    work: ['訪談業主了解沙龍定位、客群與設計師特色','規劃設計師個人頁面架構（照片、擅長、風格）','服務項目與價格頁面架構設計','協助文案，讓品牌調性與目標客群契合','整合 LINE 預約動線設計'],
    tools: ['Notion','文案撰寫','用戶動線規劃','SEO','跨部門溝通'],
    result: '網站上線後成為沙龍主要詢問管道，設計師個人頁面受顧客好評，預約量穩定提升。'
  },
  {
    name: '家樂健康學院',
    url: 'https://calebwellness.com.tw/',
    cat: '健康教育',
    intro: '健康教育平台網站，規劃課程架構與師資介紹，打造專業學習品牌形象。',
    bg: '💚', thumb: 'th-mint',
    background: '健康課程品牌希望建立線上平台，完整展示課程內容與師資陣容，吸引學員報名。',
    goal: '建立可信賴的健康學習品牌形象，促進課程報名轉換。',
    role: 'Website PM / Website Planner，主導整體規劃與文案確認。',
    work: ['課程分類架構規劃（實體課、企業課）','師資介紹頁面設計規劃','報名流程與 CTA 動線設計','文案確認，讓健康專業知識易於理解','SEO 基本關鍵字方向建議'],
    tools: ['Notion','文案撰寫','SEO','用戶動線規劃','GA4'],
    result: '網站課程架構清晰，學員反映好找、易懂。品牌形象專業提升，成為業主對外招募學員的核心工具。'
  },
  {
    name: '昱見佇所室內裝修',
    url: 'https://www.seeucorner.com/',
    cat: '設計裝修',
    intro: '室內設計公司作品集網站，規劃案例展示架構，打造高質感品牌形象。',
    bg: '🏠', thumb: 'th-warm',
    background: '室內裝修設計公司希望透過官網展示作品，吸引更多高品質客戶詢問合作。',
    goal: '展現設計品味與施工能力，建立品牌質感，吸引目標客群主動詢問。',
    role: 'Website PM / Website Planner，規劃作品集架構與文案呈現方式。',
    work: ['了解設計師風格定位與目標客群','規劃作品集頁面架構（依空間類型分類）','文案協助，讓每個案例有故事感','設計詢問 CTA 動線','確認整體品牌視覺調性方向'],
    tools: ['Notion','文案撰寫','用戶動線規劃','跨部門溝通','SEO'],
    result: '作品集呈現有質感，訪客停留時間提升。品牌形象成功升級，詢問案量品質明顯改善。'
  },
  {
    name: 'W. 手工紋繡藝術學苑',
    url: 'https://ww58888.com.tw/',
    cat: '美容教學',
    intro: '紋繡藝術學苑網站，完整規劃課程介紹、師資背景與招生報名架構。',
    bg: '🖊️', thumb: 'th-peach',
    background: '資深紋繡老師希望成立教學學苑，需要官網完整展示課程與招生資訊。',
    goal: '建立學苑專業品牌，讓有興趣學習紋繡的學員了解課程內容並主動報名。',
    role: 'Website PM / Website Planner，負責完整規劃與文案確認。',
    work: ['課程架構規劃（初階、進階、認證班）','師資介紹頁面設計規劃','報名流程與常見問題頁面架構','文案優化，強調師資資歷與教學特色','SEO 關鍵字方向（台灣紋繡課程、學紋繡）'],
    tools: ['Notion','文案撰寫','SEO','用戶動線規劃','跨部門溝通'],
    result: '學苑官網上線後成功打開知名度，招生班次穩定開課，學員透過網站直接詢問比例大幅提升。'
  }
];

const others = [
  { name: '和信當鋪', url: 'https://www.hxmoneyhelp.com.tw/', emoji: '🏦' },
  { name: 'Vescor 偉詩蔻', url: 'https://vescorsoft.com.tw/', emoji: '✨' },
  { name: '潔樂家電清洗', url: 'https://www.jerekaden.com.tw/', emoji: '🧹' },
  { name: '和信診所（骨科）', url: 'https://hexinhealth.com.tw/', emoji: '🦴' },
  { name: '視紀音響', url: 'https://www.sgec-music.com.tw/', emoji: '🎵' },
  { name: 'CH 精緻洗鞋', url: 'https://chcleaning.com.tw/', emoji: '👟' },
  { name: '翔藝舞蹈工作室', url: 'https://flyartdance.com.tw/', emoji: '💃' },
  { name: '阿周鎖店', url: 'https://www.azhou.com.tw/', emoji: '🔑' },
  { name: '立宇當鋪', url: 'https://www.lypawnshop.com.tw/', emoji: '💰' },
  { name: '忻玉閣', url: 'https://xinyuge.com.tw/', emoji: '💎' },
  { name: '應像影視', url: 'https://impressiongolf.com.tw/', emoji: '🎬' },
  { name: '大林小草國際', url: 'https://www.luckygrassoutdoor.com.tw/', emoji: '🌿' },
  { name: '達康眼鏡行', url: 'https://www.dacomglasses.com.tw/', emoji: '👓' },
  { name: '喜來得喵屋', url: 'https://www.gycatshop.com.tw/', emoji: '🐱' },
  { name: '揪揪玩工作室', url: 'https://joinplay.com.tw/', emoji: '🎨' },
  { name: '天造工程行', url: 'https://www.tzwaterproof.com.tw/', emoji: '🏗️' },
  { name: '玥夏診所', url: 'https://www.purrfectclinic.com.tw/', emoji: '🌸' },
];

/* =====================
   RENDER
===================== */
function arrowSVG() {
  return `<svg viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 10L10 2M10 2H5M10 2v5"/></svg>`;
}

// Featured cards
const fg = document.getElementById('featuredGrid');
featured.forEach((p, i) => {
  const div = document.createElement('div');
  div.className = `featured-card fade-in fade-in-delay-${(i % 3) + 1}`;
  div.innerHTML = `
    <div class="featured-card-thumb ${p.thumb}">${p.bg}</div>
    <div class="featured-card-body">
      <div class="featured-card-cat">${p.cat}</div>
      <div class="featured-card-name">${p.name}</div>
      <div class="featured-card-intro">${p.intro}</div>
      <div class="featured-card-tags">${p.tools.slice(0,3).map(t=>`<span class="tag">${t}</span>`).join('')}</div>
      <div class="featured-card-footer">
        <a class="featured-card-link" href="${p.url}" target="_blank" onclick="event.stopPropagation()">
          查看網站 ${arrowSVG()}
        </a>
        <span class="featured-card-role">Website PM</span>
      </div>
    </div>`;
  div.onclick = () => openModal(i);
  fg.appendChild(div);
});

// Other cards
const og = document.getElementById('otherGrid');
others.forEach((p, i) => {
  const div = document.createElement('div');
  div.className = `other-card fade-in fade-in-delay-${(i % 3) + 1}`;
  div.innerHTML = `
    <div class="other-card-emoji">${p.emoji}</div>
    <div>
      <div class="other-card-name">${p.name}</div>
      <a class="other-card-link" href="${p.url}" target="_blank">查看網站 ${arrowSVG()}</a>
    </div>`;
  og.appendChild(div);
});

/* =====================
   MODAL
===================== */
function openModal(i) {
  const p = featured[i];
  document.getElementById('mCat').textContent = p.cat;
  document.getElementById('mTitle').textContent = p.name;
  document.getElementById('mIntro').textContent = p.intro;
  document.getElementById('mBg').textContent = p.background;
  document.getElementById('mGoal').textContent = p.goal;
  document.getElementById('mRole').textContent = p.role;
  document.getElementById('mWork').innerHTML = p.work.map(w => `<li>${w}</li>`).join('');
  document.getElementById('mTools').innerHTML = p.tools.map(t => `<span class="tag">${t}</span>`).join('');
  document.getElementById('mResult').textContent = p.result;
  document.getElementById('mLink').href = p.url;
  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closeModal(e) {
  if (e.target === document.getElementById('modalOverlay')) closeModalDirect();
}
function closeModalDirect() {
  document.getElementById('modalOverlay').classList.remove('open');
  document.body.style.overflow = '';
}
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModalDirect(); });

/* =====================
   SCROLL ANIMATION
===================== */
const observer = new IntersectionObserver(entries => {
  entries.forEach(el => {
    if (el.isIntersecting) {
      el.target.classList.add('visible');
      observer.unobserve(el.target);
    }
  });
}, { threshold: 0.12 });

function observeAll() {
  document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
}
observeAll();
// Re-observe after cards render
setTimeout(observeAll, 100);

/* =====================
   NAV HAMBURGER
===================== */
function toggleMenu() {
  document.getElementById('navLinks').classList.toggle('open');
}
document.querySelectorAll('.nav-links a').forEach(a => {
  a.addEventListener('click', () => {
    document.getElementById('navLinks').classList.remove('open');
  });
});
</script>
</body>
</html>
