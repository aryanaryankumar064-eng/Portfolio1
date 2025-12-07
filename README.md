  <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Clutch God — Neon Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
<style>
  :root{
    --neon-blue: #00C8FF;
    --electric-blue: #008CFF;
    --ice-blue: #CCF7FF;
    --neon-white: #F5F7FF;
    --neon-black: #04050A;
    --glass: rgba(255,255,255,0.02);
    --card-bg: rgba(6,7,10,0.65);
    --radius: 14px;
  }

  /* Reset & base */
  *{box-sizing:border-box}
  html,body{height:100%}
  body{
    margin:0;
    font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;
    background:linear-gradient(180deg,var(--neon-black) 0%, #07080C 100%);
    color:var(--neon-white);
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    overflow-x:hidden;
    scroll-behavior:smooth;
  }

  /* Accessible reduced motion respect */
  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.001ms !important; animation-iteration-count:1 !important; transition-duration:0.001ms !important;}
  }

  /* Layout */
  header{
    position:fixed; inset:0 0 auto 0; height:72px; display:flex; align-items:center; justify-content:space-between;
    padding:12px 28px; backdrop-filter: blur(6px); z-index:60;
    background: linear-gradient(180deg, rgba(4,5,10,0.65), rgba(4,5,10,0.35));
    border-bottom:1px solid rgba(0,200,255,0.06);
  }
  .brand{display:flex; gap:14px; align-items:center; cursor:default}
  .logo-bubble{
    width:44px;height:44px;border-radius:10px;
    background: linear-gradient(135deg,var(--neon-blue),var(--electric-blue));
    box-shadow:0 6px 28px rgba(0,200,255,0.12), inset 0 -6px 18px rgba(255,255,255,0.02);
    display:flex;align-items:center;justify-content:center;font-weight:800;color:var(--neon-black);
  }
  nav a{color:var(--ice-blue); margin:0 12px; text-decoration:none; font-weight:600; letter-spacing:0.4px; font-size:0.95rem;}
  nav a:hover{color:var(--neon-blue); transform:translateY(-2px);}

  main{padding-top:88px;}

  /* HERO */
  .hero{
    min-height:92vh; display:flex; align-items:center; justify-content:center; text-align:center; position:relative; padding:48px 24px;
    overflow:hidden;
  }
  .hero-grid{
    width:min(1200px,95%); display:grid; grid-template-columns: 1fr 420px; gap:34px; align-items:center;
  }
  .hero-left{
    text-align:left;
  }
  .eyebrow{
    color:var(--ice-blue);
    font-weight:600;
    font-size:0.9rem;
    letter-spacing:1px;
    margin-bottom:12px;
  }
  h1{
    color:var(--neon-blue);
    font-size: clamp(2.2rem, 4.2vw, 4.2rem);
    margin:0 0 12px 0;
    line-height:1.02;
    text-shadow:
      0 0 18px rgba(0,200,255,0.12),
      0 0 48px rgba(0,200,255,0.08);
  }
  p.lead{
    color:var(--neon-white);
    opacity:0.95;
    margin:10px 0 24px 0;
    max-width:56ch;
    font-size:1.05rem;
  }
  .cta-row{display:flex; gap:16px; align-items:center; flex-wrap:wrap;}
  .btn{
    --pad:14px 22px;
    padding:var(--pad);
    border-radius:10px;
    background:linear-gradient(90deg,var(--neon-blue),var(--electric-blue));
    color:var(--neon-black);
    font-weight:700;
    border:none;
    cursor:pointer;
    box-shadow: 0 10px 40px rgba(0,200,255,0.12);
    transition: transform .22s ease, box-shadow .22s ease;
  }
  .btn:hover{ transform:translateY(-6px) scale(1.01); box-shadow:0 22px 70px rgba(0,140,255,0.14); }

  .ghost{
    padding:12px 18px; border-radius:10px; background:transparent;
    color:var(--ice-blue); border:1px solid rgba(204,247,255,0.06); font-weight:600;
  }

  /* Hero 3D card right */
  .hero-right{
    display:flex; align-items:center; justify-content:center;
  }
  .preview-card{
    width:100%; max-width:420px; background:var(--card-bg); border-radius:18px; padding:22px;
    border:1px solid rgba(0,200,255,0.06);
    transform-style:preserve-3d;
    box-shadow: 0 18px 60px rgba(2,6,12,0.6), inset 0 -6px 20px rgba(255,255,255,0.02);
    transition: transform .45s cubic-bezier(.15,.9,.2,1), box-shadow .45s;
  }
  .preview-canvas{
    height:260px; border-radius:12px; background: linear-gradient(180deg, rgba(4,6,12,0.7), rgba(4,6,12,0.45));
    display:flex; align-items:center; justify-content:center; position:relative; overflow:hidden;
    box-shadow:0 8px 30px rgba(0,0,0,0.6);
  }
  /* simple CSS '3D shape' cubes using pseudo */
  .shape {
    position:absolute; width:92px; height:92px; border-radius:10px;
    background: linear-gradient(135deg, rgba(0,200,255,0.16), rgba(0,140,255,0.06));
    box-shadow: 0 10px 36px rgba(0,200,255,0.06), 0 0 40px rgba(0,200,255,0.04);
    transform: translateZ(0);
    will-change: transform, opacity;
  }
  .shape.s1{ left:14%; top:24%; transform:rotate(16deg) scale(1.05); width:110px; height:110px;}
  .shape.s2{ right:8%; top:18%; transform:rotate(-12deg) scale(.86); width:84px;height:84px; }
  .shape.s3{ left:38%; bottom:10%; transform:rotate(6deg) scale(.9); width:70px;height:70px; }

  .preview-info{ margin-top:14px; color:var(--ice-blue); display:flex; justify-content:space-between; align-items:center; gap:12px; font-weight:600; }

  /* Sections common */
  section{padding:96px 20px;}
  .wrap{max-width:1100px;margin:0 auto;}

  /* ABOUT */
  .about-grid{display:grid; grid-template-columns: 1fr 360px; gap:28px; align-items:center;}
  .about-card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); padding:22px;border-radius:12px; border:1px solid rgba(0,200,255,0.04);}
  .about-avatar{height:220px;border-radius:12px;background:linear-gradient(135deg, rgba(0,200,255,0.07), rgba(204,247,255,0.02));display:flex;align-items:center;justify-content:center;font-weight:700;color:var(--neon-blue); font-size:1.1rem;}

  /* PROJECTS */
  .projects-grid{ display:grid; grid-template-columns: repeat(auto-fit,minmax(230px,1fr)); gap:22px; align-items:start; }
  .proj{
    background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02));
    border-radius:14px; padding:18px; border:1px solid rgba(0,200,255,0.04);
    transform-style:preserve-3d;
    transition: transform .45s cubic-bezier(.15,.9,.2,1), box-shadow .45s;
    box-shadow: 0 8px 40px rgba(3,6,12,0.55);
  }
  .proj:hover{ transform: translateY(-18px) rotateX(6deg) rotateY(-6deg) scale(1.02); box-shadow:0 28px 70px rgba(0,200,255,0.08); border-color: rgba(0,200,255,0.18); }
  .proj .title{ color:var(--neon-white); font-weight:700; margin-bottom:8px; }
  .proj .desc{ color:var(--ice-blue); font-size:0.95rem; margin-bottom:12px; }

  /* Contact */
  .contact-card{ display:flex; gap:22px; flex-wrap:wrap; align-items:flex-start; justify-content:space-between; }
  .contact-form{flex:1; min-width:260px; background:var(--card-bg); padding:18px; border-radius:12px; border:1px solid rgba(0,200,255,0.03)}
  .field{display:flex; flex-direction:column; gap:8px; margin-bottom:12px;}
  input, textarea{
    width:100%; padding:12px 14px; border-radius:8px; border:1px solid rgba(255,255,255,0.03);
    background: rgba(8,9,12,0.6); color:var(--neon-white); outline:none; box-shadow: 0 8px 30px rgba(0,0,0,0.6);
  }
  input:focus, textarea:focus{ box-shadow: 0 0 40px rgba(0,200,255,0.06); border-color: rgba(0,140,255,0.12); }
  .contact-meta{min-width:260px; max-width:360px; color:var(--ice-blue); background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02)); padding:18px; border-radius:12px; border:1px solid rgba(0,200,255,0.03); }

  /* FOOTER */
  footer{ padding:56px 20px; text-align:center; border-top:1px solid rgba(0,200,255,0.04); background: linear-gradient(90deg, rgba(4,5,10,0.8), rgba(4,5,10,0.95)); color:var(--ice-blue); }

  /* Responsive */
  @media (max-width:1000px){
    .hero-grid{grid-template-columns:1fr; text-align:center}
    .about-grid{grid-template-columns:1fr;}
    header{padding:12px 16px}
  }
  @media (max-width:640px){
    h1{font-size:2.2rem}
    .logo-bubble{width:40px;height:40px}
  }

  /* Particles layer (full-screen) */
  .particles-layer{
    position:fixed; inset:0; pointer-events:none; z-index:2; mix-blend-mode:screen;
  }
  .particle{
    position:absolute; width:8px; height:8px; border-radius:50%;
    background:var(--neon-blue); opacity:0.9;
    filter: drop-shadow(0 6px 26px rgba(0,200,255,0.18));
    will-change: transform, opacity;
  }

  /* Custom cursor (large glow) */
  .neon-cursor{
    position:fixed; width:22px; height:22px; border-radius:50%; z-index:9999; pointer-events:none;
    background: radial-gradient(circle at 30% 30%, var(--neon-white), var(--neon-blue));
    box-shadow:0 6px 26px rgba(0,200,255,0.22), 0 0 60px rgba(0,200,255,0.08);
    transform:translate(-50%,-50%) scale(1); transition: transform .08s linear;
    mix-blend-mode:screen;
  }
  .neon-cursor.big{ transform:translate(-50%,-50%) scale(2.6); opacity:0.85; box-shadow: 0 18px 80px rgba(0,200,255,0.18); }

  /* tiny helper for reveal animations */
  .reveal{opacity:0; transform: translateY(14px); transition:opacity .6s ease, transform .6s cubic-bezier(.2,.9,.3,1);}
  .reveal.show{opacity:1; transform: translateY(0)}
</style>
</head>
<body>

<!-- Particles (visual) -->
<div class="particles-layer" aria-hidden="true" id="particlesLayer"></div>

<!-- Custom neon cursor -->
<div class="neon-cursor" id="neonCursor" aria-hidden="true"></div>

<header>
  <div class="brand">
    <div class="logo-bubble">CG</div>
    <div>
      <div style="font-weight:800; color:var(--neon-white)">CLUTCH GOD</div>
      <div style="font-size:0.78rem; color:var(--ice-blue); margin-top:2px">Neon 3D Portfolio</div>
    </div>
  </div>

  <nav aria-label="Main navigation">
    <a href="#hero">Home</a>
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<main>
  <!-- HERO -->
  <section class="hero" id="hero">
    <div class="hero-grid wrap">
      <div class="hero-left">
        <div class="eyebrow reveal">NEXT-LEVEL • UI / 3D • PORTFOLIO</div>
        <h1 class="reveal">I build neon-lit 3D websites that stand out.</h1>
        <p class="lead reveal">Hi — I'm Clutch God. I design interactive, high-contrast neon portfolios and futuristic UI experiences with depth, motion and subtle 3D physics.</p>

        <div class="cta-row reveal" style="margin-top:18px">
          <button class="btn" id="btnExplore">View Work</button>
          <button class="ghost" id="btnContact">Let's talk</button>
        </div>
      </div>

      <div class="hero-right">
        <div class="preview-card" id="tiltCard" aria-hidden="true">
          <div class="preview-canvas" id="previewCanvas">
            <div class="shape s1"></div>
            <div class="shape s2"></div>
            <div class="shape s3"></div>
            <!-- center neon sphere -->
            <svg width="160" height="160" viewBox="0 0 160 160" style="z-index:2; mix-blend-mode:screen">
              <defs>
                <radialGradient id="g" cx="30%" cy="30%">
                  <stop offset="0%" stop-color="rgba(255,255,255,0.98)"/>
                  <stop offset="35%" stop-color="var(--neon-blue)"/>
                  <stop offset="100%" stop-color="rgba(0,140,255,0.03)"/>
                </radialGradient>
              </defs>
              <circle cx="80" cy="80" r="60" fill="url(#g)" style="filter:drop-shadow(0 18px 64px rgba(0,200,255,0.12))"/>
            </svg>
          </div>
          <div class="preview-info">
            <div style="font-size:0.95rem">Interactive 3D preview</div>
            <div style="color:var(--ice-blue); font-weight:700">Live • Neon</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about" aria-labelledby="aboutTitle">
    <div class="wrap about-grid">
      <div>
        <h2 id="aboutTitle" style="color:var(--neon-blue); margin-bottom:12px" class="reveal">About Me</h2>
        <div class="about-card reveal">
          <p style="color:var(--neon-white); margin-bottom:12px">I craft clean, high-contrast neon experiences. My focus is performance-friendly visuals, readable typography and subtle 3D depth that doesn't overpower content.</p>
          <ul style="color:var(--ice-blue); list-style:none; padding-left:0; display:grid; gap:8px">
            <li>• Frontend 3D (WebGL-lite/CSS) • Interactive UI</li>
            <li>• Neon design systems • Responsive layouts</li>
            <li>• Performance-aware animations</li>
          </ul>
        </div>
      </div>

      <aside class="about-avatar reveal" aria-hidden="true">
        <div style="text-align:center; padding:14px">
          <div style="font-size:1.1rem; color:var(--neon-blue); font-weight:700">Clutch God</div>
          <div style="color:var(--ice-blue); margin-top:6px">UI / Neon Designer</div>
        </div>
      </aside>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects" aria-labelledby="projectsTitle">
    <div class="wrap">
      <h2 id="projectsTitle" style="color:var(--neon-blue); margin-bottom:18px" class="reveal">Projects</h2>
      <div class="projects-grid reveal">
        <article class="proj" tabindex="0" aria-label="Project 1">
          <div class="title">Neon 3D Landing</div>
          <div class="desc">Interactive landing with floating elements and tilt interactions.</div>
          <div style="display:flex; gap:8px; margin-top:8px">
            <span style="font-size:0.9rem; color:var(--ice-blue)">HTML</span>
            <span style="font-size:0.9rem; color:var(--ice-blue)">CSS</span>
            <span style="font-size:0.9rem; color:var(--ice-blue)">JS</span>
          </div>
        </article>

        <article class="proj" tabindex="0" aria-label="Project 2">
          <div class="title">Portfolio Experience</div>
          <div class="desc">High-contrast portfolio UI with lightweight 3D accents and fast load.</div>
          <div style="display:flex; gap:8px; margin-top:8px">
            <span style="font-size:0.9rem; color:var(--ice-blue)">Design</span>
            <span style="font-size:0.9rem; color:var(--ice-blue)">Interaction</span>
          </div>
        </article>

        <article class="proj" tabindex="0" aria-label="Project 3">
          <div class="title">Micro-Interaction Kit</div>
          <div class="desc">Collection of neon micro-animations and accessible motion presets.</div>
          <div style="display:flex; gap:8px; margin-top:8px">
            <span style="font-size:0.9rem; color:var(--ice-blue)">Toolkit</span>
          </div>
        </article>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" aria-labelledby="contactTitle">
    <div class="wrap contact-card">
      <div class="contact-form reveal">
        <h2 style="color:var(--neon-blue); margin-bottom:12px" id="contactTitle">Let's build</h2>
        <form id="contactForm" onsubmit="return false" autocomplete="off" aria-label="Contact form">
          <div class="field">
            <label style="font-size:0.9rem; color:var(--ice-blue)">Name</label>
            <input id="name" type="text" placeholder="Your name" required>
          </div>
          <div class="field">
            <label style="font-size:0.9rem; color:var(--ice-blue)">Email</label>
            <input id="email" type="email" placeholder="you@domain.com" required>
          </div>
          <div class="field">
            <label style="font-size:0.9rem; color:var(--ice-blue)">Message</label>
            <textarea id="message" rows="5" placeholder="Tell me about the project"></textarea>
          </div>
          <div style="display:flex; gap:10px; align-items:center;">
            <button class="btn" id="sendBtn">Send Message</button>
            <div style="color:var(--ice-blue); font-size:0.9rem">Or email: <strong style="color:var(--neon-blue)">aryanaryankumar064@gmail.com</strong></div>
          </div>
        </form>
      </div>

      <aside class="contact-meta reveal" aria-hidden="true">
        <div style="margin-bottom:12px">Availability</div>
        <div style="font-weight:700; color:var(--neon-white); margin-bottom:10px">Open to freelance & collaboration</div>
        <div style="color:var(--ice-blue)">Based in: Online • Remote</div>
        <div style="margin-top:18px; color:var(--ice-blue)">Follow:</div>
        <div style="display:flex; gap:10px; margin-top:8px">
          <div style="width:36px;height:36px;border-radius:8px;background:rgba(255,255,255,0.02);display:flex;align-items:center;justify-content:center;color:var(--neon-blue)">G</div>
          <div style="width:36px;height:36px;border-radius:8px;background:rgba(255,255,255,0.02);display:flex;align-items:center;justify-content:center;color:var(--neon-blue)">T</div>
          <div style="width:36px;height:36px;border-radius:8px;background:rgba(255,255,255,0.02);display:flex;align-items:center;justify-content:center;color:var(--neon-blue)">I</div>
        </div>
      </aside>
    </div>
  </section>
</main>

<footer>
  <div class="wrap">
    © <strong style="color:var(--neon-white)">Clutch God</strong> — Neon Portfolio • Built with ❤️ and neon lights
  </div>
</footer>

<script>
/* ---------- Cursor ---------- */
const neonCursor = document.getElementById('neonCursor');
document.addEventListener('mousemove', (e) => {
  neonCursor.style.left = e.clientX + 'px';
  neonCursor.style.top = e.clientY + 'px';
});

/* enlarge cursor on interactive elements */
const interactive = document.querySelectorAll('button, a, .proj, input, textarea');
interactive.forEach(el=>{
  el.addEventListener('mouseenter', ()=> neonCursor.classList.add('big'));
  el.addEventListener('mouseleave', ()=> neonCursor.classList.remove('big'));
});

/* ---------- Particles (subtle) ---------- */
const particlesLayer = document.getElementById('particlesLayer');
const COUNT = Math.max(18, Math.floor(window.innerWidth/60));
const parts = [];

function rand(min,max){ return Math.random()*(max-min)+min; }

for(let i=0;i<COUNT;i++){
  const d = document.createElement('div');
  d.className='particle';
  const size = rand(4,12);
  d.style.width = size+'px';
  d.style.height = size+'px';
  d.style.left = rand(2,98)+'%';
  d.style.top = rand(2,98)+'%';
  d.style.opacity = rand(0.12,0.9);
  d.style.transform = `translate3d(0,0,0)`;
  particlesLayer.appendChild(d);
  parts.push({el:d, vx:rand(-0.02,0.02), vy:rand(-0.03,0.03), r:rand(-120,120)});
}

/* gentle motion loop */
let t0 = performance.now();
function particleStep(now){
  const dt = Math.min(40, now - t0) / 1000; t0 = now;
  parts.forEach(p=>{
    let x = parseFloat(p.el.style.left);
    let y = parseFloat(p.el.style.top);
    x += p.vx * (dt*60);
    y += p.vy * (dt*60);
    if(x<0) x=100; if(x>100) x=0;
    if(y<0) y=100; if(y>100) y=0;
    p.el.style.left = x + '%';
    p.el.style.top = y + '%';
    p.el.style.transform = `rotate(${p.r + (now*0.01)}deg)`;
  });
  requestAnimationFrame(particleStep);
}
requestAnimationFrame(particleStep);

/* ---------- Tilt 3D on preview card ---------- */
const tiltCard = document.getElementById('tiltCard');
const previewCanvas = document.getElementById('previewCanvas');
tiltCard.addEventListener('mousemove', (e) => {
  const rect = tiltCard.getBoundingClientRect();
  const cx = rect.left + rect.width/2;
  const cy = rect.top + rect.height/2;
  const dx = e.clientX - cx;
  const dy = e.clientY - cy;
  const rx = (-dy / rect.height) * 10;
  const ry = (dx / rect.width) * 10;
  tiltCard.style.transform = `rotateX(${rx}deg) rotateY(${ry}deg) translateZ(6px)`;
  tiltCard.style.boxShadow = `0 30px 80px rgba(0,140,255,0.08)`;
});
tiltCard.addEventListener('mouseleave', ()=> {
  tiltCard.style.transform = '';
  tiltCard.style.boxShadow = '';
});

/* ---------- Scroll reveal ---------- */
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){ e.target.classList.add('show'); io.unobserve(e.target); }
  });
},{threshold:0.12});
revealEls.forEach(el=> io.observe(el));

/* ---------- Projects keyboard focus accessible tilt ---------- */
document.querySelectorAll('.proj').forEach(card=>{
  card.addEventListener('focus', ()=> card.style.transform = 'translateY(-10px) rotateX(4deg) rotateY(-4deg)');
  card.addEventListener('blur', ()=> card.style.transform = '');
});

/* ---------- Simple contact feedback (no backend) ---------- */
const contactForm = document.getElementById('contactForm');
const sendBtn = document.getElementById('sendBtn');
sendBtn && sendBtn.addEventListener('click', ()=>{
  sendBtn.innerText = 'Sent ✓';
  sendBtn.disabled = true;
  setTimeout(()=>{ sendBtn.innerText = 'Send Message'; sendBtn.disabled = false; }, 2000);
});

/* ---------- small resize handler to adjust particle count on big resizes ---------- */
let resizeTimer;
window.addEventListener('resize', ()=>{
  clearTimeout(resizeTimer);
  resizeTimer = setTimeout(()=> {
    // optional: could re-calc particles, skip for performance
  }, 350);
});
</script>
</body>
</html>

