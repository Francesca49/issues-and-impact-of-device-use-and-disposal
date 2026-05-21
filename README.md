<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Issues and Impacts</title>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@200;300;400;600;700;900&family=Nunito+Sans:wght@300;400;600;700&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --deep:    #020b18;
      --mid:     #041428;
      --glass:   rgba(6, 28, 58, 0.55);
      --glass2:  rgba(10, 40, 80, 0.4);
      --b1:      #0a84ff;
      --b2:      #38bdf8;
      --b3:      #bae6fd;
      --b4:      #f0f8ff;
      --muted:   #a8c8e8;
      --border:  rgba(56,189,248,0.18);
      --glow:    0 0 30px rgba(10,132,255,0.4);
      --glow2:   0 0 60px rgba(10,132,255,0.15);
    }

    *, *::before, *::after { box-sizing: border-box; margin:0; padding:0; }
    html { scroll-behavior: auto; }

    body {
      background: var(--deep);
      color: var(--b4);
      font-family: 'Nunito', sans-serif;
      overflow-x: hidden;
    }

    body::before {
      content:'';
      position:fixed; inset:0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
      background-size: 200px 200px;
      pointer-events:none; z-index:0; opacity:0.5;
    }

    nav {
      position: fixed; top:0; left:0; right:0; z-index:200;
      display:flex; align-items:center; justify-content:space-between;
      padding: 1.2rem 4rem;
      background: rgba(2,11,24,0.7);
      backdrop-filter: blur(20px) saturate(180%);
      border-bottom: 1px solid var(--border);
    }

    .logo {
      font-family: 'Nunito', sans-serif;
      font-size:1.1rem; letter-spacing:4px;
      color: var(--b2);
      text-shadow: 0 0 20px rgba(56,189,248,0.6);
      text-decoration:none;
    }

    nav ul { list-style:none; display:flex; gap:2.5rem; }
    nav ul a {
      font-size:0.78rem; letter-spacing:3px; text-transform:uppercase;
      color:var(--muted); text-decoration:none; transition: color 0.25s;
    }
    nav ul a:hover { color:var(--b2); }

    .nav-pill {
      font-family:'Nunito', sans-serif;
      font-size:0.72rem; letter-spacing:2px;
      color:var(--deep); background:var(--b1);
      border:none; padding:0.55rem 1.4rem;
      border-radius:100px; cursor:pointer;
      box-shadow: 0 0 20px rgba(10,132,255,0.5);
      transition: background 0.2s, box-shadow 0.2s;
    }
    .nav-pill:hover { background:var(--b2); box-shadow:0 0 30px rgba(56,189,248,0.6); }

    .panel {
      position:relative; z-index:1;
      min-height:100vh;
      display:flex; flex-direction:column;
      align-items:center; justify-content:center;
      scroll-snap-align: start;
      overflow:hidden;
      padding: 6rem 2rem;
    }

    /* HERO */
    #hero {
      text-align:center;
      background:
        radial-gradient(ellipse 80% 60% at 50% 0%, rgba(10,132,255,0.18) 0%, transparent 70%),
        radial-gradient(ellipse 50% 40% at 80% 100%, rgba(56,189,248,0.1) 0%, transparent 60%),
        var(--deep);
    }

    .rings { position:absolute; inset:0; pointer-events:none; overflow:hidden; }
    .ring {
      position:absolute; border-radius:50%;
      border: 1px solid rgba(56,189,248,0.1);
      animation: ringPulse 6s ease-in-out infinite;
    }
    .ring:nth-child(1){ width:400px;height:400px;top:50%;left:50%;transform:translate(-50%,-50%); animation-delay:0s;}
    .ring:nth-child(2){ width:650px;height:650px;top:50%;left:50%;transform:translate(-50%,-50%); animation-delay:1.5s;}
    .ring:nth-child(3){ width:950px;height:950px;top:50%;left:50%;transform:translate(-50%,-50%); animation-delay:3s;}
    .ring:nth-child(4){ width:1300px;height:1300px;top:50%;left:50%;transform:translate(-50%,-50%); animation-delay:4.5s;}

    @keyframes ringPulse {
      0%,100%{ opacity:0.6; transform:translate(-50%,-50%) scale(1);}
      50%{ opacity:0.15; transform:translate(-50%,-50%) scale(1.04);}
    }

    .shield-wrap {
      position:relative; margin-bottom:2.5rem;
      opacity:0; animation: fadeUp 1s 0.2s forwards;
    }
    .shield-svg {
      width:110px; height:110px;
      filter: drop-shadow(0 0 30px rgba(10,132,255,0.7)) drop-shadow(0 0 60px rgba(56,189,248,0.3));
      animation: float 4s ease-in-out infinite;
    }
    @keyframes float { 0%,100%{transform:translateY(0);} 50%{transform:translateY(-12px);} }

    .hero-eyebrow {
      font-family:'Nunito', sans-serif;
      font-size:0.72rem; letter-spacing:6px; color:var(--b2);
      text-transform:uppercase; margin-bottom:1.2rem;
      opacity:0; animation:fadeUp 0.8s 0.5s forwards;
    }

    #hero h1 {
      font-size: clamp(3rem,10vw,7.5rem);
      font-weight:900; line-height:0.95;
      letter-spacing:-2px; margin-bottom:1.5rem;
      opacity:0; animation:fadeUp 0.9s 0.7s forwards;
    }

    #hero h1 em {
      font-style:normal;
      background: linear-gradient(135deg, var(--b1) 0%, var(--b2) 50%, var(--b3) 100%);
      -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;
      filter: drop-shadow(0 0 20px rgba(56,189,248,0.4));
    }

    .hero-sub {
      font-size:1.05rem; font-weight:300; line-height:1.9;
      color:var(--b3); max-width:520px; margin:0 auto 2.5rem;
      opacity:0; animation:fadeUp 0.9s 0.9s forwards;
    }

    .hero-btns {
      display:flex; gap:1.2rem; justify-content:center;
      opacity:0; animation:fadeUp 0.9s 1.1s forwards;
    }

    .btn-glow {
      font-family:'Nunito', sans-serif;
      font-size:0.78rem; letter-spacing:2px; text-transform:uppercase;
      color:var(--deep); background: linear-gradient(135deg,var(--b1),var(--b2));
      border:none; padding:1rem 2.4rem; border-radius:100px;
      cursor:pointer; text-decoration:none;
      box-shadow: 0 0 30px rgba(10,132,255,0.5), 0 4px 20px rgba(0,0,0,0.3);
      transition: all 0.25s;
    }
    .btn-glow:hover {
      box-shadow: 0 0 50px rgba(56,189,248,0.7), 0 4px 30px rgba(0,0,0,0.4);
      transform:translateY(-2px);
    }

    .btn-ghost {
      font-family:'Nunito', sans-serif;
      font-size:0.78rem; letter-spacing:2px; text-transform:uppercase;
      color:var(--b2); background:transparent;
      border:1px solid rgba(56,189,248,0.35);
      padding:1rem 2.4rem; border-radius:100px;
      cursor:pointer; text-decoration:none;
      backdrop-filter:blur(10px); transition: all 0.25s;
    }
    .btn-ghost:hover {
      border-color:var(--b2); background:rgba(56,189,248,0.08);
      box-shadow: 0 0 20px rgba(56,189,248,0.2);
    }

    .stats-row {
      display:flex; gap:1px; background:var(--border);
      border:1px solid var(--border); border-radius:16px; overflow:hidden;
      margin-top:4rem; width:100%; max-width:800px;
      opacity:0; animation:fadeUp 1s 1.3s forwards;
      backdrop-filter:blur(20px);
    }
    .stat-box {
      flex:1; background:var(--glass); padding:1.8rem 1rem; text-align:center;
      transition:background 0.3s;
    }
    .stat-box:hover { background:rgba(10,132,255,0.1); }
    .stat-n {
      font-family:'Nunito', sans-serif; font-size:1.8rem;
      color:var(--b2); text-shadow:0 0 20px rgba(56,189,248,0.5);
    }
    .stat-l {
      font-size:0.68rem; letter-spacing:2px; color:var(--muted);
      text-transform:uppercase; margin-top:0.4rem;
    }

    /* THREATS */
    #threats {
      background:
        radial-gradient(ellipse 60% 50% at 0% 50%, rgba(10,132,255,0.1) 0%, transparent 60%),
        var(--mid);
    }

    .section-inner { width:100%; max-width:1200px; margin:0 auto; }
    .section-head { margin-bottom:3.5rem; }

    .eyebrow {
      font-family:'Nunito', sans-serif;
      font-size:0.68rem; letter-spacing:5px; color:var(--b1);
      text-transform:uppercase; margin-bottom:1rem;
      display:flex; align-items:center; gap:0.8rem;
    }
    .eyebrow::before {
      content:''; display:block; width:30px; height:1px;
      background:var(--b1); box-shadow:0 0 8px var(--b1);
    }

    .section-head h2 {
      font-size:clamp(2rem,5vw,3.8rem);
      font-weight:900; line-height:1.05; letter-spacing:-1px;
    }
    .section-head h2 span {
      background: linear-gradient(90deg, var(--b1), var(--b3));
      -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;
    }
    .section-desc {
      font-size:1rem; font-weight:300; color:var(--b3);
      line-height:1.9; max-width:500px; margin-top:1rem;
    }

    .threat-panels {
      display:grid; grid-template-columns: repeat(3, 1fr); gap:1.5rem;
    }

    .tcard {
      background: var(--glass);
      border:1px solid var(--border); border-radius:20px;
      padding:2.5rem 2rem;
      backdrop-filter:blur(20px) saturate(150%);
      position:relative; overflow:hidden;
      transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
      cursor:default;
    }
    .tcard::before {
      content:''; position:absolute; inset:0;
      background: radial-gradient(circle at 30% 20%, rgba(10,132,255,0.12) 0%, transparent 60%);
      opacity:0; transition:opacity 0.4s;
    }
    .tcard:hover { transform:translateY(-6px); box-shadow:var(--glow2); border-color:rgba(56,189,248,0.4); }
    .tcard:hover::before { opacity:1; }

    .tcard-bar {
      position:absolute; top:0; left:0; right:0; height:2px;
      background:linear-gradient(90deg, transparent, var(--b1), var(--b2), transparent);
      opacity:0; transition:opacity 0.3s;
    }
    .tcard:hover .tcard-bar { opacity:1; }

    .tcard-icon { font-size:2.8rem; margin-bottom:1.5rem; filter:drop-shadow(0 0 12px rgba(56,189,248,0.5)); }
    .tcard h3 { font-size:1.05rem; font-weight:700; letter-spacing:0.5px; margin-bottom:0.8rem; color:var(--b3); }
    .tcard p { font-size:0.88rem; font-weight:300; line-height:1.8; color:var(--b3); }
    .tcard-badge {
      display:inline-block; margin-top:1.5rem;
      font-family:'Nunito', sans-serif; font-size:0.6rem; letter-spacing:2px;
      padding:0.3rem 0.9rem; border-radius:100px;
      background:rgba(10,132,255,0.15); border:1px solid rgba(10,132,255,0.35);
      color:var(--b2); text-transform:uppercase;
    }

    /* PRACTICES */
    #practices {
      background:
        radial-gradient(ellipse 50% 70% at 100% 50%, rgba(56,189,248,0.08) 0%, transparent 60%),
        var(--deep);
    }

    .practices-layout {
      display:grid; grid-template-columns:1fr 1.2fr; gap:5rem; align-items:center;
      width:100%; max-width:1200px;
    }

    .plist { display:flex; flex-direction:column; gap:1rem; }

    .pitem {
      display:flex; gap:1.5rem; align-items:flex-start;
      background:var(--glass); border:1px solid var(--border);
      border-radius:16px; padding:1.6rem 1.8rem;
      backdrop-filter:blur(16px);
      transition: border-color 0.3s, background 0.3s, transform 0.3s; cursor:default;
    }
    .pitem:hover {
      border-color:rgba(56,189,248,0.45); background:rgba(10,132,255,0.08);
      transform:translateX(6px);
    }
    .pnum {
      font-family:'Nunito', sans-serif; font-size:0.65rem; color:var(--b1);
      min-width:24px; padding-top:3px; text-shadow:0 0 10px var(--b1);
    }
    .pitem h4 { font-size:0.95rem; font-weight:700; color:var(--b3); margin-bottom:0.35rem; }
    .pitem p { font-size:0.85rem; font-weight:300; line-height:1.7; color:var(--b3); }

    .glass-visual {
      background:var(--glass2); border:1px solid var(--border);
      border-radius:24px; padding:2.5rem;
      backdrop-filter:blur(30px) saturate(160%);
      position:relative; overflow:hidden;
      box-shadow: var(--glow2), inset 0 1px 0 rgba(255,255,255,0.05);
    }
    .glass-visual::before {
      content:''; position:absolute; top:-50%; left:-50%;
      width:200%; height:200%;
      background: conic-gradient(from 0deg at 50% 50%,
        transparent 0deg, rgba(10,132,255,0.04) 60deg, transparent 120deg);
      animation: spinSlow 12s linear infinite;
    }
    @keyframes spinSlow { to { transform:rotate(360deg); } }

    .vis-title {
      font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:3px; color:var(--b2);
      text-transform:uppercase; margin-bottom:2rem;
      display:flex; align-items:center; gap:0.8rem;
    }
    .vis-dot {
      width:8px; height:8px; border-radius:50%; background:var(--b1);
      box-shadow:0 0 10px var(--b1); animation:pulse 2s ease-in-out infinite;
    }
    @keyframes pulse { 0%,100%{transform:scale(1);} 50%{transform:scale(1.4);} }

    .vis-bars { display:flex; flex-direction:column; gap:1rem; }
    .vis-bar-row { display:flex; align-items:center; gap:1rem; }
    .vis-bar-label { font-size:0.8rem; color:var(--muted); min-width:130px; font-weight:300; }
    .vis-bar-track { flex:1; height:6px; background:rgba(255,255,255,0.06); border-radius:100px; overflow:hidden; }
    .vis-bar-fill {
      height:100%; border-radius:100px;
      background:linear-gradient(90deg, var(--b1), var(--b2));
      box-shadow:0 0 10px rgba(10,132,255,0.5);
      width:0; transition:width 1.5s cubic-bezier(0.4,0,0.2,1);
    }
    .vis-bar-pct { font-family:'Nunito', sans-serif; font-size:0.7rem; color:var(--b2); min-width:36px; text-align:right; }

    .vis-divider { height:1px; background:var(--border); margin:1.8rem 0; }

    .vis-metrics { display:grid; grid-template-columns:1fr 1fr; gap:1rem; }
    .vis-metric {
      background:rgba(10,132,255,0.07); border:1px solid rgba(10,132,255,0.2);
      border-radius:12px; padding:1rem 1.2rem; text-align:center;
    }
    .vm-val {
      font-family:'Nunito', sans-serif; font-size:1.4rem; color:var(--b2);
      display:block; text-shadow:0 0 15px rgba(56,189,248,0.4);
    }
    .vm-lbl { font-size:0.68rem; letter-spacing:1px; color:var(--muted); text-transform:uppercase; margin-top:0.3rem; }

    /* TOOLS */
    #tools {
      background:
        radial-gradient(ellipse 70% 50% at 50% 100%, rgba(10,132,255,0.12) 0%, transparent 60%),
        var(--mid);
    }

    .tools-grid {
      display:grid; grid-template-columns:repeat(3,1fr); gap:1.5rem;
      width:100%; max-width:1000px; margin-top:3.5rem;
    }

    .toolcard {
      background:var(--glass); border:1px solid var(--border);
      border-radius:20px; padding:2.2rem 1.8rem;
      backdrop-filter:blur(20px); text-align:center;
      position:relative; overflow:hidden; transition:all 0.3s;
    }
    .toolcard::after {
      content:''; position:absolute; bottom:0; left:50%; transform:translateX(-50%);
      width:60%; height:1px;
      background:linear-gradient(90deg,transparent,var(--b1),transparent);
      opacity:0; transition:opacity 0.3s;
    }
    .toolcard:hover { transform:translateY(-5px); box-shadow:var(--glow2); border-color:rgba(56,189,248,0.4); }
    .toolcard:hover::after { opacity:1; }

    .tool-glyph { font-size:2.8rem; margin-bottom:1.2rem; filter:drop-shadow(0 0 10px rgba(56,189,248,0.4)); }
    .toolcard h3 {
      font-family:'Nunito', sans-serif; font-size:0.85rem;
      letter-spacing:2px; color:var(--b2); margin-bottom:0.7rem; text-transform:uppercase;
    }
    .toolcard p { font-size:0.85rem; font-weight:300; color:var(--b3); line-height:1.7; }

    /* CTA */
    #cta {
      text-align:center;
      background:
        radial-gradient(ellipse 80% 80% at 50% 50%, rgba(10,132,255,0.15) 0%, transparent 70%),
        var(--deep);
    }

    #cta h2 {
      font-size:clamp(2.5rem,7vw,5rem); font-weight:900;
      line-height:1; letter-spacing:-1px; margin-bottom:1.5rem;
    }
    #cta h2 em {
      font-style:normal;
      background:linear-gradient(135deg,var(--b1),var(--b2),var(--b3));
      -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;
    }
    #cta p { font-size:1rem; font-weight:300; color:var(--muted); margin-bottom:2.5rem; }

    .cta-orb {
      position:absolute; width:600px; height:600px; border-radius:50%;
      background:radial-gradient(circle, rgba(10,132,255,0.2) 0%, transparent 70%);
      pointer-events:none; animation:orbPulse 5s ease-in-out infinite;
    }
    @keyframes orbPulse { 0%,100%{transform:scale(1);opacity:0.6;} 50%{transform:scale(1.1);opacity:1;} }

    footer {
      position:relative; z-index:1;
      background:rgba(2,11,24,0.9); border-top:1px solid var(--border);
      padding:1.8rem 4rem;
      display:flex; align-items:center; justify-content:space-between;
      backdrop-filter:blur(20px);
    }
    .footer-copy {
      font-family:'Nunito', sans-serif; font-size:0.62rem;
      letter-spacing:2px; color:var(--muted); text-transform:uppercase;
    }

    /* ── AI ENERGY CALCULATOR ── */
    .ai-calc { max-width:620px; background:var(--glass); border:1px solid var(--border); border-radius:20px; padding:2rem; backdrop-filter:blur(20px); margin-bottom:2rem; }
    .calc-row { display:flex; align-items:center; justify-content:space-between; margin-bottom:1.4rem; gap:1rem; }
    .calc-label { font-size:0.85rem; font-weight:300; color:var(--b3); flex:1; }
    .calc-slider { flex:1; accent-color:var(--b1); cursor:pointer; }
    .calc-val { font-family:'Nunito', sans-serif; font-size:0.8rem; color:var(--b2); min-width:50px; text-align:right; }
    .calc-results { display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; margin-top:1.5rem; padding-top:1.5rem; border-top:1px solid var(--border); }
    .calc-result-box { background:rgba(10,132,255,0.08); border:1px solid rgba(56,189,248,0.2); border-radius:12px; padding:1rem; text-align:center; }
    .calc-result-val { font-family:'Nunito', sans-serif; font-size:1.1rem; color:var(--b2); display:block; text-shadow:0 0 12px rgba(56,189,248,0.4); }
    .calc-result-lbl { font-size:0.68rem; color:var(--muted); letter-spacing:1px; text-transform:uppercase; margin-top:0.3rem; }
    .calc-meter { height:8px; background:rgba(255,255,255,0.06); border-radius:100px; overflow:hidden; margin-top:1.5rem; }
    .calc-meter-fill { height:100%; border-radius:100px; background:linear-gradient(90deg,#4ade80,#facc15,#f87171); transition:width 0.5s ease; }
    .calc-impact-msg { font-size:0.82rem; color:var(--muted); margin-top:0.8rem; font-style:italic; min-height:1.2rem; }

    .hero-reference {
      font-family:'Nunito', sans-serif; font-size:0.58rem;
      letter-spacing:2px; color:var(--muted); opacity:0.65;
      text-transform:uppercase; margin-top:1.5rem;
      transition: opacity 0.3s;
    }
    .hero-reference:hover { opacity:1; }

    /* ── STREAK ── */
    #streak-bar { position:fixed; bottom:2rem; left:2rem; z-index:300; background:rgba(2,11,24,0.85); border:1px solid var(--border); border-radius:16px; padding:0.7rem 1.2rem; backdrop-filter:blur(16px); display:flex; align-items:center; gap:0.8rem; font-family:'Nunito', sans-serif; font-size:0.68rem; letter-spacing:1px; color:var(--muted); opacity:0; transform:translateY(10px); transition:all 0.4s; }
    #streak-bar.visible { opacity:1; transform:translateY(0); }
    .streak-flame { font-size:1.1rem; }
    #streak-count { color:var(--b2); font-size:0.9rem; }

    /* ── TOAST ── */
    #toast { position:fixed; top:5rem; right:2rem; z-index:500; background:rgba(10,132,255,0.15); border:1px solid rgba(56,189,248,0.5); border-radius:16px; padding:1rem 1.5rem; backdrop-filter:blur(20px); font-family:'Nunito', sans-serif; font-size:0.72rem; letter-spacing:1px; color:var(--b2); opacity:0; transform:translateX(20px); transition:all 0.4s; pointer-events:none; max-width:260px; }
    #toast.show { opacity:1; transform:translateX(0); }

    /* ── PROGRESS BAR ── */
    #reading-progress {
      position:fixed; top:0; left:0; height:3px; z-index:999;
      background:linear-gradient(90deg, var(--b1), var(--b2), var(--b3));
      width:0%; transition:width 0.1s linear;
      box-shadow:0 0 8px rgba(56,189,248,0.6);
    }

    /* ── BACK TO TOP ── */
    #back-to-top {
      position:fixed; bottom:2rem; right:2rem; z-index:300;
      width:44px; height:44px; border-radius:50%;
      background:rgba(10,132,255,0.2); border:1px solid rgba(56,189,248,0.4);
      color:var(--b2); font-size:1.1rem; cursor:pointer;
      display:flex; align-items:center; justify-content:center;
      backdrop-filter:blur(12px);
      opacity:0; transform:translateY(10px);
      transition:all 0.3s; pointer-events:none;
    }
    #back-to-top.visible {
      opacity:1; transform:translateY(0); pointer-events:all;
    }
    #back-to-top:hover {
      background:rgba(10,132,255,0.4); box-shadow:0 0 20px rgba(56,189,248,0.4);
      transform:translateY(-3px);
    }

    /* ── TOC VISITED ── */
    .toc-item.visited .toc-arrow { color:#4ade80; }
    .toc-item.visited .toc-num { color:#4ade80; }
    .toc-item.visited { border-left:2px solid rgba(74,222,128,0.4); }

    /* ── SECTION COUNTER ── */
    #section-counter {
      position:fixed; top:5rem; right:1.5rem; z-index:200;
      font-family:'Nunito', sans-serif; font-size:0.6rem;
      letter-spacing:2px; color:var(--muted);
      background:rgba(2,11,24,0.7); border:1px solid var(--border);
      border-radius:100px; padding:0.4rem 0.8rem;
      backdrop-filter:blur(12px);
      opacity:0; transition:opacity 0.3s;
    }
    #section-counter.visible { opacity:1; }

    .toc-quiz-locked {
      opacity:0.4; cursor:not-allowed !important;
    }
    .toc-quiz-locked.unlocked {
      opacity:1; cursor:pointer !important;
      border-top:1px solid rgba(56,189,248,0.3);
      background:rgba(10,132,255,0.06);
      animation: quizUnlock 0.6s ease forwards;
    }
    @keyframes quizUnlock {
      0%{ transform:translateX(0); box-shadow:none; }
      50%{ transform:translateX(8px); box-shadow:0 0 20px rgba(56,189,248,0.3); }
      100%{ transform:translateX(0); }
    }

    .toc-item {
      display:flex; align-items:center; gap:1.5rem;
      background:var(--glass); padding:1.3rem 2rem;
      cursor:pointer; transition: background 0.25s, transform 0.25s;
      text-align:left;
    }
    .toc-item:hover { background:rgba(10,132,255,0.1); transform:translateX(6px); }
    .toc-num {
      font-family:'Nunito', sans-serif; font-size:0.68rem;
      color:var(--b1); min-width:28px; text-shadow:0 0 10px var(--b1);
    }
    .toc-label {
      flex:1; font-size:1rem; font-weight:400; color:var(--b3); letter-spacing:0.3px;
    }
    .toc-arrow {
      font-family:'Nunito', sans-serif; font-size:0.9rem;
      color:var(--muted); transition:color 0.25s, transform 0.25s;
    }
    .toc-item:hover .toc-arrow { color:var(--b2); transform:translateX(4px); }

    /* ── MARQUEE PILLS ── */
    .marquee-wrap {
      width:520px; overflow:hidden; margin-top:2.5rem;
      opacity:0; animation: fadeUp 1s 1.1s forwards;
      mask-image: linear-gradient(90deg, transparent, black 15%, black 85%, transparent);
      -webkit-mask-image: linear-gradient(90deg, transparent, black 15%, black 85%, transparent);
    }
    .marquee-track {
      display:flex; gap:1rem; width:max-content;
      animation: marqueeScroll 10s linear infinite;
    }
    @keyframes marqueeScroll {
      0%   { transform: translateX(0); }
      100% { transform: translateX(-50%); }
    }
    .deco-pill {
      font-family:'Nunito', sans-serif; font-size:0.68rem; letter-spacing:2px;
      color:var(--b2); border:1px solid rgba(56,189,248,0.3);
      background:rgba(10,132,255,0.1); padding:0.45rem 1.1rem;
      border-radius:100px; white-space:nowrap;
      backdrop-filter:blur(10px);
      flex-shrink:0;
    }

    .content-bullets li.bullet-active {
      color:#e0f2fe !important;
      background:rgba(56,189,248,0.12) !important;
      border-color:rgba(186,230,253,0.5) !important;
      transform:translateX(10px) !important;
      box-shadow:0 0 20px rgba(56,189,248,0.15) !important;
    }
    .content-bullets li.bullet-active::before {
      background:var(--b3) !important;
      box-shadow:0 0 16px var(--b3) !important;
      transform:scale(1.6) !important;
      opacity:0 !important;
    }

    /* ── CONTENT BULLETS ── */
      list-style:none; display:flex; flex-direction:column; gap:0.6rem;
      max-width:640px; margin-bottom:2rem;
    }
    .content-bullets li {
      font-size:0.92rem; font-weight:300; color:var(--muted); line-height:1.7;
      padding:0.9rem 1.2rem 0.9rem 2.8rem; position:relative;
      border:1px solid transparent; border-radius:12px;
      background:transparent;
      cursor:pointer;
      transition: all 0.3s ease;
    }
    .content-bullets li::before {
      content:''; position:absolute; left:1rem; top:1.15em;
      width:7px; height:7px; border-radius:50%;
      background:var(--b1); box-shadow:0 0 8px var(--b1);
      transition: all 0.3s ease;
    }
    .content-bullets li:hover {
      color:var(--b3);
      background:rgba(10,132,255,0.07);
      border-color:rgba(56,189,248,0.25);
      transform:translateX(8px);
      box-shadow:0 0 20px rgba(10,132,255,0.08);
    }
    .content-bullets li:hover::before {
      background:var(--b2);
      box-shadow:0 0 14px var(--b2);
      transform:scale(1.4);
    }
    .mindmap-wrap {
      max-width:580px; margin-top:1rem;
      border:1px solid var(--border); border-radius:20px;
      background:rgba(6,28,58,0.4); padding:2rem 1.5rem 1.2rem;
      backdrop-filter:blur(16px);
    }
    .mindmap {
      position:relative; width:100%; height:280px;
    }
    .mm-center {
      position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
      width:140px; text-align:center;
      font-family:'Nunito', sans-serif; font-size:0.72rem; letter-spacing:1px;
      color:var(--b2); line-height:1.5;
      background:rgba(10,132,255,0.15);
      border:1px solid rgba(56,189,248,0.5);
      border-radius:50%; padding:1.4rem 0.8rem;
      box-shadow:0 0 30px rgba(10,132,255,0.25);
      animation: centerPulse 3s ease-in-out infinite;
      z-index:2;
    }
    @keyframes centerPulse {
      0%,100%{ box-shadow:0 0 20px rgba(10,132,255,0.2); }
      50%{ box-shadow:0 0 40px rgba(56,189,248,0.4); }
    }

    /* Branch lines as pseudo-elements on nodes */
    .mm-node { position:absolute; z-index:3; }
    .mm-tl { top:0;    left:0; }
    .mm-tr { top:0;    right:0; }
    .mm-bl { bottom:0; left:0; }
    .mm-br { bottom:0; right:0; }

    .mm-bubble {
      display:flex; flex-direction:column; align-items:center; gap:0.4rem;
      font-size:0.75rem; font-weight:300; color:var(--b3);
      background:rgba(10,132,255,0.08);
      border:1px solid rgba(56,189,248,0.2);
      border-radius:14px; padding:0.8rem 1rem;
      width:130px; text-align:center; line-height:1.5;
      cursor:pointer;
      transition: all 0.3s ease;
      position:relative;
    }
    .mm-icon { font-size:1.4rem; }

    .mm-line {
      position:absolute; background:none; pointer-events:none;
      border-top:1px dashed rgba(56,189,248,0.45);
      transform-origin:0 0;
      transition: opacity 0.3s;
    }
    .mm-line-tl { width:85px; top:38px; left:128px; transform:rotate(32deg); }
    .mm-line-tr { width:85px; top:38px; right:128px; transform:rotate(-32deg); transform-origin:100% 0; }
    .mm-line-bl { width:85px; bottom:38px; left:128px; transform:rotate(-32deg); }
    .mm-line-br { width:85px; bottom:38px; right:128px; transform:rotate(32deg); transform-origin:100% 0; }

    /* Hide lines when node is hovered or active to prevent overlap */
    .mm-node:hover .mm-line,
    .mm-node.mm-active .mm-line { opacity:0; }

    /* Active / hover states */
    .mm-node:hover .mm-bubble,
    .mm-node.mm-active .mm-bubble {
      color:var(--b3);
      background:rgba(10,132,255,0.18);
      border-color:rgba(56,189,248,0.55);
      transform:scale(1.08);
      box-shadow:0 0 20px rgba(10,132,255,0.25);
    }
    .mm-node.mm-active .mm-bubble {
      border-color:var(--b2);
      box-shadow:0 0 30px rgba(56,189,248,0.4);
    }
    .mm-node.mm-active .mm-line,
    .mm-node:hover .mm-line {
      border-top-color:rgba(56,189,248,0.7);
    }

    .next-btn {
      font-family:'Nunito', sans-serif; font-size:0.75rem; letter-spacing:2px;
      color:var(--deep); background:linear-gradient(135deg,var(--b1),var(--b2));
      border:none; padding:0.8rem 1.8rem; border-radius:100px;
      cursor:pointer; display:inline-flex; align-items:center; gap:0.5rem;
      box-shadow:0 0 20px rgba(10,132,255,0.4);
      transition: all 0.25s;
    }
    .next-btn:hover {
      box-shadow:0 0 30px rgba(56,189,248,0.6);
      transform:translateX(4px);
    }

    .hl { color:#93c5fd; font-weight:500; }

    /* ── QUIZ ── */
    .quiz-card {
      display:none; flex-direction:column; gap:1.2rem;
      background:var(--glass); border:1px solid var(--border);
      border-radius:20px; padding:2rem;
      backdrop-filter:blur(20px);
      animation: cardIn 0.4s ease forwards;
    }
    .quiz-card.active { display:flex; }
    .quiz-num {
      font-family:'Nunito', sans-serif; font-size:0.65rem;
      letter-spacing:3px; color:var(--muted); text-transform:uppercase;
    }
    .quiz-q {
      font-size:1.05rem; font-weight:500; color:var(--b4); line-height:1.6;
    }
    .quiz-opts { display:flex; flex-direction:column; gap:0.6rem; }
    .quiz-opt {
      font-size:0.88rem; font-weight:300; color:var(--b3);
      background:rgba(10,132,255,0.05); border:1px solid var(--border);
      border-radius:12px; padding:0.8rem 1.2rem; text-align:left;
      cursor:pointer; transition:all 0.2s;
    }
    .quiz-opt:hover:not(:disabled) {
      background:rgba(10,132,255,0.12); border-color:rgba(56,189,248,0.4);
      color:var(--b3); transform:translateX(4px);
    }
    .quiz-opt:disabled { cursor:default; }
    .quiz-opt.quiz-correct {
      background:rgba(74,222,128,0.12); border-color:rgba(74,222,128,0.5);
      color:#4ade80;
    }
    .quiz-opt.quiz-wrong {
      background:rgba(248,113,113,0.12); border-color:rgba(248,113,113,0.5);
      color:#f87171;
    }
    .quiz-feedback {
      font-family:'Nunito', sans-serif; font-size:0.72rem;
      letter-spacing:1px; min-height:1rem;
    }
    .quiz-result-msg {
      font-size:1rem; color:var(--b3); margin-top:0.5rem;
    }

    /* ── PPT SLIDES ── */
    .ppt-slides { max-width:480px; margin-bottom:2rem; }
    .ppt-slide {
      display:none; flex-direction:column; align-items:center; text-align:center;
      gap:1rem; background:var(--glass); border:1px solid var(--border);
      border-radius:20px; padding:2.5rem 2rem;
      backdrop-filter:blur(20px);
      animation: cardIn 0.4s ease forwards;
    }
    .ppt-slide.active { display:flex; }
    .ppt-icon { font-size:3rem; filter:drop-shadow(0 0 12px rgba(56,189,248,0.4)); }
    .ppt-title {
      font-family:'Nunito', sans-serif; font-size:0.85rem;
      letter-spacing:2px; color:var(--b2); text-transform:uppercase;
    }
    .ppt-text {
      font-size:1rem; font-weight:300; color:#ffffff; line-height:1.8;
      max-width:380px;
    }
    .ppt-progress {
      width:100%; height:3px; background:rgba(255,255,255,0.06);
      border-radius:100px; overflow:hidden;
    }
    .ppt-bar {
      height:100%; border-radius:100px;
      background:linear-gradient(90deg,var(--b1),var(--b2));
      box-shadow:0 0 8px rgba(10,132,255,0.5);
      transition:width 0.5s ease;
    }
    .ppt-counter {
      font-family:'Nunito', sans-serif; font-size:0.62rem;
      letter-spacing:2px; color:var(--muted);
    }
    .ppt-nav {
      display:flex; align-items:center; justify-content:space-between;
      margin-top:1rem; gap:1rem;
    }

    .se-click-hint {
      font-family:'Nunito', sans-serif; font-size:0.68rem;
      letter-spacing:2px; color:var(--b2); text-align:center;
      padding:0.7rem; border-top:1px solid rgba(56,189,248,0.2);
      text-transform:uppercase; opacity:1;
      animation: hintPulse 2.5s ease-in-out infinite;
    }
    @keyframes hintPulse {
      0%,100%{ opacity:0.7; } 50%{ opacity:1; }
    }

    /* ── SOCIAL ENGINEERING TABLE ── */
    .se-table {
      max-width:680px; border:1px solid rgba(56,189,248,0.3);
      border-radius:16px; overflow:hidden;
      margin-bottom:2rem; backdrop-filter:blur(16px);
    }
    .se-header {
      display:grid; grid-template-columns:200px 1fr;
      background:rgba(10,132,255,0.18);
      border-bottom:1px solid rgba(56,189,248,0.2);
    }
    .se-head {
      font-family:'Nunito', sans-serif; font-size:0.72rem;
      letter-spacing:1px; color:var(--b2); font-weight:600;
      text-transform:uppercase; padding:0.9rem 1.2rem;
      border-right:1px solid rgba(56,189,248,0.2);
    }
    .se-head:last-child { border-right:none; }
    .se-row {
      display:grid; grid-template-columns:200px 1fr;
      border-bottom:1px solid rgba(56,189,248,0.1);
      cursor:pointer; transition:background 0.25s;
    }
    .se-row:last-child { border-bottom:none; }
    .se-row:hover { background:rgba(10,132,255,0.07); }
    .se-row.se-expanded { background:rgba(10,132,255,0.1); }
    .se-row.se-expanded .se-chevron { transform:rotate(180deg); }
    .se-row.se-expanded .se-technique { color:var(--b2); }
    .se-cell { padding:0.9rem 1.2rem; }
    .se-technique {
      font-weight:600; font-size:0.88rem; color:var(--b3);
      border-right:1px solid rgba(56,189,248,0.1);
      display:flex; align-items:center; gap:0.5rem;
      flex-wrap:wrap;
      transition:color 0.25s;
    }
    .se-icon { font-size:1.2rem; }
    .se-chevron {
      font-size:0.7rem; color:var(--muted); margin-left:auto;
      transition:transform 0.3s;
    }
    .se-detail {
      font-size:0.85rem; font-weight:300; color:var(--b3);
      line-height:1.7; max-height:0; overflow:hidden;
      transition:max-height 0.4s ease, padding 0.3s;
      padding-top:0; padding-bottom:0;
    }
    .se-row.se-expanded .se-detail {
      max-height:200px; padding-top:0.9rem; padding-bottom:0.9rem;
      color:var(--b4);
    }

    /* ── HACKER CARDS ── */
    .hackers-grid {
      display:grid; grid-template-columns:1fr 1fr; gap:1.2rem;
      max-width:580px; margin-bottom:2rem;
    }
    .hacker-card {
      border-radius:20px; padding:2rem 1.5rem;
      backdrop-filter:blur(20px); text-align:center;
      display:flex; flex-direction:column; align-items:center; gap:0.8rem;
      position:relative; overflow:hidden;
      transition: transform 0.3s, box-shadow 0.3s;
      cursor:default;
    }
    .hacker-card:hover { transform:translateY(-6px); }
    .black-hat {
      background:rgba(248,113,113,0.07);
      border:1px solid rgba(248,113,113,0.3);
    }
    .black-hat:hover { box-shadow:0 0 25px rgba(248,113,113,0.15); }
    .white-hat {
      background:rgba(74,222,128,0.07);
      border:1px solid rgba(74,222,128,0.3);
    }
    .white-hat:hover { box-shadow:0 0 25px rgba(74,222,128,0.15); }
    .hacker-icon { font-size:2.5rem; }
    .hacker-card h4 {
      font-family:'Nunito', sans-serif; font-size:0.75rem;
      letter-spacing:1px; text-transform:uppercase;
    }
    .black-hat h4 { color:#f87171; }
    .white-hat h4 { color:#4ade80; }
    .hacker-card p {
      font-size:0.85rem; font-weight:300; color:var(--b3); line-height:1.7;
    }

    /* ── INLINE LINK ── */
    .inline-link {
      font-family:'Nunito', sans-serif; font-size:0.72rem;
      letter-spacing:1px; color:var(--b2);
      text-decoration:none; border-bottom:1px solid rgba(56,189,248,0.4);
      padding-bottom:1px; margin-left:0.4rem;
      transition: color 0.2s, border-color 0.2s;
    }
    .inline-link:hover {
      color:var(--b3); border-color:var(--b3);
    }

    /* ── VIDEO LINK ── */
    .video-link-btn {
      display:inline-flex; align-items:center; gap:0.8rem;
      font-family:'Nunito', sans-serif; font-size:0.8rem; letter-spacing:2px;
      color:var(--deep); background:linear-gradient(135deg, var(--b1), var(--b2));
      padding:0.9rem 1.8rem; border-radius:100px; text-decoration:none;
      box-shadow:0 0 25px rgba(10,132,255,0.4);
      transition: all 0.25s; margin-bottom:1.5rem;
    }
    .video-link-btn:hover {
      box-shadow:0 0 40px rgba(56,189,248,0.6);
      transform:translateY(-2px);
    }

    /* ── NOTE BOX ── */
    .note-box {
      display:flex; align-items:flex-start; gap:1rem;
      max-width:600px; margin-top:1.5rem; margin-bottom:1.2rem;
      background:rgba(56,189,248,0.06);
      border:1px solid rgba(56,189,248,0.25);
      border-left:3px solid var(--b2);
      border-radius:12px; padding:1rem 1.2rem;
    }
    .note-icon {
      font-size:1.3rem; color:var(--b2);
      text-shadow:0 0 10px rgba(56,189,248,0.5);
      flex-shrink:0; margin-top:2px;
    }
    .note-box p {
      font-size:0.85rem; font-weight:300; color:var(--b3); line-height:1.7;
    }

    /* ── NUMBERED OFFENCES ── */
    .offences-list {
      list-style:none; display:flex; flex-direction:column; gap:0.8rem;
      max-width:640px; margin-bottom:2rem; counter-reset:offence;
    }
    .offences-list li {
      counter-increment:offence;
      font-size:0.92rem; font-weight:300; color:var(--b3); line-height:1.7;
      padding:0.9rem 1.2rem 0.9rem 3.5rem; position:relative;
      border:1px solid transparent; border-radius:12px;
      background:transparent; cursor:default;
      transition: all 0.3s ease;
    }
    .offences-list li::before {
      content:counter(offence, decimal-leading-zero);
      position:absolute; left:1rem; top:50%; transform:translateY(-50%);
      font-family:'Nunito', sans-serif; font-size:0.7rem;
      color:var(--b1); text-shadow:0 0 10px var(--b1);
      letter-spacing:1px;
    }
    .offences-list li:hover {
      color:var(--b3);
      background:rgba(10,132,255,0.07);
      border-color:rgba(56,189,248,0.25);
      transform:translateX(8px);
      box-shadow:0 0 20px rgba(10,132,255,0.08);
    }

    /* ── DPA TABLE ── */
    .dpa-table {
      max-width:640px; border:1px solid rgba(56,189,248,0.3);
      border-radius:16px; overflow:hidden;
      margin-bottom:2rem; backdrop-filter:blur(16px);
    }
    .dpa-row {
      display:grid; grid-template-columns:200px 1fr;
      border-bottom:1px solid rgba(56,189,248,0.12);
      transition: background 0.25s;
    }
    .dpa-row:last-child { border-bottom:none; }
    .dpa-row:not(.dpa-header):hover { background:rgba(10,132,255,0.07); }
    .dpa-header { background:rgba(10,132,255,0.18); }
    .dpa-cell {
      padding:0.9rem 1.2rem; font-size:0.85rem;
      font-weight:300; color:var(--b3); line-height:1.6;
      border-right:1px solid rgba(56,189,248,0.12);
    }
    .dpa-cell:last-child { border-right:none; }
    .dpa-head {
      font-family:'Nunito', sans-serif; font-size:0.72rem;
      letter-spacing:1px; color:var(--b2); font-weight:600;
      text-transform:uppercase;
    }
    .dpa-principle {
      font-weight:600; color:var(--b3); font-size:0.85rem;
    }

    /* ── OWNERSHIP GRID ── */
    .ownership-grid {
      display:grid; grid-template-columns:repeat(2,1fr); gap:1.2rem;
      max-width:640px; margin-bottom:2rem;
    }
    .ownership-card {
      background:var(--glass); border:1px solid var(--border);
      border-radius:18px; padding:1.8rem 1.5rem;
      backdrop-filter:blur(16px); position:relative; overflow:hidden;
      transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
      cursor:default;
    }
    .ownership-card::before {
      content:''; position:absolute; top:0; left:0; right:0; height:2px;
      background:linear-gradient(90deg, transparent, var(--b1), var(--b2), transparent);
      opacity:0; transition:opacity 0.3s;
    }
    .ownership-card:hover { transform:translateY(-5px); border-color:rgba(56,189,248,0.4); box-shadow:0 0 25px rgba(10,132,255,0.12); }
    .ownership-card:hover::before { opacity:1; }
    .ownership-num {
      font-family:'Nunito', sans-serif; font-size:1.4rem;
      color:var(--b1); opacity:0.6; margin-bottom:0.8rem;
      text-shadow:0 0 12px var(--b1);
    }
    .ownership-card p {
      font-size:0.85rem; font-weight:300; color:var(--b3); line-height:1.75;
    }

    /* ── SORT CARDS ── */
    .sort-cards {
      display:grid; grid-template-columns:repeat(2, 1fr); gap:1rem;
      max-width:640px; margin-bottom:1rem;
    }
    .sort-card {
      background:var(--glass); border:1px solid var(--border);
      border-radius:16px; padding:1.4rem;
      backdrop-filter:blur(16px);
      transition: border-color 0.3s;
    }
    .sort-card.card-correct { border-color:rgba(74,222,128,0.5); background:rgba(74,222,128,0.05); }
    .sort-card.card-wrong   { border-color:rgba(248,113,113,0.5); background:rgba(248,113,113,0.05); }
    .sort-label {
      font-family:'Nunito', sans-serif; font-size:0.72rem;
      letter-spacing:2px; color:var(--b2); text-transform:uppercase;
      margin-bottom:0.5rem;
    }
    .sort-desc {
      font-size:0.82rem; font-weight:300; color:var(--b3);
      line-height:1.6; margin-bottom:1rem;
    }
    .sort-btns { display:flex; gap:0.6rem; }
    .sort-btn {
      font-family:'Nunito', sans-serif; font-size:0.62rem; letter-spacing:1px;
      padding:0.4rem 0.8rem; border-radius:100px; cursor:pointer;
      border:1px solid; transition:all 0.2s; flex:1; text-align:center;
    }
    .benefit-btn { color:#4ade80; border-color:rgba(74,222,128,0.35); background:rgba(74,222,128,0.06); }
    .benefit-btn:hover:not(:disabled) { background:rgba(74,222,128,0.18); box-shadow:0 0 12px rgba(74,222,128,0.2); }
    .drawback-btn { color:#f87171; border-color:rgba(248,113,113,0.35); background:rgba(248,113,113,0.06); }
    .drawback-btn:hover:not(:disabled) { background:rgba(248,113,113,0.18); box-shadow:0 0 12px rgba(248,113,113,0.2); }
    .sort-btn:disabled { opacity:0.4; cursor:default; }
    .sort-result { font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:1px; margin-top:0.6rem; }

    .score-box {
      display:inline-flex; align-items:baseline; gap:0.8rem;
      background:rgba(10,132,255,0.1); border:1px solid rgba(56,189,248,0.3);
      border-radius:16px; padding:1rem 2rem; margin-bottom:1.5rem;
    }
    .score-num {
      font-family:'Nunito', sans-serif; font-size:2.5rem;
      color:var(--b2); text-shadow:0 0 20px rgba(56,189,248,0.5);
    }
    .score-label { font-size:0.85rem; color:var(--muted); }
    .correct-answers { display:flex; flex-direction:column; gap:0.5rem; max-width:400px; }
    .answer-row {
      display:flex; align-items:center; gap:1rem;
      background:rgba(10,132,255,0.05); border:1px solid var(--border);
      border-radius:10px; padding:0.5rem 1rem;
    }
    .ans-benefit { font-family:'Nunito', sans-serif; font-size:0.62rem; color:#4ade80; min-width:80px; }
    .ans-drawback { font-family:'Nunito', sans-serif; font-size:0.62rem; color:#f87171; min-width:80px; }
    .ans-topic { font-size:0.85rem; color:var(--b3); }

    /* ── IMPACT CARDS ── */
    .impact-cards {
      display:grid; grid-template-columns:repeat(3,1fr); gap:1.2rem;
      max-width:700px; margin-bottom:2rem;
    }
    .impact-card {
      background:var(--glass);
      border:1px solid var(--border);
      border-radius:20px; padding:2rem 1.5rem;
      backdrop-filter:blur(20px);
      display:flex; flex-direction:column; align-items:center; text-align:center;
      gap:1rem; position:relative; overflow:hidden;
      transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
      cursor:default;
    }
    .impact-card::before {
      content:''; position:absolute; top:0; left:0; right:0; height:2px;
      background:linear-gradient(90deg, transparent, var(--b1), var(--b2), transparent);
      opacity:0; transition:opacity 0.3s;
    }
    .impact-card:hover { transform:translateY(-8px); border-color:rgba(56,189,248,0.45); box-shadow:0 0 30px rgba(10,132,255,0.15); }
    .impact-card:hover::before { opacity:1; }
    .impact-icon { font-size:2.5rem; filter:drop-shadow(0 0 10px rgba(56,189,248,0.4)); }
    .impact-title {
      font-family:'Nunito', sans-serif; font-size:0.75rem;
      letter-spacing:1px; color:var(--b2); text-transform:uppercase;
    }
    .impact-text {
      font-size:0.85rem; font-weight:300; color:var(--b3); line-height:1.7;
    }

    /* ── FLASHCARDS ── */
    .flashcard-container {
      display:flex; flex-wrap:wrap; gap:1rem;
      max-width:640px; margin-bottom:2rem;
    }
    .flashcard {
      width:240px; height:200px;
      perspective:1000px; cursor:pointer;
    }
    .flashcard-inner {
      position:relative; width:100%; height:100%;
      transition:transform 0.6s cubic-bezier(0.4,0,0.2,1);
      transform-style:preserve-3d;
    }
    .flashcard.flipped .flashcard-inner { transform:rotateY(180deg); }
    .flashcard-front, .flashcard-back {
      position:absolute; inset:0;
      display:flex; flex-direction:column; align-items:center; justify-content:center;
      border-radius:16px; padding:1rem;
      backface-visibility:hidden;
      -webkit-backface-visibility:hidden;
    }
    .flashcard-front {
      background:rgba(10,132,255,0.1);
      border:1px solid rgba(56,189,248,0.3);
      gap:0.5rem;
      transition: border-color 0.3s, background 0.3s;
    }
    .flashcard:hover .flashcard-front {
      background:rgba(10,132,255,0.18);
      border-color:rgba(56,189,248,0.6);
      box-shadow:0 0 20px rgba(10,132,255,0.2);
    }
    .flashcard-back {
      background:linear-gradient(135deg, rgba(10,132,255,0.2), rgba(56,189,248,0.1));
      border:1px solid rgba(56,189,248,0.5);
      transform:rotateY(180deg);
      text-align:center;
    }
    .flashcard-back p {
      font-size:0.78rem; font-weight:300; color:#ffffff; line-height:1.6;
    }
    .fc-num {
      font-family:'Nunito', sans-serif; font-size:1.6rem;
      color:var(--b2); text-shadow:0 0 15px rgba(56,189,248,0.5);
    }
    .fc-hint {
      font-family:'Nunito', sans-serif; font-size:0.62rem;
      letter-spacing:2px; color:var(--b2); text-transform:uppercase;
      animation: hintPulse 2.5s ease-in-out infinite;
    }
    .fc-term {
      font-size:0.8rem; font-weight:600; color:var(--b3);
      text-align:center; line-height:1.4; padding:0 0.3rem;
    }

    /* ── FACT CARDS ── */
    .fact-cards { max-width:520px; margin-top:1.2rem; }
    .fact-card-wrap { position:relative; min-height:200px; }
    .fact-card {
      display:none; flex-direction:column; align-items:flex-start; gap:1rem;
      background:var(--glass); border:1px solid var(--border);
      border-radius:20px; padding:2rem;
      backdrop-filter:blur(20px);
      animation: cardIn 0.4s ease forwards;
    }
    .fact-card.active { display:flex; }
    @keyframes cardIn {
      from{ opacity:0; transform:translateY(12px); }
      to{ opacity:1; transform:translateY(0); }
    }
    .fact-icon { font-size:2.2rem; filter:drop-shadow(0 0 10px rgba(56,189,248,0.4)); }
    .fact-text {
      font-size:0.95rem; font-weight:300; color:#ffffff; line-height:1.8;
    }
    .fact-text strong { color:var(--b2); font-weight:600; }
    .fact-progress {
      width:100%; height:3px; background:rgba(255,255,255,0.06);
      border-radius:100px; overflow:hidden;
    }
    .fact-bar {
      height:100%; border-radius:100px;
      background:linear-gradient(90deg,var(--b1),var(--b2));
      box-shadow:0 0 8px rgba(10,132,255,0.5);
      transition:width 0.6s ease;
    }
    .fact-counter {
      font-family:'Nunito', sans-serif; font-size:0.62rem;
      letter-spacing:2px; color:var(--muted); align-self:flex-end;
    }
    .fact-nav {
      display:flex; align-items:center; justify-content:space-between;
      margin-top:1.2rem; gap:1rem;
    }
    .fact-btn {
      font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:2px;
      color:var(--b2); background:transparent;
      border:1px solid rgba(56,189,248,0.3);
      padding:0.5rem 1.2rem; border-radius:100px;
      cursor:pointer; transition:all 0.25s;
    }
    .fact-btn:hover:not(:disabled) {
      border-color:var(--b2); background:rgba(56,189,248,0.08);
      box-shadow:0 0 14px rgba(56,189,248,0.2);
    }
    .fact-btn:disabled { opacity:0.25; cursor:default; }
    .fact-dots { display:flex; gap:0.5rem; align-items:center; }
    .fact-dot {
      width:8px; height:8px; border-radius:50%;
      background:rgba(56,189,248,0.2); border:1px solid rgba(56,189,248,0.3);
      cursor:pointer; transition:all 0.25s;
    }
    .fact-dot.active {
      background:var(--b2); box-shadow:0 0 10px var(--b2); transform:scale(1.3);
    }

    .content-section {
      background:
        radial-gradient(ellipse 60% 50% at 30% 50%, rgba(10,132,255,0.1) 0%, transparent 60%),
        var(--mid);
    }
    .content-inner {
      width:100%; max-width:800px; z-index:1; position:relative;
    }
    .content-inner h2 {
      font-size:clamp(2rem,5vw,3.5rem); font-weight:900;
      letter-spacing:-1px; margin-bottom:1.2rem; line-height:1.1;
    }
    .content-inner h2 span {
      background:linear-gradient(90deg,var(--b1),var(--b3));
      -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;
    }
    .back-btn {
      margin-top:2.5rem;
      font-family:'Nunito', sans-serif; font-size:0.75rem; letter-spacing:2px;
      color:var(--b2); background:transparent;
      border:1px solid rgba(56,189,248,0.35);
      padding:0.8rem 1.8rem; border-radius:100px;
      cursor:pointer; display:inline-flex; align-items:center; gap:0.5rem;
      backdrop-filter:blur(10px);
      transition: all 0.25s;
    }
    .back-btn:hover {
      border-color:var(--b2); background:rgba(56,189,248,0.08);
      box-shadow:0 0 20px rgba(56,189,248,0.2);
      transform:translateX(-4px);
    }

    /* ── SCROLL INDICATOR ── */
    .scroll-indicator {
      position:absolute; bottom:2.5rem; left:calc(50% - 30px); transform:translateX(-50%);
      display:flex; flex-direction:column; align-items:center; gap:0.6rem;
      animation: fadeUp 1s 1.5s both;
    }
    .scroll-text {
      font-family:'Nunito', sans-serif; font-size:0.6rem; letter-spacing:4px;
      color:var(--muted); text-transform:uppercase;
    }
    .scroll-mouse {
      width:22px; height:36px; border:1px solid rgba(56,189,248,0.4);
      border-radius:11px; display:flex; justify-content:center; padding-top:6px;
    }
    .scroll-wheel {
      width:3px; height:7px; background:var(--b2); border-radius:2px;
      animation: scrollWheel 1.8s ease-in-out infinite;
      box-shadow: 0 0 6px var(--b2);
    }
    @keyframes scrollWheel {
      0%{ transform:translateY(0); opacity:1; }
      100%{ transform:translateY(12px); opacity:0; }
    }

    /* ── EXTRA BG DECORATIONS ── */
    .bg-grid {
      position:absolute; inset:0; pointer-events:none;
      background-image:
        linear-gradient(rgba(56,189,248,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(56,189,248,0.04) 1px, transparent 1px);
      background-size:60px 60px;
      mask-image:radial-gradient(ellipse 80% 80% at 50% 50%, black 20%, transparent 80%);
      -webkit-mask-image:radial-gradient(ellipse 80% 80% at 50% 50%, black 20%, transparent 80%);
    }

    .streak {
      position:absolute; pointer-events:none;
      width:1px; height:120px;
      background:linear-gradient(to bottom, transparent, rgba(56,189,248,0.4), transparent);
      animation:streakFall 4s ease-in-out infinite;
    }
    .streak-1 { left:20%; top:-20%; animation-delay:0s; transform:rotate(25deg); }
    .streak-2 { left:75%; top:-10%; animation-delay:1.5s; transform:rotate(20deg); height:80px; }
    .streak-3 { left:48%; top:-15%; animation-delay:3s; transform:rotate(15deg); height:100px; }
    @keyframes streakFall {
      0%  { opacity:0; transform:translateY(0) rotate(25deg); }
      20% { opacity:1; }
      80% { opacity:1; }
      100%{ opacity:0; transform:translateY(110vh) rotate(25deg); }
    }
    .streak-2 { animation-name:streakFall2; }
    @keyframes streakFall2 {
      0%  { opacity:0; transform:translateY(0) rotate(20deg); }
      20% { opacity:1; }
      80% { opacity:1; }
      100%{ opacity:0; transform:translateY(110vh) rotate(20deg); }
    }
    .streak-3 { animation-name:streakFall3; }
    @keyframes streakFall3 {
      0%  { opacity:0; transform:translateY(0) rotate(15deg); }
      20% { opacity:1; }
      80% { opacity:1; }
      100%{ opacity:0; transform:translateY(110vh) rotate(15deg); }
    }

    .corner-dot {
      position:absolute; width:5px; height:5px; border-radius:50%;
      background:var(--b1); box-shadow:0 0 10px var(--b1);
      animation:dotBlink 2.5s ease-in-out infinite;
    }
    @keyframes dotBlink {
      0%,100%{ opacity:0.3; transform:scale(1); }
      50%{ opacity:1; transform:scale(1.5); }
    }

    .data-label {
      position:absolute; pointer-events:none;
      font-family:'Nunito', sans-serif; font-size:0.58rem;
      letter-spacing:2px; color:var(--b1); opacity:0.35;
      animation:labelFlicker 5s ease-in-out infinite;
    }
    @keyframes labelFlicker {
      0%,100%{ opacity:0.25; }
      40%{ opacity:0.6; }
      42%{ opacity:0.2; }
      44%{ opacity:0.6; }
      80%{ opacity:0.4; }
    }

    /* ── DECORATIVE ELEMENTS ── */
    .particles { position:absolute; inset:0; pointer-events:none; }
    .particle {
      position:absolute; border-radius:50%;
      background:var(--b2);
      box-shadow:0 0 6px var(--b2);
      animation: particleDrift 5s ease-in-out infinite;
    }
    @keyframes particleDrift {
      0%,100%{ transform:translateY(0) scale(1); opacity:0.4; }
      50%{ transform:translateY(-18px) scale(1.3); opacity:1; }
    }

    /* Corner brackets */
    .corner-deco {
      position:absolute; width:40px; height:40px; pointer-events:none;
    }
    .corner-tl { top:6rem; left:2rem; border-top:1px solid var(--b1); border-left:1px solid var(--b1); }
    .corner-tr { top:6rem; right:2rem; border-top:1px solid var(--b1); border-right:1px solid var(--b1); }
    .corner-bl { bottom:2rem; left:2rem; border-bottom:1px solid var(--b1); border-left:1px solid var(--b1); }
    .corner-br { bottom:2rem; right:2rem; border-bottom:1px solid var(--b1); border-right:1px solid var(--b1); }

    /* Side floating tags */
    .side-tag {
      position:absolute; top:50%; transform:translateY(-50%);
      display:flex; flex-direction:column; align-items:center; gap:0.6rem;
      pointer-events:none;
    }
    .side-left { left:2.5rem; }
    .side-right { right:2.5rem; }
    .side-tag-line {
      display:block; width:1px; height:50px;
      background:linear-gradient(to bottom, transparent, var(--b1), transparent);
    }
    .side-tag-text {
      font-family:'Nunito', sans-serif; font-size:0.55rem; letter-spacing:3px;
      color:var(--muted); text-transform:uppercase;
      writing-mode:vertical-rl; text-orientation:mixed;
    }

    /* Background orbs */
    .hero-orb {
      position:absolute; border-radius:50%; pointer-events:none;
      animation:orbDrift 8s ease-in-out infinite;
    }
    .orb-l {
      width:350px; height:350px; top:10%; left:-80px;
      background:radial-gradient(circle, rgba(10,132,255,0.12) 0%, transparent 70%);
      animation-delay:0s;
    }
    .orb-r {
      width:280px; height:280px; bottom:5%; right:-60px;
      background:radial-gradient(circle, rgba(56,189,248,0.1) 0%, transparent 70%);
      animation-delay:3s;
    }
    @keyframes orbDrift {
      0%,100%{ transform:translate(0,0); }
      50%{ transform:translate(20px,-20px); }
    }

    /* Scan line sweep */
    .scan-line {
      position:absolute; left:0; right:0; height:1px;
      background:linear-gradient(90deg, transparent, rgba(56,189,248,0.4), transparent);
      pointer-events:none;
      animation:scanSweep 5s ease-in-out infinite;
      top:0;
    }
    @keyframes scanSweep {
      0%{ top:0%; opacity:0; }
      10%{ opacity:1; }
      90%{ opacity:1; }
      100%{ top:100%; opacity:0; }
    }

    @keyframes fadeUp {
      from{opacity:0;transform:translateY(24px);}
      to{opacity:1;transform:translateY(0);}
    }
    .reveal { opacity:0; transform:translateY(32px); transition: opacity 0.8s, transform 0.8s; }
    .reveal.in { opacity:1; transform:none; }

    @media(max-width:900px){
      .threat-panels, .tools-grid { grid-template-columns:1fr; }
      .practices-layout { grid-template-columns:1fr; gap:2.5rem; }
      nav ul { display:none; }
      nav { padding:1rem 1.5rem; }
      footer { flex-direction:column; gap:0.8rem; text-align:center; padding:1.5rem; }
    }
  </style>
</head>
<body>

<div id="reading-progress"></div>
<div id="back-to-top" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</div>
<div id="section-counter"></div>
<div id="streak-bar"><span class="streak-flame">🔥</span><span>Topics visited:</span><span id="streak-count">0 / 12</span></div>
<div id="toast"></div>

<nav>
  <a class="logo" href="#">NX·SEC</a>
</nav>

<!-- HERO -->
<section class="panel" id="hero">
  <div class="rings">
    <div class="ring"></div><div class="ring"></div>
    <div class="ring"></div><div class="ring"></div>
  </div>

  <!-- Floating particles -->
  <div class="particles">
    <div class="particle" style="left:8%;top:20%;animation-delay:0s;width:3px;height:3px;"></div>
    <div class="particle" style="left:15%;top:70%;animation-delay:1.2s;width:2px;height:2px;"></div>
    <div class="particle" style="left:25%;top:40%;animation-delay:2.4s;width:4px;height:4px;"></div>
    <div class="particle" style="left:80%;top:25%;animation-delay:0.6s;width:2px;height:2px;"></div>
    <div class="particle" style="left:88%;top:60%;animation-delay:1.8s;width:3px;height:3px;"></div>
    <div class="particle" style="left:72%;top:80%;animation-delay:3s;width:2px;height:2px;"></div>
    <div class="particle" style="left:92%;top:40%;animation-delay:0.9s;width:4px;height:4px;"></div>
    <div class="particle" style="left:5%;top:55%;animation-delay:2s;width:3px;height:3px;"></div>
    <div class="particle" style="left:40%;top:10%;animation-delay:1.5s;width:2px;height:2px;"></div>
    <div class="particle" style="left:60%;top:88%;animation-delay:0.3s;width:3px;height:3px;"></div>
    <div class="particle" style="left:33%;top:85%;animation-delay:2.8s;width:2px;height:2px;"></div>
    <div class="particle" style="left:68%;top:12%;animation-delay:1.1s;width:4px;height:4px;"></div>
  </div>

  <!-- Floating grid lines -->
  <div class="bg-grid"></div>

  <!-- Diagonal streaks -->
  <div class="streak streak-1"></div>
  <div class="streak streak-2"></div>
  <div class="streak streak-3"></div>

  <!-- Corner decorations -->
  <div class="corner-deco corner-tl"></div>
  <div class="corner-deco corner-tr"></div>
  <div class="corner-deco corner-bl"></div>
  <div class="corner-deco corner-br"></div>

  <!-- Extra corner dots -->
  <div class="corner-dot" style="top:6.5rem;left:2.6rem;"></div>
  <div class="corner-dot" style="top:6.5rem;right:2.6rem;"></div>
  <div class="corner-dot" style="bottom:2.6rem;left:2.6rem;"></div>
  <div class="corner-dot" style="bottom:2.6rem;right:2.6rem;"></div>

  <!-- Side floating tags -->
  <div class="side-tag side-left">
    <span class="side-tag-line"></span>
    <span class="side-tag-text">E-WASTE</span>
    <span class="side-tag-line"></span>
  </div>
  <div class="side-tag side-right">
    <span class="side-tag-line"></span>
    <span class="side-tag-text">DIGITAL ETHICS</span>
    <span class="side-tag-line"></span>
  </div>

  <!-- Glowing orbs -->
  <div class="hero-orb orb-l"></div>
  <div class="hero-orb orb-r"></div>
  <div class="hero-orb orb-top" style="width:200px;height:200px;top:-60px;left:50%;transform:translateX(-50%);background:radial-gradient(circle,rgba(56,189,248,0.08) 0%,transparent 70%);animation-delay:1.5s;"></div>

  <!-- Floating data labels -->
  <div class="data-label" style="top:18%;left:5%;">[ SYS: ONLINE ]</div>
  <div class="data-label" style="top:22%;right:5%;">[ ENV: CRITICAL ]</div>
  <div class="data-label" style="bottom:18%;left:5%;">[ WASTE: 50MT/YR ]</div>
  <div class="data-label" style="bottom:18%;right:5%;">[ RECYCLED: 20% ]</div>

  <!-- Scan line sweep -->
  <div class="scan-line"></div>

  <div class="shield-wrap">
    <svg class="shield-svg" viewBox="0 0 100 110" fill="none" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <linearGradient id="sg" x1="0" y1="0" x2="100" y2="110" gradientUnits="userSpaceOnUse">
          <stop offset="0%" stop-color="#0a84ff"/>
          <stop offset="100%" stop-color="#38bdf8"/>
        </linearGradient>
        <filter id="gf"><feGaussianBlur stdDeviation="3" result="blur"/>
          <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
        </filter>
      </defs>
      <path d="M50 5 L90 22 L90 55 C90 78 72 97 50 105 C28 97 10 78 10 55 L10 22 Z"
        fill="url(#sg)" fill-opacity="0.15" stroke="url(#sg)" stroke-width="1.5" filter="url(#gf)"/>
      <path d="M50 18 L78 30 L78 55 C78 71 66 84 50 91 C34 84 22 71 22 55 L22 30 Z"
        fill="url(#sg)" fill-opacity="0.08" stroke="url(#sg)" stroke-width="0.8" stroke-opacity="0.5"/>
      <path d="M36 54 L45 63 L66 43" stroke="#38bdf8" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  </div>
  <p class="hero-eyebrow">Exploring the issues and impacts related to how we manage and dispose of our devices</p>
  <h1>ISSUES &amp; IMPACT<br><em>OF DEVICE USE</em><br>&amp; DISPOSAL</h1>
  <div class="marquee-wrap">
    <div class="marquee-track">
      <div class="deco-pill">♻ E-Waste</div>
      <div class="deco-pill">🔒 Data Security</div>
      <div class="deco-pill">⚖ Legislation</div>
      <div class="deco-pill">🤖 AI</div>
      <div class="deco-pill">🌍 Environment</div>
      <div class="deco-pill">♻ E-Waste</div>
      <div class="deco-pill">🔒 Data Security</div>
      <div class="deco-pill">⚖ Legislation</div>
      <div class="deco-pill">🤖 AI</div>
      <div class="deco-pill">🌍 Environment</div>
    </div>
  </div>

  <div class="scroll-indicator">
    <span class="scroll-text">SCROLL</span>
    <div class="scroll-mouse">
      <div class="scroll-wheel"></div>
    </div>
  </div>

  <p class="hero-reference">📖 Pearson Edexcel GCSE (9–1) Computer Science Revision Guide</p>

</section>


<script>
  // ── GLOBAL STATE — declared first so all functions can access ──
  const visitedSections = new Set();


  function scrollToOffset(el) {
    if (!el) return;
    const navHeight = document.querySelector('nav').offsetHeight;
    const offset = 20;
    const targetY = el.getBoundingClientRect().top + window.scrollY - navHeight - offset;
    window.scrollTo({ top: targetY, behavior: 'smooth' });
  }

  function smoothScrollTo(id) {
    const target = document.getElementById(id);
    if (!target) return;
    const navHeight = document.querySelector('nav').offsetHeight;
    const offset = 20; // extra breathing room
    const targetY = target.getBoundingClientRect().top + window.scrollY - navHeight - offset;
    const startY = window.scrollY;
    const distance = targetY - startY;
    const duration = 1800;
    let startTime = null;

    // Track visited sections
    const sectionIds = ['section-1','section-2','section-3','section-4','section-5','section-6','section-7','section-8','section-9','section-10','section-11','section-12'];
    if (sectionIds.includes(id)) {
      const wasNew = !visitedSections.has(id);
      visitedSections.add(id);
      if (wasNew) updateStreak();
      checkQuizUnlock();
    }

    function easeInOutCubic(t) {
      return t < 0.5 ? 4*t*t*t : 1 - Math.pow(-2*t+2, 3)/2;
    }

    function step(timestamp) {
      if (!startTime) startTime = timestamp;
      const elapsed = timestamp - startTime;
      const progress = Math.min(elapsed / duration, 1);
      window.scrollTo(0, startY + distance * easeInOutCubic(progress));
      if (progress < 1) requestAnimationFrame(step);
    }

    requestAnimationFrame(step);
  }

  // ── STREAK & TOAST ──
  const toastMessages = {
    1:  '🎉 First topic visited!',
    3:  '🔥 On a roll — 3 topics done!',
    6:  '⚡ Halfway there — 6 topics!',
    9:  '🚀 Almost there — 9 topics!',
    12: '🏆 All topics complete! Quiz unlocked!'
  };
  let toastTimeout;

  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    clearTimeout(toastTimeout);
    toastTimeout = setTimeout(() => t.classList.remove('show'), 3000);
  }

  function updateStreak() {
    const count = visitedSections.size;
    document.getElementById('streak-count').textContent = count + ' / 12';
    document.getElementById('streak-bar').classList.add('visible');
    if (toastMessages[count]) showToast(toastMessages[count]);
  }

  // ── AUTO-EXPAND SOCIAL ENGINEERING TABLE ──
  function autoExpandSETable() {
    const rows = document.querySelectorAll('.se-row');
    if (!rows.length) return;
    let current = 0;
    // Expand all first
    rows.forEach(r => r.classList.add('se-expanded'));
    // Then cycle through highlighting one at a time
    rows.forEach(r => r.classList.remove('se-expanded'));

    function expandNext() {
      rows.forEach(r => r.classList.remove('se-expanded'));
      rows[current].classList.add('se-expanded');
      current = (current + 1) % rows.length;
    }
    expandNext();
    setInterval(expandNext, 3000);
  }

  // Start SE auto-expand when table comes into view
  const seTable = document.querySelector('.se-table');
  if (seTable) {
    const seObs = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting) {
        autoExpandSETable();
        seObs.disconnect();
      }
    }, { threshold: 0.3 });
    seObs.observe(seTable);
  }

  // ── AUTO-CYCLE BULLET HIGHLIGHTS ──
  function initBulletCycle(ul) {
    const items = ul.querySelectorAll('li');
    if (items.length < 2) return;
    let current = 0;

    function highlightNext() {
      items.forEach(li => li.classList.remove('bullet-active'));
      items[current].classList.add('bullet-active');
      current = (current + 1) % items.length;
    }

    // Start when list comes into view
    const obs = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting) {
        highlightNext();
        const interval = setInterval(() => {
          // Stop if list is no longer visible
          if (!entry.target.offsetParent) return;
          highlightNext();
        }, 8000);
        ul.dataset.intervalId = interval;
        obs.disconnect();
      }
    }, { threshold: 0.2 });
    obs.observe(ul);
  }

  // Apply to all bullet lists
  document.querySelectorAll('.content-bullets').forEach(ul => initBulletCycle(ul));

  // Also watch for dynamically revealed bullet lists (inside hidden divs)
  const hiddenBulletObs = new MutationObserver(() => {
    document.querySelectorAll('.content-bullets:not([data-cycled])').forEach(ul => {
      ul.dataset.cycled = 'true';
      initBulletCycle(ul);
    });
  });
  hiddenBulletObs.observe(document.body, { subtree: true, attributes: true, attributeFilter: ['style'] });
  window.addEventListener('scroll', () => {
    const docH = document.documentElement.scrollHeight - window.innerHeight;
    const pct = docH > 0 ? (window.scrollY / docH) * 100 : 0;
    document.getElementById('reading-progress').style.width = pct + '%';

    // Back to top button
    const btn = document.getElementById('back-to-top');
    if (window.scrollY > 400) btn.classList.add('visible');
    else btn.classList.remove('visible');
  });

  // ── SECTION COUNTER ──
  const counterEl = document.getElementById('section-counter');
  const allSections = document.querySelectorAll('.panel, .content-section');
  const sectionObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const id = entry.target.id;
        if (id && id !== 'hero' && id !== 'toc' && id !== 'quiz') {
          const num = id.replace('section-','');
          counterEl.textContent = `SECTION ${num} / 12`;
          counterEl.classList.add('visible');
          // Mark TOC item as visited
          const tocItem = document.querySelector(`.toc-item[onclick*="'${id}'"]`);
          if (tocItem) tocItem.classList.add('visited');
        } else {
          counterEl.classList.remove('visible');
        }
      }
    });
  }, { threshold: 0.4 });
  allSections.forEach(s => sectionObserver.observe(s));

  // ── RIPPLE EFFECT on buttons ──
  document.addEventListener('click', function(e) {
    const btn = e.target.closest('.next-btn, .btn-glow, .back-btn, .fact-btn');
    if (!btn) return;
    const ripple = document.createElement('span');
    const rect = btn.getBoundingClientRect();
    ripple.style.cssText = `
      position:absolute; border-radius:50%;
      width:40px; height:40px;
      background:rgba(255,255,255,0.25);
      top:${e.clientY - rect.top - 20}px;
      left:${e.clientX - rect.left - 20}px;
      transform:scale(0); animation:ripple 0.5s ease-out forwards;
      pointer-events:none;
    `;
    btn.style.position = 'relative';
    btn.style.overflow = 'hidden';
    btn.appendChild(ripple);
    setTimeout(() => ripple.remove(), 500);
  });

  // Ripple keyframe
  const rippleStyle = document.createElement('style');
  rippleStyle.textContent = '@keyframes ripple { to { transform:scale(4); opacity:0; } }';
  document.head.appendChild(rippleStyle);

  // Unlock quiz when sections are scrolled into view
  const observeSectionIds = ['section-1','section-2','section-3','section-4','section-5','section-6','section-7','section-8','section-9','section-10','section-11','section-12'];

  const scrollObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const wasNew = !visitedSections.has(entry.target.id);
        visitedSections.add(entry.target.id);
        if (wasNew) updateStreak();
        checkQuizUnlock();
      }
    });
  }, { threshold: 0.3 });

  observeSectionIds.forEach(id => {
    const el = document.getElementById(id);
    if (el) scrollObserver.observe(el);
  });

  function checkQuizUnlock() {
    if (visitedSections.size >= 12) {
      const item = document.getElementById('toc-quiz-item');
      item.classList.add('unlocked');
      document.getElementById('quiz-lock-hint').textContent = '— you\'re ready!';
      document.getElementById('quiz-lock-hint').style.color = '#4ade80';
      document.getElementById('quiz-lock-icon').textContent = '→';
      // Show quiz section and unlock banner
      document.getElementById('quiz').style.display = '';
      document.getElementById('quiz-unlock-banner').style.display = 'block';
    }
  }

  function tryQuiz() {
    const item = document.getElementById('toc-quiz-item');
    if (!item.classList.contains('unlocked')) {
      item.style.borderColor = 'rgba(248,113,113,0.6)';
      item.style.background = 'rgba(248,113,113,0.08)';
      setTimeout(() => { item.style.borderColor = ''; item.style.background = ''; }, 1000);
      return;
    }
    smoothScrollTo('quiz');
  }
</script>




<script>
  const quizAnswers = ['b','b','a','c','b','a','b','c','a','d','c','b','c','b','b','c','b','b','c','b'];
  const optionLetters = ['a','b','c','d'];
  let quizScore = 0;
  let quizAnswered = 0;
  let currentQ = 0;
  const QUIZ_TOTAL = 20;

  function answerQuiz(qIndex, btn) {
    const card = document.getElementById('q' + qIndex);
    if (card.dataset.answered) return;
    card.dataset.answered = 'true';

    const opts = card.querySelectorAll('.quiz-opt');
    const chosen = optionLetters[Array.from(opts).indexOf(btn)];
    const isCorrect = chosen === quizAnswers[qIndex];

    opts.forEach((o, i) => {
      o.disabled = true;
      if (optionLetters[i] === quizAnswers[qIndex]) o.classList.add('quiz-correct');
    });

    const fb = document.getElementById('qf' + qIndex);
    if (isCorrect) {
      btn.classList.add('quiz-correct');
      fb.textContent = '✓ Correct!';
      fb.style.color = '#4ade80';
      quizScore++;
    } else {
      btn.classList.add('quiz-wrong');
      fb.textContent = '✗ Incorrect — the correct answer is highlighted.';
      fb.style.color = '#f87171';
    }

    quizAnswered++;
    setTimeout(() => {
      if (qIndex < QUIZ_TOTAL - 1) {
        card.classList.remove('active');
        document.getElementById('q' + (qIndex + 1)).classList.add('active');
        currentQ = qIndex + 1;
      } else {
        showQuizResult();
      }
    }, 1200);
  }

  function showQuizResult() {
    document.getElementById('q' + (QUIZ_TOTAL - 1)).style.display = 'none';
    const result = document.getElementById('quiz-result');
    result.style.display = 'block';
    document.getElementById('quiz-score-num').textContent = quizScore;
    const msg = document.getElementById('quiz-result-msg');
    if (quizScore === 20) msg.textContent = '🏆 Perfect score! Absolutely outstanding!';
    else if (quizScore >= 16) msg.textContent = '🎉 Excellent! You really know your stuff!';
    else if (quizScore >= 12) msg.textContent = '👍 Good effort! Review the topics you missed.';
    else if (quizScore >= 8) msg.textContent = '📚 Keep going — you\'re getting there!';
    else msg.textContent = '💪 Keep studying — revisit the topics and try again!';
    scrollToOffset(result);
  }

  function resetQuiz() {
    quizScore = 0; quizAnswered = 0; currentQ = 0;
    for (let i = 0; i < QUIZ_TOTAL; i++) {
      const card = document.getElementById('q' + i);
      card.classList.remove('active');
      card.style.display = '';
      delete card.dataset.answered;
      card.querySelectorAll('.quiz-opt').forEach(o => {
        o.disabled = false;
        o.classList.remove('quiz-correct','quiz-wrong');
      });
      document.getElementById('qf' + i).textContent = '';
    }
    document.getElementById('q0').classList.add('active');
    document.getElementById('quiz-result').style.display = 'none';
  }
</script>
<section class="panel" id="toc">
  <div class="rings">
    <div class="ring"></div><div class="ring"></div>
    <div class="ring"></div><div class="ring"></div>
  </div>
  <div style="width:100%;max-width:700px;text-align:center;">
    <p class="eyebrow" style="justify-content:center;">Navigation</p>
    <h2 style="font-size:clamp(2rem,5vw,3.5rem);font-weight:900;letter-spacing:-1px;margin-bottom:0.5rem;">
      Table of <span style="background:linear-gradient(90deg,var(--b1),var(--b3));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;">Contents</span>
    </h2>
    <p style="font-size:1rem;font-weight:300;color:var(--muted);margin-bottom:3rem;">Select a section to begin exploring.</p>
    <div style="display:flex;flex-direction:column;gap:1px;background:var(--border);border:1px solid var(--border);border-radius:20px;overflow:hidden;">
      <div class="toc-item" onclick="smoothScrollTo('section-1')"><span class="toc-num">01</span><span class="toc-label">Environmental Issues 1</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-2')"><span class="toc-num">02</span><span class="toc-label">Environmental Issues 2</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-3')"><span class="toc-num">03</span><span class="toc-label">Personal Data</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-4')"><span class="toc-num">04</span><span class="toc-label">Legislation</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-5')"><span class="toc-num">05</span><span class="toc-label">Artificial Intelligence (AI)</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-6')"><span class="toc-num">06</span><span class="toc-label">Protecting Intellectual Property 1</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-7')"><span class="toc-num">07</span><span class="toc-label">Protecting Intellectual Property 2</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-8')"><span class="toc-num">08</span><span class="toc-label">Threats to Digital Systems 1</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-9')"><span class="toc-num">09</span><span class="toc-label">Threats to Digital Systems 2</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-10')"><span class="toc-num">10</span><span class="toc-label">Threats to Digital Systems 3</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-11')"><span class="toc-num">11</span><span class="toc-label">Protecting Digital Systems 1</span><span class="toc-arrow">→</span></div>
      <div class="toc-item" onclick="smoothScrollTo('section-12')"><span class="toc-num">12</span><span class="toc-label">Protecting Digital Systems 2</span><span class="toc-arrow">→</span></div>
      <div class="toc-item toc-quiz-locked" id="toc-quiz-item" onclick="tryQuiz()">
        <span class="toc-num">🎯</span>
        <span class="toc-label">Quiz Time! <span id="quiz-lock-hint" style="font-size:0.72rem; color:#f87171; letter-spacing:1px; font-weight:600;">— complete all 12 topics first!</span></span>
        <span class="toc-arrow" id="quiz-lock-icon">🔒</span>
      </div>
      <div class="toc-item" onclick="smoothScrollTo('ai-calculator')">
        <span class="toc-num">⚡</span>
        <span class="toc-label">AI Energy Calculator</span>
        <span class="toc-arrow">→</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTENT SECTIONS -->
<section class="panel content-section" id="section-1">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>

  <!-- Extra background decorations -->
  <div class="particles">
    <div class="particle" style="left:6%;top:15%;animation-delay:0s;width:3px;height:3px;"></div>
    <div class="particle" style="left:12%;top:75%;animation-delay:1.4s;width:2px;height:2px;"></div>
    <div class="particle" style="left:85%;top:20%;animation-delay:0.7s;width:3px;height:3px;"></div>
    <div class="particle" style="left:90%;top:70%;animation-delay:2.1s;width:2px;height:2px;"></div>
    <div class="particle" style="left:50%;top:8%;animation-delay:1s;width:2px;height:2px;"></div>
    <div class="particle" style="left:70%;top:88%;animation-delay:2.5s;width:3px;height:3px;"></div>
  </div>
  <div class="bg-grid"></div>
  <div class="streak streak-1"></div>
  <div class="streak streak-2"></div>
  <div class="corner-deco corner-tl"></div>
  <div class="corner-deco corner-tr"></div>
  <div class="corner-deco corner-bl"></div>
  <div class="corner-deco corner-br"></div>
  <div class="corner-dot" style="top:6.5rem;left:2.6rem;"></div>
  <div class="corner-dot" style="top:6.5rem;right:2.6rem;"></div>
  <div class="corner-dot" style="bottom:2.6rem;left:2.6rem;"></div>
  <div class="corner-dot" style="bottom:2.6rem;right:2.6rem;"></div>
  <div class="data-label" style="top:18%;right:5%;">[ E-WASTE: CRITICAL ]</div>
  <div class="data-label" style="bottom:18%;left:5%;">[ SECTION: 01 ]</div>
  <div class="hero-orb orb-l" style="opacity:0.5;"></div>
  <div class="hero-orb orb-r" style="opacity:0.5;"></div>
  <div class="content-inner">
    <p class="eyebrow">01</p>
    <h2>Environmental <span>Issues 1</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">The manufacture, use and disposal of digital devices has a significant impact on the environment</p>
    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Manufacture</h3>
    <ul class="content-bullets">
      <li>Large quantities of raw materials are used to make digital devices, including copper and palladium, both of which are non-renewable, finite resources.</li>
      <li>Some materials, such as arsenic, are highly toxic and require stringent controls during extraction and processing.</li>
      <li>Mining for raw materials scars the landscape with waste and often damages wildlife habitats in the surrounding area.</li>
      <li>Much of the energy used in the manufacturing process comes from non-renewable fossil fuels, which contribute to global warming.</li>
      <li>Polluted waste water is a by-product of the manufacturing process and must be treated before it enters rivers and soil.</li>
    </ul>

    <button class="next-btn" onclick="document.getElementById('energy-section').style.display='block'; this.style.display='none'; scrollToOffset(document.getElementById('energy-section'))">Next →</button>

    <div id="energy-section" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Energy Consumption</h3>
      <div class="mindmap-wrap">
        <div class="mindmap">
          <!-- Centre -->
          <div class="mm-center">Energy Consumption</div>
          <!-- Nodes -->
          <div class="mm-node mm-tl" onclick="this.classList.toggle('mm-active')">
            <div class="mm-line mm-line-tl"></div>
            <div class="mm-bubble">
              <span class="mm-icon">⚙️</span>
              <span>Production of computer equipment</span>
            </div>
          </div>
          <div class="mm-node mm-tr" onclick="this.classList.toggle('mm-active')">
            <div class="mm-line mm-line-tr"></div>
            <div class="mm-bubble">
              <span class="mm-icon">💻</span>
              <span>Functioning of equipment</span>
            </div>
          </div>
          <div class="mm-node mm-bl" onclick="this.classList.toggle('mm-active')">
            <div class="mm-line mm-line-bl"></div>
            <div class="mm-bubble">
              <span class="mm-icon">☁️</span>
              <span>Online data storage in data centers</span>
            </div>
          </div>
          <div class="mm-node mm-br" onclick="this.classList.toggle('mm-active')">
            <div class="mm-line mm-line-br"></div>
            <div class="mm-bubble">
              <span class="mm-icon">♻️</span>
              <span>Recycling of equipment</span>
            </div>
          </div>
        </div>
        <p style="font-size:0.68rem; font-family:'Nunito', sans-serif; color:var(--b2); letter-spacing:2px; text-align:center; margin-top:1rem; animation: hintPulse 2.5s ease-in-out infinite;">CLICK EACH NODE TO HIGHLIGHT</p>
      </div>

      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('disposal-section').style.display='block'; this.style.display='none'; scrollToOffset(document.getElementById('disposal-section'))">Next →</button>

      <div id="disposal-section" style="display:none;">
        <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-top:2.5rem; margin-bottom:1rem; letter-spacing:1px;">Disposal</h3>

      <div class="fact-cards">
        <div class="fact-card-wrap">
          <div class="fact-card active" id="fact-0">
            <div class="fact-icon">🌍</div>
            <p class="fact-text">Many discarded devices end up as e-waste. Approximately <strong>50 million tonnes</strong> are produced each year.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:14%"></div></div>
            <div class="fact-counter">1 / 7</div>
          </div>
          <div class="fact-card" id="fact-1">
            <div class="fact-icon">♻️</div>
            <p class="fact-text">Only around <strong>20% of e-waste</strong> is properly recycled globally.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:28%"></div></div>
            <div class="fact-counter">2 / 7</div>
          </div>
          <div class="fact-card" id="fact-2">
            <div class="fact-icon">🏭</div>
            <p class="fact-text">E-waste can be <strong>illegally dumped</strong> in landfill sites where toxic substances such as lead, mercury and cobalt can seep into land and water.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:43%"></div></div>
            <div class="fact-counter">3 / 7</div>
          </div>
          <div class="fact-card" id="fact-3">
            <div class="fact-icon">⚠️</div>
            <p class="fact-text"><strong>Severe health issues</strong> are caused by living near, or trying to salvage sellable items from, e-waste dumps.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:57%"></div></div>
            <div class="fact-counter">4 / 7</div>
          </div>
          <div class="fact-card" id="fact-4">
            <div class="fact-icon">🔩</div>
            <p class="fact-text">Many computer components <strong>cannot be recycled or reused</strong>, adding to the growing mountain of waste.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:71%"></div></div>
            <div class="fact-counter">5 / 7</div>
          </div>
          <div class="fact-card" id="fact-5">
            <div class="fact-icon">🚢</div>
            <p class="fact-text"><strong>Millions of tonnes</strong> of e-waste are dumped in developing countries every year.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:86%"></div></div>
            <div class="fact-counter">6 / 7</div>
          </div>
          <div class="fact-card" id="fact-6">
            <div class="fact-icon">✅</div>
            <p class="fact-text">Responsible disposal, recycling schemes, and stricter legislation are key to tackling the global e-waste crisis.</p>
            <div class="fact-progress"><div class="fact-bar" style="width:100%"></div></div>
            <div class="fact-counter">7 / 7</div>
          </div>
        </div>

        <div class="fact-nav">
          <button class="fact-btn" id="fact-prev" onclick="changeFactCard(-1)" disabled>← Prev</button>
          <div class="fact-dots" id="fact-dots">
            <span class="fact-dot active" onclick="goToCard(0)"></span>
            <span class="fact-dot" onclick="goToCard(1)"></span>
            <span class="fact-dot" onclick="goToCard(2)"></span>
            <span class="fact-dot" onclick="goToCard(3)"></span>
            <span class="fact-dot" onclick="goToCard(4)"></span>
            <span class="fact-dot" onclick="goToCard(5)"></span>
            <span class="fact-dot" onclick="goToCard(6)"></span>
          </div>
          <button class="fact-btn" id="fact-next" onclick="changeFactCard(1)">Next →</button>
        </div>
      </div>

      <script>
        let currentFact = 0;
        const totalFacts = 7;

        function changeFactCard(dir) {
          goToCard(currentFact + dir);
        }

        function goToCard(index) {
          if (index < 0 || index >= totalFacts) return;
          document.getElementById('fact-' + currentFact).classList.remove('active');
          document.querySelectorAll('.fact-dot')[currentFact].classList.remove('active');
          currentFact = index;
          document.getElementById('fact-' + currentFact).classList.add('active');
          document.querySelectorAll('.fact-dot')[currentFact].classList.add('active');
          document.getElementById('fact-prev').disabled = currentFact === 0;
          document.getElementById('fact-next').disabled = currentFact === totalFacts - 1;
        }
      </script>

      <p style="font-size:0.95rem; font-weight:600; color:var(--b3); margin-top:2rem; margin-bottom:0.8rem;">Responsible recycling can:</p>
      <ul class="content-bullets">
        <li>Reduce the potential for chemical leakage and fires in landfills.</li>
        <li>Enable the recovery of valuable metals.</li>
        <li>Reduce the need for mining.</li>
        <li>Enable the recycling of plastic cases that would otherwise decompose into toxic particles.</li>
        <li>Reduce the amount of harmful toxins released into the air.</li>
      </ul>

      </div><!-- end disposal-section -->
    </div><!-- end energy-section -->
    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-2">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">02</p>
    <h2>Environmental <span>Issues 2</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">If digital devices are manufactured and used in a responsible way, the damaging effect they can have on the environment is reduced. Digital technology can also help to create a more sustainable world.</p>

    <!-- Short Replacement Cycle -->
    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Short Replacement Cycle</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:1.2rem;">The average user trades in a mobile phone for a newer model roughly once every three years. This goes for other devices too, such as smartwatches or laptops.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">Even when a user would prefer to keep their current device, designers make it difficult for them by:</p>
    <ul class="content-bullets">
      <li>Using embedded batteries that are difficult to replace.</li>
      <li>Gluing and soldering components to make repair difficult.</li>
      <li>Increasing the price of spare parts.</li>
      <li>Only providing software updates and security patches for a limited time.</li>
    </ul>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('s2-consequences').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('s2-consequences'))">Next →</button>

    <!-- Consequences -->
    <div id="s2-consequences" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Consequences of the Short Replacement Cycle</h3>
      <ul class="content-bullets">
        <li>It adds to the problem of e-waste because redundant devices are thrown away.</li>
        <li>More devices must be manufactured, with all the associated environmental costs.</li>
      </ul>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('s2-ownership').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('s2-ownership'))">Next →</button>
    </div>

    <!-- Responsible Ownership -->
    <div id="s2-ownership" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Responsible Ownership</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:1.2rem;">Responsible use can reduce the environmental impact of digital devices. It involves:</p>
      <ul class="content-bullets">
        <li>Keeping devices for longer.</li>
        <li>Considering buying a pre-owned device rather than a new one.</li>
        <li>Donating unwanted devices to charity or a recycling company.</li>
        <li>Using energy-efficient measures to reduce power consumption.</li>
        <li>Reducing internet usage.</li>
      </ul>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('s2-energy').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('s2-energy'))">Next →</button>
    </div>

    <!-- Ways to Reduce Energy Consumption -->
    <div id="s2-energy" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Ways to Reduce Energy Consumption</h3>
      <div class="flashcard-container">
        <div class="flashcard" onclick="this.classList.toggle('flipped')">
          <div class="flashcard-inner">
            <div class="flashcard-front"><span class="fc-num">01</span><span class="fc-hint">tap to reveal</span></div>
            <div class="flashcard-back"><p>Adjust the settings, such as screen brightness and 'sleep' mode.</p></div>
          </div>
        </div>
        <div class="flashcard" onclick="this.classList.toggle('flipped')">
          <div class="flashcard-inner">
            <div class="flashcard-front"><span class="fc-num">02</span><span class="fc-hint">tap to reveal</span></div>
            <div class="flashcard-back"><p>Switch off Bluetooth, Wi-Fi and GPS when not in use.</p></div>
          </div>
        </div>
        <div class="flashcard" onclick="this.classList.toggle('flipped')">
          <div class="flashcard-inner">
            <div class="flashcard-front"><span class="fc-num">03</span><span class="fc-hint">tap to reveal</span></div>
            <div class="flashcard-back"><p>Close dormant applications so that they don't continue running in the background.</p></div>
          </div>
        </div>
        <div class="flashcard" onclick="this.classList.toggle('flipped')">
          <div class="flashcard-inner">
            <div class="flashcard-front"><span class="fc-num">04</span><span class="fc-hint">tap to reveal</span></div>
            <div class="flashcard-back"><p>Disconnect peripherals when not in use.</p></div>
          </div>
        </div>
        <div class="flashcard" onclick="this.classList.toggle('flipped')">
          <div class="flashcard-inner">
            <div class="flashcard-front"><span class="fc-num">05</span><span class="fc-hint">tap to reveal</span></div>
            <div class="flashcard-back"><p>When buying a new device, choose one with a high energy-efficiency rating.</p></div>
          </div>
        </div>
        <div class="flashcard" onclick="this.classList.toggle('flipped')">
          <div class="flashcard-inner">
            <div class="flashcard-front"><span class="fc-num">06</span><span class="fc-hint">tap to reveal</span></div>
            <div class="flashcard-back"><p>Locate energy-hungry data centers in locations where they can use renewable energy.</p></div>
          </div>
        </div>
      </div>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('s2-positive').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('s2-positive'))">Next →</button>
    </div>

    <!-- Positive Impact -->
    <div id="s2-positive" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Positive Impact</h3>
      <div class="impact-cards">
        <div class="impact-card">
          <div class="impact-icon">🚦</div>
          <h4 class="impact-title">Intelligent Traffic Control</h4>
          <p class="impact-text">Intelligent traffic control systems keep traffic moving and reduce fuel consumption.</p>
        </div>
        <div class="impact-card">
          <div class="impact-icon">💡</div>
          <h4 class="impact-title">Smart Lighting</h4>
          <p class="impact-text">'Smart lighting' switches off lights when they are not needed, saving significant amounts of energy.</p>
        </div>
        <div class="impact-card">
          <div class="impact-icon">🌿</div>
          <h4 class="impact-title">Environmental Monitoring</h4>
          <p class="impact-text">Environmental monitoring ensures that regulations are being followed and prevents poaching and other illegal activities.</p>
        </div>
      </div>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-3">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">03</p>
    <h2>Personal <span>Data</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">Personal data is information that relates to a known individual or one whose identity can be deduced. It includes a person's name, passport number, fingerprints, ethnicity, medical record, shopping history and political opinion.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Digital Footprint</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:1.2rem;"><strong style="color:var(--b2);">Definition:</strong> The trail of personal data left behind each time someone uses the internet.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">People give away personal information while carrying out day-to-day activities, such as paying for a coffee with a bank card, using Google Maps to get somewhere, and in many other occasions.</p>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('s3-benefits').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('s3-benefits'))">Next →</button>

    <div id="s3-benefits" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Benefits and Drawbacks</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.5rem;">For each card, decide whether it is a <strong style="color:#4ade80;">Benefit</strong> or a <strong style="color:#f87171;">Drawback</strong> of sharing personal data.</p>

      <div class="sort-cards" id="sort-cards">

        <div class="sort-card" data-answer="benefit">
          <div class="sort-label">Personalisation</div>
          <p class="sort-desc">Offers can be tailored to an individual's preferences and location.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswer(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswer(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>

        <div class="sort-card" data-answer="benefit">
          <div class="sort-label">Convenience</div>
          <p class="sort-desc">Personal details, such as credit card numbers and addresses, only need to be entered once.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswer(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswer(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>

        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">Privacy</div>
          <p class="sort-desc">It is not always obvious who is collecting and analysing the data and who they are passing it on to.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswer(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswer(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>

        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">Security</div>
          <p class="sort-desc">Data breaches occur frequently. If personal data falls into the wrong hands, it might be misused.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswer(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswer(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>

        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">Discrimination</div>
          <p class="sort-desc">Analysis of shared data could result in some groups or individuals being discriminated against.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswer(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswer(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>

        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">Civil Liberties</div>
          <p class="sort-desc">Analysis of shared data by police forces could wrongly associate innocent people with criminal behaviour or categorise people politically.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswer(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswer(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>

      </div>

      <button class="next-btn" id="submit-sort" style="margin-top:1.5rem; display:none;" onclick="showSortResults()">Check Answers →</button>

      <div id="sort-score" style="display:none; margin-top:1.5rem;">
        <div class="score-box">
          <span class="score-num" id="score-num">0</span>
          <span class="score-label">out of 6 correct</span>
        </div>
        <div class="correct-answers">
          <p style="font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:2px; color:var(--b2); margin-bottom:1rem;">CORRECT ANSWERS:</p>
          <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Personalisation</span></div>
          <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Convenience</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Privacy</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Security</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Discrimination</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Civil Liberties</span></div>
        </div>
      </div>

      <script>
        let answeredCount = 0;
        const totalCards = 6;

        function submitAnswer(btn, chosen) {
          const card = btn.closest('.sort-card');
          if (card.dataset.answered) return;
          card.dataset.answered = 'true';
          card.dataset.chosen = chosen;
          const btns = card.querySelectorAll('.sort-btn');
          btns.forEach(b => b.disabled = true);
          answeredCount++;
          if (answeredCount === totalCards) {
            document.getElementById('submit-sort').style.display = 'inline-flex';
          }
        }

        function showSortResults() {
          let score = 0;
          const cards = document.querySelectorAll('.sort-card');
          cards.forEach(card => {
            const correct = card.dataset.answer;
            const chosen = card.dataset.chosen;
            const result = card.querySelector('.sort-result');
            if (chosen === correct) {
              score++;
              card.classList.add('card-correct');
              result.textContent = '✓ Correct!';
              result.style.color = '#4ade80';
            } else {
              card.classList.add('card-wrong');
              result.textContent = '✗ Incorrect';
              result.style.color = '#f87171';
            }
          });
          document.getElementById('score-num').textContent = score;
          document.getElementById('sort-score').style.display = 'block';
          document.getElementById('submit-sort').style.display = 'none';
          scrollToOffset(document.getElementById('sort-score'));
        }
      </script>

      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('s3-owning').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('s3-owning'))">Next →</button>
    </div>

    <div id="s3-owning" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Owning the Data</h3>
      <div class="ownership-grid">
        <div class="ownership-card">
          <div class="ownership-num">01</div>
          <p>When someone posts a photo on a social media site, they retain the intellectual property (IP), but the company has the right to do what it wants with the photo.</p>
        </div>
        <div class="ownership-card">
          <div class="ownership-num">02</div>
          <p>Users will always own their names and addresses, but it is less clear who owns the data about their activity while visiting a site.</p>
        </div>
        <div class="ownership-card">
          <div class="ownership-num">03</div>
          <p>Medical records are not the patient's property. In the UK, they belong to the National Health Service. Patients only have the right to view them.</p>
        </div>
        <div class="ownership-card">
          <div class="ownership-num">04</div>
          <p>Online retailers sell shoppers' purchase data to other retailers. Google sells people's search histories.</p>
        </div>
      </div>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-4">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">04</p>
    <h2><span>Legislation</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">Legislation regulates the collection and use of personal data and protects against misuse.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Data Protection Act 2018 (DPA)</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:1.2rem;"><strong style="color:var(--b2);">Function:</strong> Defines a set of principles that organisations must adhere to.</p>

    <div class="dpa-table">
      <div class="dpa-row dpa-header">
        <div class="dpa-cell dpa-head">Principle</div>
        <div class="dpa-cell dpa-head">Organisations must do the following</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Lawfulness, fairness and transparency</div>
        <div class="dpa-cell">Have a legitimate reason for processing a person's data, must tell them what they will use the data for and must get their consent.</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Purpose limitation</div>
        <div class="dpa-cell">Only use the data for the specific purpose for which it was collected.</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Data minimisation</div>
        <div class="dpa-cell">Only collect as much data as is necessary for the specified purpose.</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Accuracy</div>
        <div class="dpa-cell">Ensure that the data they collect is accurate and current. When notified of an error in the data, they must update it promptly.</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Storage limitation</div>
        <div class="dpa-cell">Not keep data for longer than is necessary.</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Security</div>
        <div class="dpa-cell">Keep data secure and protect it against loss or damage.</div>
      </div>
      <div class="dpa-row">
        <div class="dpa-cell dpa-principle">Accountability</div>
        <div class="dpa-cell">Demonstrate that their data protection measures are adequate.</div>
      </div>
    </div>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('leg-misuse').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('leg-misuse'))">Next →</button>

    <div id="leg-misuse" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Computer Misuse</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:0.8rem;"><strong style="color:var(--b2);">Function:</strong> Prosecute cybercriminals in the UK.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">The act identifies three offences:</p>
      <ol class="offences-list">
        <li>Unauthorised access to computer material.</li>
        <li>Unauthorised access with intent to commit further offences.</li>
        <li>Unauthorised access with intent to impair the running of a computer or to damage or destroy data.</li>
      </ol>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('leg-cookies').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('leg-cookies'))">Next →</button>
    </div>

    <div id="leg-cookies" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Cookies</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">What are cookies?</strong> A small text file that is downloaded onto a user's device when they visit a website.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">Why do we have cookies?</strong> In order to enable the website to recognise the user's device and their preferences.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;"><strong style="color:var(--b2);">What regulation governs the use of cookies?</strong> The Privacy and Electronic Communication Regulations 2003. <a href="https://whistleblowersoftware.com/en/gdpr-compliance?hsa_acc=1802811096&hsa_cam=19661600043&hsa_grp=1360098395637035&hsa_ad=&hsa_src=o&hsa_tgt=kwd-2336805807038892:loc-612&hsa_kw=whistleblowersoftware.com&hsa_mt=b&hsa_net=adwords&hsa_ver=3&msclkid=b84d3f7c4ff714352dd1557104b444e0&utm_source=bing&utm_medium=cpc&utm_campaign=Pmax%20-%20BE%20-%20A&utm_term=whistleblowersoftware.com&utm_content=BE%20-%20A%20-%20NORD" target="_blank" class="inline-link">Essential Guide to GDPR Compliance →</a></p>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-5">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">05</p>
    <h2>Artificial <span>Intelligence (AI)</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">AI affects our lives in many different ways. While the use of AI has obvious benefits, it also raises a number of important ethical and legal issues.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Narrow AI</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:1.2rem;">Machine-learning systems are designed to perform a single task or a limited range of tasks. They cannot transfer their knowledge to another type of task and fail when they encounter a situation that falls outside their area of expertise. This is narrow AI.</p>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ai-examples').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ai-examples'))">Next →</button>

    <div id="ai-examples" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Examples of Narrow AI</h3>
      <ul class="content-bullets">
        <li>Email spam folders.</li>
        <li>Social media monitoring tools.</li>
        <li>Facial / fingerprint recognition systems.</li>
        <li>Content recommendation.</li>
        <li>Self-driving cars.</li>
        <li>And many more...</li>
      </ul>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ai-bias').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ai-bias'))">Next →</button>
    </div>

    <div id="ai-bias" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Algorithmic Bias</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">Definition:</strong> When AI algorithms are biased.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">Algorithmic bias can occur because:</p>
      <ul class="content-bullets">
        <li>The dataset used to train the AI system is itself biased.</li>
        <li>There is a design flaw.</li>
        <li>The developers who design/build the AI systems unintentionally incorporate their own prejudices and preconceptions into them.</li>
      </ul>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ai-responsibility').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ai-responsibility'))">Next →</button>
    </div>

    <div id="ai-responsibility" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Responsibility</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">Problems might be the fault of:</p>
      <ul class="content-bullets">
        <li>The creator of the algorithm.</li>
        <li>The supplier of the data.</li>
        <li>The user of the algorithm.</li>
      </ul>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-6">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">06</p>
    <h2>Protecting Intellectual <span>Property 1</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">Intellectual property (IP) is a unique creation of the human mind, such as an invention, a computer program, or a graphic image. IP is protected by the Copyright Designs and Patent Act 1988.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Copyright</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">What does it do?</strong> Protects things from being copied without permission. It lasts for 70 years after the death of the copyright holder. It is automatic and does not need to be applied for.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;"><strong style="color:var(--b2);">Symbol:</strong> <span style="font-size:1.4rem; color:var(--b2); text-shadow:0 0 12px rgba(56,189,248,0.5);">©</span></p>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ip1-patents').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ip1-patents'))">Next →</button>

    <div id="ip1-patents" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Patents</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">Definition:</strong> Protects new inventions. Not automatic — it has to be applied for. The applicant has to demonstrate that their invention is unique.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;"><strong style="color:var(--b2);">What right does a patent holder have?</strong> To make, use and sell the invention for 20 years.</p>

      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-top:1.5rem; margin-bottom:1rem; letter-spacing:1px;">Disadvantages of Patents</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">Companies such as Apple, Google and Microsoft spend vast amounts of money fighting over patents, money which could have been used to innovate instead.</p>

      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ip1-licensing').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ip1-licensing'))">Next →</button>
    </div>

    <div id="ip1-licensing" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Licensing</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">The copyright holder of a work can grant a licence that permits a third party to use it.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1rem;">There are three types of licences:</p>
      <ol class="offences-list">
        <li><strong style="color:var(--b3);">Creative Commons Licence:</strong> Permits others to use, build upon and distribute the work, as long as they stick to certain conditions.</li>
        <li><strong style="color:var(--b3);">Attribution-Non-Commercial Licence:</strong> Allows work to be used, distributed and copied for non-commercial purposes, as long as the creator is given credit.</li>
        <li><strong style="color:var(--b3);">Attribution Commercial Licence:</strong> Allows the same rights and commercial use.</li>
      </ol>
      <div class="note-box">
        <span class="note-icon">♩</span>
        <p>Note that work in the public domain can be used without permission or attribution to the creator.</p>
      </div>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ip1-trademarks').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ip1-trademarks'))">Next →</button>
    </div>

    <div id="ip1-trademarks" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Trademarks</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">What are trademarks for?</strong> Unique company logos, strap lines, and more...</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">Symbols:</strong> <span style="font-size:1.3rem; color:var(--b2); text-shadow:0 0 12px rgba(56,189,248,0.5);">®</span> <span style="font-size:0.8rem; color:var(--muted);">Registered</span> &nbsp;&nbsp; <span style="font-size:1.3rem; color:var(--muted);">™</span> <span style="font-size:0.8rem; color:var(--muted);">Not registered</span></p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;"><strong style="color:var(--b2);">Why?</strong> To distinguish their goods/services from those of their competitors. Lasts for 10 years.</p>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-7">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">07</p>
    <h2>Protecting Intellectual <span>Property 2</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">Computer users can choose between open-source and proprietary software. Anyone can access and modify the code of open-source software. However, proprietary software is closed-source — no one apart from the copyright holder is allowed to view or modify the code.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Open-Source Software</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.5rem;">For each card, decide whether it is a <strong style="color:#4ade80;">Benefit</strong> or a <strong style="color:#f87171;">Drawback</strong> of open-source software.</p>

    <div class="sort-cards" id="sort-cards-oss">
      <div class="sort-card" data-answer="benefit">
        <div class="sort-label">Source Code Access</div>
        <p class="sort-desc">Users have access to the source code.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
      <div class="sort-card" data-answer="benefit">
        <div class="sort-label">Modify & Distribute</div>
        <p class="sort-desc">Users can modify and distribute the software.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
      <div class="sort-card" data-answer="benefit">
        <div class="sort-label">Unlimited Installs</div>
        <p class="sort-desc">The software can be installed on any number of machines at the same time.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
      <div class="sort-card" data-answer="drawback">
        <div class="sort-label">Community Support</div>
        <p class="sort-desc">Support is provided by community enthusiasts rather than dedicated professionals.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
      <div class="sort-card" data-answer="benefit">
        <div class="sort-label">Free to Use</div>
        <p class="sort-desc">Most open-source software is free to use.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
      <div class="sort-card" data-answer="drawback">
        <div class="sort-label">Bugs & Testing</div>
        <p class="sort-desc">May not be free of bugs or fully tested.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
      <div class="sort-card" data-answer="drawback">
        <div class="sort-label">Specialist Knowledge</div>
        <p class="sort-desc">May need specialist knowledge to install.</p>
        <div class="sort-btns">
          <button class="sort-btn benefit-btn" onclick="submitAnswerOSS(this, 'benefit')">✓ Benefit</button>
          <button class="sort-btn drawback-btn" onclick="submitAnswerOSS(this, 'drawback')">✗ Drawback</button>
        </div>
        <div class="sort-result"></div>
      </div>
    </div>

    <button class="next-btn" id="submit-oss" style="margin-top:1.5rem; display:none;" onclick="showOSSResults()">Check Answers →</button>

    <div id="oss-score" style="display:none; margin-top:1.5rem;">
      <div class="score-box">
        <span class="score-num" id="oss-score-num">0</span>
        <span class="score-label">out of 7 correct</span>
      </div>
      <div class="correct-answers">
        <p style="font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:2px; color:var(--b2); margin-bottom:1rem;">CORRECT ANSWERS:</p>
        <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Source Code Access</span></div>
        <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Modify & Distribute</span></div>
        <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Unlimited Installs</span></div>
        <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Community Support</span></div>
        <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Free to Use</span></div>
        <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Bugs & Testing</span></div>
        <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Specialist Knowledge</span></div>
      </div>
    </div>

    <script>
      let ossAnswered = 0;
      const ossTotalCards = 7;

      function submitAnswerOSS(btn, chosen) {
        const card = btn.closest('.sort-card');
        if (card.dataset.answered) return;
        card.dataset.answered = 'true';
        card.dataset.chosen = chosen;
        card.querySelectorAll('.sort-btn').forEach(b => b.disabled = true);
        ossAnswered++;
        if (ossAnswered === ossTotalCards) {
          document.getElementById('submit-oss').style.display = 'inline-flex';
        }
      }

      function showOSSResults() {
        let score = 0;
        document.querySelectorAll('#sort-cards-oss .sort-card').forEach(card => {
          const correct = card.dataset.answer;
          const chosen = card.dataset.chosen;
          const result = card.querySelector('.sort-result');
          if (chosen === correct) {
            score++;
            card.classList.add('card-correct');
            result.textContent = '✓ Correct!';
            result.style.color = '#4ade80';
          } else {
            card.classList.add('card-wrong');
            result.textContent = '✗ Incorrect';
            result.style.color = '#f87171';
          }
        });
        document.getElementById('oss-score-num').textContent = score;
        document.getElementById('oss-score').style.display = 'block';
        document.getElementById('submit-oss').style.display = 'none';
        scrollToOffset(document.getElementById('oss-score'));
      }
    </script>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('ip2-proprietary').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('ip2-proprietary'))">Next →</button>

    <div id="ip2-proprietary" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Proprietary Software</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.5rem;">For each card, decide whether it is a <strong style="color:#4ade80;">Benefit</strong> or a <strong style="color:#f87171;">Drawback</strong> of proprietary software.</p>

      <div class="sort-cards" id="sort-cards-prop">
        <div class="sort-card" data-answer="benefit">
          <div class="sort-label">Thoroughly Tested</div>
          <p class="sort-desc">Thoroughly tested by developers prior to release.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="benefit">
          <div class="sort-label">Dedicated Support</div>
          <p class="sort-desc">Supported by a dedicated team of developers employed by the copyright holder.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="benefit">
          <div class="sort-label">Quick Patches</div>
          <p class="sort-desc">Should any vulnerabilities or bugs appear, a patch will be speedily created.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="benefit">
          <div class="sort-label">Third-Party Support</div>
          <p class="sort-desc">Extensive support from third parties.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">No Source Code</div>
          <p class="sort-desc">Users don't have access to the source code.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">No Editing</div>
          <p class="sort-desc">Users aren't given permission to edit the software.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="drawback">
          <div class="sort-label">Paid & Licensed</div>
          <p class="sort-desc">Usually paid for and licensed on a per-user, per-machine basis.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerProp(this, 'benefit')">✓ Benefit</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerProp(this, 'drawback')">✗ Drawback</button>
          </div>
          <div class="sort-result"></div>
        </div>
      </div>

      <button class="next-btn" id="submit-prop" style="margin-top:1.5rem; display:none;" onclick="showPropResults()">Check Answers →</button>

      <div id="prop-score" style="display:none; margin-top:1.5rem;">
        <div class="score-box">
          <span class="score-num" id="prop-score-num">0</span>
          <span class="score-label">out of 7 correct</span>
        </div>
        <div class="correct-answers">
          <p style="font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:2px; color:var(--b2); margin-bottom:1rem;">CORRECT ANSWERS:</p>
          <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Thoroughly Tested</span></div>
          <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Dedicated Support</span></div>
          <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Quick Patches</span></div>
          <div class="answer-row"><span class="ans-benefit">✓ BENEFIT</span><span class="ans-topic">Third-Party Support</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">No Source Code</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">No Editing</span></div>
          <div class="answer-row"><span class="ans-drawback">✗ DRAWBACK</span><span class="ans-topic">Paid & Licensed</span></div>
        </div>
      </div>

      <script>
        let propAnswered = 0;
        const propTotalCards = 7;

        function submitAnswerProp(btn, chosen) {
          const card = btn.closest('.sort-card');
          if (card.dataset.answered) return;
          card.dataset.answered = 'true';
          card.dataset.chosen = chosen;
          card.querySelectorAll('.sort-btn').forEach(b => b.disabled = true);
          propAnswered++;
          if (propAnswered === propTotalCards) {
            document.getElementById('submit-prop').style.display = 'inline-flex';
          }
        }

        function showPropResults() {
          let score = 0;
          document.querySelectorAll('#sort-cards-prop .sort-card').forEach(card => {
            const correct = card.dataset.answer;
            const chosen = card.dataset.chosen;
            const result = card.querySelector('.sort-result');
            if (chosen === correct) {
              score++;
              card.classList.add('card-correct');
              result.textContent = '✓ Correct!';
              result.style.color = '#4ade80';
            } else {
              card.classList.add('card-wrong');
              result.textContent = '✗ Incorrect';
              result.style.color = '#f87171';
            }
          });
          document.getElementById('prop-score-num').textContent = score;
          document.getElementById('prop-score').style.display = 'block';
          document.getElementById('submit-prop').style.display = 'none';
          scrollToOffset(document.getElementById('prop-score'));
        }
      </script>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-8">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">08</p>
    <h2>Threats to Digital <span>Systems 1</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">A cyberattack is a malicious attempt by a hacker to gain unauthorised access to a digital system in order to cause damage or steal data.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Malware</h3>
    <a href="https://video.pictory.ai/20260503152642420216bbdb030ec48f28eb7d634267943c2/20260503160359126in6ndplJrQkxKF4" target="_blank" class="video-link-btn">
      <span>▶</span> Watch Video — Why Do Hackers Use Malware?
    </a>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('tds1-hackers').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('tds1-hackers'))">Next →</button>

    <div id="tds1-hackers" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Types of Hackers</h3>
      <div class="hackers-grid">
        <div class="hacker-card black-hat">
          <div class="hacker-icon">🖤</div>
          <h4>Black-Hat Hackers</h4>
          <p>Cybercriminals that break into systems to cause harm.</p>
        </div>
        <div class="hacker-card white-hat">
          <div class="hacker-icon">🤍</div>
          <h4>White-Hat Hackers</h4>
          <p>Help organisations strengthen their defences against cyber attacks.</p>
        </div>
      </div>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-9">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">09</p>
    <h2>Threats to Digital <span>Systems 2</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">A technical vulnerability is a hardware, software or configuration fault that makes it easier for a hacker to attack. Such a fault is called a security hole.</p>
    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Technical Vulnerabilities that Hackers Exploit</h3>

    <div class="flashcard-container">
      <div class="flashcard" onclick="this.classList.toggle('flipped')">
        <div class="flashcard-inner">
          <div class="flashcard-front">
            <span class="fc-num">01</span>
            <span class="fc-term">Unpatched Software</span>
            <span class="fc-hint">tap to reveal</span>
          </div>
          <div class="flashcard-back"><p>Hackers exchange information about known security vulnerabilities in software. They target these weaknesses. When a security flaw is discovered, the software producer must quickly produce a patch to fix the issue.</p></div>
        </div>
      </div>

      <div class="flashcard" onclick="this.classList.toggle('flipped')">
        <div class="flashcard-inner">
          <div class="flashcard-front">
            <span class="fc-num">02</span>
            <span class="fc-term">Out of Date Malware</span>
            <span class="fc-hint">tap to reveal</span>
          </div>
          <div class="flashcard-back"><p>The best defence against malware is anti-malware software. It scans files and compares them to a database of known malware signatures. It only works if the signature library is kept up to date.</p></div>
        </div>
      </div>

      <div class="flashcard" onclick="this.classList.toggle('flipped')">
        <div class="flashcard-inner">
          <div class="flashcard-front">
            <span class="fc-num">03</span>
            <span class="fc-term">Open Ports</span>
            <span class="fc-hint">tap to reveal</span>
          </div>
          <div class="flashcard-back"><p>Services that rely on the internet use dedicated computer ports to transmit information. Hackers can identify which software is running using port scanning, helping them find possible targets.</p></div>
        </div>
      </div>

      <div class="flashcard" onclick="this.classList.toggle('flipped')">
        <div class="flashcard-inner">
          <div class="flashcard-front">
            <span class="fc-num">04</span>
            <span class="fc-term">Default Admin Passwords</span>
            <span class="fc-hint">tap to reveal</span>
          </div>
          <div class="flashcard-back"><p>Some hardware devices such as routers and modems are shipped with factory-set admin passwords. Hackers can look up default passwords on the web and use password hacking software to crack weak passwords.</p></div>
        </div>
      </div>
    </div>
    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-10">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">10</p>
    <h2>Threats to Digital <span>Systems 3</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">Some hackers use social engineering techniques to make people reveal confidential information or install harmful software on their computers. Social engineering exploits human nature.</p>
    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Social Engineering Techniques and How They Work</h3>

    <div class="se-table">
      <div class="se-header">
        <div class="se-cell se-head">Technique</div>
        <div class="se-cell se-head">How It Works</div>
      </div>
      <div class="se-row" onclick="this.classList.toggle('se-expanded')">
        <div class="se-cell se-technique"><span class="se-icon">🎣</span>Phishing<span class="se-chevron">▾</span></div>
        <div class="se-cell se-detail">Victims receive an email from a seemingly reputable source. This asks them to click on a link to what appears to be a genuine website, but which is actually controlled by the hacker. Once on the website, the victim is asked to enter their ID and password or credit card details. This confidential information is then harvested by the attacker.</div>
      </div>
      <div class="se-row" onclick="this.classList.toggle('se-expanded')">
        <div class="se-cell se-technique"><span class="se-icon">🎭</span>Pretexting (Blagging)<span class="se-chevron">▾</span></div>
        <div class="se-cell se-detail">The hacker pretends to be from a trusted organisation known to the victim. The hacker says there is an emergency that has to be dealt with. By stressing the situation, the attacker panics the victim into giving away personal data.</div>
      </div>
      <div class="se-row" onclick="this.classList.toggle('se-expanded')">
        <div class="se-cell se-technique"><span class="se-icon">🪤</span>Baiting<span class="se-chevron">▾</span></div>
        <div class="se-cell se-detail">Victims are offered a free giveaway. This giveaway comes with a handful of harmful malware which infects the victim's computer.</div>
      </div>
      <div class="se-row" onclick="this.classList.toggle('se-expanded')">
        <div class="se-cell se-technique"><span class="se-icon">🤝</span>Quid Pro Quo<span class="se-chevron">▾</span></div>
        <div class="se-cell se-detail">Victims provide their login details and other security information in exchange for a service. The attacker then offers to help with the setup and installation. This gives them an opportunity to install malware.</div>
      </div>
      <div class="se-row" onclick="this.classList.toggle('se-expanded')">
        <div class="se-cell se-technique"><span class="se-icon">👁️</span>Shoulder-Surfing<span class="se-chevron">▾</span></div>
        <div class="se-cell se-detail">The hacker looks over a victim's shoulder, uses binoculars to watch from a distance, or uses a camera to note their login name, password, PIN, and more.</div>
      </div>
      <div class="se-click-hint">👆 Click any row to reveal how it works</div>
    </div>
    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-11">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">11</p>
    <h2>Protecting Digital <span>Systems 1</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:0.8rem;">There are a number of measures that can protect digital systems and data from cyberattacks.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:2rem;">Defence-in-depth involves using a combination of defence mechanisms, so that, if an attacker gets around one obstacle, they meet another and another.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Firewall</h3>

    <div class="ppt-slides">
      <div class="ppt-slide active" id="fw-slide-0">
        <div class="ppt-icon">🛡️</div>
        <h4 class="ppt-title">First Line of Defence</h4>
        <p class="ppt-text">Firewalls are the first line of defence against cyberattacks.</p>
        <div class="ppt-progress"><div class="ppt-bar" style="width:33%"></div></div>
        <div class="ppt-counter">1 / 3</div>
      </div>
      <div class="ppt-slide" id="fw-slide-1">
        <div class="ppt-icon">🔀</div>
        <h4 class="ppt-title">Barrier & Traffic Monitor</h4>
        <p class="ppt-text">A firewall acts as a barrier and monitors all incoming and outgoing network traffic.</p>
        <div class="ppt-progress"><div class="ppt-bar" style="width:66%"></div></div>
        <div class="ppt-counter">2 / 3</div>
      </div>
      <div class="ppt-slide" id="fw-slide-2">
        <div class="ppt-icon">📋</div>
        <h4 class="ppt-title">Predefined Rules</h4>
        <p class="ppt-text">Firewalls use a predefined set of rules to decide what traffic is allowed to pass from one side to another.</p>
        <div class="ppt-progress"><div class="ppt-bar" style="width:100%"></div></div>
        <div class="ppt-counter">3 / 3</div>
      </div>

      <div class="ppt-nav">
        <button class="fact-btn" id="fw-prev" onclick="changeFWSlide(-1)" disabled>← Back</button>
        <div class="fact-dots">
          <span class="fact-dot active" onclick="goToFWSlide(0)"></span>
          <span class="fact-dot" onclick="goToFWSlide(1)"></span>
          <span class="fact-dot" onclick="goToFWSlide(2)"></span>
        </div>
        <button class="fact-btn" id="fw-next" onclick="changeFWSlide(1)">Next →</button>
      </div>
    </div>

    <script>
      let fwSlide = 0;
      const fwTotal = 3;

      function changeFWSlide(dir) { goToFWSlide(fwSlide + dir); }

      function goToFWSlide(index) {
        if (index < 0 || index >= fwTotal) return;
        document.getElementById('fw-slide-' + fwSlide).classList.remove('active');
        document.querySelectorAll('.ppt-slides .fact-dot')[fwSlide].classList.remove('active');
        fwSlide = index;
        document.getElementById('fw-slide-' + fwSlide).classList.add('active');
        document.querySelectorAll('.ppt-slides .fact-dot')[fwSlide].classList.add('active');
        document.getElementById('fw-prev').disabled = fwSlide === 0;
        document.getElementById('fw-next').disabled = fwSlide === fwTotal - 1;
      }
    </script>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('pds1-antimalware').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('pds1-antimalware'))">Next →</button>

    <div id="pds1-antimalware" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1.5rem; letter-spacing:1px;">Anti-Malware Software</h3>

      <div class="ppt-slides">
        <div class="ppt-slide active" id="am-slide-0">
          <div class="ppt-icon">🔍</div>
          <h4 class="ppt-title">Best Defence</h4>
          <p class="ppt-text">The best defence against malware is <span class="hl">anti-malware software</span>.</p>
          <div class="ppt-progress"><div class="ppt-bar" style="width:20%"></div></div>
          <div class="ppt-counter">1 / 5</div>
        </div>
        <div class="ppt-slide" id="am-slide-1">
          <div class="ppt-icon">📂</div>
          <h4 class="ppt-title">Signature Scanning</h4>
          <p class="ppt-text">Traditional anti-malware works by <span class="hl">scanning files</span> and comparing them with a <span class="hl">library of known malware signatures</span>. If any signature patterns are found, the file is <span class="hl">quarantined</span> until the user decides what to do.</p>
          <div class="ppt-progress"><div class="ppt-bar" style="width:40%"></div></div>
          <div class="ppt-counter">2 / 5</div>
        </div>
        <div class="ppt-slide" id="am-slide-2">
          <div class="ppt-icon">⚠️</div>
          <h4 class="ppt-title">Expiry Risk</h4>
          <p class="ppt-text">As modern malware is constantly released, this type of protection <span class="hl">expires</span> unless its <span class="hl">signature database is refreshed</span> regularly.</p>
          <div class="ppt-progress"><div class="ppt-bar" style="width:60%"></div></div>
          <div class="ppt-counter">3 / 5</div>
        </div>
        <div class="ppt-slide" id="am-slide-3">
          <div class="ppt-icon">🧠</div>
          <h4 class="ppt-title">Heuristic Analysis</h4>
          <p class="ppt-text">More sophisticated software uses <span class="hl">heuristic analysis</span> to look for suspicious behaviours. <span class="hl">Static heuristic analysis</span> compares the source code of a suspicious file with known malware. If most of the code matches, the file is identified as malware. <a href="https://cerafor.com/blog/what-is-heuristic-analysis/" target="_blank" class="inline-link">What is Heuristic Analysis? →</a></p>
          <div class="ppt-progress"><div class="ppt-bar" style="width:80%"></div></div>
          <div class="ppt-counter">4 / 5</div>
        </div>
        <div class="ppt-slide" id="am-slide-4">
          <div class="ppt-icon">🧪</div>
          <h4 class="ppt-title">Dynamic Analysis</h4>
          <p class="ppt-text"><span class="hl">Dynamic heuristic analysis</span> isolates the suspicious file inside a <span class="hl">virtual machine (sandbox)</span> to test what would happen if it was allowed to run.</p>
          <div class="ppt-progress"><div class="ppt-bar" style="width:100%"></div></div>
          <div class="ppt-counter">5 / 5</div>
        </div>

        <div class="ppt-nav">
          <button class="fact-btn" id="am-prev" onclick="changeAMSlide(-1)" disabled>← Back</button>
          <div class="fact-dots">
            <span class="fact-dot active" onclick="goToAMSlide(0)"></span>
            <span class="fact-dot" onclick="goToAMSlide(1)"></span>
            <span class="fact-dot" onclick="goToAMSlide(2)"></span>
            <span class="fact-dot" onclick="goToAMSlide(3)"></span>
            <span class="fact-dot" onclick="goToAMSlide(4)"></span>
          </div>
          <button class="fact-btn" id="am-next" onclick="changeAMSlide(1)">Next →</button>
        </div>
      </div>

      <script>
        let amSlide = 0;
        const amTotal = 5;
        function changeAMSlide(dir) { goToAMSlide(amSlide + dir); }
        function goToAMSlide(index) {
          if (index < 0 || index >= amTotal) return;
          document.getElementById('am-slide-' + amSlide).classList.remove('active');
          document.querySelectorAll('#pds1-antimalware .fact-dot')[amSlide].classList.remove('active');
          amSlide = index;
          document.getElementById('am-slide-' + amSlide).classList.add('active');
          document.querySelectorAll('#pds1-antimalware .fact-dot')[amSlide].classList.add('active');
          document.getElementById('am-prev').disabled = amSlide === 0;
          document.getElementById('am-next').disabled = amSlide === amTotal - 1;
        }
      </script>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('pds1-encryption').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('pds1-encryption'))">Next →</button>
    </div>

    <div id="pds1-encryption" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Encryption</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.5rem;"><strong style="color:var(--b2);">Definition:</strong> The process of converting data into a scrambled format that isn't understandable.</p>

      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.5rem;">For each statement, decide whether it is <strong style="color:#4ade80;">True</strong> or <strong style="color:#f87171;">False</strong>.</p>

      <div class="sort-cards" id="sort-cards-enc">
        <div class="sort-card" data-answer="true">
          <div class="sort-label">Statement 1</div>
          <p class="sort-desc">Encryption will not prevent data from being stolen.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerEnc(this, 'true')">✓ True</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerEnc(this, 'false')">✗ False</button>
          </div>
          <div class="sort-result"></div>
        </div>
        <div class="sort-card" data-answer="true">
          <div class="sort-label">Statement 2</div>
          <p class="sort-desc">Encryption protects data's confidentiality.</p>
          <div class="sort-btns">
            <button class="sort-btn benefit-btn" onclick="submitAnswerEnc(this, 'true')">✓ True</button>
            <button class="sort-btn drawback-btn" onclick="submitAnswerEnc(this, 'false')">✗ False</button>
          </div>
          <div class="sort-result"></div>
        </div>
      </div>

      <button class="next-btn" id="submit-enc" style="margin-top:1.5rem; display:none;" onclick="showEncResults()">Check Answers →</button>

      <div id="enc-score" style="display:none; margin-top:1.5rem;">
        <div class="score-box">
          <span class="score-num" id="enc-score-num">0</span>
          <span class="score-label">out of 2 correct</span>
        </div>
        <div class="correct-answers">
          <p style="font-family:'Nunito', sans-serif; font-size:0.7rem; letter-spacing:2px; color:var(--b2); margin-bottom:1rem;">CORRECT ANSWERS:</p>
          <div class="answer-row"><span class="ans-benefit">✓ TRUE</span><span class="ans-topic">Encryption will not prevent data from being stolen</span></div>
          <div class="answer-row"><span class="ans-benefit">✓ TRUE</span><span class="ans-topic">Encryption protects data's confidentiality</span></div>
        </div>
      </div>

      <script>
        let encAnswered = 0;
        const encTotal = 2;
        function submitAnswerEnc(btn, chosen) {
          const card = btn.closest('.sort-card');
          if (card.dataset.answered) return;
          card.dataset.answered = 'true';
          card.dataset.chosen = chosen;
          card.querySelectorAll('.sort-btn').forEach(b => b.disabled = true);
          encAnswered++;
          if (encAnswered === encTotal) document.getElementById('submit-enc').style.display = 'inline-flex';
        }
        function showEncResults() {
          let score = 0;
          document.querySelectorAll('#sort-cards-enc .sort-card').forEach(card => {
            const correct = card.dataset.answer;
            const chosen = card.dataset.chosen;
            const result = card.querySelector('.sort-result');
            if (chosen === correct) {
              score++;
              card.classList.add('card-correct');
              result.textContent = '✓ Correct!';
              result.style.color = '#4ade80';
            } else {
              card.classList.add('card-wrong');
              result.textContent = '✗ Incorrect';
              result.style.color = '#f87171';
            }
          });
          document.getElementById('enc-score-num').textContent = score;
          document.getElementById('enc-score').style.display = 'block';
          document.getElementById('submit-enc').style.display = 'none';
          scrollToOffset(document.getElementById('enc-score'));
        }
      </script>

      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:2rem; margin-bottom:1.2rem;">There are two types of encryption:</p>
      <ul class="content-bullets">
        <li><strong style="color:var(--b3);">Symmetric Encryption:</strong> Uses the same key to encrypt and decrypt the data.</li>
        <li><strong style="color:var(--b3);">Asymmetric Encryption:</strong> Uses two different keys — a public key to encrypt and a private one to decrypt.</li>
      </ul>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<section class="panel content-section" id="section-12">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner">
    <p class="eyebrow">12</p>
    <h2>Protecting Digital <span>Systems 2</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:2rem;">An organisation's system and data must be protected from a wide range of threats, including natural disasters, technical failures and accidental or malicious actions of employees.</p>

    <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Backup and Recovery Procedures</h3>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-top:0.3rem; margin-bottom:1.2rem;">Having a backup and recovery procedure will not protect an organisation's data from loss or damage, but will enable it to be recovered if the worst happens.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;"><strong style="color:var(--b2);">Backing up</strong> involves making a copy of the data and storing it on a different device in a different location, offsite or in the cloud.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;"><strong style="color:var(--b2);">Recovery</strong> is the process of restoring data and/or system states from the backup copy.</p>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1rem;">Backing up is often automated. Two approaches are:</p>
    <ul class="content-bullets">
      <li><strong style="color:var(--b3);">Full Backup:</strong> A full copy is made of all the data, regardless of whether it has been changed since the last backup.</li>
      <li><strong style="color:var(--b3);">Incremental Backup:</strong> Copies new files and those changed since the last backup.</li>
    </ul>

    <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('pds2-aup').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('pds2-aup'))">Next →</button>

    <div id="pds2-aup" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">Acceptable Use Policy (AUP)</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:0.8rem;">Social engineering relies on people being tricked into behaving foolishly or making mistakes. The best tool an organisation can use to avoid this is an <strong style="color:var(--b2);">AUP</strong>.</p>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">An AUP is a collection of rules and procedures a user must follow. It states what appropriate and inappropriate behaviours would be, and the actions that will be taken if the policy is ignored.</p>

      <p style="font-size:0.85rem; font-weight:600; color:#4ade80; margin-bottom:0.6rem;">✓ Examples of appropriate behaviour:</p>
      <ul class="content-bullets" style="margin-bottom:1.5rem;">
        <li>Log off the screen when leaving a computer unattended.</li>
        <li>Use a secure password and don't tell anyone.</li>
        <li>Exercise caution when opening email attachments.</li>
      </ul>

      <p style="font-size:0.85rem; font-weight:600; color:#f87171; margin-bottom:0.6rem;">✗ Examples of inappropriate behaviour:</p>
      <ul class="content-bullets" style="margin-bottom:1.5rem;">
        <li>Install software downloaded from the web.</li>
        <li>Plug a memory stick into a USB slot.</li>
        <li>Give out confidential information over the phone or email.</li>
      </ul>

      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;">Users must sign a copy of the AUP to acknowledge that they have read it and agree to abide by it.</p>
      <button class="next-btn" style="margin-top:1.5rem;" onclick="document.getElementById('pds2-raid').style.display='block';this.style.display='none';scrollToOffset(document.getElementById('pds2-raid'))">Next →</button>
    </div>

    <div id="pds2-raid" style="display:none; margin-top:2rem;">
      <h3 style="font-size:1.3rem; font-weight:600; color:var(--b3); margin-bottom:1rem; letter-spacing:1px;">RAID</h3>
      <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:1.2rem;"><strong style="color:var(--b2);">RAID</strong> is one of the most common approaches to backing up. The contents of each hard disk on a server are replicated on a second disk. Should one disk fail, the other springs into action, allowing the failed disk to be swapped out without the server having to be shut down.</p>
    </div>

    <!-- Quiz unlock button - appears after all topics visited -->
    <div id="quiz-unlock-banner" style="display:none; margin-top:2.5rem; padding:1.5rem; background:rgba(10,132,255,0.1); border:1px solid rgba(56,189,248,0.4); border-radius:16px; max-width:600px; text-align:center;">
      <p style="font-family:'Nunito', sans-serif; font-size:0.8rem; letter-spacing:2px; color:var(--b2); margin-bottom:1rem;">🎯 YOU'VE COMPLETED ALL TOPICS!</p>
      <button class="btn-glow" onclick="smoothScrollTo('quiz')">Start Quiz Time! →</button>
    </div>

    <button class="back-btn" style="margin-top:1.5rem;" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>
<!-- QUIZ SECTION -->
<section class="panel content-section" id="quiz" style="display:none;">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="particles">
    <div class="particle" style="left:8%;top:20%;animation-delay:0s;width:3px;height:3px;"></div>
    <div class="particle" style="left:88%;top:60%;animation-delay:1.4s;width:2px;height:2px;"></div>
    <div class="particle" style="left:50%;top:10%;animation-delay:0.7s;width:3px;height:3px;"></div>
  </div>
  <div class="content-inner" style="max-width:680px;">
    <p class="eyebrow">🎯</p>
    <h2>Quiz <span>Time!</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:2rem;">Test your knowledge on everything covered in this website. Answer all 10 questions and see how you score!</p>

    <div id="quiz-container">
      <div class="quiz-card active" id="q0">
        <p class="quiz-num">Question 1 / 20</p>
        <p class="quiz-q">Approximately how many tonnes of e-waste are produced each year?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(0, this)">a) 10 million tonnes</button>
          <button class="quiz-opt" onclick="answerQuiz(0, this)">b) 50 million tonnes</button>
          <button class="quiz-opt" onclick="answerQuiz(0, this)">c) 100 million tonnes</button>
          <button class="quiz-opt" onclick="answerQuiz(0, this)">d) 5 million tonnes</button>
        </div>
        <div class="quiz-feedback" id="qf0"></div>
      </div>

      <div class="quiz-card" id="q1">
        <p class="quiz-num">Question 2 / 20</p>
        <p class="quiz-q">What percentage of e-waste is properly recycled globally?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(1, this)">a) 50%</button>
          <button class="quiz-opt" onclick="answerQuiz(1, this)">b) 20%</button>
          <button class="quiz-opt" onclick="answerQuiz(1, this)">c) 75%</button>
          <button class="quiz-opt" onclick="answerQuiz(1, this)">d) 35%</button>
        </div>
        <div class="quiz-feedback" id="qf1"></div>
      </div>

      <div class="quiz-card" id="q2">
        <p class="quiz-num">Question 3 / 20</p>
        <p class="quiz-q">What is a digital footprint?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(2, this)">a) The trail of personal data left behind each time someone uses the internet</button>
          <button class="quiz-opt" onclick="answerQuiz(2, this)">b) A type of malware that tracks your location</button>
          <button class="quiz-opt" onclick="answerQuiz(2, this)">c) A password used to log into websites</button>
          <button class="quiz-opt" onclick="answerQuiz(2, this)">d) A cookie stored on your device</button>
        </div>
        <div class="quiz-feedback" id="qf2"></div>
      </div>

      <div class="quiz-card" id="q3">
        <p class="quiz-num">Question 4 / 20</p>
        <p class="quiz-q">How long does copyright protection last?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(3, this)">a) 20 years after creation</button>
          <button class="quiz-opt" onclick="answerQuiz(3, this)">b) 10 years after publication</button>
          <button class="quiz-opt" onclick="answerQuiz(3, this)">c) 70 years after the death of the copyright holder</button>
          <button class="quiz-opt" onclick="answerQuiz(3, this)">d) 50 years after creation</button>
        </div>
        <div class="quiz-feedback" id="qf3"></div>
      </div>

      <div class="quiz-card" id="q4">
        <p class="quiz-num">Question 5 / 20</p>
        <p class="quiz-q">What is narrow AI?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(4, this)">a) AI that can perform any task a human can</button>
          <button class="quiz-opt" onclick="answerQuiz(4, this)">b) Machine-learning systems designed to perform a single task or limited range of tasks</button>
          <button class="quiz-opt" onclick="answerQuiz(4, this)">c) AI used only in military applications</button>
          <button class="quiz-opt" onclick="answerQuiz(4, this)">d) A type of encryption algorithm</button>
        </div>
        <div class="quiz-feedback" id="qf4"></div>
      </div>

      <div class="quiz-card" id="q5">
        <p class="quiz-num">Question 6 / 20</p>
        <p class="quiz-q">What does the Data Protection Act 2018 do?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(5, this)">a) Defines principles that organisations must follow when handling personal data</button>
          <button class="quiz-opt" onclick="answerQuiz(5, this)">b) Prevents all companies from collecting data</button>
          <button class="quiz-opt" onclick="answerQuiz(5, this)">c) Allows governments to access all personal data</button>
          <button class="quiz-opt" onclick="answerQuiz(5, this)">d) Regulates the use of cookies only</button>
        </div>
        <div class="quiz-feedback" id="qf5"></div>
      </div>

      <div class="quiz-card" id="q6">
        <p class="quiz-num">Question 7 / 20</p>
        <p class="quiz-q">What is phishing?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(6, this)">a) A type of firewall</button>
          <button class="quiz-opt" onclick="answerQuiz(6, this)">b) A social engineering attack where victims receive deceptive emails to steal their credentials</button>
          <button class="quiz-opt" onclick="answerQuiz(6, this)">c) A method of encrypting data</button>
          <button class="quiz-opt" onclick="answerQuiz(6, this)">d) A backup procedure</button>
        </div>
        <div class="quiz-feedback" id="qf6"></div>
      </div>

      <div class="quiz-card" id="q7">
        <p class="quiz-num">Question 8 / 20</p>
        <p class="quiz-q">What is asymmetric encryption?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(7, this)">a) Uses the same key to encrypt and decrypt data</button>
          <button class="quiz-opt" onclick="answerQuiz(7, this)">b) Converts data into plain text</button>
          <button class="quiz-opt" onclick="answerQuiz(7, this)">c) Uses two different keys — a public key to encrypt and a private key to decrypt</button>
          <button class="quiz-opt" onclick="answerQuiz(7, this)">d) A method of backing up data</button>
        </div>
        <div class="quiz-feedback" id="qf7"></div>
      </div>

      <div class="quiz-card" id="q8">
        <p class="quiz-num">Question 9 / 20</p>
        <p class="quiz-q">What is RAID used for?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(8, this)">a) Backing up data by replicating hard disk contents on a second disk</button>
          <button class="quiz-opt" onclick="answerQuiz(8, this)">b) Scanning files for malware signatures</button>
          <button class="quiz-opt" onclick="answerQuiz(8, this)">c) Monitoring network traffic</button>
          <button class="quiz-opt" onclick="answerQuiz(8, this)">d) Encrypting data in transit</button>
        </div>
        <div class="quiz-feedback" id="qf8"></div>
      </div>

      <div class="quiz-card" id="q9">
        <p class="quiz-num">Question 10 / 20</p>
        <p class="quiz-q">What does an Acceptable Use Policy (AUP) require users to do?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(9, this)">a) Install all software updates immediately</button>
          <button class="quiz-opt" onclick="answerQuiz(9, this)">b) Share their passwords with IT departments</button>
          <button class="quiz-opt" onclick="answerQuiz(9, this)">c) Use only open-source software</button>
          <button class="quiz-opt" onclick="answerQuiz(9, this)">d) Sign to acknowledge they have read and agree to follow the rules and procedures</button>
        </div>
        <div class="quiz-feedback" id="qf9"></div>
      </div>

      <div class="quiz-card" id="q10">
        <p class="quiz-num">Question 11 / 20</p>
        <p class="quiz-q">What is the average time a user keeps a mobile phone before replacing it?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(10, this)">a) 1 year</button>
          <button class="quiz-opt" onclick="answerQuiz(10, this)">b) 5 years</button>
          <button class="quiz-opt" onclick="answerQuiz(10, this)">c) Roughly every 3 years</button>
          <button class="quiz-opt" onclick="answerQuiz(10, this)">d) 10 years</button>
        </div>
        <div class="quiz-feedback" id="qf10"></div>
      </div>

      <div class="quiz-card" id="q11">
        <p class="quiz-num">Question 12 / 20</p>
        <p class="quiz-q">What is algorithmic bias?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(11, this)">a) When AI deliberately breaks rules</button>
          <button class="quiz-opt" onclick="answerQuiz(11, this)">b) When AI algorithms produce unfair or prejudiced results</button>
          <button class="quiz-opt" onclick="answerQuiz(11, this)">c) A firewall error</button>
          <button class="quiz-opt" onclick="answerQuiz(11, this)">d) A type of malware</button>
        </div>
        <div class="quiz-feedback" id="qf11"></div>
      </div>

      <div class="quiz-card" id="q12">
        <p class="quiz-num">Question 13 / 20</p>
        <p class="quiz-q">What does a patent protect and for how long?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(12, this)">a) Creative works for 70 years</button>
          <button class="quiz-opt" onclick="answerQuiz(12, this)">b) Company logos for 10 years</button>
          <button class="quiz-opt" onclick="answerQuiz(12, this)">c) New inventions for 20 years</button>
          <button class="quiz-opt" onclick="answerQuiz(12, this)">d) Software code for 50 years</button>
        </div>
        <div class="quiz-feedback" id="qf12"></div>
      </div>

      <div class="quiz-card" id="q13">
        <p class="quiz-num">Question 14 / 20</p>
        <p class="quiz-q">What is shoulder-surfing?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(13, this)">a) A type of data encryption</button>
          <button class="quiz-opt" onclick="answerQuiz(13, this)">b) When a hacker watches a victim to note their login details</button>
          <button class="quiz-opt" onclick="answerQuiz(13, this)">c) A backup method using cloud storage</button>
          <button class="quiz-opt" onclick="answerQuiz(13, this)">d) A technique for scanning ports</button>
        </div>
        <div class="quiz-feedback" id="qf13"></div>
      </div>

      <div class="quiz-card" id="q14">
        <p class="quiz-num">Question 15 / 20</p>
        <p class="quiz-q">What is the difference between open-source and proprietary software?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(14, this)">a) Open-source is always paid for; proprietary is free</button>
          <button class="quiz-opt" onclick="answerQuiz(14, this)">b) Open-source code is accessible to all; proprietary code is closed and owned by the copyright holder</button>
          <button class="quiz-opt" onclick="answerQuiz(14, this)">c) There is no difference</button>
          <button class="quiz-opt" onclick="answerQuiz(14, this)">d) Proprietary software can be modified by anyone</button>
        </div>
        <div class="quiz-feedback" id="qf14"></div>
      </div>

      <div class="quiz-card" id="q15">
        <p class="quiz-num">Question 16 / 20</p>
        <p class="quiz-q">What is a firewall's main function?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(15, this)">a) To scan files for viruses</button>
          <button class="quiz-opt" onclick="answerQuiz(15, this)">b) To back up data automatically</button>
          <button class="quiz-opt" onclick="answerQuiz(15, this)">c) To monitor and filter incoming and outgoing network traffic using predefined rules</button>
          <button class="quiz-opt" onclick="answerQuiz(15, this)">d) To encrypt all data on a device</button>
        </div>
        <div class="quiz-feedback" id="qf15"></div>
      </div>

      <div class="quiz-card" id="q16">
        <p class="quiz-num">Question 17 / 20</p>
        <p class="quiz-q">What does heuristic analysis in anti-malware software do?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(16, this)">a) Compares files against a list of known safe files</button>
          <button class="quiz-opt" onclick="answerQuiz(16, this)">b) Looks for suspicious behaviours that could indicate new or unknown malware</button>
          <button class="quiz-opt" onclick="answerQuiz(16, this)">c) Backs up data to the cloud</button>
          <button class="quiz-opt" onclick="answerQuiz(16, this)">d) Monitors social media activity</button>
        </div>
        <div class="quiz-feedback" id="qf16"></div>
      </div>

      <div class="quiz-card" id="q17">
        <p class="quiz-num">Question 18 / 20</p>
        <p class="quiz-q">What is the difference between a full backup and an incremental backup?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(17, this)">a) A full backup only saves new files; incremental saves everything</button>
          <button class="quiz-opt" onclick="answerQuiz(17, this)">b) A full backup copies all data; incremental only copies new or changed files since the last backup</button>
          <button class="quiz-opt" onclick="answerQuiz(17, this)">c) They are the same thing</button>
          <button class="quiz-opt" onclick="answerQuiz(17, this)">d) Incremental backups are stored offsite; full backups are not</button>
        </div>
        <div class="quiz-feedback" id="qf17"></div>
      </div>

      <div class="quiz-card" id="q18">
        <p class="quiz-num">Question 19 / 20</p>
        <p class="quiz-q">Which regulation governs the use of cookies in the UK?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(18, this)">a) The Data Protection Act 2018</button>
          <button class="quiz-opt" onclick="answerQuiz(18, this)">b) The Computer Misuse Act</button>
          <button class="quiz-opt" onclick="answerQuiz(18, this)">c) The Privacy and Electronic Communication Regulations 2003</button>
          <button class="quiz-opt" onclick="answerQuiz(18, this)">d) The Copyright Designs and Patent Act 1988</button>
        </div>
        <div class="quiz-feedback" id="qf18"></div>
      </div>

      <div class="quiz-card" id="q19">
        <p class="quiz-num">Question 20 / 20</p>
        <p class="quiz-q">Which of the following is an example of responsible digital device ownership?</p>
        <div class="quiz-opts">
          <button class="quiz-opt" onclick="answerQuiz(19, this)">a) Buying the latest device every year</button>
          <button class="quiz-opt" onclick="answerQuiz(19, this)">b) Donating unwanted devices to charity or a recycling company</button>
          <button class="quiz-opt" onclick="answerQuiz(19, this)">c) Throwing old devices in the bin</button>
          <button class="quiz-opt" onclick="answerQuiz(19, this)">d) Keeping Bluetooth always on</button>
        </div>
        <div class="quiz-feedback" id="qf19"></div>
      </div>

      <div id="quiz-result" style="display:none; margin-top:2rem; text-align:center;">
        <div class="score-box" style="justify-content:center;">
          <span class="score-num" id="quiz-score-num">0</span>
          <span class="score-label">out of 20</span>
        </div>
        <p class="quiz-result-msg" id="quiz-result-msg"></p>
        <button class="next-btn" style="margin-top:1.5rem;" onclick="resetQuiz()">🔄 Try Again</button>
      </div>
    </div>

    <button class="back-btn" style="margin-top:2rem;" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<!-- AI ENERGY CALCULATOR -->
<section class="panel content-section" id="ai-calculator">
  <div class="rings"><div class="ring"></div><div class="ring"></div><div class="ring"></div><div class="ring"></div></div>
  <div class="content-inner" style="max-width:680px;">
    <p class="eyebrow">⚡</p>
    <h2>AI Energy <span>Calculator</span></h2>
    <p class="section-desc" style="max-width:600px; line-height:1.4; margin-bottom:2rem;">How much energy does your daily AI use actually consume? Drag the sliders to find out — and see the real environmental cost of your digital habits.</p>

    <div class="ai-calc">
      <div class="calc-row">
        <span class="calc-label">🤖 AI chat queries per day</span>
        <input type="range" class="calc-slider" id="sl-queries" min="1" max="100" value="10" oninput="updateCalc()">
        <span class="calc-val" id="v-queries">10</span>
      </div>
      <div class="calc-row">
        <span class="calc-label">🖼️ AI images generated per day</span>
        <input type="range" class="calc-slider" id="sl-images" min="0" max="50" value="2" oninput="updateCalc()">
        <span class="calc-val" id="v-images">2</span>
      </div>
      <div class="calc-row">
        <span class="calc-label">🔍 Google searches per day</span>
        <input type="range" class="calc-slider" id="sl-searches" min="0" max="200" value="20" oninput="updateCalc()">
        <span class="calc-val" id="v-searches">20</span>
      </div>
      <div class="calc-row">
        <span class="calc-label">📺 Hours of video streaming per day</span>
        <input type="range" class="calc-slider" id="sl-video" min="0" max="12" value="2" oninput="updateCalc()">
        <span class="calc-val" id="v-video">2h</span>
      </div>

      <div class="calc-results">
        <div class="calc-result-box">
          <span class="calc-result-val" id="r-wh">0</span>
          <p class="calc-result-lbl">Wh / day</p>
        </div>
        <div class="calc-result-box">
          <span class="calc-result-val" id="r-yearly">0</span>
          <p class="calc-result-lbl">kWh / year</p>
        </div>
        <div class="calc-result-box">
          <span class="calc-result-val" id="r-water">0</span>
          <p class="calc-result-lbl">ml water / day</p>
        </div>
      </div>

      <div class="calc-meter"><div class="calc-meter-fill" id="calc-meter-fill" style="width:0%"></div></div>
      <p class="calc-impact-msg" id="calc-impact-msg"></p>
    </div>

    <button class="back-btn" onclick="smoothScrollTo('toc')">← Back to Contents</button>
  </div>
</section>

<script>
  function updateCalc() {
    const queries = parseInt(document.getElementById('sl-queries').value);
    const images  = parseInt(document.getElementById('sl-images').value);
    const searches= parseInt(document.getElementById('sl-searches').value);
    const video   = parseInt(document.getElementById('sl-video').value);

    document.getElementById('v-queries').textContent  = queries;
    document.getElementById('v-images').textContent   = images;
    document.getElementById('v-searches').textContent = searches;
    document.getElementById('v-video').textContent    = video + 'h';

    // Energy constants (Wh)
    const whQuery   = 0.34;   // per AI query (OpenAI/Sam Altman figure)
    const whImage   = 2.9;    // per AI image (higher compute)
    const whSearch  = 0.03;   // per Google search
    const whVideo   = 100;    // per hour of HD streaming

    // Water constants (ml)
    const mlQuery   = 0.32;   // ~0.000085 gallons per query
    const mlImage   = 3.0;
    const mlSearch  = 0.01;
    const mlVideo   = 5;

    const totalWh = (queries * whQuery) + (images * whImage) + (searches * whSearch) + (video * whVideo);
    const totalMl = (queries * mlQuery) + (images * mlImage) + (searches * mlSearch) + (video * mlVideo);
    const yearlyKwh = (totalWh * 365 / 1000).toFixed(1);

    document.getElementById('r-wh').textContent    = totalWh.toFixed(1);
    document.getElementById('r-yearly').textContent= yearlyKwh;
    document.getElementById('r-water').textContent = Math.round(totalMl);

    // Impact meter (max ~500Wh)
    const pct = Math.min((totalWh / 500) * 100, 100);
    document.getElementById('calc-meter-fill').style.width = pct + '%';

    const msg = document.getElementById('calc-impact-msg');
    if (totalWh < 20)       msg.textContent = '🌱 Light footprint — equivalent to running a lightbulb for ' + Math.round(totalWh * 6) + ' minutes.';
    else if (totalWh < 80)  msg.textContent = '⚠️ Moderate footprint — equivalent to charging your phone ' + Math.round(totalWh / 12) + ' times.';
    else if (totalWh < 200) msg.textContent = '🔴 High footprint — equivalent to driving ' + (totalWh * 0.004).toFixed(1) + ' km in a petrol car.';
    else                    msg.textContent = '🚨 Very high footprint — equivalent to powering a fridge for ' + Math.round(totalWh / 150) + ' days!';
  }
  updateCalc();
</script>

</body>
</html>
