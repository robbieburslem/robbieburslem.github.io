<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Robbie Burslem — Mechanical Engineer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=IBM+Plex+Sans:wght@300;400;500&family=IBM+Plex+Mono:wght@400&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #f5f3ef;
      --ink: #1c1b18;
      --muted: #7a7870;
      --accent: #b84c1e;
      --accent-light: #f0e6df;
      --border: #dedad3;
      --card: #fdfcfa;
      --serif: 'Playfair Display', Georgia, serif;
      --sans: 'IBM Plex Sans', system-ui, sans-serif;
      --mono: 'IBM Plex Mono', monospace;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--ink);
      font-family: var(--sans);
      font-size: 16px;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.2rem 3rem;
      background: rgba(245,243,239,0.92);
      backdrop-filter: blur(14px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo { display: flex; flex-direction: column; text-decoration: none; }
    .nav-logo-name { font-family: var(--serif); font-size: 1.05rem; color: var(--ink); line-height: 1.1; }
    .nav-logo-title { font-size: 0.7rem; font-weight: 400; letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted); }

    .nav-links { display: flex; gap: 2.25rem; list-style: none; align-items: center; }
    .nav-links a { font-size: 0.82rem; font-weight: 400; letter-spacing: 0.09em; text-transform: uppercase; color: var(--muted); text-decoration: none; transition: color 0.2s; }
    .nav-links a:hover { color: var(--ink); }
    .nav-cta { color: var(--accent) !important; font-weight: 500 !important; }

    /* HERO */
    #hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      max-width: 1200px;
      margin: 0 auto;
      padding: 8rem 3rem 4rem;
      gap: 4rem;
    }

    .hero-eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      font-family: var(--mono);
      font-size: 0.75rem;
      color: var(--accent);
      margin-bottom: 1.75rem;
      opacity: 0;
      animation: fadeUp 0.6s 0.1s forwards;
    }

    .hero-eyebrow::before { content: ''; width: 28px; height: 1px; background: var(--accent); }

    .hero-name {
      font-family: var(--serif);
      font-size: clamp(3.2rem, 6vw, 5.2rem);
      line-height: 1.0;
      letter-spacing: -0.01em;
      margin-bottom: 1.5rem;
      opacity: 0;
      animation: fadeUp 0.6s 0.22s forwards;
    }

    .hero-name em { font-style: italic; color: var(--accent); display: block; }

    .hero-bio {
      font-size: 1rem;
      font-weight: 300;
      color: var(--muted);
      max-width: 440px;
      line-height: 1.85;
      margin-bottom: 2.5rem;
      opacity: 0;
      animation: fadeUp 0.6s 0.36s forwards;
    }

    .hero-actions {
      display: flex;
      gap: 0.875rem;
      flex-wrap: wrap;
      opacity: 0;
      animation: fadeUp 0.6s 0.48s forwards;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.7rem 1.5rem;
      border-radius: 1px;
      font-size: 0.82rem;
      font-weight: 500;
      letter-spacing: 0.06em;
      text-decoration: none;
      cursor: pointer;
      border: none;
      font-family: var(--sans);
      transition: all 0.2s;
    }

    .btn-primary { background: var(--ink); color: var(--bg); }
    .btn-primary:hover { background: var(--accent); }
    .btn-ghost { background: transparent; color: var(--ink); border: 1px solid var(--border); }
    .btn-ghost:hover { border-color: var(--ink); }

    /* Blueprint panel */
    .hero-right { opacity: 0; animation: fadeIn 1s 0.6s forwards; }

    .blueprint {
      background: #1a2740;
      border-radius: 2px;
      padding: 2.5rem;
      aspect-ratio: 1;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
    }

    .blueprint::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(100,160,255,0.07) 1px, transparent 1px),
        linear-gradient(90deg, rgba(100,160,255,0.07) 1px, transparent 1px);
      background-size: 32px 32px;
    }

    .bp-svg { width: 80%; height: 80%; position: relative; z-index: 1; }

    .bp-label {
      position: absolute;
      bottom: 1.25rem; left: 1.5rem;
      font-family: var(--mono);
      font-size: 0.65rem;
      color: rgba(100,160,255,0.45);
      letter-spacing: 0.1em;
    }

    .bp-corner { position: absolute; width: 14px; height: 14px; border-color: rgba(100,160,255,0.35); border-style: solid; }
    .bp-corner.tl { top: 12px; left: 12px; border-width: 1px 0 0 1px; }
    .bp-corner.tr { top: 12px; right: 12px; border-width: 1px 1px 0 0; }
    .bp-corner.bl { bottom: 12px; left: 12px; border-width: 0 0 1px 1px; }
    .bp-corner.br { bottom: 12px; right: 12px; border-width: 0 1px 1px 0; }

    /* SECTIONS */
    section {
      padding: 6rem 3rem;
      max-width: 1200px;
      margin: 0 auto;
      border-top: 1px solid var(--border);
    }

    .section-header { display: flex; align-items: baseline; gap: 1.25rem; margin-bottom: 3.5rem; }
    .section-num { font-family: var(--mono); font-size: 0.72rem; color: var(--accent); opacity: 0.7; }
    .section-title { font-family: var(--serif); font-size: clamp(1.8rem, 3.5vw, 2.6rem); line-height: 1.1; }

    /* ABOUT */
    .about-grid { display: grid; grid-template-columns: 3fr 2fr; gap: 5rem; align-items: start; }

    .about-text p { font-weight: 300; color: #4a4843; line-height: 1.9; margin-bottom: 1.25rem; font-size: 1.025rem; }

    .about-stats { display: flex; flex-direction: column; gap: 1px; border: 1px solid var(--border); }

    .stat-row { display: flex; justify-content: space-between; align-items: center; padding: 1.1rem 1.25rem; background: var(--card); border-bottom: 1px solid var(--border); }
    .stat-row:last-child { border-bottom: none; }
    .stat-label { font-size: 0.72rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
    .stat-value { font-family: var(--mono); font-size: 0.85rem; color: var(--ink); }

    /* PROJECTS */
    .projects-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; }

    .project-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 2rem;
      text-decoration: none;
      color: inherit;
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
      transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
      position: relative;
      overflow: hidden;
    }

    .project-card::after { content: ''; position: absolute; bottom: 0; left: 0; height: 2px; width: 0; background: var(--accent); transition: width 0.35s ease; }
    .project-card:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(0,0,0,0.07); border-color: #c8c3bb; }
    .project-card:hover::after { width: 100%; }

    .project-tag { font-family: var(--mono); font-size: 0.68rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--accent); }
    .project-card h3 { font-family: var(--serif); font-size: 1.35rem; line-height: 1.2; }
    .project-card p { font-size: 0.9rem; font-weight: 300; color: var(--muted); line-height: 1.7; flex: 1; }

    .project-pills { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.25rem; }
    .pill { font-size: 0.7rem; font-family: var(--mono); padding: 0.2rem 0.6rem; background: var(--accent-light); color: var(--accent); border-radius: 1px; }

    .project-arrow { font-size: 0.82rem; font-weight: 500; color: var(--ink); margin-top: 0.5rem; display: inline-flex; align-items: center; gap: 0.4rem; transition: gap 0.2s; }
    .project-card:hover .project-arrow { gap: 0.7rem; }

    /* SKILLS */
    .skills-layout { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.25rem; }

    .skill-group { background: var(--card); border: 1px solid var(--border); padding: 1.75rem; }
    .skill-group-icon { font-size: 1.4rem; margin-bottom: 1rem; }
    .skill-group h4 { font-size: 0.7rem; letter-spacing: 0.14em; text-transform: uppercase; color: var(--muted); margin-bottom: 1rem; padding-bottom: 0.75rem; border-bottom: 1px solid var(--border); }

    .skill-list { list-style: none; display: flex; flex-direction: column; gap: 0.55rem; }
    .skill-list li { font-size: 0.875rem; font-weight: 400; color: var(--ink); display: flex; align-items: center; gap: 0.5rem; }
    .skill-list li::before { content: ''; width: 3px; height: 3px; border-radius: 50%; background: var(--accent); flex-shrink: 0; }

    /* CONTACT */
    .contact-inner { display: grid; grid-template-columns: 1fr 1fr; gap: 6rem; align-items: start; }

    .contact-text p { font-size: 1rem; font-weight: 300; color: var(--muted); line-height: 1.9; margin-bottom: 2rem; }

    .contact-links { display: flex; flex-direction: column; gap: 0.6rem; }

    .contact-link { display: flex; align-items: center; gap: 0.875rem; font-size: 0.875rem; color: var(--ink); text-decoration: none; padding: 0.875rem 1.1rem; border: 1px solid var(--border); background: var(--card); transition: border-color 0.2s, transform 0.15s; }
    .contact-link:hover { border-color: var(--ink); transform: translateX(3px); }
    .contact-link-icon { font-family: var(--mono); font-size: 0.8rem; color: var(--accent); width: 1.5rem; flex-shrink: 0; }
    .contact-link-label { flex: 1; }
    .contact-link-sub { font-size: 0.75rem; color: var(--muted); font-family: var(--mono); }

    .contact-form { display: flex; flex-direction: column; gap: 1.25rem; }
    .form-group { display: flex; flex-direction: column; gap: 0.4rem; }
    .form-group label { font-size: 0.7rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); font-family: var(--mono); }
    .form-group input, .form-group textarea { background: var(--card); border: 1px solid var(--border); padding: 0.75rem 1rem; font-family: var(--sans); font-size: 0.95rem; font-weight: 300; color: var(--ink); outline: none; transition: border-color 0.2s; resize: vertical; border-radius: 1px; }
    .form-group input:focus, .form-group textarea:focus { border-color: var(--accent); }
    .form-group textarea { min-height: 120px; }

    /* FOOTER */
    footer { border-top: 1px solid var(--border); padding: 2rem 3rem; max-width: 1200px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; }
    .footer-left { font-family: var(--serif); font-size: 0.95rem; color: var(--ink); }
    .footer-right { font-family: var(--mono); font-size: 0.72rem; color: var(--muted); }

    /* ANIMATIONS */
    @keyframes fadeUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

    .reveal { opacity: 0; transform: translateY(18px); transition: opacity 0.6s ease, transform 0.6s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      #hero { grid-template-columns: 1fr; }
      .hero-right { display: none; }
      .about-grid { grid-template-columns: 1fr; gap: 2.5rem; }
      .projects-grid { grid-template-columns: 1fr; }
      .skills-layout { grid-template-columns: repeat(2, 1fr); }
      .contact-inner { grid-template-columns: 1fr; gap: 3rem; }
    }

    @media (max-width: 600px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      section { padding: 4rem 1.5rem; }
      #hero { padding: 7rem 1.5rem 3rem; }
      .skills-layout { grid-template-columns: 1fr; }
      footer { flex-direction: column; gap: 0.5rem; text-align: center; padding: 1.5rem; }
    }
  </style>
</head>
<body>

  <nav>
    <a href="#hero" class="nav-logo">
      <span class="nav-logo-name">Robbie Burslem</span>
      <span class="nav-logo-title">Mechanical Engineer</span>
    </a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#contact" class="nav-cta">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <div id="hero">
    <div class="hero-left">
      <p class="hero-eyebrow">Mechanical Engineer</p>
      <h1 class="hero-name">
        Robbie
        <em>Burslem.</em>
      </h1>
      <p class="hero-bio">I design and build things — from precise CAD models and manufactured components to automated systems. My work sits at the intersection of mechanical design, manufacturing, and robotics.</p>
      <div class="hero-actions">
        <a href="#projects" class="btn btn-primary">See my projects</a>
        <a href="https://github.com/robbieburslem" target="_blank" class="btn btn-ghost">GitHub ↗</a>
      </div>
    </div>
    <div class="hero-right">
      <div class="blueprint">
        <div class="bp-corner tl"></div>
        <div class="bp-corner tr"></div>
        <div class="bp-corner bl"></div>
        <div class="bp-corner br"></div>
        <svg class="bp-svg" viewBox="0 0 220 220" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="110" cy="110" r="90" stroke="rgba(100,160,255,0.15)" stroke-width="0.5" stroke-dasharray="4 4"/>
          <circle cx="110" cy="110" r="62" stroke="rgba(100,160,255,0.55)" stroke-width="1"/>
          <circle cx="110" cy="110" r="22" stroke="rgba(100,160,255,0.55)" stroke-width="1"/>
          <circle cx="110" cy="110" r="9" stroke="rgba(100,160,255,0.8)" stroke-width="1.5"/>
          <line x1="110" y1="20" x2="110" y2="200" stroke="rgba(100,160,255,0.15)" stroke-width="0.5"/>
          <line x1="20" y1="110" x2="200" y2="110" stroke="rgba(100,160,255,0.15)" stroke-width="0.5"/>
          <g stroke="rgba(100,160,255,0.55)" stroke-width="1" fill="none">
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(0 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(30 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(60 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(90 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(120 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(150 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(180 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(210 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(240 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(270 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(300 110 110) translate(0 -6)"/>
            <rect x="104" y="42" width="12" height="12" rx="1" transform="rotate(330 110 110) translate(0 -6)"/>
          </g>
          <g stroke="rgba(100,160,255,0.3)" stroke-width="0.75">
            <line x1="110" y1="88" x2="110" y2="48"/>
            <line x1="110" y1="88" x2="110" y2="48" transform="rotate(120 110 110)"/>
            <line x1="110" y1="88" x2="110" y2="48" transform="rotate(240 110 110)"/>
          </g>
          <line x1="20" y1="190" x2="200" y2="190" stroke="rgba(100,160,255,0.25)" stroke-width="0.5"/>
          <line x1="20" y1="186" x2="20" y2="194" stroke="rgba(100,160,255,0.25)" stroke-width="0.5"/>
          <line x1="200" y1="186" x2="200" y2="194" stroke="rgba(100,160,255,0.25)" stroke-width="0.5"/>
          <text x="110" y="187" fill="rgba(100,160,255,0.4)" font-size="6" font-family="monospace" text-anchor="middle">∅ 124.0 mm</text>
        </svg>
        <span class="bp-label">DWG-001 / GEAR ASSEMBLY / REV A</span>
      </div>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about">
    <div class="section-header reveal">
      <span class="section-num">01</span>
      <h2 class="section-title">About me</h2>
    </div>
    <div class="about-grid">
      <div class="about-text reveal">
        <p>I'm Robbie Burslem, a mechanical engineer with a focus on design, manufacturing, and robotics & automation. I enjoy the full arc of engineering — from the first SolidWorks sketch to a manufactured part or working prototype.</p>
        <p>My work spans precision component design, design-for-manufacture, and building automated systems. I'm drawn to problems that demand both rigorous analysis and hands-on ingenuity.</p>
        <p>This portfolio showcases projects I've built and engineered. If something catches your eye or you want to work together, feel free to get in touch.</p>
      </div>
      <div class="about-stats reveal">
        <div class="stat-row">
          <span class="stat-label">Discipline</span>
          <span class="stat-value">Mechanical Engineering</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Focus Areas</span>
          <span class="stat-value">Design · Mfg · Robotics</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Primary CAD</span>
          <span class="stat-value">SolidWorks</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">GitHub</span>
          <span class="stat-value">@robbieburslem</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Status</span>
          <span class="stat-value">Open to opportunities</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="section-header reveal">
      <span class="section-num">02</span>
      <h2 class="section-title">Projects</h2>
    </div>
    <div class="projects-grid">

      <a href="https://github.com/robbieburslem/project-one" target="_blank" class="project-card reveal">
        <span class="project-tag">Design & CAD</span>
        <h3>Project One Title</h3>
        <p>Describe what you designed, the engineering problem you solved, and any interesting design decisions. What were the key constraints? What was the outcome?</p>
        <div class="project-pills">
          <span class="pill">SolidWorks</span>
          <span class="pill">FEA</span>
          <span class="pill">3D Printing</span>
        </div>
        <span class="project-arrow">View project →</span>
      </a>

      <a href="https://github.com/robbieburslem/project-two" target="_blank" class="project-card reveal">
        <span class="project-tag">Robotics & Automation</span>
        <h3>Project Two Title</h3>
        <p>Describe the robotic or automated system you built. What actuators, sensors, or control systems were involved? What problem did it solve?</p>
        <div class="project-pills">
          <span class="pill">Arduino</span>
          <span class="pill">Servo Control</span>
          <span class="pill">Python</span>
        </div>
        <span class="project-arrow">View project →</span>
      </a>

      <a href="https://github.com/robbieburslem/project-three" target="_blank" class="project-card reveal">
        <span class="project-tag">Manufacturing</span>
        <h3>Project Three Title</h3>
        <p>Describe a manufacturing or fabrication project. What process did you use — machining, sheet metal, welding? What were the tolerances and constraints?</p>
        <div class="project-pills">
          <span class="pill">CNC Machining</span>
          <span class="pill">GD&T</span>
          <span class="pill">SolidWorks</span>
        </div>
        <span class="project-arrow">View project →</span>
      </a>

      <a href="https://github.com/robbieburslem/project-four" target="_blank" class="project-card reveal">
        <span class="project-tag">Design & CAD</span>
        <h3>Project Four Title</h3>
        <p>A capstone, competition entry, or personal build. Describe the design challenge, your engineering approach, and the final result.</p>
        <div class="project-pills">
          <span class="pill">SolidWorks</span>
          <span class="pill">Simulation</span>
          <span class="pill">Prototyping</span>
        </div>
        <span class="project-arrow">View project →</span>
      </a>

    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="section-header reveal">
      <span class="section-num">03</span>
      <h2 class="section-title">Skills & tools</h2>
    </div>
    <div class="skills-layout">
      <div class="skill-group reveal">
        <div class="skill-group-icon">✏️</div>
        <h4>CAD & Design</h4>
        <ul class="skill-list">
          <li>SolidWorks</li>
          <li>Technical Drawing</li>
          <li>GD&T</li>
          <li>Design for Manufacture</li>
          <li>FEA / Simulation</li>
        </ul>
      </div>
      <div class="skill-group reveal">
        <div class="skill-group-icon">⚙️</div>
        <h4>Manufacturing</h4>
        <ul class="skill-list">
          <li>CNC Machining</li>
          <li>3D Printing / FDM</li>
          <li>Sheet Metal</li>
          <li>Welding</li>
          <li>Workshop Practice</li>
        </ul>
      </div>
      <div class="skill-group reveal">
        <div class="skill-group-icon">🤖</div>
        <h4>Robotics & Automation</h4>
        <ul class="skill-list">
          <li>Mechanism Design</li>
          <li>Actuators & Sensors</li>
          <li>Arduino / Embedded</li>
          <li>Control Systems</li>
          <li>Python</li>
        </ul>
      </div>
      <div class="skill-group reveal">
        <div class="skill-group-icon">📐</div>
        <h4>Engineering</h4>
        <ul class="skill-list">
          <li>Statics & Dynamics</li>
          <li>Materials Science</li>
          <li>Thermodynamics</li>
          <li>MATLAB</li>
          <li>Technical Writing</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="section-header reveal">
      <span class="section-num">04</span>
      <h2 class="section-title">Get in touch</h2>
    </div>
    <div class="contact-inner">
      <div class="contact-text reveal">
        <p>I'm always happy to talk about interesting engineering problems, collaborations, or opportunities. Send me a message and I'll get back to you.</p>
        <div class="contact-links">
          <a href="mailto:robbie@example.com" class="contact-link">
            <span class="contact-link-icon">✉</span>
            <span class="contact-link-label">robbie@example.com</span>
            <span class="contact-link-sub">Email</span>
          </a>
          <a href="https://github.com/robbieburslem" target="_blank" class="contact-link">
            <span class="contact-link-icon">⌥</span>
            <span class="contact-link-label">github.com/robbieburslem</span>
            <span class="contact-link-sub">GitHub</span>
          </a>
          <a href="https://linkedin.com/in/robbieburslem" target="_blank" class="contact-link">
            <span class="contact-link-icon">↗</span>
            <span class="contact-link-label">linkedin.com/in/robbieburslem</span>
            <span class="contact-link-sub">LinkedIn</span>
          </a>
        </div>
      </div>
      <form class="contact-form reveal" onsubmit="handleSubmit(event)">
        <div class="form-group">
          <label for="cname">Name</label>
          <input type="text" id="cname" placeholder="Jane Smith" required />
        </div>
        <div class="form-group">
          <label for="cemail">Email</label>
          <input type="email" id="cemail" placeholder="jane@example.com" required />
        </div>
        <div class="form-group">
          <label for="cmessage">Message</label>
          <textarea id="cmessage" placeholder="Tell me about your project or enquiry..." required></textarea>
        </div>
        <button type="submit" class="btn btn-primary">Send message →</button>
      </form>
    </div>
  </section>

  <footer>
    <span class="footer-left">Robbie Burslem</span>
    <span class="footer-right">© 2026 · robbieburslem.github.io</span>
  </footer>

  <script>
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((e, i) => {
        if (e.isIntersecting) {
          e.target.style.transitionDelay = `${(i % 4) * 0.08}s`;
          e.target.classList.add('visible');
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

    function handleSubmit(e) {
      e.preventDefault();
      const btn = e.target.querySelector('button[type="submit"]');
      btn.textContent = 'Sent ✓';
      btn.style.background = '#2d6a4f';
      btn.disabled = true;
      e.target.reset();
      setTimeout(() => {
        btn.textContent = 'Send message →';
        btn.style.background = '';
        btn.disabled = false;
      }, 4000);
    }
  </script>

</body>
</html>
