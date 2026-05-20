# vets-flower-boutique
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>VETS — Flower Boutique</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --cream: #fff7ec;
      --dark: #442f2a;
      --blush: #f5cbd7;
      --black: #070d0d;
      --blush-dark: #e8a8bc;
      --cream-dark: #f0e4d0;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--cream);
      color: var(--dark);
      font-family: 'DM Sans', sans-serif;
      overflow-x: hidden;
      cursor: none;
    }

    /* CUSTOM CURSOR */
    .cursor {
      width: 12px; height: 12px;
      background: var(--dark);
      border-radius: 50%;
      position: fixed; top: 0; left: 0;
      pointer-events: none; z-index: 9999;
      transition: transform 0.15s ease, background 0.2s;
      transform: translate(-50%, -50%);
    }
    .cursor-follower {
      width: 36px; height: 36px;
      border: 1.5px solid var(--dark);
      border-radius: 50%;
      position: fixed; top: 0; left: 0;
      pointer-events: none; z-index: 9998;
      transition: transform 0.4s cubic-bezier(.23,1,.32,1), opacity 0.2s;
      transform: translate(-50%, -50%);
      opacity: 0.5;
    }

    /* SCROLLBAR */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--cream); }
    ::-webkit-scrollbar-thumb { background: var(--blush-dark); border-radius: 3px; }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 24px 48px;
      background: rgba(255,247,236,0.85);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid rgba(68,47,42,0.08);
      animation: slideDown 0.8s cubic-bezier(.23,1,.32,1) both;
    }
    @keyframes slideDown { from { transform: translateY(-100%); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

    .nav-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 28px; font-weight: 300; letter-spacing: 0.15em;
      color: var(--dark); text-decoration: none;
    }
    .nav-logo span { font-style: italic; color: var(--blush-dark); }

    .nav-links { display: flex; gap: 36px; list-style: none; }
    .nav-links a {
      font-size: 13px; font-weight: 400; letter-spacing: 0.08em;
      text-transform: uppercase; color: var(--dark);
      text-decoration: none; position: relative; padding-bottom: 2px;
      transition: color 0.2s;
    }
    .nav-links a::after {
      content: ''; position: absolute; bottom: 0; left: 0;
      width: 0; height: 1px; background: var(--dark);
      transition: width 0.3s cubic-bezier(.23,1,.32,1);
    }
    .nav-links a:hover::after { width: 100%; }

    .nav-btn {
      background: var(--dark); color: var(--cream);
      border: none; padding: 10px 24px;
      font-family: 'DM Sans', sans-serif; font-size: 13px;
      letter-spacing: 0.06em; text-transform: uppercase;
      border-radius: 100px; cursor: none;
      transition: background 0.25s, transform 0.2s;
    }
    .nav-btn:hover { background: var(--blush-dark); color: var(--dark); transform: scale(1.04); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      align-items: center;
      padding: 120px 48px 80px;
      position: relative; overflow: hidden;
    }

    .hero-bg-blob {
      position: absolute; top: -120px; right: -80px;
      width: 600px; height: 600px;
      background: radial-gradient(circle, var(--blush) 0%, transparent 70%);
      border-radius: 50%; opacity: 0.55;
      animation: blobFloat 8s ease-in-out infinite;
      pointer-events: none;
    }
    .hero-bg-blob2 {
      position: absolute; bottom: -100px; left: -60px;
      width: 400px; height: 400px;
      background: radial-gradient(circle, var(--blush-dark) 0%, transparent 70%);
      border-radius: 50%; opacity: 0.3;
      animation: blobFloat 10s ease-in-out infinite reverse;
    }
    @keyframes blobFloat {
      0%, 100% { transform: translate(0,0) scale(1); }
      33% { transform: translate(20px,-30px) scale(1.05); }
      66% { transform: translate(-15px,15px) scale(0.97); }
    }

    .hero-text { position: relative; z-index: 2; }

    .hero-tag {
      display: inline-flex; align-items: center; gap: 8px;
      background: var(--blush); color: var(--dark);
      padding: 6px 16px; border-radius: 100px;
      font-size: 12px; letter-spacing: 0.1em; text-transform: uppercase;
      margin-bottom: 28px;
      animation: fadeUp 0.8s 0.3s both;
    }
    .hero-tag::before { content: '✿'; font-size: 14px; }

    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(52px, 6vw, 88px);
      font-weight: 300; line-height: 1.05;
      letter-spacing: -0.01em;
      margin-bottom: 24px;
      animation: fadeUp 0.8s 0.45s both;
    }
    .hero-title em { font-style: italic; color: var(--blush-dark); }
    .hero-title .outline-text {
      -webkit-text-stroke: 1.5px var(--dark);
      color: transparent;
    }

    .hero-desc {
      font-size: 16px; line-height: 1.75; color: rgba(68,47,42,0.7);
      max-width: 400px; margin-bottom: 40px;
      animation: fadeUp 0.8s 0.6s both;
    }

    .hero-actions {
      display: flex; gap: 16px; align-items: center;
      animation: fadeUp 0.8s 0.75s both;
    }

    .btn-primary {
      background: var(--dark); color: var(--cream);
      border: none; padding: 16px 36px;
      font-family: 'DM Sans', sans-serif; font-size: 14px;
      letter-spacing: 0.06em; text-transform: uppercase;
      border-radius: 100px; cursor: none;
      transition: all 0.3s cubic-bezier(.23,1,.32,1);
      position: relative; overflow: hidden;
    }
    .btn-primary::after {
      content: ''; position: absolute; inset: 0;
      background: var(--blush);
      transform: translateX(-100%);
      transition: transform 0.4s cubic-bezier(.23,1,.32,1);
      z-index: 0; border-radius: 100px;
    }
    .btn-primary:hover::after { transform: translateX(0); }
    .btn-primary:hover { color: var(--dark); }
    .btn-primary span { position: relative; z-index: 1; }

    .btn-ghost {
      background: transparent; color: var(--dark);
      border: 1.5px solid rgba(68,47,42,0.3); padding: 15px 28px;
      font-family: 'DM Sans', sans-serif; font-size: 14px;
      letter-spacing: 0.06em; text-transform: uppercase;
      border-radius: 100px; cursor: none;
      transition: all 0.25s;
      display: flex; align-items: center; gap: 8px;
    }
    .btn-ghost:hover { border-color: var(--dark); background: rgba(68,47,42,0.05); }

    .hero-visual {
      position: relative; z-index: 2;
      display: grid; grid-template-columns: 1fr 1fr; grid-template-rows: auto auto;
      gap: 16px; padding: 20px;
      animation: fadeUp 0.9s 0.4s both;
    }

    .hero-card {
      border-radius: 20px; overflow: hidden;
      position: relative; background: var(--blush);
    }
    .hero-card-large {
      grid-column: 1 / 3;
      height: 280px;
      background: linear-gradient(135deg, var(--blush) 0%, var(--blush-dark) 100%);
      display: flex; align-items: flex-end; padding: 28px;
    }
    .hero-card-sm { height: 160px; }
    .hero-card:nth-child(2) { background: linear-gradient(135deg, var(--cream-dark), var(--blush)); }
    .hero-card:nth-child(3) { background: linear-gradient(135deg, var(--dark), #6b4a43); }

    .card-flower {
      position: absolute; font-size: 80px;
      opacity: 0.18; top: 50%; left: 50%;
      transform: translate(-50%,-50%) rotate(-15deg);
      animation: floatFlower 4s ease-in-out infinite;
      pointer-events: none; user-select: none;
    }
    @keyframes floatFlower {
      0%,100% { transform: translate(-50%,-50%) rotate(-15deg) scale(1); }
      50% { transform: translate(-50%,-54%) rotate(-10deg) scale(1.06); }
    }

    .card-price-tag {
      background: rgba(255,247,236,0.9);
      backdrop-filter: blur(8px);
      border-radius: 12px; padding: 10px 16px;
      font-size: 13px; font-weight: 500;
    }

    .hero-stats {
      grid-column: 1 / 3;
      display: flex; gap: 0;
      background: var(--dark); border-radius: 16px;
      overflow: hidden;
    }
    .stat-item {
      flex: 1; padding: 20px 24px; text-align: center;
      color: var(--cream); position: relative;
    }
    .stat-item + .stat-item::before {
      content: ''; position: absolute; left: 0; top: 25%; bottom: 25%;
      width: 1px; background: rgba(255,247,236,0.15);
    }
    .stat-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 32px; font-weight: 300;
      display: block; margin-bottom: 2px;
    }
    .stat-label { font-size: 11px; opacity: 0.6; letter-spacing: 0.08em; text-transform: uppercase; }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* MARQUEE */
    .marquee-section {
      overflow: hidden; background: var(--dark);
      padding: 18px 0; border-top: none;
    }
    .marquee-track {
      display: flex; gap: 40px; width: max-content;
      animation: marquee 20s linear infinite;
    }
    .marquee-item {
      display: flex; align-items: center; gap: 16px;
      color: var(--blush); font-family: 'Cormorant Garamond', serif;
      font-size: 22px; font-style: italic; white-space: nowrap;
    }
    .marquee-dot { width: 6px; height: 6px; background: var(--blush-dark); border-radius: 50%; }
    @keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }

    /* SECTIONS */
    section { padding: 100px 48px; }

    .section-tag {
      display: inline-block;
      font-size: 12px; letter-spacing: 0.14em; text-transform: uppercase;
      color: var(--blush-dark); margin-bottom: 14px;
    }
    .section-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(36px, 4vw, 60px);
      font-weight: 300; line-height: 1.1;
    }
    .section-title em { font-style: italic; }

    /* ABOUT / MENTORS */
    .about-section {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 80px; align-items: center;
    }

    .about-visual {
      position: relative; height: 500px;
    }
    .about-card-main {
      position: absolute; top: 0; left: 0; right: 80px; bottom: 80px;
      background: linear-gradient(160deg, var(--blush) 0%, var(--blush-dark) 100%);
      border-radius: 24px;
      display: flex; align-items: center; justify-content: center;
      font-size: 120px; overflow: hidden;
    }
    .about-card-accent {
      position: absolute; bottom: 0; right: 0;
      width: 180px; height: 180px;
      background: var(--dark);
      border-radius: 20px;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      gap: 6px; color: var(--cream);
      box-shadow: 0 20px 60px rgba(7,13,13,0.3);
    }
    .accent-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 48px; font-weight: 300; line-height: 1;
    }
    .accent-text { font-size: 11px; opacity: 0.7; letter-spacing: 0.1em; text-transform: uppercase; }

    .floating-badge {
      position: absolute; top: 40px; right: 60px;
      background: var(--cream);
      border: 1px solid var(--blush-dark);
      border-radius: 100px; padding: 10px 20px;
      font-size: 13px; color: var(--dark);
      box-shadow: 0 8px 30px rgba(68,47,42,0.12);
      animation: floatBadge 5s ease-in-out infinite;
      white-space: nowrap;
    }
    @keyframes floatBadge {
      0%,100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    .about-text .section-title { margin-bottom: 24px; }
    .about-text p { font-size: 15px; line-height: 1.8; color: rgba(68,47,42,0.7); margin-bottom: 32px; }

    .team-row {
      display: flex; gap: 16px; margin-top: 40px;
    }
    .team-card {
      flex: 1; background: var(--blush);
      border-radius: 16px; padding: 20px;
      transition: transform 0.3s cubic-bezier(.23,1,.32,1), box-shadow 0.3s;
    }
    .team-card:hover { transform: translateY(-6px); box-shadow: 0 16px 40px rgba(68,47,42,0.12); }
    .team-avatar {
      width: 56px; height: 56px; border-radius: 50%;
      background: var(--blush-dark);
      margin-bottom: 12px;
      display: flex; align-items: center; justify-content: center;
      font-size: 24px;
    }
    .team-name { font-family: 'Cormorant Garamond', serif; font-size: 20px; margin-bottom: 4px; }
    .team-role { font-size: 12px; color: rgba(68,47,42,0.6); letter-spacing: 0.06em; }

    /* PRODUCT GRID */
    .products-section { background: var(--cream); }
    .products-header {
      display: flex; align-items: flex-end; justify-content: space-between;
      margin-bottom: 60px;
    }

    .filter-pills {
      display: flex; gap: 10px;
    }
    .pill {
      padding: 8px 20px;
      border-radius: 100px;
      font-size: 13px; letter-spacing: 0.04em;
      border: 1.5px solid transparent;
      cursor: none;
      transition: all 0.25s;
      background: transparent;
      color: var(--dark);
      border-color: rgba(68,47,42,0.2);
    }
    .pill.active, .pill:hover {
      background: var(--dark); color: var(--cream); border-color: var(--dark);
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 24px;
    }

    .product-card {
      border-radius: 20px; overflow: hidden;
      background: white;
      box-shadow: 0 4px 20px rgba(68,47,42,0.07);
      transition: transform 0.4s cubic-bezier(.23,1,.32,1), box-shadow 0.4s;
      cursor: none;
    }
    .product-card:hover { transform: translateY(-10px); box-shadow: 0 20px 50px rgba(68,47,42,0.14); }

    .product-img {
      height: 240px;
      position: relative; overflow: hidden;
      display: flex; align-items: center; justify-content: center;
    }
    .product-img-emoji {
      font-size: 90px;
      transition: transform 0.4s cubic-bezier(.23,1,.32,1);
      position: relative; z-index: 1;
    }
    .product-card:hover .product-img-emoji { transform: scale(1.15) rotate(5deg); }

    .product-bg-circle {
      position: absolute; width: 180px; height: 180px;
      border-radius: 50%;
      opacity: 0.35;
      transition: transform 0.5s;
    }
    .product-card:hover .product-bg-circle { transform: scale(1.4); }

    .product-badge {
      position: absolute; top: 16px; left: 16px;
      background: var(--dark); color: var(--cream);
      font-size: 11px; padding: 4px 12px;
      border-radius: 100px; letter-spacing: 0.06em;
    }
    .product-badge.sale { background: var(--blush-dark); color: var(--dark); }

    .product-body { padding: 20px 22px 24px; }
    .product-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 22px; margin-bottom: 6px; font-weight: 400;
    }
    .product-desc { font-size: 13px; color: rgba(68,47,42,0.6); line-height: 1.6; margin-bottom: 16px; }
    .product-footer {
      display: flex; align-items: center; justify-content: space-between;
    }
    .product-price {
      font-family: 'Cormorant Garamond', serif;
      font-size: 26px; font-weight: 300;
    }
    .add-btn {
      width: 42px; height: 42px;
      border-radius: 50%; background: var(--dark); color: var(--cream);
      border: none; font-size: 22px; cursor: none;
      display: flex; align-items: center; justify-content: center;
      transition: all 0.25s; line-height: 1;
    }
    .add-btn:hover { background: var(--blush-dark); color: var(--dark); transform: rotate(90deg) scale(1.1); }

    /* FEATURED BANNER */
    .featured-banner {
      background: var(--dark);
      border-radius: 28px; overflow: hidden;
      display: grid; grid-template-columns: 1.2fr 1fr;
      min-height: 400px;
      margin: 0 48px 80px;
      position: relative;
    }
    .featured-content { padding: 60px; z-index: 2; }
    .featured-tag {
      display: inline-block;
      background: var(--blush); color: var(--dark);
      font-size: 11px; padding: 5px 14px; border-radius: 100px;
      letter-spacing: 0.1em; text-transform: uppercase;
      margin-bottom: 24px;
    }
    .featured-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 52px; font-weight: 300; line-height: 1.1;
      color: var(--cream); margin-bottom: 20px;
    }
    .featured-title em { font-style: italic; color: var(--blush); }
    .featured-desc { font-size: 15px; color: rgba(255,247,236,0.65); line-height: 1.7; margin-bottom: 36px; }
    .featured-price-row { display: flex; align-items: center; gap: 24px; }
    .featured-price {
      font-family: 'Cormorant Garamond', serif;
      font-size: 48px; color: var(--blush); font-weight: 300;
    }
    .featured-old-price {
      font-size: 22px; color: rgba(255,247,236,0.4);
      text-decoration: line-through;
      font-family: 'Cormorant Garamond', serif;
    }

    .featured-visual {
      position: relative; display: flex;
      align-items: center; justify-content: center;
    }
    .featured-blob {
      position: absolute; width: 350px; height: 350px;
      background: radial-gradient(circle, rgba(245,203,215,0.2) 0%, transparent 70%);
      border-radius: 50%;
      animation: blobFloat 6s ease-in-out infinite;
    }
    .featured-emoji { font-size: 160px; position: relative; z-index: 1;
      animation: floatFlower 5s ease-in-out infinite; }

    .featured-dots {
      position: absolute; bottom: -1px; left: 0; right: 0;
      height: 80px;
      background: linear-gradient(to bottom, transparent, var(--black));
      opacity: 0; /* subtle */
    }

    /* TESTIMONIALS */
    .testimonials-section { background: var(--blush); }
    .testimonials-grid {
      display: grid; grid-template-columns: repeat(3, 1fr);
      gap: 20px; margin-top: 50px;
    }
    .testimonial-card {
      background: white; border-radius: 20px; padding: 28px;
      position: relative; overflow: hidden;
      transition: transform 0.3s;
    }
    .testimonial-card:hover { transform: translateY(-5px); }
    .testimonial-card.featured-review {
      background: var(--dark); color: var(--cream);
    }
    .t-quote {
      font-size: 42px; line-height: 1;
      font-family: 'Cormorant Garamond', serif;
      color: var(--blush-dark); margin-bottom: 12px;
      display: block;
    }
    .featured-review .t-quote { color: var(--blush); }
    .t-text {
      font-size: 14px; line-height: 1.75;
      color: rgba(68,47,42,0.75); margin-bottom: 20px;
    }
    .featured-review .t-text { color: rgba(255,247,236,0.75); }
    .t-author { display: flex; align-items: center; gap: 12px; }
    .t-avatar {
      width: 40px; height: 40px; border-radius: 50%;
      background: var(--blush); display: flex; align-items: center; justify-content: center;
      font-size: 18px; flex-shrink: 0;
    }
    .featured-review .t-avatar { background: rgba(245,203,215,0.2); }
    .t-name { font-size: 14px; font-weight: 500; }
    .t-handle { font-size: 12px; opacity: 0.5; }
    .t-stars { color: var(--blush-dark); font-size: 13px; margin-bottom: 4px; }
    .featured-review .t-stars { color: var(--blush); }

    /* WORKSHOPS AGENDA */
    .agenda-section { background: var(--cream); }
    .agenda-grid {
      display: grid; grid-template-columns: 1.5fr 1fr;
      gap: 40px; margin-top: 50px; align-items: start;
    }
    .agenda-list { display: flex; flex-direction: column; gap: 16px; }
    .agenda-item {
      display: grid; grid-template-columns: 80px 1fr auto;
      align-items: center; gap: 20px;
      background: white;
      border: 1px solid rgba(68,47,42,0.08);
      border-radius: 16px; padding: 20px 24px;
      transition: all 0.3s;
      cursor: none;
    }
    .agenda-item:hover, .agenda-item.active {
      background: var(--dark); color: var(--cream);
      border-color: var(--dark);
      transform: translateX(8px);
    }
    .agenda-time {
      font-family: 'Cormorant Garamond', serif;
      font-size: 22px; font-weight: 300; line-height: 1.1;
    }
    .agenda-item:hover .agenda-time, .agenda-item.active .agenda-time { color: var(--blush); }
    .agenda-info h4 { font-size: 15px; font-weight: 500; margin-bottom: 3px; }
    .agenda-info p { font-size: 13px; opacity: 0.6; }
    .agenda-icon { font-size: 28px; }

    .agenda-cta-card {
      background: var(--dark); border-radius: 24px; padding: 40px;
      color: var(--cream); position: relative; overflow: hidden;
    }
    .cta-blob {
      position: absolute; width: 300px; height: 300px;
      background: radial-gradient(circle, rgba(245,203,215,0.15) 0%, transparent 70%);
      border-radius: 50%; top: -100px; right: -100px;
    }
    .agenda-cta-card h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 36px; font-weight: 300;
      margin-bottom: 16px; position: relative; z-index: 1;
    }
    .agenda-cta-card h3 em { font-style: italic; color: var(--blush); }
    .agenda-cta-card p { font-size: 14px; opacity: 0.65; line-height: 1.7; margin-bottom: 32px; position: relative; z-index: 1; }

    /* PRICING */
    .pricing-section {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 24px; align-items: start;
    }
    .pricing-card {
      border-radius: 24px; padding: 40px;
      border: 1.5px solid rgba(68,47,42,0.1);
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .pricing-card:hover { transform: translateY(-8px); box-shadow: 0 24px 60px rgba(68,47,42,0.1); }
    .pricing-card.featured {
      background: var(--dark); color: var(--cream);
      border-color: var(--dark);
    }
    .pricing-label {
      display: inline-block;
      font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase;
      padding: 5px 14px; border-radius: 100px;
      background: var(--blush); color: var(--dark);
      margin-bottom: 24px;
    }
    .pricing-card.featured .pricing-label { background: var(--blush-dark); }
    .pricing-price {
      font-family: 'Cormorant Garamond', serif;
      font-size: 64px; font-weight: 300; line-height: 1; margin-bottom: 6px;
    }
    .pricing-sub { font-size: 14px; opacity: 0.6; margin-bottom: 32px; }
    .pricing-features { list-style: none; margin-bottom: 36px; }
    .pricing-features li {
      padding: 10px 0; font-size: 14px;
      border-bottom: 1px solid rgba(68,47,42,0.08);
      display: flex; gap: 10px; align-items: center;
    }
    .pricing-card.featured .pricing-features li { border-color: rgba(255,247,236,0.1); }
    .pricing-features li::before { content: '✓'; color: var(--blush-dark); font-weight: 600; }

    /* JOIN SECTION */
    .join-section {
      background: var(--dark); margin: 0 48px 80px;
      border-radius: 28px; padding: 80px 60px;
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 60px; align-items: center;
    }
    .join-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(40px, 4vw, 62px);
      font-weight: 300; line-height: 1.1; color: var(--cream);
    }
    .join-title em { font-style: italic; color: var(--blush); }
    .join-form { display: flex; flex-direction: column; gap: 14px; }
    .join-input {
      background: rgba(255,247,236,0.07); border: 1px solid rgba(255,247,236,0.15);
      border-radius: 12px; padding: 14px 20px;
      font-family: 'DM Sans', sans-serif; font-size: 14px;
      color: var(--cream); outline: none;
      transition: border-color 0.2s, background 0.2s;
    }
    .join-input::placeholder { color: rgba(255,247,236,0.35); }
    .join-input:focus { border-color: var(--blush); background: rgba(245,203,215,0.06); }
    .join-submit {
      background: var(--blush); color: var(--dark);
      border: none; padding: 16px 32px;
      font-family: 'DM Sans', sans-serif; font-size: 14px;
      font-weight: 500; letter-spacing: 0.04em;
      border-radius: 12px; cursor: none;
      transition: all 0.25s; margin-top: 4px;
    }
    .join-submit:hover { background: var(--cream); transform: scale(1.02); }

    .join-perks { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 32px; }
    .perk-chip {
      background: rgba(255,247,236,0.06); border: 1px solid rgba(255,247,236,0.12);
      border-radius: 12px; padding: 14px 16px;
      font-size: 13px; color: rgba(255,247,236,0.7);
      display: flex; align-items: center; gap: 8px;
    }
    .perk-icon { font-size: 18px; }

    /* FAQ */
    .faq-section { padding: 100px 48px; }
    .faq-grid {
      display: grid; grid-template-columns: 1fr 1.4fr;
      gap: 80px; margin-top: 60px;
    }
    .faq-intro p { font-size: 15px; line-height: 1.8; color: rgba(68,47,42,0.65); margin-top: 20px; margin-bottom: 36px; }

    .faq-list { display: flex; flex-direction: column; gap: 0; }
    .faq-item {
      border-bottom: 1px solid rgba(68,47,42,0.1);
      overflow: hidden;
    }
    .faq-question {
      width: 100%; background: none; border: none;
      text-align: left; padding: 20px 0;
      font-family: 'DM Sans', sans-serif; font-size: 15px;
      color: var(--dark); cursor: none;
      display: flex; justify-content: space-between; align-items: center;
      font-weight: 400;
    }
    .faq-toggle {
      width: 30px; height: 30px; border-radius: 50%;
      background: var(--blush); display: flex;
      align-items: center; justify-content: center;
      font-size: 18px; flex-shrink: 0;
      transition: transform 0.3s, background 0.2s;
    }
    .faq-item.open .faq-toggle { transform: rotate(45deg); background: var(--dark); color: var(--cream); }
    .faq-answer {
      max-height: 0; overflow: hidden;
      transition: max-height 0.4s cubic-bezier(.23,1,.32,1), padding 0.3s;
      font-size: 14px; line-height: 1.75; color: rgba(68,47,42,0.65);
    }
    .faq-item.open .faq-answer { max-height: 200px; padding-bottom: 18px; }

    /* FOOTER */
    footer {
      background: var(--black); color: var(--cream);
      padding: 60px 48px 36px;
    }
    .footer-top {
      display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 48px; margin-bottom: 48px;
      padding-bottom: 48px;
      border-bottom: 1px solid rgba(255,247,236,0.1);
    }
    .footer-brand .nav-logo { display: block; margin-bottom: 16px; color: var(--cream); }
    .footer-brand p { font-size: 14px; line-height: 1.7; opacity: 0.5; margin-bottom: 24px; }
    .social-row { display: flex; gap: 12px; }
    .social-btn {
      width: 38px; height: 38px; border-radius: 50%;
      background: rgba(255,247,236,0.08); border: 1px solid rgba(255,247,236,0.1);
      color: var(--cream); font-size: 14px;
      display: flex; align-items: center; justify-content: center;
      cursor: none; transition: all 0.25s; text-decoration: none;
    }
    .social-btn:hover { background: var(--blush-dark); color: var(--dark); border-color: var(--blush-dark); }
    .footer-col h5 {
      font-size: 12px; letter-spacing: 0.12em; text-transform: uppercase;
      opacity: 0.4; margin-bottom: 20px;
    }
    .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
    .footer-col a { font-size: 14px; opacity: 0.7; text-decoration: none; color: var(--cream); transition: opacity 0.2s; }
    .footer-col a:hover { opacity: 1; }
    .footer-bottom { display: flex; justify-content: space-between; align-items: center; }
    .footer-bottom p { font-size: 13px; opacity: 0.35; }

    /* REVEAL ANIMATION */
    .reveal { opacity: 0; transform: translateY(40px); transition: opacity 0.8s cubic-bezier(.23,1,.32,1), transform 0.8s cubic-bezier(.23,1,.32,1); }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* PETAL RAIN */
    .petal {
      position: fixed; pointer-events: none;
      font-size: 18px; opacity: 0;
      animation: petalFall linear forwards;
      z-index: 50;
    }
    @keyframes petalFall {
      0% { opacity: 0.8; transform: translateY(-20px) rotate(0deg); }
      100% { opacity: 0; transform: translateY(100vh) rotate(720deg); }
    }

    /* RESPONSIVE ROUGH */
    @media (max-width: 900px) {
      nav { padding: 18px 24px; }
      .nav-links { display: none; }
      section { padding: 70px 24px; }
      .hero { grid-template-columns: 1fr; padding: 120px 24px 60px; gap: 40px; }
      .hero-visual { grid-template-columns: 1fr 1fr; }
      .about-section, .agenda-grid, .faq-grid, .join-section { grid-template-columns: 1fr; gap: 40px; }
      .products-grid { grid-template-columns: 1fr 1fr; }
      .featured-banner { grid-template-columns: 1fr; margin: 0 24px 60px; }
      .footer-top { grid-template-columns: 1fr 1fr; }
      .join-section { margin: 0 24px 60px; padding: 48px 32px; }
    }
  </style>
</head>
<body>

  <!-- CURSOR -->
  <div class="cursor" id="cursor"></div>
  <div class="cursor-follower" id="follower"></div>

  <!-- NAV -->
  <nav>
    <a href="#" class="nav-logo">VE<span>TS</span></a>
    <ul class="nav-links">
      <li><a href="#shop">Shop</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#workshops">Workshop</a></li>
      <li><a href="#faq">FAQ</a></li>
    </ul>
    <button class="nav-btn">Order Now</button>
  </nav>

  <!-- HERO -->
  <section class="hero" id="home">
    <div class="hero-bg-blob"></div>
    <div class="hero-bg-blob2"></div>

    <div class="hero-text">
      <div class="hero-tag">KYIV`S BEST BLOOMS </div>
      <h1 class="hero-title">
        Where every<br>
        <em>petal</em> tells a<br>
        <span class="outline-text">story</span>
      </h1>
      <p class="hero-desc">
        Handcrafted bouquets made with love in the heart of Kyiv. 
        Fresh, seasonal flowers delivered to your door within hours. @d1shalis
      </p>
      <div class="hero-actions">
        <button class="btn-primary"><span>Explore Bouquets</span></button>
        <button class="btn-ghost">
          <span>↓</span> Watch Story
        </button>
      </div>
    </div>

    <div class="hero-visual">
      <div class="hero-card hero-card-large">
        <div class="card-flower">🌸</div>
        <div class="card-price-tag">🌷 Seasonal Collection — From $15</div>
      </div>
      <div class="hero-card hero-card-sm">
        <div class="card-flower" style="font-size:50px;">🌺</div>
      </div>
      <div class="hero-card hero-card-sm">
        <div class="card-flower" style="font-size:50px;color:var(--cream);opacity:0.3;">🌻</div>
      </div>
      <div class="hero-stats">
        <div class="stat-item">
          <span class="stat-num">2k+</span>
          <span class="stat-label">Happy Clients</span>
        </div>
        <div class="stat-item">
          <span class="stat-num">150+</span>
          <span class="stat-label">Arrangements</span>
        </div>
        <div class="stat-item">
          <span class="stat-num">8yr</span>
          <span class="stat-label">Experience</span>
        </div>
      </div>
    </div>
  </section>

  <!-- MARQUEE -->
  <div class="marquee-section">
    <div class="marquee-track">
      <div class="marquee-item"><span class="marquee-dot"></span> Same Day Delivery</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Seasonal Blooms</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Handcrafted Bouquets</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Subscription Plans</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Wedding Flowers</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Custom Arrangements</div>
      <!-- duplicate for loop -->
      <div class="marquee-item"><span class="marquee-dot"></span> Same Day Delivery</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Seasonal Blooms</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Handcrafted Bouquets</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Subscription Plans</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Wedding Flowers</div>
      <div class="marquee-item"><span class="marquee-dot"></span> Custom Arrangements</div>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about" style="padding: 100px 48px;">
    <div class="about-section reveal">
      <div class="about-visual">
        <div class="about-card-main">
          <div class="card-flower" style="font-size:180px;opacity:0.22;">🌸</div>
        </div>
        <div class="about-card-accent">
          <span class="accent-num">8+</span>
          <span class="accent-text">Years Crafting</span>
        </div>
        <div class="floating-badge">✿ Award Winning Florist</div>
      </div>

      <div class="about-text">
        <span class="section-tag">Meet Your Florists</span>
        <h2 class="section-title">Sweet mentors,<br><em>blooming hearts</em></h2>
        <p>
          We are a collective of passionate florists dedicated to the art of floral design. 
          Every arrangement is crafted with intention, seasonal awareness, and a deep love for nature's most beautiful creations.
        </p>

        <div class="team-row">
          <div class="team-card">
            <div class="team-avatar">🌺</div>
            <div class="team-name">Diana</div>
            <div class="team-role">Head Florist & Founder</div>
          </div>
          <div class="team-card">
            <div class="team-avatar">🌸</div>
            <div class="team-name">Elena</div>
            <div class="team-role">Colour Specialist</div>
          </div>
          <div class="team-card">
            <div class="team-avatar">🌼</div>
            <div class="team-name">Daria</div>
            <div class="team-role">Wedding Designer</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SHOP -->
  <section id="shop" class="products-section">
    <div class="products-header reveal">
      <div>
        <span class="section-tag">Our Collection</span>
        <h2 class="section-title">Curated for<br><em>every moment</em></h2>
      </div>
      <div class="filter-pills">
        <button class="pill active">All</button>
        <button class="pill">Bouquets</button>
        <button class="pill">Seasonal</button>
        <button class="pill">Wedding</button>
      </div>
    </div>

    <div class="products-grid">
      <div class="product-card reveal">
        <div class="product-img" style="background: linear-gradient(135deg,#fce4ec,#f8bbd0);">
          <div class="product-bg-circle" style="background:var(--blush-dark);"></div>
          <div class="product-img-emoji">🌹</div>
          <div class="product-badge sale">Bestseller</div>
        </div>
        <div class="product-body">
          <div class="product-name">Eternal Rose</div>
          <div class="product-desc">Classic red roses, symbol of timeless love. Hand-tied in soft linen.</div>
          <div class="product-footer">
            <div class="product-price">$40</div>
            <button class="add-btn">+</button>
          </div>
        </div>
      </div>

      <div class="product-card reveal">
        <div class="product-img" style="background: linear-gradient(135deg,#fff3e0,#ffe0b2);">
          <div class="product-bg-circle" style="background:#ffcc80;"></div>
          <div class="product-img-emoji">🌻</div>
          <div class="product-badge">New</div>
        </div>
        <div class="product-body">
          <div class="product-name">Sunlit Garden</div>
          <div class="product-desc">Vibrant sunflowers & wildflowers, capturing a summer afternoon.</div>
          <div class="product-footer">
            <div class="product-price">$30</div>
            <button class="add-btn">+</button>
          </div>
        </div>
      </div>

      <div class="product-card reveal">
        <div class="product-img" style="background: linear-gradient(135deg,#e8f5e9,#c8e6c9);">
          <div class="product-bg-circle" style="background:#a5d6a7;"></div>
          <div class="product-img-emoji">🌸</div>
        </div>
        <div class="product-body">
          <div class="product-name">Cherry Blossom</div>
          <div class="product-desc">Delicate pink blooms celebrating the season's first whisper of spring.</div>
          <div class="product-footer">
            <div class="product-price">$50</div>
            <button class="add-btn">+</button>
          </div>
        </div>
      </div>

      <div class="product-card reveal">
        <div class="product-img" style="background: linear-gradient(135deg,#ede7f6,#d1c4e9);">
          <div class="product-bg-circle" style="background:#b39ddb;"></div>
          <div class="product-img-emoji">💐</div>
          <div class="product-badge">Popular</div>
        </div>
        <div class="product-body">
          <div class="product-name">Lavender Dream</div>
          <div class="product-desc">Mixed lavender and white blooms for a romantic, dreamy atmosphere.</div>
          <div class="product-footer">
            <div class="product-price">$40</div>
            <button class="add-btn">+</button>
          </div>
        </div>
      </div>

      <div class="product-card reveal">
        <div class="product-img" style="background: linear-gradient(135deg,#fff8e1,#fff3e0);">
          <div class="product-bg-circle" style="background:#ffe082;"></div>
          <div class="product-img-emoji">🌷</div>
        </div>
        <div class="product-body">
          <div class="product-name">Tulip Parade</div>
          <div class="product-desc">Fresh spring tulips in a rainbow of soft, joyful hues.</div>
          <div class="product-footer">
            <div class="product-price">$30</div>
            <button class="add-btn">+</button>
          </div>
        </div>
      </div>

      <div class="product-card reveal">
        <div class="product-img" style="background: linear-gradient(135deg, var(--cream-dark), var(--blush));">
          <div class="product-bg-circle" style="background:var(--blush-dark);"></div>
          <div class="product-img-emoji">🌺</div>
          <div class="product-badge sale">Wedding</div>
        </div>
        <div class="product-body">
          <div class="product-name">Bridal Reverie</div>
          <div class="product-desc">Elegant bridal bouquet, thoughtfully composed for your perfect day.</div>
          <div class="product-footer">
            <div class="product-price">$120</div>
            <button class="add-btn">+</button>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- FEATURED DEAL -->
  <div class="featured-banner reveal">
    <div class="featured-content">
      <span class="featured-tag">✦ Delicious Deal of the Week</span>
      <h2 class="featured-title">The Perfect<br><em>Bouquet</em> for You</h2>
      <p class="featured-desc">
        Our signature seasonal subscription 12 hand selected stems 
        delivered every week, wrapped in recycled kraft paper with a personal note.
      </p>
      <div class="featured-price-row">
        <div class="featured-price">$20</div>
        <div class="featured-old-price">$40</div>
        <button class="btn-primary" style="background:var(--blush);color:var(--dark);"><span>Subscribe Now</span></button>
      </div>
    </div>
    <div class="featured-visual">
      <div class="featured-blob"></div>
      <div class="featured-emoji">🌸</div>
    </div>
  </div>

  <!-- GALLERY TEASER -->
  <section style="padding: 60px 48px 100px; background: var(--blush);">
    <div class="reveal" style="text-align:center;margin-bottom:48px;">
      <span class="section-tag">Gallery</span>
      <h2 class="section-title">What we have<br><em>done together</em></h2>
    </div>
    <div class="reveal" style="display:grid;grid-template-columns:2fr 1fr 1fr;grid-template-rows:200px 200px;gap:16px;">
      <div style="grid-row:1/3;border-radius:20px;background:linear-gradient(135deg,var(--cream),var(--blush-dark));display:flex;align-items:center;justify-content:center;font-size:100px;">🌷</div>
      <div style="border-radius:20px;background:linear-gradient(135deg,var(--dark),#6b4a43);display:flex;align-items:center;justify-content:center;font-size:60px;">🌺</div>
      <div style="border-radius:20px;background:linear-gradient(135deg,var(--cream-dark),var(--blush));display:flex;align-items:center;justify-content:center;font-size:60px;">🌸</div>
      <div style="border-radius:20px;background:linear-gradient(135deg,var(--blush),var(--cream));display:flex;align-items:center;justify-content:center;font-size:60px;">💐</div>
      <div style="border-radius:20px;background:linear-gradient(135deg,var(--blush-dark),var(--dark));display:flex;align-items:center;justify-content:center;font-size:60px;">🌹</div>
    </div>
  </section>

  <!-- TESTIMONIALS -->
  <section class="testimonials-section">
    <div class="reveal" style="text-align:center;margin-bottom:12px;">
      <span class="section-tag">Happy Clients</span>
      <h2 class="section-title">What our clients <em>say</em></h2>
    </div>
    <div class="testimonials-grid reveal">
      <div class="testimonial-card featured-review">
        <span class="t-quote">"</span>
        <p class="t-text">Absolutely breathtaking arrangements every single time. Daria understands exactly the feeling I want to convey. My home feels completely transformed.</p>
        <div class="t-author">
          <div class="t-avatar">🌸</div>
          <div>
            <div class="t-stars">★★★★★</div>
            <div class="t-name">@kendalljener</div>
            <div class="t-handle">Kyiv, UA</div>
          </div>
        </div>
      </div>

      <div class="testimonial-card">
        <span class="t-quote">"</span>
        <p class="t-text">You can literally smell the care in every bouquet. Ordered for my mum's birthday and she cried happy tears. Will be a regular from now on!</p>
        <div class="t-author">
          <div class="t-avatar">🌺</div>
          <div>
            <div class="t-stars">★★★★★</div>
            <div class="t-name">Alica Miller</div>
            <div class="t-handle">Obuchiv, UA</div>
          </div>
        </div>
      </div>

      <div class="testimonial-card">
        <span class="t-quote">"</span>
        <p class="t-text">The weekly subscription is the best thing I've done for my office. Everyone comments on the flowers and it brings such warmth to the space.</p>
        <div class="t-author">
          <div class="t-avatar">🌼</div>
          <div>
            <div class="t-stars">★★★★★</div>
            <div class="t-name">@BlueNight</div>
            <div class="t-handle">Koncha Zaspa, UA</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- WORKSHOPS AGENDA -->
  <section id="workshops" class="agenda-section">
    <div class="reveal">
      <span class="section-tag">Flower`s Workshop</span>
      <h2 class="section-title">Workshop <em>agenda</em></h2>
    </div>
    <div class="agenda-grid reveal">
      <div class="agenda-list">
        <div class="agenda-item active">
          <div class="agenda-time">10:00<br>AM</div>
          <div class="agenda-info"><h4>Welcome & Introduction</h4><p>Meet your florists, tour the studio</p></div>
          <div class="agenda-icon">🌸</div>
        </div>
        <div class="agenda-item">
          <div class="agenda-time">10:30<br>AM</div>
          <div class="agenda-info"><h4>Flower Selection</h4><p>Learn to choose seasonal blooms</p></div>
          <div class="agenda-icon">🌺</div>
        </div>
        <div class="agenda-item">
          <div class="agenda-time">11:30<br>AM</div>
          <div class="agenda-info"><h4>Arrangement Techniques</h4><p>Hands-on bouquet construction</p></div>
          <div class="agenda-icon">💐</div>
        </div>
        <div class="agenda-item">
          <div class="agenda-time">12:30<br>PM</div>
          <div class="agenda-info"><h4>Wrapping & Styling</h4><p>Professional finishing touches</p></div>
          <div class="agenda-icon">🎀</div>
        </div>
        <div class="agenda-item">
          <div class="agenda-time">1:00<br>PM</div>
          <div class="agenda-info"><h4>Take Home & Celebrate</h4><p>Your creation, yours to keep</p></div>
          <div class="agenda-icon">🌷</div>
        </div>
      </div>

      <div class="agenda-cta-card">
        <div class="cta-blob"></div>
        <h3>Perfect<br><em>for You</em></h3>
        <p>Join our intimate workshops for a 3-hour hands-on experience. All skill levels welcome leave with your own stunning arrangement.</p>
        <div style="margin-bottom:24px;font-size:13px;color:rgba(255,247,236,0.5);position:relative;z-index:1;">
          📅 Every Saturday · Max 8 people · Includes materials
        </div>

        <div class="pricing-section" style="grid-template-columns:1fr 1fr;gap:16px;padding:0;margin-bottom:0;">
          <div class="pricing-card" style="background:rgba(255,247,236,0.06);border-color:rgba(255,247,236,0.12);padding:24px;">
            <div class="pricing-label">Single</div>
            <div class="pricing-price" style="color:var(--cream);font-size:48px;">$50</div>
            <div class="pricing-sub" style="color:rgba(255,247,236,0.5);margin-bottom:0;">per person</div>
          </div>
          <div class="pricing-card" style="background:var(--blush);border-color:var(--blush);padding:24px;">
            <div class="pricing-label" style="background:var(--dark);color:var(--cream);">Group</div>
            <div class="pricing-price" style="font-size:48px;">$40</div>
            <div class="pricing-sub" style="margin-bottom:0;">per person · 3–8</div>
          </div>
        </div>

        <button class="btn-primary" style="margin-top:24px;position:relative;z-index:1;"><span>Book Your Spot →</span></button>
      </div>
    </div>
  </section>

  <!-- JOIN / NEWSLETTER -->
  <div class="join-section reveal">
    <div>
      <h2 class="join-title">Join the<br><em>flower</em><br>community</h2>
      <div class="join-perks">
        <div class="perk-chip"><span class="perk-icon">💌</span> Weekly bloom updates</div>
        <div class="perk-chip"><span class="perk-icon">🎁</span> Exclusive discounts</div>
        <div class="perk-chip"><span class="perk-icon">🌿</span> Care & styling tips</div>
        <div class="perk-chip"><span class="perk-icon">⭐</span> Early access drops</div>
      </div>
    </div>
    <div>
      <p style="color:rgba(255,247,236,0.55);font-size:14px;line-height:1.7;margin-bottom:28px;">
        Subscribe to our newsletter and be the first to discover new seasonal collections, workshop dates, and exclusive arrangements.
      </p>
      <div class="join-form">
        <input type="text" class="join-input" placeholder="Your full name" />
        <input type="email" class="join-input" placeholder="Email address" />
        <select class="join-input" style="appearance:none;cursor:none;">
          <option value="">How often would you like updates?</option>
          <option>Weekly</option>
          <option>Bi-weekly</option>
          <option>Monthly</option>
        </select>
        <button class="join-submit">Subscribe ✿</button>
      </div>
    </div>
  </div>

  <!-- FAQ -->
  <section id="faq" class="faq-section">
    <div class="faq-grid">
      <div class="faq-intro reveal">
        <span class="section-tag">Have questions?</span>
        <h2 class="section-title">Frequently<br><em>asked questions</em></h2>
        <p>Everything you need to know before your first order. Can't find your answer? Drop us a message we respond within the hour.</p>
        <button class="btn-primary"><span>Contact Us</span></button>
      </div>

      <div class="faq-list reveal">
        <div class="faq-item open">
          <button class="faq-question">
            What is included in the masterclass?
            <span class="faq-toggle">+</span>
          </button>
          <div class="faq-answer">
            All materials, flowers, wrapping paper and ribbon are included. You'll also receive a printed care guide and a 15% discount on your next order.
          </div>
        </div>
        <div class="faq-item">
          <button class="faq-question">
            When and where are the masterclasses held?
            <span class="faq-toggle">+</span>
          </button>
          <div class="faq-answer">
            Workshops are held every Saturday 10am–1pm at our studio, 13 Khreshchatyk Street, Kyiv 01001. Directions and exact details are sent via email upon booking.
          </div>
        </div>
        <div class="faq-item">
          <button class="faq-question">
            Can I attend the class as part of a group?
            <span class="faq-toggle">+</span>
          </button>
          <div class="faq-answer">
            Absolutely! Groups of 3–8 receive a discounted rate of $40 per person. Perfect for hen parties, team events, or a birthday treat.
          </div>
        </div>
        <div class="faq-item">
          <button class="faq-question">
            How do I register for the masterclass?
            <span class="faq-toggle">+</span>
          </button>
          <div class="faq-answer">
            Simply click "Book Your Spot" on the workshops section, choose your date, and complete the checkout. You'll receive a confirmation within minutes.
          </div>
        </div>
        <div class="faq-item">
          <button class="faq-question">
            What should I bring to the masterclass?
            <span class="faq-toggle">+</span>
          </button>
          <div class="faq-answer">
            Just yourself and your enthusiasm! We provide everything. You may want to wear comfortable clothes as we'll be working with flowers and some soil.
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-top">
      <div class="footer-brand">
        <a href="#" class="nav-logo">VE<span style="font-style:italic;color:var(--blush-dark);">TS</span></a>
        <p>Kyiv's best floral boutique. Crafting moments of beauty since 2016.</p>
        <div class="social-row">
          <a href="#" class="social-btn">𝕏</a>
          <a href="#" class="social-btn">in</a>
          <a href="#" class="social-btn">ig</a>
          <a href="#" class="social-btn">yt</a>
        </div>
      </div>
      <div class="footer-col">
        <h5>Shop</h5>
        <ul>
          <li><a href="#">Bouquets</a></li>
          <li><a href="#">Subscriptions</a></li>
          <li><a href="#">Wedding</a></li>
          <li><a href="#">Corporate</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h5>Learn</h5>
        <ul>
          <li><a href="#">Workshops</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Flower Care</a></li>
          <li><a href="#">Seasonal Guide</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h5>Company</h5>
        <ul>
          <li><a href="#">About Us</a></li>
          <li><a href="#">Contact</a></li>
          <li><a href="#">Delivery</a></li>
          <li><a href="#">Returns</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2026 VETS KYIV. All rights reserved. @d1shalis</p>
      <p>Privacy · Terms · Cookies</p>
    </div>
  </footer>

  <script>
    // CURSOR
    const cursor = document.getElementById('cursor');
    const follower = document.getElementById('follower');
    let mx = 0, my = 0, fx = 0, fy = 0;

    document.addEventListener('mousemove', e => {
      mx = e.clientX; my = e.clientY;
      cursor.style.left = mx + 'px';
      cursor.style.top = my + 'px';
    });

    function animateFollower() {
      fx += (mx - fx) * 0.12;
      fy += (my - fy) * 0.12;
      follower.style.left = fx + 'px';
      follower.style.top = fy + 'px';
      requestAnimationFrame(animateFollower);
    }
    animateFollower();

    document.querySelectorAll('button, a, .product-card, .team-card, .agenda-item, .pill').forEach(el => {
      el.addEventListener('mouseenter', () => {
        cursor.style.transform = 'translate(-50%,-50%) scale(2.5)';
        cursor.style.background = 'var(--blush-dark)';
        follower.style.opacity = '0';
      });
      el.addEventListener('mouseleave', () => {
        cursor.style.transform = 'translate(-50%,-50%) scale(1)';
        cursor.style.background = 'var(--dark)';
        follower.style.opacity = '0.5';
      });
    });

    // SCROLL REVEAL
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach((e, i) => {
        if (e.isIntersecting) {
          e.target.style.transitionDelay = (i % 3) * 0.1 + 's';
          e.target.classList.add('visible');
        }
      });
    }, { threshold: 0.1 });
    reveals.forEach(el => observer.observe(el));

    // FILTER PILLS
    document.querySelectorAll('.pill').forEach(pill => {
      pill.addEventListener('click', () => {
        document.querySelectorAll('.pill').forEach(p => p.classList.remove('active'));
        pill.classList.add('active');
      });
    });

    // FAQ ACCORDION
    document.querySelectorAll('.faq-question').forEach(btn => {
      btn.addEventListener('click', () => {
        const item = btn.parentElement;
        const isOpen = item.classList.contains('open');
        document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
        if (!isOpen) item.classList.add('open');
      });
    });

    // AGENDA ITEMS
    document.querySelectorAll('.agenda-item').forEach(item => {
      item.addEventListener('click', () => {
        document.querySelectorAll('.agenda-item').forEach(i => i.classList.remove('active'));
        item.classList.add('active');
      });
    });

    // PETAL RAIN (occasional)
    function dropPetal() {
      const petal = document.createElement('div');
      petal.className = 'petal';
      petal.textContent = ['🌸','🌺','🌷','🌼','💮'][Math.floor(Math.random()*5)];
      petal.style.left = Math.random() * 100 + 'vw';
      petal.style.top = '-30px';
      const dur = 4 + Math.random() * 4;
      petal.style.animationDuration = dur + 's';
      document.body.appendChild(petal);
      setTimeout(() => petal.remove(), dur * 1000);
    }
    setInterval(dropPetal, 1800);

    // COUNTER ANIMATION
    function animateCounter(el, target) {
      let start = 0;
      const duration = 1500;
      const step = timestamp => {
        if (!step.startTime) step.startTime = timestamp;
        const progress = Math.min((timestamp - step.startTime) / duration, 1);
        const val = Math.floor(progress * target);
        el.textContent = val + (el.dataset.suffix || '');
        if (progress < 1) requestAnimationFrame(step);
        else el.textContent = target + (el.dataset.suffix || '');
      };
      requestAnimationFrame(step);
    }

    const statsObserver = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.querySelectorAll('.stat-num').forEach(el => {
            const text = el.textContent;
            const num = parseInt(text);
            const suffix = text.replace(num, '');
            el.dataset.suffix = suffix;
            animateCounter(el, num);
          });
          statsObserver.unobserve(e.target);
        }
      });
    }, { threshold: 0.5 });

    const statsSection = document.querySelector('.hero-stats');
    if (statsSection) statsObserver.observe(statsSection);
  </script>
</body>
</html>
