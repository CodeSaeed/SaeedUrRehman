<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CodeSaeed — Saeed Ur Rehman · GitHub</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #080b10;
    --surface: #0f1318;
    --surface2: #161b23;
    --border: rgba(255,255,255,0.07);
    --text: #e4e8f0;
    --muted: #6b7585;
    --green: #2dff7a;
    --blue: #3d9bff;
    --purple: #b06cff;
    --orange: #ff8c42;
    --pink: #ff4fa3;
    --cyan: #00e5cc;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ─── NAV ─── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 16px 48px;
    background: rgba(8,11,16,0.75);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    display: flex; align-items: center; gap: 10px;
    font-family: 'Syne', sans-serif; font-size: 1.25rem; font-weight: 800;
    color: var(--text); text-decoration: none;
  }
  .nav-logo svg { width: 28px; height: 28px; fill: var(--text); }
  .nav-right { display: flex; align-items: center; gap: 20px; }
  .nav-link { color: var(--muted); text-decoration: none; font-size: .88rem; transition: color .2s; }
  .nav-link:hover { color: var(--text); }
  .btn-sm {
    padding: 7px 18px; border-radius: 8px; font-size: .85rem; font-weight: 600;
    font-family: 'DM Sans', sans-serif; cursor: pointer; text-decoration: none; transition: opacity .2s;
  }
  .btn-sm-green { background: var(--green); color: #05120a; border: none; }
  .btn-sm-ghost { background: transparent; border: 1px solid var(--border); color: var(--text); }
  .btn-sm:hover { opacity: .8; }

  /* ─── LAYOUT ─── */
  .hero {
    min-height: 100vh;
    display: grid; grid-template-columns: 340px 1fr;
    align-items: start;
    padding-top: 70px;
    position: relative; overflow: hidden;
  }

  .hero-bg {
    position: absolute; inset: 0; z-index: 0;
    background:
      radial-gradient(ellipse 55% 60% at 10% 50%, rgba(45,255,122,.08) 0%, transparent 65%),
      radial-gradient(ellipse 45% 55% at 85% 25%, rgba(61,155,255,.09) 0%, transparent 60%),
      radial-gradient(ellipse 40% 45% at 75% 85%, rgba(176,108,255,.08) 0%, transparent 60%);
    animation: bgPulse 14s ease-in-out infinite alternate;
  }
  @keyframes bgPulse {
    0%   { opacity: .8; transform: scale(1); }
    100% { opacity: 1; transform: scale(1.05); }
  }
  .hero::after {
    content: '';
    position: absolute; inset: 0; z-index: 0;
    background-image:
      linear-gradient(rgba(255,255,255,.016) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,.016) 1px, transparent 1px);
    background-size: 44px 44px;
    mask-image: radial-gradient(ellipse 90% 90% at 50% 50%, black, transparent);
  }

  /* SIDEBAR */
  .sidebar {
    position: relative; z-index: 1;
    padding: 48px 36px 60px 48px;
    border-right: 1px solid var(--border);
    min-height: calc(100vh - 70px);
    display: flex; flex-direction: column; gap: 28px;
    animation: fadeUp .7s .05s ease both;
  }

  .avatar-wrap {
    position: relative; display: inline-block; width: fit-content;
  }
  .avatar-wrap img {
    width: 200px; height: 200px; border-radius: 50%;
    border: 3px solid var(--border); display: block;
  }
  .avatar-ring {
    position: absolute; inset: -6px; border-radius: 50%;
    border: 2px solid transparent;
    background: linear-gradient(135deg, var(--green), var(--blue), var(--purple)) border-box;
    -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: destination-out;
    mask-composite: exclude;
    animation: ringRotate 6s linear infinite;
  }
  @keyframes ringRotate {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
  }
  .online-badge {
    position: absolute; bottom: 12px; right: 12px;
    width: 20px; height: 20px; border-radius: 50%;
    background: var(--green); border: 3px solid var(--bg);
    animation: onlinePulse 2.5s ease infinite;
  }
  @keyframes onlinePulse {
    0%,100% { box-shadow: 0 0 0 0 rgba(45,255,122,.5); }
    50%      { box-shadow: 0 0 0 8px rgba(45,255,122,0); }
  }

  .profile-name {
    font-family: 'Syne', sans-serif; font-size: 1.45rem; font-weight: 800; line-height: 1.1;
    margin-bottom: 4px;
  }
  .profile-handle { color: var(--muted); font-size: .95rem; }

  .profile-bio {
    font-size: .875rem; color: var(--muted); line-height: 1.72;
    padding: 16px; background: var(--surface); border: 1px solid var(--border);
    border-radius: 12px; position: relative;
  }
  .profile-bio::before {
    content: '👋'; position: absolute; top: -14px; left: 14px; font-size: 1.3rem;
  }

  .follow-row { display: flex; gap: 10px; }
  .follow-btn {
    flex: 1; padding: 10px; border-radius: 9px; border: none;
    font-family: 'DM Sans', sans-serif; font-size: .875rem; font-weight: 600;
    cursor: pointer; transition: opacity .2s; text-align: center;
    text-decoration: none; display: flex; align-items: center; justify-content: center;
  }
  .fb-g { background: var(--green); color: #05120a; }
  .fb-s { background: var(--surface2); color: var(--text); border: 1px solid var(--border); }
  .follow-btn:hover { opacity: .82; }

  .meta-list { display: flex; flex-direction: column; gap: 10px; }
  .meta-row {
    display: flex; align-items: center; gap: 10px;
    font-size: .855rem; color: var(--muted);
  }
  .meta-row strong { color: var(--text); }

  .skills-wrap { display: flex; flex-wrap: wrap; gap: 7px; }
  .stag {
    padding: 5px 11px; border-radius: 100px; font-size: .73rem; font-weight: 600;
    letter-spacing: .03em;
  }
  .sg { background: rgba(45,255,122,.11); color: var(--green); border: 1px solid rgba(45,255,122,.2); }
  .sb { background: rgba(61,155,255,.11); color: var(--blue);  border: 1px solid rgba(61,155,255,.2); }
  .sp { background: rgba(176,108,255,.11); color: var(--purple); border: 1px solid rgba(176,108,255,.2); }
  .so { background: rgba(255,140,66,.11); color: var(--orange); border: 1px solid rgba(255,140,66,.2); }
  .spk{ background: rgba(255,79,163,.11); color: var(--pink); border: 1px solid rgba(255,79,163,.2); }
  .sc { background: rgba(0,229,204,.11); color: var(--cyan); border: 1px solid rgba(0,229,204,.2); }

  /* MAIN */
  .main {
    position: relative; z-index: 1;
    padding: 40px 52px 60px 48px;
    display: flex; flex-direction: column; gap: 44px;
    animation: fadeUp .7s .15s ease both;
  }

  .sec-head {
    display: flex; align-items: center; justify-content: space-between; margin-bottom: 18px;
  }
  .sec-title {
    font-family: 'Syne', sans-serif; font-size: 1rem; font-weight: 700;
  }
  .sec-link { font-size: .8rem; color: var(--blue); text-decoration: none; }
  .sec-link:hover { text-decoration: underline; }

  /* STATS */
  .stats-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; }
  .stat-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 12px; padding: 18px 20px;
  }
  .sn {
    font-family: 'Syne', sans-serif; font-size: 1.6rem; font-weight: 800;
    line-height: 1; margin-bottom: 4px;
  }
  .sl { font-size: .78rem; color: var(--muted); }

  /* CONTRIB */
  .contrib-box {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 14px; padding: 20px 24px;
  }
  .contrib-note { font-size: .82rem; color: var(--muted); margin-bottom: 16px; }
  .contrib-note strong { color: var(--text); }
  .grid-wrap { display: flex; gap: 4px; overflow-x: auto; }
  .wk { display: flex; flex-direction: column; gap: 4px; }
  .dc {
    width: 13px; height: 13px; border-radius: 3px;
    background: var(--surface2); cursor: default;
    transition: transform .15s;
  }
  .dc:hover { transform: scale(1.35); }
  .l1 { background: rgba(45,255,122,.18); }
  .l2 { background: rgba(45,255,122,.38); }
  .l3 { background: rgba(45,255,122,.62); }
  .l4 { background: rgba(45,255,122,.88); }
  .leg {
    display: flex; align-items: center; gap: 5px; margin-top: 10px;
    justify-content: flex-end; font-size: .7rem; color: var(--muted);
  }
  .lc { width: 11px; height: 11px; border-radius: 2px; }

  /* REPOS */
  .repo-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  .rcard {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 13px; padding: 18px 20px;
    text-decoration: none; display: flex; flex-direction: column;
    transition: border-color .25s, transform .25s;
    position: relative; overflow: hidden;
  }
  .rcard::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px;
    opacity: 0; transition: opacity .25s;
  }
  .rcard:hover { transform: translateY(-3px); border-color: rgba(255,255,255,.15); }
  .rcard:hover::before { opacity: 1; }
  .rc-g::before  { background: var(--green); }
  .rc-b::before  { background: var(--blue); }
  .rc-p::before  { background: var(--purple); }
  .rc-o::before  { background: var(--orange); }
  .rc-pk::before { background: var(--pink); }
  .rc-c::before  { background: var(--cyan); }

  .ri { font-size: 1.4rem; margin-bottom: 10px; }
  .rn {
    font-family: 'Syne', sans-serif; font-size: .92rem; font-weight: 700;
    color: var(--blue); margin-bottom: 7px;
  }
  .rd { font-size: .81rem; color: var(--muted); line-height: 1.65; flex: 1; margin-bottom: 14px; }
  .rf { display: flex; gap: 14px; font-size: .76rem; color: var(--muted); align-items: center; }
  .lw { display: flex; align-items: center; gap: 5px; }
  .ld { width: 9px; height: 9px; border-radius: 50%; display: inline-block; }

  /* ACTIVITY */
  .tl { display: flex; flex-direction: column; }
  .ti {
    display: flex; gap: 14px; padding: 14px 0;
    border-bottom: 1px solid var(--border);
  }
  .ti:last-child { border-bottom: none; }
  .tic {
    width: 34px; height: 34px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: .88rem; flex-shrink: 0; margin-top: 2px;
  }
  .tb { flex: 1; }
  .tm { font-size: .86rem; color: var(--text); margin-bottom: 3px; }
  .tm a { color: var(--blue); text-decoration: none; }
  .tm a:hover { text-decoration: underline; }
  .tt { font-size: .74rem; color: var(--muted); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  footer {
    background: var(--surface); border-top: 1px solid var(--border);
    padding: 32px 48px; display: flex; align-items: center; justify-content: space-between;
    font-size: .78rem; color: var(--muted);
  }
  footer a { color: var(--muted); text-decoration: none; }
  footer a:hover { color: var(--text); }
  .fdots { display: flex; gap: 6px; }
  .fd { width: 8px; height: 8px; border-radius: 50%; }

  @media (max-width: 960px) {
    nav { padding: 14px 20px; }
    .hero { grid-template-columns: 1fr; }
    .sidebar { padding: 40px 20px 28px; border-right: none; border-bottom: 1px solid var(--border); min-height: auto; }
    .avatar-wrap img { width: 140px; height: 140px; }
    .main { padding: 28px 20px 48px; }
    .repo-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: 1fr 1fr; }
    footer { flex-direction: column; gap: 14px; text-align: center; }
  }
</style>
</head>
<body>

<nav>
  <a class="nav-logo" href="#">
    <svg viewBox="0 0 98 96" xmlns="http://www.w3.org/2000/svg">
      <path fill-rule="evenodd" clip-rule="evenodd" d="M48.854 0C21.839 0 0 22 0 49.217c0 21.756 13.993 40.172 33.405 46.69 2.427.49 3.316-1.059 3.316-2.362 0-1.141-.08-5.052-.08-9.127-13.59 2.934-16.42-5.867-16.42-5.867-2.184-5.704-5.42-7.17-5.42-7.17-4.448-3.015.324-3.015.324-3.015 4.934.326 7.523 5.052 7.523 5.052 4.367 7.496 11.404 5.378 14.235 4.074.404-3.178 1.699-5.378 3.074-6.6-10.839-1.141-22.243-5.378-22.243-24.283 0-5.378 1.94-9.778 5.014-13.2-.485-1.222-2.184-6.275.486-13.038 0 0 4.125-1.304 13.426 5.052a46.97 46.97 0 0 1 12.214-1.63c4.125 0 8.33.571 12.213 1.63 9.302-6.356 13.427-5.052 13.427-5.052 2.67 6.763.97 11.816.485 13.038 3.155 3.422 5.015 7.822 5.015 13.2 0 18.905-11.404 23.06-22.324 24.283 1.78 1.548 3.316 4.481 3.316 9.126 0 6.6-.08 11.897-.08 13.526 0 1.304.89 2.853 3.316 2.364 19.412-6.52 33.405-24.935 33.405-46.691C97.707 22 75.788 0 48.854 0z"/>
    </svg>
    GitHub
  </a>
  <div class="nav-right">
    <a href="#" class="nav-link">Explore</a>
    <a href="#" class="nav-link">Marketplace</a>
    <a href="#" class="btn-sm btn-sm-ghost">Sign in</a>
    <a href="#" class="btn-sm btn-sm-green">Sign up</a>
  </div>
</nav>

<div class="hero">
  <div class="hero-bg"></div>

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="avatar-wrap">
      <img src="https://avatars.githubusercontent.com/u/156462713?v=4" alt="Saeed Ur Rehman">
      <div class="avatar-ring"></div>
      <div class="online-badge"></div>
    </div>

    <div>
      <div class="profile-name">Saeed Ur Rehman</div>
      <div class="profile-handle">CodeSaeed</div>
    </div>

    <div class="profile-bio">
      Hi, I'm a Software Engineer passionate about software development — specializing in OutSystems, Shopify, Magento &amp; WordPress. Building clean, scalable web solutions.
    </div>

    <div class="follow-row">
      <a href="https://github.com/CodeSaeed" class="follow-btn fb-g" target="_blank">Follow</a>
      <a href="https://github.com/CodeSaeed?tab=repositories" class="follow-btn fb-s" target="_blank">Repos</a>
    </div>

    <div class="meta-list">
      <div class="meta-row"><span>🏢</span><span>Software Engineer</span></div>
      <div class="meta-row"><span>📦</span><span><strong>6</strong> public repositories</span></div>
      <div class="meta-row"><span>👥</span><span><strong>0</strong> followers · <strong>0</strong> following</span></div>
      <div class="meta-row"><span>🌐</span><span>Web · E-commerce · Low-code</span></div>
    </div>

    <div>
      <div style="font-size:.76rem;color:var(--muted);text-transform:uppercase;letter-spacing:.1em;margin-bottom:11px;font-weight:600;">Tech Stack</div>
      <div class="skills-wrap">
        <span class="stag so">OutSystems</span>
        <span class="stag sg">Shopify</span>
        <span class="stag sb">Magento</span>
        <span class="stag sp">WordPress</span>
        <span class="stag sc">JavaScript</span>
        <span class="stag spk">HTML / CSS</span>
      </div>
    </div>
  </aside>

  <!-- MAIN -->
  <main class="main">

    <!-- STATS -->
    <div class="stats-row">
      <div class="stat-card">
        <div class="sn" style="color:var(--green)">6</div>
        <div class="sl">Repositories</div>
      </div>
      <div class="stat-card">
        <div class="sn" style="color:var(--blue)">0</div>
        <div class="sl">Followers</div>
      </div>
      <div class="stat-card">
        <div class="sn" style="color:var(--purple)">0</div>
        <div class="sl">Following</div>
      </div>
      <div class="stat-card">
        <div class="sn" style="color:var(--orange)">6</div>
        <div class="sl">Projects built</div>
      </div>
    </div>

    <!-- CONTRIBUTIONS -->
    <div>
      <div class="sec-head">
        <div class="sec-title">📈 Contributions</div>
        <a href="https://github.com/CodeSaeed" class="sec-link" target="_blank">View on GitHub →</a>
      </div>
      <div class="contrib-box">
        <div class="contrib-note"><strong>Growing every day</strong> — every commit counts 🚀</div>
        <div class="grid-wrap" id="contrib-grid"></div>
        <div class="leg">
          Less
          <div class="lc" style="background:var(--surface2)"></div>
          <div class="lc l1"></div>
          <div class="lc l2"></div>
          <div class="lc l3"></div>
          <div class="lc l4"></div>
          More
        </div>
      </div>
    </div>

    <!-- PINNED REPOS -->
    <div>
      <div class="sec-head">
        <div class="sec-title">📌 Pinned Repositories</div>
        <a href="https://github.com/CodeSaeed?tab=repositories" class="sec-link" target="_blank">All 6 repos →</a>
      </div>
      <div class="repo-grid">

        <a class="rcard rc-g" href="https://github.com/CodeSaeed/Swiggy-Ui-main" target="_blank">
          <div class="ri">🍔</div>
          <div class="rn">Swiggy-Ui-main</div>
          <div class="rd">A pixel-perfect UI clone of the popular food delivery platform Swiggy. Built with HTML &amp; CSS with clean, responsive layouts.</div>
          <div class="rf">
            <span class="lw"><span class="ld" style="background:#e34c26"></span>HTML</span>
            <span>⭐ 0</span><span>🍴 0</span>
          </div>
        </a>

        <a class="rcard rc-b" href="https://github.com/CodeSaeed/labnix-website" target="_blank">
          <div class="ri">🔬</div>
          <div class="rn">labnix-website</div>
          <div class="rd">A modern website project for Labnix, built with JavaScript. Showcases clean frontend architecture and professional web development skills.</div>
          <div class="rf">
            <span class="lw"><span class="ld" style="background:#f1e05a"></span>JavaScript</span>
            <span>⭐ 0</span><span>🍴 0</span>
          </div>
        </a>

        <a class="rcard rc-o" href="https://github.com/CodeSaeed/backend-vehicle-booking-app" target="_blank">
          <div class="ri">🚗</div>
          <div class="rn">backend-vehicle-booking-app</div>
          <div class="rd">Backend REST API for a vehicle booking system — managing reservations, availability, and user workflows with JavaScript.</div>
          <div class="rf">
            <span class="lw"><span class="ld" style="background:#f1e05a"></span>JavaScript</span>
            <span>⭐ 0</span><span>🍴 0</span>
          </div>
        </a>

        <a class="rcard rc-p" href="https://github.com/CodeSaeed/vehicle-rental" target="_blank">
          <div class="ri">🚙</div>
          <div class="rn">vehicle-rental</div>
          <div class="rd">Full-stack vehicle rental web application — browse, book, and manage rentals end-to-end for modern rental businesses.</div>
          <div class="rf">
            <span class="lw"><span class="ld" style="background:#f1e05a"></span>JavaScript</span>
            <span>⭐ 0</span><span>🍴 0</span>
          </div>
        </a>

        <a class="rcard rc-pk" href="https://github.com/CodeSaeed/VehicleProj" target="_blank">
          <div class="ri">🏎️</div>
          <div class="rn">VehicleProj</div>
          <div class="rd">A JavaScript project exploring vehicle management systems with different UI/UX approaches and architectural patterns.</div>
          <div class="rf">
            <span class="lw"><span class="ld" style="background:#f1e05a"></span>JavaScript</span>
            <span>⭐ 0</span><span>🍴 0</span>
          </div>
        </a>

        <a class="rcard rc-c" href="https://github.com/CodeSaeed/SaeedUrRehman" target="_blank">
          <div class="ri">👨‍💻</div>
          <div class="rn">SaeedUrRehman</div>
          <div class="rd">Profile README — "Code with me." The special repository that powers the GitHub profile introduction and personal branding.</div>
          <div class="rf">
            <span class="lw"><span class="ld" style="background:#083fa1"></span>Markdown</span>
            <span>✨ Profile repo</span>
          </div>
        </a>

      </div>
    </div>

    <!-- ACTIVITY -->
    <div>
      <div class="sec-head">
        <div class="sec-title">⚡ Recent Activity</div>
      </div>
      <div class="contrib-box">
        <div class="tl">
          <div class="ti">
            <div class="tic" style="background:rgba(45,255,122,.12)">🔀</div>
            <div class="tb">
              <div class="tm">Created repository <a href="https://github.com/CodeSaeed/backend-vehicle-booking-app" target="_blank">backend-vehicle-booking-app</a></div>
              <div class="tt">Recently · JavaScript · Backend REST API</div>
            </div>
          </div>
          <div class="ti">
            <div class="tic" style="background:rgba(61,155,255,.12)">📁</div>
            <div class="tb">
              <div class="tm">Pushed commits to <a href="https://github.com/CodeSaeed/vehicle-rental" target="_blank">vehicle-rental</a></div>
              <div class="tt">Recently · Full-stack vehicle rental webapp</div>
            </div>
          </div>
          <div class="ti">
            <div class="tic" style="background:rgba(176,108,255,.12)">🌟</div>
            <div class="tb">
              <div class="tm">Created <a href="https://github.com/CodeSaeed/Swiggy-Ui-main" target="_blank">Swiggy-Ui-main</a> — food delivery UI clone</div>
              <div class="tt">Recently · HTML &amp; CSS</div>
            </div>
          </div>
          <div class="ti">
            <div class="tic" style="background:rgba(255,140,66,.12)">🚀</div>
            <div class="tb">
              <div class="tm">Set up profile README at <a href="https://github.com/CodeSaeed/SaeedUrRehman" target="_blank">SaeedUrRehman</a></div>
              <div class="tt">Recently · GitHub Profile</div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </main>
</div>

<footer>
  <span>© 2026 GitHub, Inc. — <a href="https://github.com/CodeSaeed" target="_blank">github.com/CodeSaeed</a></span>
  <div class="fdots">
    <div class="fd" style="background:var(--green)"></div>
    <div class="fd" style="background:var(--blue)"></div>
    <div class="fd" style="background:var(--purple)"></div>
    <div class="fd" style="background:var(--orange)"></div>
    <div class="fd" style="background:var(--pink)"></div>
  </div>
  <span>
    <a href="#">Terms</a> &nbsp;·&nbsp;
    <a href="#">Privacy</a> &nbsp;·&nbsp;
    <a href="https://github.com/CodeSaeed" target="_blank">View on GitHub ↗</a>
  </span>
</footer>

<script>
  const grid = document.getElementById('contrib-grid');
  for (let w = 0; w < 52; w++) {
    const col = document.createElement('div');
    col.className = 'wk';
    for (let d = 0; d < 7; d++) {
      const cell = document.createElement('div');
      const r = Math.random();
      let cls = 'dc';
      if (r > 0.91) cls += ' l4';
      else if (r > 0.83) cls += ' l3';
      else if (r > 0.74) cls += ' l2';
      else if (r > 0.63) cls += ' l1';
      cell.className = cls;
      col.appendChild(cell);
    }
    grid.appendChild(col);
  }
</script>
</body>
</html>
