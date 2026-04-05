
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AssetShield — Digital Asset Protection</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #050a0f;
    --bg2: #0a1118;
    --bg3: #0f1923;
    --card: #111c26;
    --card2: #162030;
    --border: rgba(0,200,255,0.1);
    --border2: rgba(0,200,255,0.2);
    --cyan: #00c8ff;
    --cyan2: #00e5ff;
    --green: #00ff9d;
    --amber: #ffb800;
    --red: #ff4757;
    --purple: #a855f7;
    --text: #e8f4ff;
    --text2: #7a9ab8;
    --text3: #4a6a88;
    --font-head: 'Syne', sans-serif;
    --font-body: 'DM Sans', sans-serif;
    --font-mono: 'JetBrains Mono', monospace;
    --glow: 0 0 20px rgba(0,200,255,0.15);
    --glow-strong: 0 0 40px rgba(0,200,255,0.25);
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    font-size: 15px;
    line-height: 1.6;
    overflow-x: hidden;
  }
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(0,200,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,200,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none; z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    background: rgba(5,10,15,0.9);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    padding: 0 2rem;
    height: 64px;
    display: flex; align-items: center; justify-content: space-between;
  }
  .nav-logo {
    font-family: var(--font-head);
    font-size: 1.3rem;
    font-weight: 800;
    color: var(--cyan);
    letter-spacing: -0.5px;
    display: flex; align-items: center; gap: 10px;
    cursor: pointer;
  }
  .nav-logo .shield-icon {
    width: 28px; height: 32px;
    background: linear-gradient(135deg, var(--cyan), var(--purple));
    clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
    display: flex; align-items: center; justify-content: center;
    font-size: 12px;
  }
  .nav-links { display: flex; gap: 2rem; align-items: center; }
  .nav-links a {
    color: var(--text2); text-decoration: none; font-size: 14px;
    transition: color 0.2s; cursor: pointer;
  }
  .nav-links a:hover { color: var(--cyan); }
  .nav-btn {
    background: var(--cyan);
    color: #000;
    border: none;
    padding: 8px 20px;
    border-radius: 6px;
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 13px;
    cursor: pointer;
    transition: all 0.2s;
  }
  .nav-btn:hover { background: var(--cyan2); transform: translateY(-1px); }

  main { padding-top: 64px; position: relative; z-index: 1; }

  /* HERO */
  .hero {
    min-height: 90vh;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    text-align: center;
    padding: 4rem 2rem;
    position: relative;
  }
  .hero::before {
    content: '';
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(0,200,255,0.08) 0%, transparent 70%);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    pointer-events: none;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(0,200,255,0.08);
    border: 1px solid var(--border2);
    border-radius: 20px;
    padding: 6px 16px;
    font-size: 12px;
    font-family: var(--font-mono);
    color: var(--cyan);
    margin-bottom: 2rem;
    animation: fadeDown 0.6s ease both;
  }
  .hero-badge .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }
  @keyframes fadeDown { from{opacity:0;transform:translateY(-12px)} to{opacity:1;transform:translateY(0)} }
  @keyframes fadeUp { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }
  @keyframes slideIn { from{opacity:0;transform:translateX(-20px)} to{opacity:1;transform:translateX(0)} }
  @keyframes spin { to{transform:rotate(360deg)} }

  .hero h1 {
    font-family: var(--font-head);
    font-size: clamp(2.8rem, 6vw, 5.5rem);
    font-weight: 800;
    line-height: 1.05;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.7s 0.1s ease both;
  }
  .hero h1 .accent { color: var(--cyan); }
  .hero h1 .line2 { display: block; color: var(--text2); font-weight: 600; }
  .hero-desc {
    max-width: 560px;
    color: var(--text2);
    font-size: 1.05rem;
    margin-bottom: 2.5rem;
    animation: fadeUp 0.7s 0.2s ease both;
  }
  .hero-actions {
    display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center;
    animation: fadeUp 0.7s 0.3s ease both;
  }
  .btn-primary {
    background: var(--cyan);
    color: #000;
    border: none;
    padding: 14px 32px;
    border-radius: 8px;
    font-family: var(--font-body);
    font-weight: 700;
    font-size: 15px;
    cursor: pointer;
    transition: all 0.2s;
    display: flex; align-items: center; gap: 8px;
  }
  .btn-primary:hover { background: var(--cyan2); transform: translateY(-2px); box-shadow: 0 8px 30px rgba(0,200,255,0.3); }
  .btn-secondary {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border2);
    padding: 14px 32px;
    border-radius: 8px;
    font-family: var(--font-body);
    font-weight: 500;
    font-size: 15px;
    cursor: pointer;
    transition: all 0.2s;
  }
  .btn-secondary:hover { border-color: var(--cyan); color: var(--cyan); }

  /* STATS ROW */
  .stats-row {
    display: flex; justify-content: center; gap: 3rem; flex-wrap: wrap;
    padding: 2rem 2rem 4rem;
    animation: fadeUp 0.7s 0.4s ease both;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: var(--font-head);
    font-size: 2rem;
    font-weight: 800;
    color: var(--cyan);
  }
  .stat-label { font-size: 12px; color: var(--text3); text-transform: uppercase; letter-spacing: 1px; margin-top: 2px; }

  section { padding: 5rem 2rem; max-width: 1200px; margin: 0 auto; }
  .section-tag {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--cyan);
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: var(--font-head);
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    font-weight: 800;
    margin-bottom: 1rem;
    line-height: 1.15;
  }
  .section-sub { color: var(--text2); max-width: 560px; margin-bottom: 3rem; }

  /* ARCHITECTURE DIAGRAM */
  .arch-container {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem;
    margin-bottom: 2rem;
    overflow: hidden;
    position: relative;
  }
  .arch-container::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
  }

  /* FEATURE CARDS */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 1.5rem;
  }
  .feature-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.8rem;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    cursor: pointer;
  }
  .feature-card::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,200,255,0.03), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .feature-card:hover { border-color: var(--border2); transform: translateY(-4px); box-shadow: var(--glow); }
  .feature-card:hover::before { opacity: 1; }
  .feature-icon {
    width: 48px; height: 48px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 1.2rem;
    font-size: 22px;
  }
  .icon-cyan { background: rgba(0,200,255,0.12); color: var(--cyan); }
  .icon-green { background: rgba(0,255,157,0.12); color: var(--green); }
  .icon-amber { background: rgba(255,184,0,0.12); color: var(--amber); }
  .icon-purple { background: rgba(168,85,247,0.12); color: var(--purple); }
  .icon-red { background: rgba(255,71,87,0.12); color: var(--red); }
  .feature-title {
    font-family: var(--font-head);
    font-size: 1.05rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }
  .feature-desc { color: var(--text2); font-size: 14px; line-height: 1.6; }
  .feature-tag {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--cyan);
    background: rgba(0,200,255,0.08);
    border: 1px solid rgba(0,200,255,0.2);
    border-radius: 4px;
    padding: 2px 8px;
    margin-top: 1rem;
  }

  /* WORKFLOW */
  .workflow { padding: 5rem 2rem; background: var(--bg2); }
  .workflow-inner { max-width: 1200px; margin: 0 auto; }
  .steps-row {
    display: flex;
    gap: 0;
    margin-top: 3rem;
    overflow-x: auto;
    padding-bottom: 1rem;
  }
  .step {
    flex: 1;
    min-width: 160px;
    position: relative;
    text-align: center;
  }
  .step:not(:last-child)::after {
    content: '';
    position: absolute;
    top: 24px;
    left: 60%;
    width: calc(80%);
    height: 1px;
    background: linear-gradient(90deg, var(--cyan), transparent);
  }
  .step-num {
    width: 48px; height: 48px;
    border-radius: 50%;
    border: 1.5px solid var(--cyan);
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 1rem;
    font-family: var(--font-mono);
    font-size: 14px;
    font-weight: 500;
    color: var(--cyan);
    background: rgba(0,200,255,0.08);
    position: relative; z-index: 1;
  }
  .step-label { font-size: 13px; font-weight: 500; color: var(--text2); line-height: 1.4; }

  /* DEMO SECTION */
  .demo-section { padding: 5rem 2rem; }
  .demo-inner { max-width: 1200px; margin: 0 auto; }
  .demo-tabs { display: flex; gap: 0.5rem; margin-bottom: 1.5rem; flex-wrap: wrap; }
  .tab-btn {
    background: var(--card);
    border: 1px solid var(--border);
    color: var(--text2);
    padding: 10px 20px;
    border-radius: 8px;
    font-family: var(--font-body);
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
  }
  .tab-btn:hover { color: var(--cyan); border-color: var(--border2); }
  .tab-btn.active { background: rgba(0,200,255,0.1); border-color: var(--cyan); color: var(--cyan); }
  .tab-content { display: none; }
  .tab-content.active { display: block; animation: fadeUp 0.3s ease; }

  /* DEMO PANELS */
  .demo-panel {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }
  .panel-header {
    padding: 1rem 1.5rem;
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 10px;
    background: var(--card2);
  }
  .panel-dots { display: flex; gap: 6px; }
  .panel-dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }
  .panel-title { font-family: var(--font-mono); font-size: 12px; color: var(--text3); }
  .panel-body { padding: 1.5rem; }

  /* URL SCANNER */
  .url-input-row { display: flex; gap: 0.75rem; margin-bottom: 1.5rem; }
  .url-input {
    flex: 1;
    background: var(--bg3);
    border: 1px solid var(--border2);
    border-radius: 8px;
    color: var(--text);
    font-family: var(--font-mono);
    font-size: 13px;
    padding: 12px 16px;
    outline: none;
    transition: border-color 0.2s;
  }
  .url-input:focus { border-color: var(--cyan); }
  .scan-btn {
    background: var(--cyan);
    color: #000;
    border: none;
    padding: 12px 24px;
    border-radius: 8px;
    font-weight: 700;
    font-size: 13px;
    cursor: pointer;
    font-family: var(--font-body);
    transition: all 0.2s;
    white-space: nowrap;
  }
  .scan-btn:hover { background: var(--cyan2); }
  .scan-btn:disabled { opacity: 0.5; cursor: not-allowed; }
  .scan-progress { display: none; margin-bottom: 1.5rem; }
  .scan-progress.active { display: block; }
  .progress-label {
    display: flex; justify-content: space-between;
    font-size: 12px; color: var(--text3); margin-bottom: 6px;
    font-family: var(--font-mono);
  }
  .progress-bar { height: 4px; border-radius: 2px; background: var(--card2); overflow: hidden; }
  .progress-fill { height: 100%; border-radius: 2px; background: linear-gradient(90deg,var(--cyan),var(--purple)); transition: width 0.3s; }
  .log-lines {
    margin-top: 1rem;
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1rem;
    height: 160px;
    overflow-y: auto;
    font-family: var(--font-mono);
    font-size: 11px;
    line-height: 1.8;
  }
  .log-cyan { color: var(--cyan); }
  .log-red { color: var(--red); }
  .log-green { color: var(--green); }
  .log-amber { color: var(--amber); }

  /* RESULTS GRID */
  .results-grid {
    display: none;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    margin-bottom: 1.5rem;
  }
  .results-grid.show { display: grid; animation: fadeUp 0.4s ease; }
  .result-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 1rem;
    display: flex; align-items: center; gap: 1rem;
    position: relative;
    transition: all 0.2s;
  }
  .result-card:hover { border-color: var(--border2); }
  .result-thumb { font-size: 2rem; }
  .result-badge {
    position: absolute; top: 8px; right: 8px;
    font-family: var(--font-mono); font-size: 9px; font-weight: 700;
    padding: 2px 8px; border-radius: 3px;
  }
  .badge-match { background: rgba(255,71,87,0.15); color: var(--red); border: 1px solid rgba(255,71,87,0.3); }
  .badge-clean { background: rgba(0,255,157,0.1); color: var(--green); border: 1px solid rgba(0,255,157,0.2); }
  .result-name { font-size: 12px; font-weight: 600; margin-bottom: 2px; font-family: var(--font-mono); }
  .result-conf { font-size: 11px; font-family: var(--font-mono); }

  /* SUMMARY BANNER */
  .summary-banner {
    display: none;
    background: var(--card2);
    border: 1px solid var(--border2);
    border-radius: 12px;
    padding: 1.2rem 1.5rem;
    flex-direction: row; align-items: center; justify-content: space-between; gap: 1rem;
    flex-wrap: wrap;
  }
  .summary-banner.show { display: flex; animation: fadeUp 0.4s ease; }
  .summary-stats { display: flex; gap: 2rem; }
  .summary-stat-val { font-family: var(--font-head); font-size: 1.8rem; font-weight: 800; }
  .summary-stat-val.cyan { color: var(--cyan); }
  .summary-stat-val.red { color: var(--red); }
  .summary-stat-label { font-size: 11px; color: var(--text3); text-transform: uppercase; letter-spacing: 1px; font-family: var(--font-mono); }

  /* UPLOAD ZONE */
  .upload-zone {
    border: 2px dashed var(--border2);
    border-radius: 12px;
    padding: 3rem;
    text-align: center;
    cursor: pointer;
    transition: all 0.3s;
    margin-bottom: 1.5rem;
    position: relative;
  }
  .upload-zone:hover { border-color: var(--cyan); background: rgba(0,200,255,0.03); }
  .upload-zone.dragover { border-color: var(--cyan); background: rgba(0,200,255,0.06); }
  .upload-icon { font-size: 3rem; margin-bottom: 1rem; display: block; }
  .upload-text { font-weight: 600; margin-bottom: 0.5rem; }
  .upload-sub { font-size: 13px; color: var(--text3); }
  .upload-zone input[type=file] { position: absolute; inset: 0; opacity: 0; cursor: pointer; width: 100%; height: 100%; }

  /* FP DISPLAY */
  .fp-display {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    display: none;
  }
  .fp-display.show { display: block; animation: fadeUp 0.4s ease; }
  .fp-row {
    display: flex; align-items: center; justify-content: space-between;
    padding: 0.8rem 1rem;
    border-bottom: 1px solid var(--border);
  }
  .fp-row:last-of-type { border-bottom: none; }
  .fp-label { font-size: 12px; color: var(--text3); font-family: var(--font-mono); }
  .fp-value { font-size: 12px; font-weight: 600; font-family: var(--font-mono); }
  .fp-hash {
    padding: 1rem;
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--text3);
    background: var(--card2);
    border-top: 1px solid var(--border);
    line-height: 2;
  }
  .fp-hash span { color: var(--cyan); }

  /* AI ANALYSIS BOX */
  .ai-analysis-box {
    background: var(--bg3);
    border: 1px solid rgba(168,85,247,0.3);
    border-radius: 10px;
    padding: 1rem 1.2rem;
    margin-top: 1rem;
    display: none;
  }
  .ai-analysis-box.show { display: block; animation: fadeUp 0.4s ease; }
  .ai-analysis-title { font-family: var(--font-mono); font-size: 11px; color: var(--purple); margin-bottom: 0.5rem; }
  .ai-analysis-text { font-size: 13px; color: var(--text2); line-height: 1.7; }

  /* ALERTS */
  .alerts-list { display: flex; flex-direction: column; gap: 0.75rem; }
  .alert-item {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-left: 3px solid transparent;
    border-radius: 10px;
    padding: 1rem 1.2rem;
    display: flex; align-items: flex-start; gap: 1rem;
    transition: all 0.2s;
  }
  .alert-item:hover { border-color: var(--border2); }
  .alert-item.high { border-left-color: var(--red); }
  .alert-item.med { border-left-color: var(--amber); }
  .alert-item.low { border-left-color: var(--green); }
  .alert-item.dismissed { opacity: 0.4; transition: opacity 0.3s; }
  .alert-icon { font-size: 18px; flex-shrink: 0; margin-top: 2px; }
  .alert-site { font-weight: 600; font-size: 14px; margin-bottom: 2px; }
  .alert-meta { font-size: 12px; color: var(--text3); font-family: var(--font-mono); }
  .alert-actions { display: flex; gap: 8px; margin-top: 8px; flex-wrap: wrap; }
  .alert-btn {
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 5px;
    border: 1px solid var(--border2);
    background: transparent;
    color: var(--text2);
    cursor: pointer;
    font-family: var(--font-body);
    transition: all 0.2s;
  }
  .alert-btn:hover { border-color: var(--cyan); color: var(--cyan); }
  .alert-btn.danger { border-color: rgba(255,71,87,0.3); color: var(--red); }
  .alert-btn.danger:hover { background: rgba(255,71,87,0.1); }
  .risk-badge {
    font-size: 10px; font-weight: 700;
    padding: 3px 10px; border-radius: 4px;
    font-family: var(--font-mono);
    margin-left: auto; flex-shrink: 0;
  }
  .risk-high { background: rgba(255,71,87,0.15); color: var(--red); border: 1px solid rgba(255,71,87,0.3); }
  .risk-med { background: rgba(255,184,0,0.12); color: var(--amber); border: 1px solid rgba(255,184,0,0.3); }
  .risk-low { background: rgba(0,255,157,0.1); color: var(--green); border: 1px solid rgba(0,255,157,0.2); }

  /* ANALYTICS */
  .analytics-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; }
  .analytics-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.5rem;
    transition: all 0.2s;
  }
  .analytics-card:hover { border-color: var(--border2); }
  .analytics-title { font-family: var(--font-head); font-size: 11px; font-weight: 700; margin-bottom: 1.5rem; color: var(--text2); text-transform: uppercase; letter-spacing: 1px; }
  .chart-bar-row { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .chart-bar-label { font-size: 11px; color: var(--text3); width: 50px; text-align: right; }
  .chart-bar-wrap { flex: 1; height: 8px; background: var(--bg3); border-radius: 4px; overflow: hidden; }
  .chart-bar { height: 100%; border-radius: 4px; background: linear-gradient(90deg, var(--cyan), var(--purple)); transition: width 0.6s ease; }
  .chart-bar-val { font-family: var(--font-mono); font-size: 11px; color: var(--text2); width: 36px; }

  .donut-row { display: flex; align-items: center; gap: 2rem; justify-content: center; margin-top: 1rem; }
  .donut-wrap { position: relative; }
  .donut-center {
    position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
    text-align: center;
  }
  .donut-num { font-family: var(--font-head); font-size: 1.4rem; font-weight: 800; color: var(--text); }
  .donut-sub { font-size: 9px; color: var(--text3); font-family: var(--font-mono); }
  .donut-legend { display: flex; flex-direction: column; gap: 8px; }
  .legend-item { display: flex; align-items: center; gap: 8px; font-size: 12px; }
  .legend-dot { width: 8px; height: 8px; border-radius: 50%; }

  /* METRICS ROW */
  .metrics-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
    margin-bottom: 3rem;
  }
  .metric-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.2rem 1.4rem;
    position: relative;
    overflow: hidden;
    transition: all 0.2s;
  }
  .metric-card::after {
    content: '';
    position: absolute; bottom: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .metric-card:hover::after { opacity: 1; }
  .metric-label { font-size: 11px; color: var(--text3); text-transform: uppercase; letter-spacing: 1px; font-family: var(--font-mono); margin-bottom: 8px; }
  .metric-val { font-family: var(--font-head); font-size: 1.8rem; font-weight: 800; }
  .metric-change { font-size: 11px; margin-top: 4px; }
  .change-up { color: var(--green); }
  .change-down { color: var(--red); }

  /* EXTENSION */
  .ext-demo { background: var(--bg3); border: 1px solid var(--border); border-radius: 12px; overflow: hidden; margin-bottom: 1.5rem; }
  .ext-browser-bar {
    background: var(--card2);
    border-bottom: 1px solid var(--border);
    padding: 0.75rem 1rem;
    display: flex; align-items: center; gap: 10px;
  }
  .ext-url-bar {
    flex: 1;
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 5px;
    padding: 5px 12px;
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--text2);
  }
  .ext-page {
    padding: 1.5rem;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }
  .ext-img-card {
    border-radius: 8px;
    overflow: hidden;
    border: 2px solid transparent;
    transition: all 0.3s;
    position: relative;
    cursor: pointer;
  }
  .ext-img-card:hover { border-color: var(--border2); }
  .ext-img-card.flagged { border-color: var(--red); }
  .ext-img-thumb {
    height: 70px;
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem;
  }
  .ext-flag-popup {
    position: absolute; top: 4px; left: 4px; right: 4px;
    background: rgba(255,71,87,0.9);
    color: #fff;
    font-size: 9px;
    font-family: var(--font-mono);
    padding: 3px 6px;
    border-radius: 3px;
    display: none;
  }
  .ext-img-card.flagged .ext-flag-popup { display: block; }
  .ext-alert-popup {
    background: rgba(0,0,0,0.95);
    border: 1px solid var(--red);
    border-radius: 10px;
    padding: 1rem 1.2rem;
    margin: 0 1.5rem 1.5rem;
    display: flex; align-items: flex-start; gap: 12px;
    animation: slideIn 0.4s ease;
  }
  .ext-alert-icon { font-size: 20px; flex-shrink: 0; }
  .ext-alert-title { font-weight: 700; font-size: 13px; color: var(--red); margin-bottom: 4px; }
  .ext-alert-desc { font-size: 12px; color: var(--text2); }
  .ext-alert-conf { font-family: var(--font-mono); font-size: 11px; color: var(--amber); margin-top: 4px; }

  /* REVERSE SEARCH */
  .reverse-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    margin-top: 1.5rem;
  }
  .reverse-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    transition: all 0.2s;
    cursor: pointer;
  }
  .reverse-card:hover { border-color: var(--border2); transform: translateY(-2px); }
  .reverse-thumb {
    height: 100px;
    display: flex; align-items: center; justify-content: center;
    font-size: 3rem;
    background: linear-gradient(135deg, var(--card2), var(--bg3));
    border-bottom: 1px solid var(--border);
  }
  .reverse-info { padding: 0.75rem; }
  .reverse-site { font-size: 12px; font-weight: 600; margin-bottom: 4px; }
  .reverse-url { font-family: var(--font-mono); font-size: 10px; color: var(--text3); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .match-bar { margin-top: 8px; }
  .match-label { display: flex; justify-content: space-between; font-size: 10px; color: var(--text3); font-family: var(--font-mono); margin-bottom: 4px; }
  .match-progress { height: 3px; background: var(--card2); border-radius: 2px; overflow: hidden; }
  .match-fill { height: 100%; background: var(--cyan); border-radius: 2px; transition: width 0.8s ease; }

  /* CTA SECTION */
  .cta-section { padding: 5rem 2rem; text-align: center; background: var(--bg2); }
  .cta-inner { max-width: 700px; margin: 0 auto; }
  .cta-title { font-family: var(--font-head); font-size: clamp(2rem, 4vw, 3.5rem); font-weight: 800; margin-bottom: 1rem; }
  .cta-desc { color: var(--text2); margin-bottom: 2rem; }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem;
    text-align: center;
    color: var(--text3);
    font-size: 13px;
    font-family: var(--font-mono);
  }
  footer span { color: var(--cyan); }

  /* MODAL */
  .modal-overlay {
    position: fixed; inset: 0; z-index: 200;
    background: rgba(0,0,0,0.8);
    backdrop-filter: blur(8px);
    display: none; align-items: center; justify-content: center;
    padding: 1rem;
  }
  .modal-overlay.show { display: flex; }
  .modal {
    background: var(--card);
    border: 1px solid var(--border2);
    border-radius: 16px;
    padding: 2rem;
    max-width: 600px;
    width: 100%;
    max-height: 80vh;
    overflow-y: auto;
    animation: fadeUp 0.3s ease;
    position: relative;
  }
  .modal-close {
    position: absolute; top: 1rem; right: 1rem;
    background: none; border: none; color: var(--text3);
    cursor: pointer; font-size: 1.2rem; padding: 4px;
    transition: color 0.2s;
  }
  .modal-close:hover { color: var(--text); }
  .modal-title { font-family: var(--font-head); font-size: 1.3rem; font-weight: 700; margin-bottom: 0.5rem; }
  .modal-sub { color: var(--text3); font-size: 13px; font-family: var(--font-mono); margin-bottom: 1.5rem; }
  .dmca-field { margin-bottom: 1rem; }
  .dmca-label { font-size: 12px; color: var(--text3); font-family: var(--font-mono); margin-bottom: 4px; display: block; }
  .dmca-input {
    width: 100%;
    background: var(--bg3);
    border: 1px solid var(--border2);
    border-radius: 8px;
    color: var(--text);
    font-family: var(--font-body);
    font-size: 13px;
    padding: 10px 14px;
    outline: none;
    transition: border-color 0.2s;
  }
  .dmca-input:focus { border-color: var(--cyan); }
  .dmca-textarea { resize: vertical; min-height: 120px; }
  .dmca-notice-output {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1rem;
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--text2);
    line-height: 1.8;
    white-space: pre-wrap;
    display: none;
    margin-top: 1rem;
  }
  .dmca-notice-output.show { display: block; }

  /* TOAST */
  .toast-container {
    position: fixed; bottom: 2rem; right: 2rem; z-index: 300;
    display: flex; flex-direction: column; gap: 0.5rem;
  }
  .toast {
    background: var(--card);
    border: 1px solid var(--border2);
    border-radius: 10px;
    padding: 12px 16px;
    font-size: 13px;
    display: flex; align-items: center; gap: 10px;
    animation: slideIn 0.3s ease;
    min-width: 280px;
    box-shadow: 0 8px 30px rgba(0,0,0,0.3);
  }
  .toast.success { border-left: 3px solid var(--green); }
  .toast.error { border-left: 3px solid var(--red); }
  .toast.info { border-left: 3px solid var(--cyan); }

  /* LOADING SPINNER */
  .spinner {
    width: 16px; height: 16px;
    border: 2px solid rgba(0,200,255,0.3);
    border-top-color: var(--cyan);
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
    display: inline-block;
  }

  /* SIGN UP FORM */
  .signup-form { display: flex; flex-direction: column; gap: 1rem; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
  .plan-cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin: 1rem 0; }
  .plan-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 1rem;
    cursor: pointer;
    transition: all 0.2s;
    text-align: center;
  }
  .plan-card:hover, .plan-card.selected { border-color: var(--cyan); background: rgba(0,200,255,0.05); }
  .plan-name { font-family: var(--font-head); font-size: 1rem; font-weight: 700; color: var(--cyan); }
  .plan-price { font-size: 1.4rem; font-weight: 800; margin: 0.3rem 0; }
  .plan-desc { font-size: 11px; color: var(--text3); }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 3px; }

  @media (max-width: 768px) {
    .nav-links { display: none; }
    .metrics-row { grid-template-columns: 1fr 1fr; }
    .analytics-grid { grid-template-columns: 1fr; }
    .results-grid { grid-template-columns: 1fr 1fr; }
    .reverse-grid { grid-template-columns: 1fr 1fr; }
    .ext-page { grid-template-columns: 1fr 1fr; }
    .form-row { grid-template-columns: 1fr; }
    .plan-cards { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- TOAST CONTAINER -->
<div class="toast-container" id="toastContainer"></div>

<!-- DMCA MODAL -->
<div class="modal-overlay" id="dmcaModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('dmcaModal')">✕</button>
    <div class="modal-title">⚖️ Generate DMCA Takedown Notice</div>
    <div class="modal-sub">// AI-powered legal notice generation</div>
    <div class="dmca-field">
      <label class="dmca-label">Your Full Name / Company</label>
      <input class="dmca-input" id="dmca-name" placeholder="e.g. Acme Corp / John Smith" value="Team Cyber Sports">
    </div>
    <div class="dmca-field">
      <label class="dmca-label">Your Email Address</label>
      <input class="dmca-input" id="dmca-email" type="email" placeholder="legal@yourcompany.com" value="legal@teamcyber.com">
    </div>
    <div class="dmca-field">
      <label class="dmca-label">Infringing URL</label>
      <input class="dmca-input" id="dmca-url" placeholder="https://offendingsite.com/stolen-image">
    </div>
    <div class="dmca-field">
      <label class="dmca-label">Original Asset Description</label>
      <textarea class="dmca-input dmca-textarea" id="dmca-desc" placeholder="Describe the original asset and where it was first published...">Hero banner image originally published at teamcyber.com/assets, pHash: a3f7c2b4e8d1a9b6, Watermark ID: SHIELD-2024-00847</textarea>
    </div>
    <div style="display:flex;gap:1rem;margin-top:1rem;flex-wrap:wrap">
      <button class="btn-primary" style="font-size:13px;padding:10px 20px" onclick="generateDMCA()">
        <span id="dmca-btn-text">⚡ Generate with AI</span>
      </button>
      <button class="btn-secondary" style="font-size:13px;padding:10px 20px" onclick="copyDMCA()">📋 Copy Notice</button>
    </div>
    <div class="dmca-notice-output" id="dmca-output"></div>
  </div>
</div>

<!-- SIGN UP MODAL -->
<div class="modal-overlay" id="signupModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('signupModal')">✕</button>
    <div class="modal-title">🛡 Start Protecting Your Assets</div>
    <div class="modal-sub">// Deploy the full AssetShield stack in minutes</div>
    <div class="plan-cards">
      <div class="plan-card" onclick="selectPlan(this,'Starter')">
        <div class="plan-name">Starter</div>
        <div class="plan-price">$29<span style="font-size:14px;font-weight:400;color:var(--text3)">/mo</span></div>
        <div class="plan-desc">500 assets · 10K scans</div>
      </div>
      <div class="plan-card selected" onclick="selectPlan(this,'Pro')">
        <div class="plan-name">Pro</div>
        <div class="plan-price">$99<span style="font-size:14px;font-weight:400;color:var(--text3)">/mo</span></div>
        <div class="plan-desc">5K assets · 100K scans</div>
      </div>
      <div class="plan-card" onclick="selectPlan(this,'Enterprise')">
        <div class="plan-name">Enterprise</div>
        <div class="plan-price">Custom</div>
        <div class="plan-desc">Unlimited · SLA</div>
      </div>
    </div>
    <div class="signup-form">
      <div class="form-row">
        <div class="dmca-field" style="margin:0">
          <label class="dmca-label">First Name</label>
          <input class="dmca-input" id="su-fname" placeholder="John">
        </div>
        <div class="dmca-field" style="margin:0">
          <label class="dmca-label">Last Name</label>
          <input class="dmca-input" id="su-lname" placeholder="Smith">
        </div>
      </div>
      <div class="dmca-field" style="margin:0">
        <label class="dmca-label">Work Email</label>
        <input class="dmca-input" id="su-email" type="email" placeholder="you@company.com">
      </div>
      <div class="dmca-field" style="margin:0">
        <label class="dmca-label">Company / Organization</label>
        <input class="dmca-input" id="su-company" placeholder="Acme Corp">
      </div>
      <button class="btn-primary" style="width:100%;justify-content:center;font-size:14px" onclick="submitSignup()">
        <span id="su-btn-text">🛡 Start Free 14-Day Trial</span>
      </button>
    </div>
  </div>
</div>

<!-- NAV -->
<nav>
  <div class="nav-logo" onclick="window.scrollTo({top:0,behavior:'smooth'})">
    <div class="shield-icon"></div>
    AssetShield
  </div>
  <div class="nav-links">
    <a onclick="gotoSection('features')">Features</a>
    <a onclick="gotoSection('workflow')">How It Works</a>
    <a onclick="gotoSection('demo')">Live Demo</a>
    <a onclick="gotoSection('alerts')">Alerts</a>
    <a onclick="gotoSection('analytics')">Analytics</a>
  </div>
  <button class="nav-btn" onclick="openModal('signupModal')">Start Protecting</button>
</nav>

<main>
  <!-- HERO -->
  <div class="hero">
    <div class="hero-badge">
      <div class="dot"></div>
      AI-Powered • Real-Time Monitoring • v2.4.1
    </div>
    <h1>
      <span class="accent">Shield</span> Your Digital Assets
      <span class="line2">Before They're Stolen</span>
    </h1>
    <p class="hero-desc">
      Protect, fingerprint, and actively monitor your media across the entire internet using AI-powered pHash matching, URL scanning, reverse image search, and browser extension detection.
    </p>
    <div class="hero-actions">
      <button class="btn-primary" onclick="gotoSection('demo')">
        ⚡ Try Live Demo
      </button>
      <button class="btn-secondary" onclick="gotoSection('features')">
        Explore Features
      </button>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-row">
    <div class="stat">
      <div class="stat-num" id="stat-accuracy">98.7%</div>
      <div class="stat-label">Detection Accuracy</div>
    </div>
    <div class="stat">
      <div class="stat-num" id="stat-assets">2.4M+</div>
      <div class="stat-label">Assets Protected</div>
    </div>
    <div class="stat">
      <div class="stat-num">&lt;200ms</div>
      <div class="stat-label">Match Latency</div>
    </div>
    <div class="stat">
      <div class="stat-num" id="stat-urls">50K+</div>
      <div class="stat-label">URLs Scanned Daily</div>
    </div>
  </div>

  <!-- FEATURES -->
  <section id="features">
    <div class="section-tag">// CORE MODULES</div>
    <h2 class="section-title">Complete Protection Stack</h2>
    <p class="section-sub">Every layer of digital asset protection — from upload to active web monitoring — in one unified platform.</p>
    <div class="features-grid">
      <div class="feature-card" onclick="gotoSection('demo')">
        <div class="feature-icon icon-cyan">🧬</div>
        <div class="feature-title">AI Image Fingerprinting</div>
        <div class="feature-desc">Generate perceptual hashes (pHash) for every uploaded asset. Detects stolen images even after resizing, cropping, compression, or color modification.</div>
        <div class="feature-tag">pHash Engine</div>
      </div>
      <div class="feature-card" onclick="gotoSection('demo')">
        <div class="feature-icon icon-purple">💧</div>
        <div class="feature-title">Invisible Watermarking</div>
        <div class="feature-desc">Embed imperceptible digital watermarks into your images. Survives social media compression, screenshots, and format conversion to trace ownership definitively.</div>
        <div class="feature-tag">Steganography</div>
      </div>
      <div class="feature-card" onclick="switchTab('url');gotoSection('demo')">
        <div class="feature-icon icon-green">🌐</div>
        <div class="feature-title">URL-Based Scanner</div>
        <div class="feature-desc">Enter any website URL — our crawler scrapes all images, downloads them, generates fingerprints, and compares against your protected asset database in seconds.</div>
        <div class="feature-tag">Web Crawler</div>
      </div>
      <div class="feature-card" onclick="switchTab('reverse');gotoSection('demo')">
        <div class="feature-icon icon-amber">🔎</div>
        <div class="feature-title">Reverse Image Search</div>
        <div class="feature-desc">Upload any image to find where it appears across the web. Powered by similarity matching against a curated index and API integrations for maximum coverage.</div>
        <div class="feature-tag">Similarity Search</div>
      </div>
      <div class="feature-card" onclick="switchTab('extension');gotoSection('demo')">
        <div class="feature-icon icon-cyan">🧩</div>
        <div class="feature-title">Browser Extension</div>
        <div class="feature-desc">Real-time detection while browsing. The extension silently scans every page for your protected assets and triggers instant alerts when a match is found.</div>
        <div class="feature-tag">Live Detection</div>
      </div>
      <div class="feature-card" onclick="gotoSection('alerts')">
        <div class="feature-icon icon-red">🚨</div>
        <div class="feature-title">Smart Alert System</div>
        <div class="feature-desc">Risk-scored alerts with confidence percentages, offending URLs, detection timestamp, and one-click AI-generated DMCA takedown notice for each violation.</div>
        <div class="feature-tag">Risk Scoring</div>
      </div>
    </div>
  </section>

  <!-- ARCHITECTURE DIAGRAM -->
  <section>
    <div class="section-tag">// SYSTEM ARCHITECTURE</div>
    <h2 class="section-title">How the Engine Works</h2>
    <div class="arch-container">
      <svg width="100%" viewBox="0 0 900 320" xmlns="http://www.w3.org/2000/svg" style="display:block">
        <defs>
          <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto">
            <path d="M2 2L8 5L2 8" fill="none" stroke="#00c8ff" stroke-width="1.5" stroke-linecap="round"/>
          </marker>
        </defs>
        <rect x="350" y="20" width="200" height="52" rx="10" fill="rgba(0,200,255,0.12)" stroke="#00c8ff" stroke-width="1"/>
        <text x="450" y="43" text-anchor="middle" fill="#00c8ff" font-family="Syne,sans-serif" font-size="13" font-weight="700">📤 Upload Media</text>
        <text x="450" y="62" text-anchor="middle" fill="#4a6a88" font-family="DM Sans,sans-serif" font-size="11">Images, Videos, Documents</text>
        <line x1="450" y1="72" x2="450" y2="110" stroke="#00c8ff" stroke-width="1" marker-end="url(#arrow)" stroke-dasharray="4,3"/>
        <rect x="280" y="110" width="340" height="52" rx="10" fill="rgba(168,85,247,0.1)" stroke="#a855f7" stroke-width="1"/>
        <text x="450" y="132" text-anchor="middle" fill="#a855f7" font-family="Syne,sans-serif" font-size="12" font-weight="700">🧬 Watermark + Fingerprint + Store</text>
        <text x="450" y="150" text-anchor="middle" fill="#4a6a88" font-family="DM Sans,sans-serif" font-size="11">pHash Generation • DB Indexing • Watermark Embed</text>
        <line x1="340" y1="162" x2="180" y2="210" stroke="#00c8ff" stroke-width="1" marker-end="url(#arrow)" stroke-dasharray="4,3"/>
        <line x1="450" y1="162" x2="450" y2="210" stroke="#00c8ff" stroke-width="1" marker-end="url(#arrow)" stroke-dasharray="4,3"/>
        <line x1="560" y1="162" x2="720" y2="210" stroke="#00c8ff" stroke-width="1" marker-end="url(#arrow)" stroke-dasharray="4,3"/>
        <rect x="80" y="210" width="200" height="50" rx="10" fill="rgba(0,255,157,0.08)" stroke="#00ff9d" stroke-width="1"/>
        <text x="180" y="232" text-anchor="middle" fill="#00ff9d" font-family="Syne,sans-serif" font-size="12" font-weight="700">🌐 URL Scanner</text>
        <text x="180" y="249" text-anchor="middle" fill="#4a6a88" font-family="DM Sans,sans-serif" font-size="10">Crawl → Download → Match</text>
        <rect x="340" y="210" width="220" height="50" rx="10" fill="rgba(255,184,0,0.08)" stroke="#ffb800" stroke-width="1"/>
        <text x="450" y="232" text-anchor="middle" fill="#ffb800" font-family="Syne,sans-serif" font-size="12" font-weight="700">🔎 Reverse Search</text>
        <text x="450" y="249" text-anchor="middle" fill="#4a6a88" font-family="DM Sans,sans-serif" font-size="10">Similarity Matching</text>
        <rect x="620" y="210" width="200" height="50" rx="10" fill="rgba(0,200,255,0.08)" stroke="#00c8ff" stroke-width="1"/>
        <text x="720" y="232" text-anchor="middle" fill="#00c8ff" font-family="Syne,sans-serif" font-size="12" font-weight="700">🧩 Extension</text>
        <text x="720" y="249" text-anchor="middle" fill="#4a6a88" font-family="DM Sans,sans-serif" font-size="10">Live Browser Detection</text>
        <line x1="180" y1="260" x2="370" y2="290" stroke="#4a6a88" stroke-width="1" marker-end="url(#arrow)"/>
        <line x1="450" y1="260" x2="450" y2="290" stroke="#4a6a88" stroke-width="1" marker-end="url(#arrow)"/>
        <line x1="720" y1="260" x2="530" y2="290" stroke="#4a6a88" stroke-width="1" marker-end="url(#arrow)"/>
        <rect x="280" y="290" width="340" height="22" rx="6" fill="rgba(255,71,87,0.1)" stroke="#ff4757" stroke-width="1"/>
        <text x="450" y="305" text-anchor="middle" fill="#ff4757" font-family="Syne,sans-serif" font-size="11" font-weight="700">🔴 Detection Engine → Alerts + Dashboard</text>
      </svg>
    </div>
  </section>

  <!-- WORKFLOW -->
  <div class="workflow" id="workflow">
    <div class="workflow-inner">
      <div class="section-tag">// DETECTION WORKFLOW</div>
      <h2 class="section-title">End-to-End Protection Pipeline</h2>
      <div class="steps-row">
        <div class="step"><div class="step-num">01</div><div class="step-label">Upload Original</div></div>
        <div class="step"><div class="step-num">02</div><div class="step-label">Watermark Embed</div></div>
        <div class="step"><div class="step-num">03</div><div class="step-label">pHash Generate</div></div>
        <div class="step"><div class="step-num">04</div><div class="step-label">DB Index Store</div></div>
        <div class="step"><div class="step-num">05</div><div class="step-label">Web Monitoring</div></div>
        <div class="step"><div class="step-num">06</div><div class="step-label">Match Detection</div></div>
        <div class="step"><div class="step-num">07</div><div class="step-label">Alert + DMCA</div></div>
      </div>
    </div>
  </div>

  <!-- DEMO SECTION -->
  <div class="demo-section" id="demo">
    <div class="demo-inner">
      <div class="section-tag">// LIVE DEMO</div>
      <h2 class="section-title">See It In Action</h2>
      <p class="section-sub">Interact with all four detection modules — fully functional with AI-powered analysis.</p>

      <!-- METRICS ROW -->
      <div class="metrics-row">
        <div class="metric-card">
          <div class="metric-label">Protected Assets</div>
          <div class="metric-val" style="color:var(--cyan)" id="m-assets">1,284</div>
          <div class="metric-change change-up">↑ 42 this week</div>
        </div>
        <div class="metric-card">
          <div class="metric-label">Violations Found</div>
          <div class="metric-val" style="color:var(--red)" id="m-violations">37</div>
          <div class="metric-change change-down">↑ 8 today</div>
        </div>
        <div class="metric-card">
          <div class="metric-label">URLs Scanned</div>
          <div class="metric-val" style="color:var(--green)" id="m-urls">9,421</div>
          <div class="metric-change change-up">Live scanning</div>
        </div>
        <div class="metric-card">
          <div class="metric-label">Avg Confidence</div>
          <div class="metric-val" style="color:var(--amber)">91.4%</div>
          <div class="metric-change" style="color:var(--text3)">pHash engine</div>
        </div>
      </div>

      <!-- TABS -->
      <div class="demo-tabs">
        <button class="tab-btn active" onclick="switchTab('upload')">📤 Upload & Protect</button>
        <button class="tab-btn" onclick="switchTab('url')">🌐 URL Scanner</button>
        <button class="tab-btn" onclick="switchTab('reverse')">🔎 Reverse Search</button>
        <button class="tab-btn" onclick="switchTab('extension')">🧩 Browser Extension</button>
      </div>

      <!-- UPLOAD TAB -->
      <div id="tab-upload" class="tab-content active">
        <div class="demo-panel">
          <div class="panel-header">
            <div class="panel-dots"><div class="panel-dot dot-r"></div><div class="panel-dot dot-y"></div><div class="panel-dot dot-g"></div></div>
            <div class="panel-title">AssetShield / Upload & Protect Module</div>
          </div>
          <div class="panel-body">
            <div class="upload-zone" id="upload-zone" ondragover="handleDragOver(event)" ondragleave="handleDragLeave(event)" ondrop="handleDrop(event)">
              <div class="upload-icon" id="upload-icon">📁</div>
              <div class="upload-text">Drop your image or click to upload</div>
              <div class="upload-sub">Supports JPG, PNG, WEBP, SVG, GIF • Max 50MB</div>
              <input type="file" id="file-input" accept="image/*" onchange="handleFileSelect(event)">
            </div>
            <div class="fp-display" id="fp-display">
              <div class="fp-row">
                <div class="fp-label">File Name</div>
                <div class="fp-value" id="fp-filename">—</div>
              </div>
              <div class="fp-row">
                <div class="fp-label">File Size</div>
                <div class="fp-value" id="fp-filesize">—</div>
              </div>
              <div class="fp-row">
                <div class="fp-label">pHash</div>
                <div class="fp-value" style="color:var(--green)">✓ Generated</div>
              </div>
              <div class="fp-row">
                <div class="fp-label">Watermark</div>
                <div class="fp-value" style="color:var(--green)">✓ Embedded</div>
              </div>
              <div class="fp-row">
                <div class="fp-label">DB Status</div>
                <div class="fp-value" style="color:var(--green)">✓ Indexed</div>
              </div>
              <div class="fp-hash" id="fp-hash">
                <span>pHash:</span> a3f7c2b4e8d1a9b6c4f2e7d3a8b5c1f9<br>
                <span>Watermark ID:</span> SHIELD-2024-00847-TEAM_CYBER<br>
                <span>Asset UUID:</span> 9f4b2e1a-3c7d-48f9-b2a1-e6c4d8f3a2b7
              </div>
            </div>
            <div class="ai-analysis-box" id="upload-ai-analysis">
              <div class="ai-analysis-title">🤖 AI ASSET ANALYSIS</div>
              <div class="ai-analysis-text" id="upload-ai-text">Analyzing...</div>
            </div>
          </div>
        </div>
      </div>

      <!-- URL SCANNER TAB -->
      <div id="tab-url" class="tab-content">
        <div class="demo-panel">
          <div class="panel-header">
            <div class="panel-dots"><div class="panel-dot dot-r"></div><div class="panel-dot dot-y"></div><div class="panel-dot dot-g"></div></div>
            <div class="panel-title">AssetShield / URL Scanner — Web Crawler Engine</div>
          </div>
          <div class="panel-body">
            <div class="url-input-row">
              <input class="url-input" id="url-input" type="text" placeholder="https://sportsnews.com" value="https://sportsnews.com">
              <button class="scan-btn" id="scan-btn" onclick="startScan()">⚡ Scan URL</button>
            </div>
            <div class="scan-progress" id="scan-progress">
              <div class="progress-label">
                <span id="progress-status">Initializing crawler...</span>
                <span id="progress-pct">0%</span>
              </div>
              <div class="progress-bar"><div class="progress-fill" id="progress-fill"></div></div>
              <div class="log-lines" id="log-lines"></div>
            </div>
            <div class="results-grid" id="results-grid">
              <div class="result-card">
                <div class="result-thumb">🏆</div>
                <div class="result-badge badge-match">MATCH</div>
                <div class="result-info">
                  <div class="result-name">hero_banner_01.jpg</div>
                  <div class="result-conf" style="color:var(--red)">Confidence: 94.2%</div>
                </div>
              </div>
              <div class="result-card">
                <div class="result-thumb">⚽</div>
                <div class="result-badge badge-match">MATCH</div>
                <div class="result-info">
                  <div class="result-name">player_action_03.jpg</div>
                  <div class="result-conf" style="color:var(--red)">Confidence: 87.6%</div>
                </div>
              </div>
              <div class="result-card">
                <div class="result-thumb">📰</div>
                <div class="result-badge badge-clean">CLEAN</div>
                <div class="result-info">
                  <div class="result-name">article_thumb_07.jpg</div>
                  <div class="result-conf" style="color:var(--green)">No match found</div>
                </div>
              </div>
              <div class="result-card">
                <div class="result-thumb">🎽</div>
                <div class="result-badge badge-clean">CLEAN</div>
                <div class="result-info">
                  <div class="result-name">team_logo_bg.png</div>
                  <div class="result-conf" style="color:var(--green)">No match found</div>
                </div>
              </div>
              <div class="result-card">
                <div class="result-thumb">📸</div>
                <div class="result-badge badge-clean">CLEAN</div>
                <div class="result-info">
                  <div class="result-name">stadium_wide.jpg</div>
                  <div class="result-conf" style="color:var(--green)">No match found</div>
                </div>
              </div>
              <div class="result-card">
                <div class="result-thumb">🎯</div>
                <div class="result-badge badge-clean">CLEAN</div>
                <div class="result-info">
                  <div class="result-name">ad_banner_side.jpg</div>
                  <div class="result-conf" style="color:var(--green)">No match found</div>
                </div>
              </div>
            </div>
            <div class="summary-banner" id="summary-banner">
              <div class="summary-stats">
                <div>
                  <div class="summary-stat-val cyan">15</div>
                  <div class="summary-stat-label">Images Scanned</div>
                </div>
                <div>
                  <div class="summary-stat-val red" id="match-count-display">2</div>
                  <div class="summary-stat-label">Matches Found</div>
                </div>
                <div>
                  <div class="summary-stat-val" style="color:var(--amber)">91%</div>
                  <div class="summary-stat-label">Avg Confidence</div>
                </div>
              </div>
              <button class="btn-primary" style="font-size:13px;padding:10px 20px" onclick="openDMCAModal()">🔔 Generate DMCA Notice</button>
            </div>
            <div class="ai-analysis-box" id="scan-ai-analysis" style="margin-top:1rem">
              <div class="ai-analysis-title">🤖 AI SCAN ANALYSIS</div>
              <div class="ai-analysis-text" id="scan-ai-text">Analyzing results...</div>
            </div>
          </div>
        </div>
      </div>

      <!-- REVERSE SEARCH TAB -->
      <div id="tab-reverse" class="tab-content">
        <div class="demo-panel">
          <div class="panel-header">
            <div class="panel-dots"><div class="panel-dot dot-r"></div><div class="panel-dot dot-y"></div><div class="panel-dot dot-g"></div></div>
            <div class="panel-title">AssetShield / Reverse Image Search Engine</div>
          </div>
          <div class="panel-body">
            <div class="upload-zone" id="reverse-zone" ondragover="handleDragOver(event)" ondragleave="handleDragLeave(event)" ondrop="handleReverseDrop(event)" style="padding:2rem">
              <div class="upload-icon">🔎</div>
              <div class="upload-text">Upload image to find where it exists online</div>
              <div class="upload-sub">Click or drop image — simulates search across indexed web database</div>
              <input type="file" id="reverse-file-input" accept="image/*" onchange="simulateReverse(event)">
            </div>
            <div class="reverse-grid" id="reverse-grid" style="display:none">
              <div class="reverse-card" onclick="showToast('Opening page in new tab...','info')">
                <div class="reverse-thumb">📸</div>
                <div class="reverse-info">
                  <div class="reverse-site">SportsCentral.com</div>
                  <div class="reverse-url">sportscentral.com/news/hero-image</div>
                  <div class="match-bar">
                    <div class="match-label"><span>Match Score</span><span style="color:var(--red)">94%</span></div>
                    <div class="match-progress"><div class="match-fill" style="width:0%;background:var(--red)" data-width="94"></div></div>
                  </div>
                </div>
              </div>
              <div class="reverse-card" onclick="showToast('Opening page in new tab...','info')">
                <div class="reverse-thumb">🏅</div>
                <div class="reverse-info">
                  <div class="reverse-site">GameBlog.net</div>
                  <div class="reverse-url">gameblog.net/gallery/sports-01</div>
                  <div class="match-bar">
                    <div class="match-label"><span>Match Score</span><span style="color:var(--amber)">78%</span></div>
                    <div class="match-progress"><div class="match-fill" style="width:0%;background:var(--amber)" data-width="78"></div></div>
                  </div>
                </div>
              </div>
              <div class="reverse-card" onclick="showToast('Opening page in new tab...','info')">
                <div class="reverse-thumb">📰</div>
                <div class="reverse-info">
                  <div class="reverse-site">NewsFeed.io</div>
                  <div class="reverse-url">newsfeed.io/content/img23</div>
                  <div class="match-bar">
                    <div class="match-label"><span>Match Score</span><span style="color:var(--amber)">72%</span></div>
                    <div class="match-progress"><div class="match-fill" style="width:0%;background:var(--amber)" data-width="72"></div></div>
                  </div>
                </div>
              </div>
              <div class="reverse-card" onclick="showToast('Opening page in new tab...','info')">
                <div class="reverse-thumb">🎽</div>
                <div class="reverse-info">
                  <div class="reverse-site">SportsDB.org</div>
                  <div class="reverse-url">sportsdb.org/assets/compressed</div>
                  <div class="match-bar">
                    <div class="match-label"><span>Match Score</span><span style="color:var(--cyan)">61%</span></div>
                    <div class="match-progress"><div class="match-fill" style="width:0%" data-width="61"></div></div>
                  </div>
                </div>
              </div>
              <div class="reverse-card" onclick="showToast('Opening page in new tab...','info')">
                <div class="reverse-thumb">🌍</div>
                <div class="reverse-info">
                  <div class="reverse-site">MediaHub.co</div>
                  <div class="reverse-url">mediahub.co/free-images/sp</div>
                  <div class="match-bar">
                    <div class="match-label"><span>Match Score</span><span style="color:var(--cyan)">55%</span></div>
                    <div class="match-progress"><div class="match-fill" style="width:0%" data-width="55"></div></div>
                  </div>
                </div>
              </div>
              <div class="reverse-card" onclick="showToast('Opening page in new tab...','info')">
                <div class="reverse-thumb">🖼️</div>
                <div class="reverse-info">
                  <div class="reverse-site">PixelShare.in</div>
                  <div class="reverse-url">pixelshare.in/uploads/img774</div>
                  <div class="match-bar">
                    <div class="match-label"><span>Match Score</span><span style="color:var(--green)">41%</span></div>
                    <div class="match-progress"><div class="match-fill" style="width:0%;background:var(--green)" data-width="41"></div></div>
                  </div>
                </div>
              </div>
            </div>
            <div class="ai-analysis-box" id="reverse-ai-analysis">
              <div class="ai-analysis-title">🤖 AI REVERSE SEARCH ANALYSIS</div>
              <div class="ai-analysis-text" id="reverse-ai-text">Analyzing results...</div>
            </div>
          </div>
        </div>
      </div>

      <!-- EXTENSION TAB -->
      <div id="tab-extension" class="tab-content">
        <div class="demo-panel">
          <div class="panel-header">
            <div class="panel-dots"><div class="panel-dot dot-r"></div><div class="panel-dot dot-y"></div><div class="panel-dot dot-g"></div></div>
            <div class="panel-title">AssetShield / Browser Extension Simulator</div>
          </div>
          <div class="panel-body">
            <p style="color:var(--text2);font-size:13px;margin-bottom:1rem">Simulating a user browsing <span style="color:var(--cyan);font-family:var(--font-mono)">sportsnews.com</span> with the AssetShield extension active. <strong style="color:var(--cyan)">Click any image card to inspect it.</strong></p>
            <div class="ext-demo">
              <div class="ext-browser-bar">
                <div style="font-size:11px;color:var(--text3)">◀ ▶ ↻</div>
                <div class="ext-url-bar">🔒 https://sportsnews.com/latest-news</div>
                <div style="background:rgba(0,200,255,0.15);border:1px solid rgba(0,200,255,0.3);border-radius:5px;padding:4px 10px;font-size:11px;color:var(--cyan);font-family:var(--font-mono)">🛡 Active</div>
              </div>
              <div class="ext-page">
                <div class="ext-img-card" style="background:rgba(0,255,157,0.05)" onclick="inspectExtImage(this,'banner_01.jpg','clean')">
                  <div class="ext-img-thumb" style="background:rgba(0,200,255,0.08)">🏅</div>
                  <div style="padding:6px;font-size:10px;color:var(--text3)">banner_01.jpg</div>
                </div>
                <div class="ext-img-card flagged" onclick="inspectExtImage(this,'stolen_img.jpg','match')">
                  <div class="ext-flag-popup">⚠ MATCH DETECTED</div>
                  <div class="ext-img-thumb" style="background:rgba(255,71,87,0.12)">🏆</div>
                  <div style="padding:6px;font-size:10px;color:var(--red)">stolen_img.jpg</div>
                </div>
                <div class="ext-img-card" style="background:rgba(0,255,157,0.05)" onclick="inspectExtImage(this,'action_03.jpg','clean')">
                  <div class="ext-img-thumb" style="background:rgba(255,184,0,0.08)">⚽</div>
                  <div style="padding:6px;font-size:10px;color:var(--text3)">action_03.jpg</div>
                </div>
                <div class="ext-img-card" onclick="inspectExtImage(this,'article_bg.jpg','clean')">
                  <div class="ext-img-thumb">📰</div>
                  <div style="padding:6px;font-size:10px;color:var(--text3)">article_bg.jpg</div>
                </div>
              </div>
              <div class="ext-alert-popup" id="ext-alert-popup">
                <div class="ext-alert-icon">🚨</div>
                <div>
                  <div class="ext-alert-title" id="ext-alert-title">Unauthorized Asset Detected!</div>
                  <div class="ext-alert-desc" id="ext-alert-desc">This image belongs to <strong>Team_Cyber</strong> · sportsnews.com/latest-news</div>
                  <div class="ext-alert-conf" id="ext-alert-conf">Confidence: 94% · Asset ID: SHIELD-2024-00847</div>
                  <div class="alert-actions">
                    <button class="alert-btn" onclick="copyURL()">📋 Copy URL</button>
                    <button class="alert-btn" onclick="openDMCAModal()">⚖️ File DMCA</button>
                    <button class="alert-btn" onclick="showToast('Opening asset viewer...','info')">👁 View Asset</button>
                  </div>
                </div>
              </div>
            </div>
            <div style="font-family:var(--font-mono);font-size:11px;color:var(--text3);padding:0.75rem;background:var(--bg3);border-radius:8px;margin-top:1rem">
              <div style="color:var(--text3)">// Extension content.js — scanning page images</div>
              <div style="color:var(--cyan)">let images = document.getElementsByTagName("img");</div>
              <div style="color:var(--text2)">for (let img of images) {</div>
              <div style="padding-left:1rem;color:var(--green)">  fetch("https://api.assetshield.io/check", { method: "POST",</div>
              <div style="padding-left:1rem;color:var(--green)">    body: JSON.stringify({url: img.src, origin: location.href}) });</div>
              <div style="color:var(--text2)">}</div>
            </div>
            <div class="ai-analysis-box" id="ext-ai-analysis" style="margin-top:1rem">
              <div class="ai-analysis-title">🤖 AI EXTENSION ANALYSIS</div>
              <div class="ai-analysis-text" id="ext-ai-text">Click an image to get AI analysis...</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- ALERTS -->
  <section id="alerts">
    <div class="section-tag">// ALERTS PANEL</div>
    <h2 class="section-title">Live Detection Alerts</h2>
    <p class="section-sub">Real-time unauthorized usage events, risk-scored and ready for action.</p>
    <div style="display:flex;gap:0.5rem;margin-bottom:1.5rem;flex-wrap:wrap">
      <button class="tab-btn active" id="filter-all" onclick="filterAlerts('all')">All Alerts (4)</button>
      <button class="tab-btn" id="filter-high" onclick="filterAlerts('high')">🔴 High Risk</button>
      <button class="tab-btn" id="filter-med" onclick="filterAlerts('med')">🟡 Medium</button>
      <button class="tab-btn" id="filter-low" onclick="filterAlerts('low')">🟢 Low</button>
    </div>
    <div class="alerts-list" id="alerts-list">
      <div class="alert-item high" data-risk="high">
        <div class="alert-icon">🔴</div>
        <div style="flex:1">
          <div class="alert-site">sportsnews.com/world-cup-hero</div>
          <div class="alert-meta">URL Scanner · 2 minutes ago · hero_banner_01.jpg · Confidence 94%</div>
          <div class="alert-actions">
            <button class="alert-btn danger" onclick="openDMCAModalWith(this,'https://sportsnews.com/world-cup-hero')">⚖️ DMCA Takedown</button>
            <button class="alert-btn" onclick="viewAlertPage('sportsnews.com/world-cup-hero')">🔗 View Page</button>
            <button class="alert-btn" onclick="markReviewed(this)">📌 Mark Reviewed</button>
            <button class="alert-btn" onclick="getAIAlertAnalysis(this,'sportsnews.com/world-cup-hero','hero_banner_01.jpg','94','high')">🤖 AI Analysis</button>
          </div>
        </div>
        <div class="risk-badge risk-high">HIGH</div>
      </div>
      <div class="alert-item high" data-risk="high">
        <div class="alert-icon">🔴</div>
        <div style="flex:1">
          <div class="alert-site">gameblog.net/gallery/sports-2024</div>
          <div class="alert-meta">Reverse Search · 18 minutes ago · player_action_03.jpg · Confidence 87%</div>
          <div class="alert-actions">
            <button class="alert-btn danger" onclick="openDMCAModalWith(this,'https://gameblog.net/gallery/sports-2024')">⚖️ DMCA Takedown</button>
            <button class="alert-btn" onclick="viewAlertPage('gameblog.net/gallery/sports-2024')">🔗 View Page</button>
            <button class="alert-btn" onclick="markReviewed(this)">📌 Mark Reviewed</button>
            <button class="alert-btn" onclick="getAIAlertAnalysis(this,'gameblog.net/gallery/sports-2024','player_action_03.jpg','87','high')">🤖 AI Analysis</button>
          </div>
        </div>
        <div class="risk-badge risk-high">HIGH</div>
      </div>
      <div class="alert-item med" data-risk="med">
        <div class="alert-icon">🟡</div>
        <div style="flex:1">
          <div class="alert-site">socialmedia-clone.io/posts/77312</div>
          <div class="alert-meta">Browser Extension · 1 hour ago · team_photo_2024.jpg · Confidence 73%</div>
          <div class="alert-actions">
            <button class="alert-btn" onclick="openDMCAModalWith(this,'https://socialmedia-clone.io/posts/77312')">⚖️ DMCA Takedown</button>
            <button class="alert-btn" onclick="viewAlertPage('socialmedia-clone.io/posts/77312')">🔗 View Page</button>
            <button class="alert-btn" onclick="markReviewed(this)">📌 Mark Reviewed</button>
            <button class="alert-btn" onclick="getAIAlertAnalysis(this,'socialmedia-clone.io/posts/77312','team_photo_2024.jpg','73','medium')">🤖 AI Analysis</button>
          </div>
        </div>
        <div class="risk-badge risk-med">MEDIUM</div>
      </div>
      <div class="alert-item low" data-risk="low">
        <div class="alert-icon">🟢</div>
        <div style="flex:1">
          <div class="alert-site">mediahub.co/free/unverified-sports</div>
          <div class="alert-meta">URL Scanner · 3 hours ago · logo_variant.png · Confidence 61%</div>
          <div class="alert-actions">
            <button class="alert-btn" onclick="openDMCAModalWith(this,'https://mediahub.co/free/unverified-sports')">⚖️ DMCA Takedown</button>
            <button class="alert-btn" onclick="viewAlertPage('mediahub.co/free/unverified-sports')">🔗 View Page</button>
            <button class="alert-btn" onclick="markReviewed(this)">📌 Mark Reviewed</button>
            <button class="alert-btn" onclick="getAIAlertAnalysis(this,'mediahub.co/free/unverified-sports','logo_variant.png','61','low')">🤖 AI Analysis</button>
          </div>
        </div>
        <div class="risk-badge risk-low">LOW</div>
      </div>
    </div>
  </section>

  <!-- ANALYTICS -->
  <section id="analytics" style="background:var(--bg2);max-width:100%;padding:5rem 2rem">
    <div style="max-width:1200px;margin:0 auto">
      <div class="section-tag">// ANALYTICS DASHBOARD</div>
      <h2 class="section-title">Detection Intelligence</h2>
      <div class="analytics-grid">
        <div class="analytics-card">
          <div class="analytics-title">Detections Over Time</div>
          <div class="chart-bar-row"><div class="chart-bar-label">Mon</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="45"></div></div><div class="chart-bar-val">9</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Tue</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="70"></div></div><div class="chart-bar-val">14</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Wed</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="30"></div></div><div class="chart-bar-val">6</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Thu</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="85"></div></div><div class="chart-bar-val">17</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Fri</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="60"></div></div><div class="chart-bar-val">12</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Sat</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="40"></div></div><div class="chart-bar-val">8</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Sun</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="100"></div></div><div class="chart-bar-val">20</div></div>
        </div>
        <div class="analytics-card">
          <div class="analytics-title">Detection Source Breakdown</div>
          <div class="donut-row">
            <div class="donut-wrap">
              <svg width="120" height="120" viewBox="0 0 120 120">
                <circle cx="60" cy="60" r="45" fill="none" stroke="rgba(0,200,255,0.2)" stroke-width="16"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#00c8ff" stroke-width="16" stroke-dasharray="169 114" stroke-dashoffset="0" transform="rotate(-90 60 60)"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#ffb800" stroke-width="16" stroke-dasharray="85 198" stroke-dashoffset="-169" transform="rotate(-90 60 60)"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#a855f7" stroke-width="16" stroke-dasharray="29 254" stroke-dashoffset="-254" transform="rotate(-90 60 60)"/>
              </svg>
              <div class="donut-center">
                <div class="donut-num">37</div>
                <div class="donut-sub">TOTAL</div>
              </div>
            </div>
            <div class="donut-legend">
              <div class="legend-item"><div class="legend-dot" style="background:var(--cyan)"></div><div><div style="font-size:13px;font-weight:600">URL Scanner</div><div style="font-size:11px;color:var(--text3)">20 detections · 54%</div></div></div>
              <div class="legend-item"><div class="legend-dot" style="background:var(--amber)"></div><div><div style="font-size:13px;font-weight:600">Reverse Search</div><div style="font-size:11px;color:var(--text3)">10 detections · 27%</div></div></div>
              <div class="legend-item"><div class="legend-dot" style="background:var(--purple)"></div><div><div style="font-size:13px;font-weight:600">Extension</div><div style="font-size:11px;color:var(--text3)">7 detections · 19%</div></div></div>
            </div>
          </div>
        </div>
        <div class="analytics-card">
          <div class="analytics-title">Top Offending Domains</div>
          <div class="chart-bar-row"><div class="chart-bar-label" style="width:90px;font-size:10px">sportsnews.com</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%;background:linear-gradient(90deg,var(--red),var(--amber))" data-w="90"></div></div><div class="chart-bar-val" style="color:var(--red)">9</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label" style="width:90px;font-size:10px">gameblog.net</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%;background:linear-gradient(90deg,var(--red),var(--amber))" data-w="70"></div></div><div class="chart-bar-val" style="color:var(--red)">7</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label" style="width:90px;font-size:10px">socialmedia.io</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%;background:linear-gradient(90deg,var(--amber),var(--cyan))" data-w="55"></div></div><div class="chart-bar-val" style="color:var(--amber)">5</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label" style="width:90px;font-size:10px">newsfeed.io</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="40"></div></div><div class="chart-bar-val">4</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label" style="width:90px;font-size:10px">pixelshare.in</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="30"></div></div><div class="chart-bar-val">3</div></div>
        </div>
        <div class="analytics-card">
          <div class="analytics-title">Asset Type Protection</div>
          <div class="chart-bar-row"><div class="chart-bar-label">Images</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="88"></div></div><div class="chart-bar-val">1,130</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Videos</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="45"></div></div><div class="chart-bar-val">84</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Logos</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="35"></div></div><div class="chart-bar-val">52</div></div>
          <div class="chart-bar-row"><div class="chart-bar-label">Docs</div><div class="chart-bar-wrap"><div class="chart-bar" style="width:0%" data-w="15"></div></div><div class="chart-bar-val">18</div></div>
        </div>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <div class="cta-section">
    <div class="cta-inner">
      <div class="hero-badge" style="margin:0 auto 2rem">
        <div class="dot"></div>
        Ready to Deploy
      </div>
      <h2 class="cta-title">Start Protecting Your Digital Assets Today</h2>
      <p class="cta-desc">Deploy the complete AssetShield stack — fingerprinting, watermarking, URL scanning, reverse search, and browser extension — in under 10 minutes.</p>
      <div class="hero-actions">
        <button class="btn-primary" onclick="openModal('signupModal')">🛡 Start Free Trial</button>
        <button class="btn-secondary" onclick="viewDocs()">📋 View Documentation</button>
      </div>
    </div>
  </div>
</main>

<footer>
  <span>AssetShield</span> — AI-Powered Digital Asset Protection Platform · Built with pHash + Watermarking + Web Intelligence
</footer>

<script>
// ─── GLOBAL STATE ──────────────────────────────────────────────────────────────
const state = {
  selectedPlan: 'Pro',
  alertFilter: 'all',
  protectedAssets: 1284,
  violations: 37,
  urlsScanned: 9421
};

// ─── NAV & SCROLL ──────────────────────────────────────────────────────────────
function gotoSection(id) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' });
}

// ─── TABS ──────────────────────────────────────────────────────────────────────
function switchTab(name) {
  const names = ['upload', 'url', 'reverse', 'extension'];
  document.querySelectorAll('.tab-btn').forEach((b, i) => b.classList.toggle('active', names[i] === name));
  document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
  document.getElementById('tab-' + name).classList.add('active');
}

// ─── MODALS ────────────────────────────────────────────────────────────────────
function openModal(id) {
  document.getElementById(id).classList.add('show');
}
function closeModal(id) {
  document.getElementById(id).classList.remove('show');
}
document.querySelectorAll('.modal-overlay').forEach(m => {
  m.addEventListener('click', e => { if (e.target === m) m.classList.remove('show'); });
});

function openDMCAModal() {
  document.getElementById('dmca-url').value = document.getElementById('url-input').value || '';
  openModal('dmcaModal');
}
function openDMCAModalWith(btn, url) {
  document.getElementById('dmca-url').value = url;
  const site = btn.closest('.alert-item').querySelector('.alert-site').textContent;
  document.getElementById('dmca-output').classList.remove('show');
  openModal('dmcaModal');
}

// ─── TOAST ────────────────────────────────────────────────────────────────────
function showToast(msg, type='info') {
  const container = document.getElementById('toastContainer');
  const toast = document.createElement('div');
  toast.className = `toast ${type}`;
  const icons = { success: '✅', error: '❌', info: 'ℹ️' };
  toast.innerHTML = `<span>${icons[type]||'ℹ️'}</span><span>${msg}</span>`;
  container.appendChild(toast);
  setTimeout(() => { toast.style.opacity='0'; toast.style.transition='opacity 0.3s'; setTimeout(()=>toast.remove(),300); }, 3000);
}

// ─── UPLOAD & PROTECT ─────────────────────────────────────────────────────────
function handleDragOver(e) { e.preventDefault(); e.currentTarget.classList.add('dragover'); }
function handleDragLeave(e) { e.currentTarget.classList.remove('dragover'); }
function handleDrop(e) {
  e.preventDefault();
  e.currentTarget.classList.remove('dragover');
  const file = e.dataTransfer.files[0];
  if (file && file.type.startsWith('image/')) processUpload(file);
}
function handleReverseDrop(e) {
  e.preventDefault();
  e.currentTarget.classList.remove('dragover');
  const file = e.dataTransfer.files[0];
  if (file && file.type.startsWith('image/')) simulateReverse({ target: { files: [file] } });
}

function handleFileSelect(event) {
  const file = event.target.files[0];
  if (file) processUpload(file);
}

function generatePHash() {
  const chars = '0123456789abcdef';
  return Array.from({length:32}, () => chars[Math.floor(Math.random()*16)]).join('');
}
function generateUUID() {
  return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, c => {
    const r = Math.random()*16|0, v = c==='x'?r:(r&0x3|0x8);
    return v.toString(16);
  });
}

function processUpload(file) {
  const icon = document.getElementById('upload-icon');
  const fpDisplay = document.getElementById('fp-display');
  const aiBox = document.getElementById('upload-ai-analysis');
  
  icon.textContent = '⏳';
  fpDisplay.classList.remove('show');
  aiBox.classList.remove('show');
  
  const pHash = generatePHash();
  const uuid = generateUUID();
  const watermarkId = `SHIELD-${new Date().getFullYear()}-${Math.floor(Math.random()*90000+10000)}-ASSET`;
  
  setTimeout(() => {
    icon.textContent = '✅';
    document.getElementById('fp-filename').textContent = file.name;
    document.getElementById('fp-filesize').textContent = (file.size / 1024).toFixed(1) + ' KB';
    document.getElementById('fp-hash').innerHTML = `<span>pHash:</span> ${pHash}<br><span>Watermark ID:</span> ${watermarkId}<br><span>Asset UUID:</span> ${uuid}`;
    fpDisplay.classList.add('show');
    
    state.protectedAssets++;
    document.getElementById('m-assets').textContent = state.protectedAssets.toLocaleString();
    showToast(`Asset "${file.name}" protected successfully!`, 'success');
    
    // AI Analysis
    aiBox.classList.add('show');
    document.getElementById('upload-ai-text').textContent = 'Generating AI analysis...';
    callClaudeAPI(`You are an AI assistant for AssetShield, a digital asset protection platform. A user just uploaded an image file named "${file.name}" (${(file.size/1024).toFixed(1)}KB). Provide a concise 2-3 sentence analysis about: 1) what type of digital asset this likely is based on the filename, 2) the protection measures applied (pHash fingerprinting and watermarking), and 3) what monitoring will be done to protect it. Be specific and professional.`)
      .then(text => {
        document.getElementById('upload-ai-text').textContent = text;
      });
  }, 1200);
}

// ─── URL SCANNER ──────────────────────────────────────────────────────────────
const logMessages = [
  ['Connecting to URL...', 'cyan'],
  ['Parsing HTML document...', ''],
  ['Found 15 image elements', 'cyan'],
  ['Downloading img[1]: banner_hero.jpg', ''],
  ['Downloading img[2]: player_action.jpg', ''],
  ['Generating pHash fingerprints...', 'cyan'],
  ['Comparing against 1,284 protected assets...', ''],
  ['⚠ MATCH: hero_banner_01.jpg (94.2%)', 'red'],
  ['⚠ MATCH: player_action_03.jpg (87.6%)', 'red'],
  ['✓ No match: 13 remaining images', 'green'],
  ['Scan complete. 2 violations found.', 'amber']
];

function startScan() {
  const url = document.getElementById('url-input').value.trim();
  if (!url) { showToast('Please enter a URL to scan', 'error'); return; }
  
  const btn = document.getElementById('scan-btn');
  const progress = document.getElementById('scan-progress');
  const fill = document.getElementById('progress-fill');
  const status = document.getElementById('progress-status');
  const pct = document.getElementById('progress-pct');
  const logEl = document.getElementById('log-lines');
  const grid = document.getElementById('results-grid');
  const banner = document.getElementById('summary-banner');
  const aiBox = document.getElementById('scan-ai-analysis');

  btn.disabled = true; btn.textContent = '⏳ Scanning...';
  progress.classList.add('active');
  grid.classList.remove('show'); banner.classList.remove('show');
  aiBox.classList.remove('show');
  logEl.innerHTML = '';
  fill.style.width = '0%';

  let pctVal = 0, logIdx = 0;

  const pctInterval = setInterval(() => {
    pctVal = Math.min(100, pctVal + Math.random() * 8 + 2);
    fill.style.width = pctVal + '%';
    pct.textContent = Math.round(pctVal) + '%';
    if (pctVal >= 100) {
      clearInterval(pctInterval);
      status.textContent = 'Scan complete!';
      grid.classList.add('show');
      banner.classList.add('show');
      btn.disabled = false; btn.textContent = '⚡ Scan Again';
      state.urlsScanned += Math.floor(Math.random()*5+1);
      document.getElementById('m-urls').textContent = state.urlsScanned.toLocaleString();
      state.violations += 2;
      document.getElementById('m-violations').textContent = state.violations;
      showToast('Scan complete: 2 violations found!', 'error');

      // AI Analysis after scan
      aiBox.classList.add('show');
      document.getElementById('scan-ai-text').textContent = 'Generating AI analysis of scan results...';
      callClaudeAPI(`You are an AI assistant for AssetShield. A URL scan of "${url}" just completed. Results: 15 images scanned, 2 DMCA violations found (hero_banner_01.jpg at 94.2% confidence, player_action_03.jpg at 87.6% confidence). Provide a concise 2-3 sentence threat assessment including: the severity of these violations, what action the user should take first, and what the confidence scores suggest about the nature of the theft.`)
        .then(text => { document.getElementById('scan-ai-text').textContent = text; });
    }
  }, 180);

  const logInterval = setInterval(() => {
    if (logIdx >= logMessages.length) { clearInterval(logInterval); return; }
    const [msg, cls] = logMessages[logIdx];
    const div = document.createElement('div');
    div.className = cls ? 'log-' + cls : '';
    if (!cls) div.style.color = 'var(--text3)';
    div.textContent = '> ' + msg;
    logEl.appendChild(div);
    logEl.scrollTop = logEl.scrollHeight;
    logIdx++;
  }, 350);
  status.textContent = 'Crawling target URL...';
}

// ─── REVERSE SEARCH ────────────────────────────────────────────────────────────
function simulateReverse(event) {
  const file = event.target?.files?.[0];
  const grid = document.getElementById('reverse-grid');
  const aiBox = document.getElementById('reverse-ai-analysis');
  const zone = document.getElementById('reverse-zone');
  
  zone.querySelector('.upload-icon').textContent = '⏳';
  grid.style.display = 'none';
  aiBox.classList.remove('show');
  
  setTimeout(() => {
    zone.querySelector('.upload-icon').textContent = '✅';
    grid.style.display = 'grid';
    grid.style.animation = 'fadeUp 0.5s ease';
    
    // Animate match fills
    setTimeout(() => {
      grid.querySelectorAll('.match-fill[data-width]').forEach(el => {
        el.style.width = el.dataset.width + '%';
      });
    }, 100);
    
    showToast('Reverse search complete: 6 matches found', 'error');
    
    aiBox.classList.add('show');
    const fname = file ? file.name : 'image.jpg';
    document.getElementById('reverse-ai-text').textContent = 'Analyzing matches...';
    callClaudeAPI(`You are an AI assistant for AssetShield. A reverse image search for "${fname}" returned 6 matches across the web: SportsCentral.com (94% match), GameBlog.net (78%), NewsFeed.io (72%), SportsDB.org (61%), MediaHub.co (55%), PixelShare.in (41%). Provide a 2-3 sentence analysis: which of these are likely copyright violations vs possibly legitimate uses (fair use/low similarity), and what priority action should the user take.`)
      .then(text => { document.getElementById('reverse-ai-text').textContent = text; });
  }, 1500);
}

// ─── BROWSER EXTENSION ────────────────────────────────────────────────────────
function inspectExtImage(card, filename, status) {
  const popup = document.getElementById('ext-alert-popup');
  const title = document.getElementById('ext-alert-title');
  const desc = document.getElementById('ext-alert-desc');
  const conf = document.getElementById('ext-alert-conf');
  const aiBox = document.getElementById('ext-ai-analysis');

  if (status === 'match') {
    popup.style.borderColor = 'var(--red)';
    title.textContent = '🚨 Unauthorized Asset Detected!';
    title.style.color = 'var(--red)';
    desc.innerHTML = `This image belongs to <strong>Team_Cyber</strong> · sportsnews.com/latest-news`;
    conf.textContent = 'Confidence: 94% · Asset ID: SHIELD-2024-00847';
    showToast('Match detected: stolen_img.jpg (94% confidence)', 'error');
  } else {
    popup.style.borderColor = 'var(--green)';
    title.textContent = '✅ Asset Cleared';
    title.style.color = 'var(--green)';
    desc.innerHTML = `"${filename}" does not match any protected assets in your database.`;
    conf.textContent = 'No violations detected · Asset is clean';
    showToast(`${filename} — no match found`, 'success');
  }

  aiBox.classList.add('show');
  document.getElementById('ext-ai-text').textContent = 'Analyzing...';
  callClaudeAPI(`You are an AI assistant for AssetShield's browser extension. The extension just inspected an image "${filename}" on sportsnews.com. Status: ${status === 'match' ? 'VIOLATION DETECTED at 94% confidence match' : 'CLEAN — no match found'}. Write 1-2 sentences: what this means for the user and what immediate action (if any) they should take.`)
    .then(text => { document.getElementById('ext-ai-text').textContent = text; });
}

function copyURL() {
  navigator.clipboard.writeText('https://sportsnews.com/latest-news').catch(()=>{});
  showToast('URL copied to clipboard!', 'success');
}

// ─── ALERTS ───────────────────────────────────────────────────────────────────
function filterAlerts(risk) {
  state.alertFilter = risk;
  document.querySelectorAll('#alerts-list .alert-item').forEach(item => {
    item.style.display = (risk === 'all' || item.dataset.risk === risk) ? 'flex' : 'none';
  });
  document.querySelectorAll('#alerts + div .tab-btn, [id^="filter-"]').forEach(b => b.classList.remove('active'));
  document.getElementById('filter-' + risk)?.classList.add('active');
}

function markReviewed(btn) {
  const alertItem = btn.closest('.alert-item');
  alertItem.classList.add('dismissed');
  btn.textContent = '✓ Reviewed';
  btn.disabled = true;
  showToast('Alert marked as reviewed', 'success');
}

function viewAlertPage(url) {
  showToast(`Opening ${url} in new tab...`, 'info');
  window.open('https://' + url, '_blank');
}

function getAIAlertAnalysis(btn, url, filename, confidence, risk) {
  const alertItem = btn.closest('.alert-item');
  let aiBox = alertItem.querySelector('.ai-analysis-box');
  if (!aiBox) {
    aiBox = document.createElement('div');
    aiBox.className = 'ai-analysis-box show';
    aiBox.innerHTML = '<div class="ai-analysis-title">🤖 AI ALERT ANALYSIS</div><div class="ai-analysis-text">Analyzing...</div>';
    alertItem.querySelector('div[style="flex:1"]').appendChild(aiBox);
  } else {
    aiBox.classList.add('show');
    aiBox.querySelector('.ai-analysis-text').textContent = 'Refreshing analysis...';
  }
  
  callClaudeAPI(`You are an AI legal/IP analyst for AssetShield. An alert was triggered: URL "${url}", file "${filename}", match confidence ${confidence}%, risk level ${risk}. In 2 sentences max: assess the legal severity of this infringement and recommend the single most important next step (DMCA notice, monitoring, or dismissal).`)
    .then(text => { aiBox.querySelector('.ai-analysis-text').textContent = text; });
}

// ─── DMCA GENERATOR ──────────────────────────────────────────────────────────
async function generateDMCA() {
  const name = document.getElementById('dmca-name').value.trim();
  const email = document.getElementById('dmca-email').value.trim();
  const url = document.getElementById('dmca-url').value.trim();
  const desc = document.getElementById('dmca-desc').value.trim();
  
  if (!name || !email || !url) { showToast('Please fill in all required fields', 'error'); return; }
  
  const btnText = document.getElementById('dmca-btn-text');
  btnText.innerHTML = '<span class="spinner"></span> Generating...';
  
  const output = document.getElementById('dmca-output');
  output.classList.add('show');
  output.textContent = 'Generating DMCA notice with AI...';
  
  const prompt = `Generate a professional, legally-formatted DMCA takedown notice with these details:
- Claimant: ${name}
- Email: ${email}  
- Infringing URL: ${url}
- Original Asset: ${desc}
- Date: ${new Date().toLocaleDateString('en-US', {year:'numeric',month:'long',day:'numeric'})}

Format it as a proper DMCA notice under 17 U.S.C. § 512(c)(3) with all required elements: identification of the copyrighted work, location of infringing material, contact info, good faith statement, accuracy statement under penalty of perjury, and signature block. Make it professional and complete.`;

  const text = await callClaudeAPI(prompt, 800);
  output.textContent = text;
  btnText.textContent = '⚡ Generate with AI';
  showToast('DMCA notice generated!', 'success');
}

function copyDMCA() {
  const output = document.getElementById('dmca-output');
  if (!output.textContent || output.textContent === 'Generating DMCA notice with AI...') {
    showToast('Please generate the notice first', 'error'); return;
  }
  navigator.clipboard.writeText(output.textContent).catch(()=>{});
  showToast('DMCA notice copied to clipboard!', 'success');
}

// ─── SIGNUP ───────────────────────────────────────────────────────────────────
function selectPlan(card, plan) {
  document.querySelectorAll('.plan-card').forEach(c => c.classList.remove('selected'));
  card.classList.add('selected');
  state.selectedPlan = plan;
}

async function submitSignup() {
  const fname = document.getElementById('su-fname').value.trim();
  const lname = document.getElementById('su-lname').value.trim();
  const email = document.getElementById('su-email').value.trim();
  const company = document.getElementById('su-company').value.trim();
  
  if (!fname || !email) { showToast('Please fill in your name and email', 'error'); return; }
  if (!email.includes('@')) { showToast('Please enter a valid email address', 'error'); return; }
  
  const btn = document.getElementById('su-btn-text');
  btn.innerHTML = '<span class="spinner"></span> Setting up your account...';
  
  await new Promise(r => setTimeout(r, 1500));
  
  closeModal('signupModal');
  showToast(`Welcome, ${fname}! Your ${state.selectedPlan} trial has started.`, 'success');
  setTimeout(() => showToast('Check your email for setup instructions', 'info'), 1000);
  btn.textContent = '🛡 Start Free 14-Day Trial';
}

// ─── DOCS ─────────────────────────────────────────────────────────────────────
function viewDocs() {
  showToast('Documentation portal opening...', 'info');
  // In a real app, this would open the docs
}

// ─── CLAUDE API ───────────────────────────────────────────────────────────────
async function callClaudeAPI(prompt, maxTokens = 300) {
  try {
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: maxTokens,
        system: 'You are a professional AI assistant for AssetShield, a digital asset protection platform. Be concise, expert, and actionable. Do not use bullet points or headers unless generating a formal document.',
        messages: [{ role: 'user', content: prompt }]
      })
    });
    const data = await response.json();
    return data.content?.[0]?.text || 'Analysis unavailable.';
  } catch (err) {
    return 'AI analysis unavailable. Please check your connection.';
  }
}

// ─── ANIMATED CHART BARS (Intersection Observer) ──────────────────────────────
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.querySelectorAll('.chart-bar[data-w]').forEach(bar => {
        setTimeout(() => { bar.style.width = bar.dataset.w + '%'; }, 100);
      });
      entry.target.querySelectorAll('.match-fill[data-width]').forEach(bar => {
        setTimeout(() => { bar.style.width = bar.dataset.width + '%'; }, 100);
      });
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.2 });

document.querySelectorAll('.analytics-card').forEach(card => observer.observe(card));

// ─── LIVE COUNTER ANIMATION ───────────────────────────────────────────────────
setInterval(() => {
  state.urlsScanned += Math.floor(Math.random() * 3 + 1);
  const el = document.getElementById('m-urls');
  if (el) el.textContent = state.urlsScanned.toLocaleString();
}, 3000);

// ─── KEYBOARD SHORTCUT ────────────────────────────────────────────────────────
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') {
    document.querySelectorAll('.modal-overlay.show').forEach(m => m.classList.remove('show'));
  }
});

// ─── INIT ─────────────────────────────────────────────────────────────────────
// Set filter button IDs properly
document.addEventListener('DOMContentLoaded', () => {
  // Re-observe analytics cards after DOM is fully ready
  document.querySelectorAll('.analytics-card').forEach(card => observer.observe(card));
});
</script>
</body>
</html>
