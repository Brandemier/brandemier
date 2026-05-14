<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Brandemier — Building Brands People Remember</title>
<meta name="description" content="Brandemier is a premium creative branding agency focused on building modern and memorable brands. Brand identity, logo design, packaging, and more.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --blue-50: #f0f7ff;
    --blue-100: #e0efff;
    --blue-200: #bbd9ff;
    --blue-300: #8abeff;
    --blue-400: #5599f8;
    --blue-500: #3b7df0;
    --blue-600: #2b63d9;
    --white: #ffffff;
    --gray-50: #f8fafc;
    --gray-100: #f1f5f9;
    --gray-200: #e2e8f0;
    --gray-400: #94a3b8;
    --gray-600: #475569;
    --gray-800: #1e293b;
    --gray-900: #0f172a;
    --font-display: 'Syne', sans-serif;
    --font-body: 'Outfit', sans-serif;
    --radius-sm: 8px;
    --radius-md: 16px;
    --radius-lg: 24px;
    --radius-xl: 32px;
    --shadow-sm: 0 1px 3px rgba(15,23,42,0.06), 0 1px 2px rgba(15,23,42,0.04);
    --shadow-md: 0 4px 16px rgba(15,23,42,0.08), 0 2px 6px rgba(15,23,42,0.04);
    --shadow-lg: 0 12px 40px rgba(15,23,42,0.1), 0 4px 12px rgba(15,23,42,0.06);
    --shadow-blue: 0 8px 32px rgba(59,125,240,0.18);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; font-size: 16px; }

  body {
    font-family: var(--font-body);
    color: var(--gray-800);
    background: var(--white);
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ── LOADER ── */
  #loader {
    position: fixed; inset: 0; z-index: 9999;
    background: var(--white);
    display: flex; align-items: center; justify-content: center;
    transition: opacity 0.5s ease, visibility 0.5s ease;
  }
  #loader.hidden { opacity: 0; visibility: hidden; }
  .loader-inner {
    display: flex; flex-direction: column; align-items: center; gap: 20px;
  }
  .loader-logo {
    font-family: var(--font-display);
    font-size: 1.6rem;
    font-weight: 800;
    color: var(--gray-900);
    letter-spacing: -0.02em;
  }
  .loader-logo span { color: var(--blue-500); }
  .loader-bar {
    width: 160px; height: 3px;
    background: var(--blue-100);
    border-radius: 99px;
    overflow: hidden;
  }
  .loader-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--blue-400), var(--blue-500));
    border-radius: 99px;
    animation: loaderFill 1.2s ease forwards;
  }
  @keyframes loaderFill { from { width: 0 } to { width: 100% } }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
    padding: 0 5%;
    height: 72px;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(255,255,255,0.85);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border-bottom: 1px solid transparent;
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  nav.scrolled {
    border-color: var(--blue-100);
    box-shadow: 0 2px 20px rgba(59,125,240,0.07);
  }
  .nav-logo {
    font-family: var(--font-display);
    font-size: 1.25rem;
    font-weight: 800;
    color: var(--gray-900);
    letter-spacing: -0.02em;
    text-decoration: none;
  }
  .nav-logo span { color: var(--blue-500); }
  .nav-links {
    display: flex; align-items: center; gap: 36px;
    list-style: none;
  }
  .nav-links a {
    font-size: 0.9rem;
    font-weight: 500;
    color: var(--gray-600);
    text-decoration: none;
    transition: color 0.2s;
    letter-spacing: 0.01em;
  }
  .nav-links a:hover { color: var(--blue-500); }
  .nav-cta {
    background: var(--gray-900);
    color: var(--white) !important;
    padding: 10px 22px;
    border-radius: 99px;
    font-weight: 600 !important;
    transition: background 0.2s, transform 0.2s !important;
  }
  .nav-cta:hover { background: var(--blue-500) !important; color: var(--white) !important; transform: translateY(-1px); }
  .hamburger {
    display: none; flex-direction: column; gap: 5px; cursor: pointer;
    background: none; border: none; padding: 4px;
  }
  .hamburger span {
    display: block; width: 24px; height: 2px;
    background: var(--gray-800); border-radius: 2px;
    transition: all 0.3s;
  }
  .mobile-menu {
    display: none; position: fixed; inset: 0; z-index: 999;
    background: var(--white);
    flex-direction: column; align-items: center; justify-content: center; gap: 32px;
    opacity: 0; transition: opacity 0.3s;
  }
  .mobile-menu.open { opacity: 1; }
  .mobile-menu a {
    font-family: var(--font-display);
    font-size: 1.8rem; font-weight: 700;
    color: var(--gray-900); text-decoration: none;
    transition: color 0.2s;
  }
  .mobile-menu a:hover { color: var(--blue-500); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    padding: 72px 5% 0;
    display: flex; align-items: center;
    position: relative; overflow: hidden;
    background: linear-gradient(160deg, #f0f7ff 0%, #ffffff 50%, #e8f3ff 100%);
  }
  .hero-bg {
    position: absolute; inset: 0; pointer-events: none; overflow: hidden;
  }
  .hero-shape {
    position: absolute;
    border-radius: 50%;
    filter: blur(60px);
    opacity: 0.45;
    animation: floatShape 8s ease-in-out infinite;
  }
  .hero-shape-1 {
    width: 480px; height: 480px;
    background: radial-gradient(circle, #bbd9ff, #8abeff);
    top: -120px; right: -80px;
    animation-duration: 9s;
  }
  .hero-shape-2 {
    width: 280px; height: 280px;
    background: radial-gradient(circle, #dbeeff, #b3d4ff);
    bottom: 80px; left: -60px;
    animation-duration: 11s; animation-delay: -3s;
  }
  .hero-shape-3 {
    width: 180px; height: 180px;
    background: radial-gradient(circle, #c5e2ff, #8abeff);
    top: 40%; right: 20%;
    animation-duration: 7s; animation-delay: -5s;
  }
  .hero-dots {
    position: absolute; inset: 0;
    background-image: radial-gradient(circle, var(--blue-200) 1px, transparent 1px);
    background-size: 36px 36px;
    opacity: 0.35;
  }
  @keyframes floatShape {
    0%, 100% { transform: translate(0, 0) scale(1); }
    33% { transform: translate(20px, -20px) scale(1.04); }
    66% { transform: translate(-15px, 15px) scale(0.97); }
  }
  .hero-content {
    position: relative; z-index: 2;
    max-width: 780px;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--blue-50);
    border: 1px solid var(--blue-200);
    border-radius: 99px;
    padding: 6px 16px;
    font-size: 0.8rem; font-weight: 600;
    color: var(--blue-600);
    margin-bottom: 28px;
    letter-spacing: 0.04em; text-transform: uppercase;
  }
  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--blue-500);
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.7); }
  }
  .hero h1 {
    font-family: var(--font-display);
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 800;
    line-height: 1.08;
    letter-spacing: -0.03em;
    color: var(--gray-900);
    margin-bottom: 24px;
  }
  .hero h1 em {
    font-style: normal;
    color: var(--blue-500);
    position: relative;
  }
  .hero h1 em::after {
    content: '';
    position: absolute; bottom: -4px; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--blue-400), var(--blue-200));
    border-radius: 2px;
  }
  .hero p {
    font-size: 1.15rem; font-weight: 400;
    color: var(--gray-600);
    max-width: 560px;
    line-height: 1.75;
    margin-bottom: 40px;
  }
  .hero-btns {
    display: flex; flex-wrap: wrap; gap: 14px; align-items: center;
  }
  .btn-primary {
    background: var(--gray-900);
    color: var(--white);
    padding: 15px 32px;
    border-radius: 99px;
    font-family: var(--font-body);
    font-size: 0.95rem; font-weight: 600;
    text-decoration: none;
    border: none; cursor: pointer;
    transition: background 0.25s, transform 0.25s, box-shadow 0.25s;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-primary:hover {
    background: var(--blue-600);
    transform: translateY(-2px);
    box-shadow: var(--shadow-blue);
  }
  .btn-secondary {
    background: transparent;
    color: var(--gray-800);
    padding: 14px 30px;
    border-radius: 99px;
    font-family: var(--font-body);
    font-size: 0.95rem; font-weight: 600;
    text-decoration: none;
    border: 1.5px solid var(--gray-200);
    cursor: pointer;
    transition: border-color 0.25s, color 0.25s, transform 0.25s;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-secondary:hover {
    border-color: var(--blue-400);
    color: var(--blue-600);
    transform: translateY(-2px);
  }
  .hero-stats {
    display: flex; gap: 40px; margin-top: 60px;
    padding-top: 40px;
    border-top: 1px solid var(--blue-100);
  }
  .hero-stat h3 {
    font-family: var(--font-display);
    font-size: 2rem; font-weight: 800;
    color: var(--gray-900);
    letter-spacing: -0.03em;
  }
  .hero-stat p {
    font-size: 0.82rem; font-weight: 500;
    color: var(--gray-400);
    margin-bottom: 0; line-height: 1.4;
    letter-spacing: 0.02em; text-transform: uppercase;
  }

  /* ── SECTIONS COMMON ── */
  section { padding: 100px 5%; }
  .section-label {
    display: inline-flex; align-items: center; gap: 8px;
    font-size: 0.75rem; font-weight: 700;
    letter-spacing: 0.1em; text-transform: uppercase;
    color: var(--blue-500);
    margin-bottom: 16px;
  }
  .section-label::before {
    content: '';
    display: block;
    width: 20px; height: 2px;
    background: var(--blue-400);
    border-radius: 1px;
  }
  .section-title {
    font-family: var(--font-display);
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    font-weight: 800;
    letter-spacing: -0.025em;
    line-height: 1.15;
    color: var(--gray-900);
    margin-bottom: 16px;
  }
  .section-sub {
    font-size: 1rem; color: var(--gray-600);
    max-width: 520px; line-height: 1.75;
    margin-bottom: 60px;
  }

  /* ── ABOUT ── */
  .about {
    background: var(--gray-900);
    position: relative; overflow: hidden;
  }
  .about-bg {
    position: absolute; inset: 0; pointer-events: none;
    background: radial-gradient(ellipse 60% 60% at 80% 50%, rgba(59,125,240,0.12) 0%, transparent 70%);
  }
  .about-inner {
    position: relative; z-index: 2;
    display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center;
  }
  .about .section-label { color: var(--blue-300); }
  .about .section-label::before { background: var(--blue-300); }
  .about .section-title { color: var(--white); }
  .about-text {
    font-size: 1.05rem; color: rgba(255,255,255,0.65);
    line-height: 1.8;
  }
  .about-right {
    display: grid; grid-template-columns: 1fr 1fr; gap: 16px;
  }
  .about-card {
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: var(--radius-md);
    padding: 28px 24px;
    transition: background 0.3s, border-color 0.3s;
  }
  .about-card:hover {
    background: rgba(59,125,240,0.12);
    border-color: rgba(59,125,240,0.3);
  }
  .about-card-num {
    font-family: var(--font-display);
    font-size: 2.2rem; font-weight: 800;
    color: var(--blue-400);
    letter-spacing: -0.04em;
    line-height: 1;
    margin-bottom: 8px;
  }
  .about-card-label {
    font-size: 0.85rem; font-weight: 500;
    color: rgba(255,255,255,0.5);
    line-height: 1.4;
  }

  /* ── SERVICES ── */
  .services { background: var(--white); }
  .services-header {
    display: flex; justify-content: space-between; align-items: flex-end;
    margin-bottom: 56px; flex-wrap: wrap; gap: 24px;
  }
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 20px;
  }
  .service-card {
    background: var(--gray-50);
    border: 1px solid var(--gray-200);
    border-radius: var(--radius-lg);
    padding: 36px 32px;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s, background 0.3s;
    cursor: default;
    position: relative; overflow: hidden;
  }
  .service-card::after {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(59,125,240,0.06), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .service-card:hover {
    transform: translateY(-6px);
    border-color: var(--blue-200);
    box-shadow: var(--shadow-lg), var(--shadow-blue);
    background: var(--white);
  }
  .service-card:hover::after { opacity: 1; }
  .service-icon {
    width: 52px; height: 52px;
    background: var(--blue-50);
    border-radius: var(--radius-sm);
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 22px;
    font-size: 1.5rem;
    transition: background 0.3s, transform 0.3s;
  }
  .service-card:hover .service-icon {
    background: var(--blue-100);
    transform: scale(1.1);
  }
  .service-card h3 {
    font-family: var(--font-display);
    font-size: 1.05rem; font-weight: 700;
    color: var(--gray-900); margin-bottom: 10px;
    letter-spacing: -0.01em;
  }
  .service-card p {
    font-size: 0.875rem; color: var(--gray-400);
    line-height: 1.65;
  }

  /* ── WHY US ── */
  .why { background: var(--blue-50); }
  .why-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 24px;
  }
  .why-card {
    background: var(--white);
    border-radius: var(--radius-lg);
    padding: 40px 32px;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--blue-100);
    transition: transform 0.3s, box-shadow 0.3s;
    text-align: center;
  }
  .why-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-lg);
  }
  .why-icon {
    width: 64px; height: 64px;
    background: var(--blue-50);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.8rem;
    margin: 0 auto 20px;
    border: 1px solid var(--blue-100);
  }
  .why-card h3 {
    font-family: var(--font-display);
    font-size: 1.05rem; font-weight: 700;
    color: var(--gray-900); margin-bottom: 10px;
    letter-spacing: -0.01em;
  }
  .why-card p {
    font-size: 0.875rem; color: var(--gray-400);
    line-height: 1.65;
  }

  /* ── PORTFOLIO ── */
  .portfolio { background: var(--white); }
  .portfolio-header {
    display: flex; justify-content: space-between; align-items: flex-end;
    margin-bottom: 48px; flex-wrap: wrap; gap: 24px;
  }
  .portfolio-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto auto;
    gap: 20px;
  }
  .portfolio-item {
    border-radius: var(--radius-lg);
    overflow: hidden;
    position: relative;
    cursor: pointer;
    aspect-ratio: 4/3;
  }
  .portfolio-item:first-child {
    grid-column: 1 / 2; grid-row: 1 / 3;
    aspect-ratio: unset;
  }
  .portfolio-item-bg {
    width: 100%; height: 100%;
    transition: transform 0.5s ease;
  }
  .portfolio-item:hover .portfolio-item-bg { transform: scale(1.05); }
  .portfolio-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to top, rgba(15,23,42,0.75) 0%, transparent 60%);
    opacity: 0; transition: opacity 0.3s;
    display: flex; align-items: flex-end; padding: 24px;
  }
  .portfolio-item:hover .portfolio-overlay { opacity: 1; }
  .portfolio-overlay-text h4 {
    font-family: var(--font-display);
    font-size: 1rem; font-weight: 700; color: var(--white);
    letter-spacing: -0.01em;
  }
  .portfolio-overlay-text p {
    font-size: 0.8rem; color: rgba(255,255,255,0.6);
  }
  /* Portfolio item designs */
  .pi-1 { background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%); }
  .pi-1-inner {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
    flex-direction: column; gap: 16px;
  }
  .pi-1-logo {
    font-family: var(--font-display);
    font-size: 2.2rem; font-weight: 800;
    color: var(--white); letter-spacing: -0.04em;
  }
  .pi-1-tagline {
    font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
    color: rgba(255,255,255,0.4);
  }
  .pi-1-bar {
    width: 60px; height: 2px;
    background: var(--blue-400);
    border-radius: 1px;
  }

  .pi-2 { background: linear-gradient(135deg, #f8f4f0 0%, #ede8e1 100%); }
  .pi-2-inner {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
  }
  .pi-2-circle {
    width: 80px; height: 80px;
    border-radius: 50%;
    background: linear-gradient(135deg, #c8a97e, #a07850);
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-display);
    font-size: 1.4rem; font-weight: 800; color: white;
  }

  .pi-3 { background: linear-gradient(135deg, #0d1b2a 0%, #1b263b 100%); }
  .pi-3-inner {
    width: 100%; height: 100%;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center; gap: 12px;
  }
  .pi-3-lines { display: flex; flex-direction: column; gap: 6px; align-items: center; }
  .pi-3-line {
    height: 2px; background: var(--blue-400);
    border-radius: 1px;
  }

  .pi-4 { background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%); }
  .pi-4-inner {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
    flex-direction: column; gap: 10px;
  }
  .pi-4-box {
    width: 60px; height: 60px;
    border-radius: 12px;
    background: #92400e;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-display);
    font-weight: 800; font-size: 1.2rem; color: #fef3c7;
  }
  .pi-4-text {
    font-family: var(--font-display);
    font-size: 0.7rem; font-weight: 700;
    letter-spacing: 0.15em; text-transform: uppercase;
    color: #92400e;
  }

  .pi-5 { background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%); }
  .pi-5-inner {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
  }
  .pi-5-leaf {
    font-size: 3rem;
  }

  .portfolio-cta { text-align: center; margin-top: 48px; }

  /* ── TESTIMONIALS ── */
  .testimonials { background: var(--gray-50); }
  .testimonials-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 24px;
  }
  .testimonial-card {
    background: var(--white);
    border: 1px solid var(--gray-200);
    border-radius: var(--radius-lg);
    padding: 36px 32px;
    box-shadow: var(--shadow-sm);
    transition: transform 0.3s, box-shadow 0.3s;
  }
  .testimonial-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-md);
  }
  .testimonial-stars {
    display: flex; gap: 4px; margin-bottom: 18px;
    color: #f59e0b;
    font-size: 0.9rem;
  }
  .testimonial-card blockquote {
    font-size: 0.95rem; color: var(--gray-600);
    line-height: 1.75; font-style: italic;
    margin-bottom: 24px;
    border: none; padding: 0;
  }
  .testimonial-author {
    display: flex; align-items: center; gap: 14px;
  }
  .testimonial-avatar {
    width: 44px; height: 44px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-display);
    font-size: 1rem; font-weight: 700;
    color: var(--white);
    flex-shrink: 0;
  }
  .testimonial-author-info h4 {
    font-family: var(--font-display);
    font-size: 0.9rem; font-weight: 700;
    color: var(--gray-900);
  }
  .testimonial-author-info p {
    font-size: 0.78rem; color: var(--gray-400);
  }

  /* ── CONTACT ── */
  .contact { background: var(--gray-900); position: relative; overflow: hidden; }
  .contact-bg {
    position: absolute; inset: 0; pointer-events: none;
    background: radial-gradient(ellipse 50% 80% at 10% 50%, rgba(59,125,240,0.1) 0%, transparent 70%);
  }
  .contact-inner {
    position: relative; z-index: 2;
    display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center;
  }
  .contact .section-label { color: var(--blue-300); }
  .contact .section-label::before { background: var(--blue-300); }
  .contact .section-title { color: var(--white); }
  .contact-sub {
    font-size: 1rem; color: rgba(255,255,255,0.55);
    line-height: 1.75; margin-bottom: 40px;
  }
  .contact-links {
    display: flex; flex-direction: column; gap: 16px;
  }
  .contact-link {
    display: flex; align-items: center; gap: 16px;
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: var(--radius-md);
    padding: 18px 22px;
    text-decoration: none; color: var(--white);
    transition: background 0.3s, border-color 0.3s, transform 0.3s;
  }
  .contact-link:hover {
    background: rgba(59,125,240,0.15);
    border-color: rgba(59,125,240,0.35);
    transform: translateX(4px);
  }
  .contact-link-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.2rem; flex-shrink: 0;
  }
  .contact-link-text strong {
    display: block;
    font-family: var(--font-display);
    font-size: 0.9rem; font-weight: 700;
    margin-bottom: 2px;
  }
  .contact-link-text span {
    font-size: 0.82rem; color: rgba(255,255,255,0.45);
  }
  .contact-right {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: var(--radius-xl);
    padding: 48px 40px;
  }
  .contact-right h3 {
    font-family: var(--font-display);
    font-size: 1.3rem; font-weight: 700; color: var(--white);
    margin-bottom: 8px;
  }
  .contact-right p { color: rgba(255,255,255,0.45); font-size: 0.875rem; margin-bottom: 28px; }
  .form-group { margin-bottom: 18px; }
  .form-group label {
    display: block; font-size: 0.8rem; font-weight: 600;
    color: rgba(255,255,255,0.5); margin-bottom: 8px;
    letter-spacing: 0.04em; text-transform: uppercase;
  }
  .form-group input,
  .form-group textarea {
    width: 100%;
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: var(--radius-sm);
    padding: 14px 16px;
    font-family: var(--font-body);
    font-size: 0.9rem; color: var(--white);
    outline: none;
    transition: border-color 0.2s, background 0.2s;
  }
  .form-group input::placeholder,
  .form-group textarea::placeholder { color: rgba(255,255,255,0.25); }
  .form-group input:focus,
  .form-group textarea:focus {
    border-color: var(--blue-400);
    background: rgba(59,125,240,0.08);
  }
  .form-group textarea { height: 110px; resize: none; }
  .btn-submit {
    width: 100%;
    background: var(--blue-500);
    color: var(--white);
    border: none; cursor: pointer;
    font-family: var(--font-body);
    font-size: 0.95rem; font-weight: 600;
    padding: 16px;
    border-radius: var(--radius-md);
    transition: background 0.2s, transform 0.2s;
    margin-top: 8px;
  }
  .btn-submit:hover {
    background: var(--blue-600);
    transform: translateY(-2px);
  }

  /* ── FOOTER ── */
  footer {
    background: #080d14;
    padding: 60px 5% 40px;
    border-top: 1px solid rgba(255,255,255,0.06);
  }
  .footer-inner {
    display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 60px;
    margin-bottom: 48px;
  }
  .footer-brand p {
    font-size: 0.875rem; color: rgba(255,255,255,0.35);
    line-height: 1.75; margin-top: 14px; max-width: 260px;
  }
  .footer-col h4 {
    font-family: var(--font-display);
    font-size: 0.8rem; font-weight: 700;
    color: rgba(255,255,255,0.5);
    letter-spacing: 0.1em; text-transform: uppercase;
    margin-bottom: 18px;
  }
  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .footer-col ul a {
    font-size: 0.875rem; color: rgba(255,255,255,0.4);
    text-decoration: none;
    transition: color 0.2s;
  }
  .footer-col ul a:hover { color: var(--blue-400); }
  .footer-socials { display: flex; gap: 10px; margin-top: 4px; }
  .footer-social {
    width: 36px; height: 36px;
    border-radius: var(--radius-sm);
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.08);
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem; text-decoration: none;
    transition: background 0.2s, border-color 0.2s;
  }
  .footer-social:hover {
    background: rgba(59,125,240,0.2);
    border-color: rgba(59,125,240,0.4);
  }
  .footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.06);
    padding-top: 28px;
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 12px;
  }
  .footer-bottom p {
    font-size: 0.8rem; color: rgba(255,255,255,0.25);
  }
  .footer-logo {
    font-family: var(--font-display);
    font-size: 1.1rem; font-weight: 800;
    color: var(--white); letter-spacing: -0.02em;
    text-decoration: none;
  }
  .footer-logo span { color: var(--blue-400); }

  /* ── WHATSAPP FLOAT ── */
  .wa-float {
    position: fixed; bottom: 28px; right: 28px; z-index: 999;
    width: 58px; height: 58px;
    background: #25D366;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 6px 24px rgba(37,211,102,0.4);
    text-decoration: none;
    transition: transform 0.3s, box-shadow 0.3s;
    animation: waPulseOut 2.5s ease-in-out infinite;
  }
  .wa-float:hover {
    transform: scale(1.1);
    box-shadow: 0 10px 32px rgba(37,211,102,0.55);
    animation: none;
  }
  .wa-float svg { width: 28px; height: 28px; fill: white; }
  @keyframes waPulseOut {
    0%, 100% { box-shadow: 0 6px 24px rgba(37,211,102,0.4), 0 0 0 0 rgba(37,211,102,0.25); }
    50% { box-shadow: 0 6px 24px rgba(37,211,102,0.4), 0 0 0 12px rgba(37,211,102,0); }
  }

  /* ── ANIMATIONS ── */
  .fade-up {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.65s ease, transform 0.65s ease;
  }
  .fade-up.visible { opacity: 1; transform: translateY(0); }
  .fade-up-delay-1 { transition-delay: 0.1s; }
  .fade-up-delay-2 { transition-delay: 0.2s; }
  .fade-up-delay-3 { transition-delay: 0.3s; }
  .fade-up-delay-4 { transition-delay: 0.4s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 1024px) {
    .about-inner { grid-template-columns: 1fr; gap: 48px; }
    .contact-inner { grid-template-columns: 1fr; gap: 48px; }
    .footer-inner { grid-template-columns: 1fr 1fr; gap: 40px; }
    .portfolio-grid { grid-template-columns: 1fr 1fr; }
    .portfolio-item:first-child { grid-column: 1 / 3; grid-row: 1 / 1; aspect-ratio: 16/7; }
  }
  @media (max-width: 768px) {
    section { padding: 72px 5%; }
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .mobile-menu { display: flex; }
    .hero { text-align: center; }
    .hero-btns { justify-content: center; }
    .hero-stats { justify-content: center; flex-wrap: wrap; gap: 28px; }
    .services-header { flex-direction: column; align-items: flex-start; }
    .portfolio-header { flex-direction: column; align-items: flex-start; }
    .portfolio-grid { grid-template-columns: 1fr; }
    .portfolio-item:first-child { grid-column: 1; grid-row: 1; aspect-ratio: 4/3; }
    .footer-inner { grid-template-columns: 1fr; gap: 32px; }
    .footer-bottom { flex-direction: column; text-align: center; }
    .about-right { grid-template-columns: 1fr 1fr; }
    .hero-content { max-width: 100%; }
    .hero p { margin: 0 auto 40px; }
    .section-sub { margin-bottom: 40px; }
  }
  @media (max-width: 480px) {
    .why-grid { grid-template-columns: 1fr; }
    .about-right { grid-template-columns: 1fr; }
    .testimonials-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- LOADER -->
<div id="loader">
  <div class="loader-inner">
    <div class="loader-logo">Brand<span>emier</span></div>
    <div class="loader-bar"><div class="loader-bar-fill"></div></div>
  </div>
</div>

<!-- NAV -->
<nav id="navbar">
  <a href="#" class="nav-logo">Brand<span>emier</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#portfolio">Portfolio</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#contact" class="nav-cta">Get Started</a></li>
  </ul>
  <button class="hamburger" id="hamburger" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mobileMenu">
  <a href="#about" class="mobile-link">About</a>
  <a href="#services" class="mobile-link">Services</a>
  <a href="#portfolio" class="mobile-link">Portfolio</a>
  <a href="#testimonials" class="mobile-link">Reviews</a>
  <a href="#contact" class="mobile-link">Contact</a>
</div>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-bg">
    <div class="hero-dots"></div>
    <div class="hero-shape hero-shape-1"></div>
    <div class="hero-shape hero-shape-2"></div>
    <div class="hero-shape hero-shape-3"></div>
  </div>
  <div class="hero-content">
    <div class="hero-badge fade-up">Premium Branding Studio</div>
    <h1 class="fade-up fade-up-delay-1">Building Brands<br><em>People Remember.</em></h1>
    <p class="fade-up fade-up-delay-2">Brandemier helps businesses create premium brand identities, visuals, and digital experiences that connect, attract, and convert.</p>
    <div class="hero-btns fade-up fade-up-delay-3">
      <a href="#contact" class="btn-primary">Work With Us <span>→</span></a>
      <a href="#portfolio" class="btn-secondary">View Portfolio <span>↗</span></a>
    </div>
    <div class="hero-stats fade-up fade-up-delay-4">
      <div class="hero-stat">
        <h3>80+</h3>
        <p>Projects<br>Delivered</p>
      </div>
      <div class="hero-stat">
        <h3>50+</h3>
        <p>Happy<br>Clients</p>
      </div>
      <div class="hero-stat">
        <h3>3+</h3>
        <p>Years<br>Experience</p>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="about">
  <div class="about-bg"></div>
  <div class="about-inner">
    <div>
      <div class="section-label fade-up">Who We Are</div>
      <h2 class="section-title fade-up fade-up-delay-1">Where Strategy<br>Meets Creativity</h2>
      <p class="about-text fade-up fade-up-delay-2">Brandemier is a creative branding agency focused on building modern and memorable brands. From visual identity design to brand strategy, we help businesses stand out with clarity and confidence.</p>
      <p class="about-text fade-up fade-up-delay-2" style="margin-top:16px;">Every project we take on is an opportunity to craft something that not only looks exceptional but tells a story — your story — in a way that resonates with your audience and sets you apart from the competition.</p>
    </div>
    <div class="about-right">
      <div class="about-card fade-up">
        <div class="about-card-num">80+</div>
        <div class="about-card-label">Projects Completed</div>
      </div>
      <div class="about-card fade-up fade-up-delay-1">
        <div class="about-card-num">50+</div>
        <div class="about-card-label">Happy Clients</div>
      </div>
      <div class="about-card fade-up fade-up-delay-2">
        <div class="about-card-num">3+</div>
        <div class="about-card-label">Years of Expertise</div>
      </div>
      <div class="about-card fade-up fade-up-delay-3">
        <div class="about-card-num">100%</div>
        <div class="about-card-label">Client Satisfaction</div>
      </div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section class="services" id="services">
  <div class="services-header">
    <div>
      <div class="section-label fade-up">What We Offer</div>
      <h2 class="section-title fade-up fade-up-delay-1">Our Creative Services</h2>
    </div>
    <p class="section-sub fade-up fade-up-delay-1" style="margin-bottom:0; max-width:340px;">Every service is crafted with intention — designed to elevate your brand to its fullest potential.</p>
  </div>
  <div class="services-grid">
    <div class="service-card fade-up">
      <div class="service-icon">🎨</div>
      <h3>Brand Identity Design</h3>
      <p>Complete visual systems that define who you are — from color palettes and typography to brand guidelines that keep you consistent.</p>
    </div>
    <div class="service-card fade-up fade-up-delay-1">
      <div class="service-icon">✏️</div>
      <h3>Logo Design</h3>
      <p>Iconic, timeless logos crafted with purpose. We distill your brand's essence into a mark that makes a lasting impression.</p>
    </div>
    <div class="service-card fade-up fade-up-delay-2">
      <div class="service-icon">📦</div>
      <h3>Packaging Design</h3>
      <p>Packaging that sells before a word is spoken. Strategic, beautiful designs that stand out on shelves and screens alike.</p>
    </div>
    <div class="service-card fade-up fade-up-delay-3">
      <div class="service-icon">📱</div>
      <h3>Social Media Branding</h3>
      <p>Cohesive social presence with branded templates, covers, and post designs that grow your audience with visual consistency.</p>
    </div>
    <div class="service-card fade-up">
      <div class="service-icon">🎬</div>
      <h3>Creative Direction</h3>
      <p>Big-picture creative guidance for campaigns, launches, and content — ensuring every visual decision serves your brand story.</p>
    </div>
    <div class="service-card fade-up fade-up-delay-1">
      <div class="service-icon">🧭</div>
      <h3>Visual Strategy</h3>
      <p>Data-informed creative strategy that aligns your visuals with your business goals, audience, and competitive landscape.</p>
    </div>
    <div class="service-card fade-up fade-up-delay-2">
      <div class="service-icon">📐</div>
      <h3>Marketing Designs</h3>
      <p>Flyers, banners, ads, and pitch decks that convert. High-impact marketing materials that reflect your premium brand.</p>
    </div>
  </div>
</section>

<!-- WHY US -->
<section class="why" id="why">
  <div style="text-align:center; margin-bottom: 56px;">
    <div class="section-label fade-up" style="justify-content:center;">Why Brandemier</div>
    <h2 class="section-title fade-up fade-up-delay-1">The Brandemier Difference</h2>
    <p class="section-sub fade-up fade-up-delay-2" style="margin: 0 auto; text-align:center;">We don't just design — we build brand experiences that drive real results and lasting recognition.</p>
  </div>
  <div class="why-grid">
    <div class="why-card fade-up">
      <div class="why-icon">💎</div>
      <h3>Premium & Modern Designs</h3>
      <p>Every deliverable is crafted to the highest standard — refined, contemporary, and built to impress your audience from the first glance.</p>
    </div>
    <div class="why-card fade-up fade-up-delay-1">
      <div class="why-icon">⚡</div>
      <h3>Fast Communication</h3>
      <p>We respond quickly, meet deadlines, and keep you in the loop at every step. Your time is valuable — we respect it fully.</p>
    </div>
    <div class="why-card fade-up fade-up-delay-2">
      <div class="why-icon">🧠</div>
      <h3>Strategic Branding Approach</h3>
      <p>We go beyond aesthetics. Every design decision is rooted in strategy, ensuring your brand communicates effectively and converts.</p>
    </div>
    <div class="why-card fade-up fade-up-delay-3">
      <div class="why-icon">✅</div>
      <h3>Clean & Professional Delivery</h3>
      <p>Organized files, proper formats, and thorough handover documentation. Your brand assets are delivered ready to use immediately.</p>
    </div>
  </div>
</section>

<!-- PORTFOLIO -->
<section class="portfolio" id="portfolio">
  <div class="portfolio-header">
    <div>
      <div class="section-label fade-up">Our Work</div>
      <h2 class="section-title fade-up fade-up-delay-1">Selected Projects</h2>
    </div>
    <p class="section-sub fade-up fade-up-delay-1" style="margin-bottom:0; max-width:320px;">A glimpse into the brands we've helped build from concept to launch.</p>
  </div>
  <div class="portfolio-grid fade-up">
    <!-- Main large item -->
    <div class="portfolio-item">
      <div class="portfolio-item-bg pi-1">
        <div class="pi-1-inner">
          <div class="pi-1-logo">NEXUS</div>
          <div class="pi-1-bar"></div>
          <div class="pi-1-tagline">Technology · Innovation · Future</div>
        </div>
      </div>
      <div class="portfolio-overlay">
        <div class="portfolio-overlay-text">
          <h4>Nexus Technology</h4>
          <p>Full Brand Identity System</p>
        </div>
      </div>
    </div>
    <!-- Item 2 -->
    <div class="portfolio-item">
      <div class="portfolio-item-bg pi-2" style="height:100%;">
        <div class="pi-2-inner">
          <div style="text-align:center;">
            <div class="pi-2-circle">A</div>
            <div style="font-family: var(--font-display); margin-top:12px; font-weight:700; color:#8b6a3e; font-size:1rem; letter-spacing:-0.01em;">AURUM</div>
            <div style="font-size:0.65rem; letter-spacing:0.15em; text-transform:uppercase; color:#bfa070; margin-top:4px;">Luxury Jewels</div>
          </div>
        </div>
      </div>
      <div class="portfolio-overlay">
        <div class="portfolio-overlay-text"><h4>Aurum Jewels</h4><p>Logo & Brand Identity</p></div>
      </div>
    </div>
    <!-- Item 3 -->
    <div class="portfolio-item">
      <div class="portfolio-item-bg pi-3" style="height:100%;">
        <div class="pi-3-inner">
          <div style="font-family: var(--font-display); color: var(--blue-400); font-size:1.6rem; font-weight:800; letter-spacing:-0.03em;">PULSE</div>
          <div class="pi-3-lines">
            <div class="pi-3-line" style="width:48px;"></div>
            <div class="pi-3-line" style="width:32px; opacity:0.5;"></div>
            <div class="pi-3-line" style="width:40px; opacity:0.3;"></div>
          </div>
          <div style="font-size:0.65rem; letter-spacing:0.15em; text-transform:uppercase; color:rgba(255,255,255,0.3);">Media Group</div>
        </div>
      </div>
      <div class="portfolio-overlay">
        <div class="portfolio-overlay-text"><h4>Pulse Media</h4><p>Brand Strategy & Identity</p></div>
      </div>
    </div>
    <!-- Item 4 -->
    <div class="portfolio-item">
      <div class="portfolio-item-bg pi-4" style="height:100%;">
        <div class="pi-4-inner">
          <div class="pi-4-box">V</div>
          <div class="pi-4-text">Vita Organics</div>
        </div>
      </div>
      <div class="portfolio-overlay">
        <div class="portfolio-overlay-text"><h4>Vita Organics</h4><p>Packaging & Brand Design</p></div>
      </div>
    </div>
    <!-- Item 5 -->
    <div class="portfolio-item">
      <div class="portfolio-item-bg pi-5" style="height:100%;">
        <div class="pi-5-inner">
          <div style="text-align:center;">
            <div class="pi-5-leaf">🌿</div>
            <div style="font-family: var(--font-display); font-weight:800; color:#166534; margin-top:10px; letter-spacing:-0.02em; font-size:1.1rem;">VERDE</div>
            <div style="font-size:0.65rem; letter-spacing:0.12em; color:#4ade80; text-transform:uppercase; margin-top:4px;">Wellness Co.</div>
          </div>
        </div>
      </div>
      <div class="portfolio-overlay">
        <div class="portfolio-overlay-text"><h4>Verde Wellness</h4><p>Social Media Branding</p></div>
      </div>
    </div>
  </div>
  <div class="portfolio-cta fade-up">
    <a href="#contact" class="btn-primary" style="margin:0 auto; display:inline-flex;">See More Projects ↗</a>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="testimonials" id="testimonials">
  <div style="text-align:center; margin-bottom:56px;">
    <div class="section-label fade-up" style="justify-content:center;">Client Reviews</div>
    <h2 class="section-title fade-up fade-up-delay-1">What Our Clients Say</h2>
    <p class="section-sub fade-up fade-up-delay-2" style="margin: 0 auto; text-align:center;">Real words from real people who trusted Brandemier with their brand.</p>
  </div>
  <div class="testimonials-grid">
    <div class="testimonial-card fade-up">
      <div class="testimonial-stars">★★★★★</div>
      <blockquote>"Brandemier completely transformed our brand. The logo and visual identity they created was beyond what we imagined. Professional, creative, and incredibly fast to work with."</blockquote>
      <div class="testimonial-author">
        <div class="testimonial-avatar" style="background: linear-gradient(135deg, #3b7df0, #5599f8);">AO</div>
        <div class="testimonial-author-info">
          <h4>Adebayo Okonkwo</h4>
          <p>CEO, Nexus Technology</p>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-up fade-up-delay-1">
      <div class="testimonial-stars">★★★★★</div>
      <blockquote>"The packaging design Brandemier delivered made our product look premium instantly. Sales improved and customers keep commenting on how beautiful the branding is. Absolutely worth it."</blockquote>
      <div class="testimonial-author">
        <div class="testimonial-avatar" style="background: linear-gradient(135deg, #c8a97e, #a07850);">FI</div>
        <div class="testimonial-author-info">
          <h4>Fatima Ibrahim</h4>
          <p>Founder, Vita Organics</p>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-up fade-up-delay-2">
      <div class="testimonial-stars">★★★★★</div>
      <blockquote>"Working with Brandemier was seamless. They understood our vision immediately and delivered a brand identity that positioned us perfectly in the market. Highly recommended!"</blockquote>
      <div class="testimonial-author">
        <div class="testimonial-avatar" style="background: linear-gradient(135deg, #166534, #4ade80);">CN</div>
        <div class="testimonial-author-info">
          <h4>Chidi Nwosu</h4>
          <p>Director, Pulse Media Group</p>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-up">
      <div class="testimonial-stars">★★★★★</div>
      <blockquote>"Our social media branding is now consistent and eye-catching. Brandemier gave us a system that our whole team can easily use. The results speak for themselves — more engagement, more trust."</blockquote>
      <div class="testimonial-author">
        <div class="testimonial-avatar" style="background: linear-gradient(135deg, #7c3aed, #a78bfa);">ZA</div>
        <div class="testimonial-author-info">
          <h4>Zainab Aliyu</h4>
          <p>Marketing Lead, Verde Wellness</p>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-up fade-up-delay-1">
      <div class="testimonial-stars">★★★★★</div>
      <blockquote>"Clean, modern, and premium — that's exactly what we wanted and exactly what we got. The team at Brandemier truly understands branding at a deep level. We'll definitely be back."</blockquote>
      <div class="testimonial-author">
        <div class="testimonial-avatar" style="background: linear-gradient(135deg, #dc2626, #f87171);">EO</div>
        <div class="testimonial-author-info">
          <h4>Emeka Obi</h4>
          <p>Co-founder, Aurum Jewels</p>
        </div>
      </div>
    </div>
    <div class="testimonial-card fade-up fade-up-delay-2">
      <div class="testimonial-stars">★★★★★</div>
      <blockquote>"From the first call to the final delivery, the experience was excellent. Brandemier brought strategic thinking and beautiful execution. Our brand finally looks as good as our product."</blockquote>
      <div class="testimonial-author">
        <div class="testimonial-avatar" style="background: linear-gradient(135deg, #0891b2, #38bdf8);">KM</div>
        <div class="testimonial-author-info">
          <h4>Kemi Martins</h4>
          <p>CEO, Luminar Studios</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="contact-bg"></div>
  <div class="contact-inner">
    <div>
      <div class="section-label fade-up">Get In Touch</div>
      <h2 class="section-title fade-up fade-up-delay-1">Let's Build Your Brand Together</h2>
      <p class="contact-sub fade-up fade-up-delay-2">Ready to elevate your brand? Reach out through any of our channels and let's start creating something remarkable.</p>
      <div class="contact-links fade-up fade-up-delay-2">
        <a href="https://wa.me/2349045408582" target="_blank" class="contact-link">
          <div class="contact-link-icon" style="background:rgba(37,211,102,0.15);">📱</div>
          <div class="contact-link-text">
            <strong>WhatsApp</strong>
            <span>+234 904 540 8582</span>
          </div>
        </a>
        <a href="https://instagram.com/brandemier.co" target="_blank" class="contact-link">
          <div class="contact-link-icon" style="background:rgba(225,48,108,0.15);">📸</div>
          <div class="contact-link-text">
            <strong>Instagram</strong>
            <span>@brandemier.co</span>
          </div>
        </a>
        <a href="https://x.com/brandemier" target="_blank" class="contact-link">
          <div class="contact-link-icon" style="background:rgba(255,255,255,0.08);">𝕏</div>
          <div class="contact-link-text">
            <strong>X (Twitter)</strong>
            <span>@brandemier</span>
          </div>
        </a>
        <a href="mailto:brandemier@gmail.com" class="contact-link">
          <div class="contact-link-icon" style="background:rgba(59,125,240,0.15);">✉️</div>
          <div class="contact-link-text">
            <strong>Email</strong>
            <span>brandemier@gmail.com</span>
          </div>
        </a>
      </div>
    </div>
    <div class="contact-right fade-up fade-up-delay-1">
      <h3>Send Us a Message</h3>
      <p>Tell us about your project and we'll get back to you within 24 hours.</p>
      <div class="form-group">
        <label>Your Name</label>
        <input type="text" placeholder="John Doe">
      </div>
      <div class="form-group">
        <label>Email Address</label>
        <input type="email" placeholder="john@example.com">
      </div>
      <div class="form-group">
        <label>Service Needed</label>
        <input type="text" placeholder="e.g. Brand Identity, Logo Design...">
      </div>
      <div class="form-group">
        <label>Tell Us About Your Project</label>
        <textarea placeholder="Describe your brand, goals, and what you're looking for..."></textarea>
      </div>
      <button class="btn-submit" onclick="handleFormSubmit(this)">Send Message →</button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-brand">
      <a href="#" class="footer-logo">Brand<span>emier</span></a>
      <p>Premium creative branding agency building modern, memorable brands that connect, attract, and convert.</p>
      <div class="footer-socials" style="margin-top:20px;">
        <a href="https://instagram.com/brandemier.co" target="_blank" class="footer-social" title="Instagram">📸</a>
        <a href="https://x.com/brandemier" target="_blank" class="footer-social" title="X/Twitter">𝕏</a>
        <a href="https://wa.me/2349045408582" target="_blank" class="footer-social" title="WhatsApp">📱</a>
        <a href="mailto:brandemier@gmail.com" class="footer-social" title="Email">✉️</a>
      </div>
    </div>
    <div class="footer-col">
      <h4>Services</h4>
      <ul>
        <li><a href="#services">Brand Identity</a></li>
        <li><a href="#services">Logo Design</a></li>
        <li><a href="#services">Packaging Design</a></li>
        <li><a href="#services">Social Branding</a></li>
        <li><a href="#services">Marketing Design</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Company</h4>
      <ul>
        <li><a href="#about">About Us</a></li>
        <li><a href="#portfolio">Portfolio</a></li>
        <li><a href="#testimonials">Reviews</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Contact</h4>
      <ul>
        <li><a href="mailto:brandemier@gmail.com">brandemier@gmail.com</a></li>
        <li><a href="https://wa.me/2349045408582">+234 904 540 8582</a></li>
        <li><a href="https://instagram.com/brandemier.co">@brandemier.co</a></li>
        <li><a href="https://x.com/brandemier">@brandemier</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2025 Brandemier. All rights reserved. Building brands people remember.</p>
    <p style="color:rgba(255,255,255,0.15);">Crafted with care ♡</p>
  </div>
</footer>

<!-- WHATSAPP FLOAT -->
<a href="https://wa.me/2349045408582" target="_blank" class="wa-float" title="Chat on WhatsApp">
  <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
  </svg>
</a>

<script>
  // Loader
  window.addEventListener('load', () => {
    setTimeout(() => {
      document.getElementById('loader').classList.add('hidden');
    }, 1400);
  });

  // Navbar scroll
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 20);
  });

  // Mobile menu
  const hamburger = document.getElementById('hamburger');
  const mobileMenu = document.getElementById('mobileMenu');
  let menuOpen = false;

  hamburger.addEventListener('click', () => {
    menuOpen = !menuOpen;
    mobileMenu.style.display = menuOpen ? 'flex' : 'none';
    requestAnimationFrame(() => {
      mobileMenu.classList.toggle('open', menuOpen);
    });
    const spans = hamburger.querySelectorAll('span');
    if (menuOpen) {
      spans[0].style.transform = 'rotate(45deg) translate(5px,5px)';
      spans[1].style.opacity = '0';
      spans[2].style.transform = 'rotate(-45deg) translate(5px,-5px)';
    } else {
      spans[0].style.transform = ''; spans[1].style.opacity = ''; spans[2].style.transform = '';
    }
  });

  document.querySelectorAll('.mobile-link').forEach(link => {
    link.addEventListener('click', () => {
      menuOpen = false;
      mobileMenu.style.display = 'none';
      mobileMenu.classList.remove('open');
      const spans = hamburger.querySelectorAll('span');
      spans[0].style.transform = ''; spans[1].style.opacity = ''; spans[2].style.transform = '';
    });
  });

  // Hero fade-ups trigger immediately
  document.querySelectorAll('.hero .fade-up').forEach((el, i) => {
    setTimeout(() => el.classList.add('visible'), 200 + i * 120);
  });

  // Intersection Observer for sections
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('section:not(.hero) .fade-up').forEach(el => observer.observe(el));

  // Form submit
  function handleFormSubmit(btn) {
    const original = btn.textContent;
    btn.textContent = 'Sending...';
    btn.disabled = true;
    setTimeout(() => {
      btn.textContent = '✓ Message Sent!';
      btn.style.background = '#16a34a';
      setTimeout(() => {
        btn.textContent = original;
        btn.style.background = '';
        btn.disabled = false;
      }, 3000);
    }, 1500);
  }

  // Smooth anchor behavior
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', e => {
      const target = document.querySelector(a.getAttribute('href'));
      if (target) {
        e.preventDefault();
        target.scrollIntoView({ behavior: 'smooth' });
      }
    });
  });
</script>
</body>
</html>
