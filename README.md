<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>EaglerClientsForgex</title>
  <style>
    :root{
      --bg:#000;
      --panel:#071013;
      --accent:#22c55e;
      --muted:#9be39b;
      --muted-2:#94f6b0;
    }
    html,body{height:100%;margin:0;background:var(--bg);color:#fff;font-family:Inter,ui-sans-serif,system-ui,Arial,sans-serif}
    a{color:var(--accent);text-decoration:none}
    .min-h-screen{min-height:100vh}
    header{padding:1.2rem;border-bottom:1px solid rgba(255,255,255,0.03);display:flex;align-items:center;justify-content:space-between;gap:1rem}
    .title{font-weight:800;color:var(--accent);text-align:center;flex:1}
    .menu-btn{background:none;border:0;color:var(--accent);font-size:1.8rem;cursor:pointer}
    .layout{display:flex;min-height:calc(100vh - 64px)}
    /* sidebar */
    aside{width:18rem;background:transparent;padding:1rem;border-right:1px solid rgba(255,255,255,0.03);box-sizing:border-box}
    .side-link{display:block;padding:.65rem .8rem;border-radius:.6rem;color:#fff;margin-bottom:.5rem;background:transparent;cursor:pointer}
    .side-link:hover{background:rgba(255,255,255,0.02)}
    /* mobile slide */
    .side-wrap{position:fixed;left:0;top:0;bottom:0;width:18rem;transform:translateX(-110%);background:var(--bg);z-index:60;transition:transform .28s ease;box-shadow: 8px 0 30px rgba(0,0,0,0.6)}
    .side-wrap.open{transform:translateX(0)}
    main{flex:1;padding:1.2rem;box-sizing:border-box}
    .grid{display:grid;gap:1rem}
    .grid.cols-3{grid-template-columns:repeat(3,1fr)}
    .card{border:1px solid rgba(34,197,94,0.18);padding:1.2rem;border-radius:.6rem;text-align:center;min-height:5rem;display:flex;align-items:center;justify-content:center;background:rgba(255,255,255,0.01)}
    .card:hover{transform:scale(1.03);box-shadow:0 8px 30px rgba(34,197,94,0.06);transition:all .18s ease}
    h2{color:var(--accent);margin:0 0 1rem 0}
    /* loading */
    #loadingScreen{position:fixed;inset:0;display:flex;align-items:center;justify-content:center;flex-direction:column;background:var(--bg);z-index:1000}
    .mono{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, monospace}
    /* overlay terminal */
    .overlay{position:fixed;inset:0;background:rgba(0,0,0,0.6);backdrop-filter:blur(2px);display:flex;align-items:center;justify-content:center;z-index:120;opacity:0;pointer-events:none;transition:opacity .18s ease}
    .overlay.show{opacity:1;pointer-events:auto}
    .terminal{background:var(--panel);border:1px solid rgba(34,197,94,0.12);padding:1rem;border-radius:.5rem;min-width:300px;max-width:720px;color:var(--muted-2)}
    .term-line{opacity:0;margin:6px 0}
    .term-line.show{opacity:1;transition:opacity .25s ease}
    .term-actions{margin-top:.8rem;display:flex;gap:.5rem;align-items:center}
    .btn{background:transparent;border:1px solid rgba(255,255,255,0.06);padding:.5rem .7rem;border-radius:.4rem;color:#fff;cursor:pointer}
    .btn.positive{background:var(--accent);border-color:transparent;color:#000}
    /* header small button */
    .btn-small{padding:.35rem .5rem;font-size:.9rem}
    /* responsive */
    @media (max-width:768px){aside{display:none}.side-wrap{display:block}}
  </style>
</head>
<body class="min-h-screen">

  <!-- Audio -->
  <audio id="menuSound" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_bf6a58e3b0.mp3?filename=interface-124464.mp3"></audio>
  <audio id="confirmSound" src="https://cdn.pixabay.com/download/audio/2021/08/04/audio_2a1b2c8a5a.mp3?filename=beep-03.mp3"></audio>

  <!-- Loading Screen -->
  <div id="loadingScreen" aria-hidden="false">
    <p id="loader" class="mono" style="color:var(--accent);font-size:28px;margin:0">LOADING...</p>
    <p class="mono" style="color:rgba(155,227,155,0.8);margin-top:12px">Initializing terminal_</p>
  </div>

  <header role="banner">
    <button id="menuToggle" class="menu-btn" aria-label="Abrir menú">☰</button>
    <div class="title" role="heading" aria-level="1">HOME FORGEX</div>
    <div style="width:36px"></div>
  </header>

  <div class="layout">
    <!-- Sidebar for desktop -->
    <aside aria-hidden="false" style="display:block">
      <nav aria-label="Navegación">
        <a class="side-link" href="#tops">🔥 TOPS</a>
        <a class="side-link" href="#links">🏠 Home</a>
        <a class="side-link" href="#info">ℹ️ INFO</a>
      </nav>
    </aside>

    <!-- mobile sliding menu -->
    <div id="sideWrap" class="side-wrap" aria-hidden="true">
      <nav style="padding:1rem">
        <button id="closeMenu" class="btn" style="margin-bottom:.6rem">Cerrar</button>
        <div style="margin-top:.6rem">
          <a class="side-link" href="#tops">🔥 TOPS</a>
          <a class="side-link" href="#links">🏠 Home</a>
          <a class="side-link" href="#info">ℹ️ INFO</a>
        </div>
      </nav>
    </div>

    <main>
      <section id="tops" style="text-align:center;margin-bottom:36px">
        <h2>TOP 3</h2>
        <div class="grid cols-3" id="topGrid" style="max-width:960px;margin:0 auto">
          <a class="card" href="https://eaglerhacks.github.io/UwUClient%20v1%20Full.html" target="_blank" rel="noopener">UwUClient</a>
          <a class="card" href="https://eaglerhacks.github.io/dragonv4.html" target="_blank" rel="noopener">DragonX Client</a>
          <a class="card" href="https://eaglerhacks.github.io/wurstX.html" target="_blank" rel="noopener">WurstX Client</a>
        </div>
      </section>

      <section id="links" style="text-align:center;margin-bottom:36px">
        <h2>TODOS LOS LINKS</h2>
        <div class="grid" style="max-width:1100px;margin:0 auto;grid-template-columns:repeat(auto-fit,minmax(220px,1fr))">
          <a class="card" href="https://eaglerhacks.github.io/Shadow_Client_2.5_1.8.8_International.html" target="_blank" rel="noopener">Shadow Client</a>
          <a class="card" href="https://eaglerhacks.github.io/justinv3.html" target="_blank" rel="noopener">Justin Client V3</a>
          <a class="card" href="https://eaglerhacks.github.io/moonlight.html" target="_blank" rel="noopener">MoonLight Client</a>
          <a class="card" href="https://eaglerhacks.github.io/PiClient.html" target="_blank" rel="noopener">PiClient</a>
          <a class="card" href="https://eaglerhacks.github.io/meteor.html" target="_blank" rel="noopener">Meteor Client</a>
          <a class="card" href="https://eaglerhacks.github.io/demon.html" target="_blank" rel="noopener">Demon Client</a>
          <a class="card" href="https://eaglerhacks.github.io/justinclient.html" target="_blank" rel="noopener">Justin Client V1.2.4</a>
          <a class="card" href="https://eaglerhacks.github.io/Koneclient-1.8.8-offlineDownload.html" target="_blank" rel="noopener">Koneclient 1.8.8 Offline</a>
          <a class="card" href="https://eaglerhacks.github.io/flameclient%203.7.html" target="_blank" rel="noopener">FlameClient 3.7</a>
          <a class="card" href="https://eaglerhacks.github.io/daniel.html" target="_blank" rel="noopener">Daniel Client V1</a>
        </div>
      </section>

      <section id="info" style="max-width:760px;margin:0 auto">
        <h2>Información que debes tener en cuenta ⚠️</h2>
        <p>Este contenido es únicamente educativo. No promovemos el uso de hacks en servidores públicos.</p>

        <h3>¿Qué es un client modificado? 🤖</h3>
        <p>Un hacked client añade funciones como fly, kill aura, x-ray, entre otros.</p>

        <h3>¿Para qué sirven? 🛠️</h3>
        <ul>
          <li>Aprender programación</li>
          <li>Experimentar funciones</li>
          <li>Probar mecánicas en mundos privados</li>
        </ul>

        <h3>Riesgos 🚫</h3>
        <ul>
          <li>Baneos permanentes</li>
          <li>Bloqueo por IP</li>
          <li>Virus y malware</li>
          <li>Pérdida de progreso</li>
        </ul>

        <h3 style="color:var(--accent)">DISFRÚTALO 😎🔥</h3>
        <p>No olvides compartir esta página con más usuarios. Tu cuenta puede estar en riesgo si usas hacks en servidores públicos.</p>
      </section>
    </main>
  </div>

  <!-- Terminal modal -->
  <div id="termOverlay" class="overlay" aria-hidden="true">
    <div class="terminal" role="dialog" aria-modal="true" aria-labelledby="terminalTitle">
      <div id="termLines">
        <div class="term-line">&gt; Verificando archivos...</div>
        <div class="term-line">&gt; Escaneando integridad...</div>
        <div class="term-line">&gt; Descarga autorizada.</div>
      </div>

      <div id="termResult" style="display:none;margin-top:.8rem">
        <p style="margin:0 0 .6rem 0">Tu enlace de descarga:</p>
        <div style="display:flex;gap:.6rem">
          <a id="finalLink" class="btn btn-link" href="#" target="_blank" rel="noopener" style="background:var(--accent);color:#000;padding:.5rem .8rem;border-radius:.4rem;text-decoration:none">Abrir enlace</a>
          <button id="setLink" class="btn">Configurar enlace</button>
        </div>
      </div>

      <div style="margin-top:.7rem;color:rgba(255,255,255,0.6);font-size:.9rem">Presiona ESC o clic fuera para cerrar.</div>
    </div>
  </div>

<script>
// Static JS to reproduce React behavior

// Loading removal
window.addEventListener('load', () => {
  setTimeout(()=>{
    const ls = document.getElementById('loadingScreen');
    if (ls) ls.style.display = 'none';
  }, 900);
});

// menu toggle (mobile)
const menuToggle = document.getElementById('menuToggle');
const sideWrap = document.getElementById('sideWrap');
const closeMenu = document.getElementById('closeMenu');
const menuSound = document.getElementById('menuSound');
menuToggle.addEventListener('click', ()=> {
  sideWrap.classList.add('open');
  sideWrap.setAttribute('aria-hidden','false');
  try { menuSound.currentTime=0; menuSound.play(); } catch(e) {}
});
closeMenu.addEventListener('click', ()=> {
  sideWrap.classList.remove('open');
  sideWrap.setAttribute('aria-hidden','true');
});

// Terminal modal flow
const overlay = document.getElementById('termOverlay');
const termLines = document.querySelectorAll('.term-line');
const termResult = document.getElementById('termResult');
const finalLink = document.getElementById('finalLink');
const setLink = document.getElementById('setLink');
const confirmSound = document.getElementById('confirmSound');

// small button in header to open terminal
const header = document.querySelector('header');
const openBtn = document.createElement('button');
openBtn.textContent = 'Abrir terminal';
openBtn.className = 'btn btn-small';
openBtn.style.marginLeft = '12px';
openBtn.addEventListener('click', openTerminal);
header.appendChild(openBtn);

function getStoredURL(){ return localStorage.getItem('forgex_download_url') || ''; }
function setStoredURL(u){ localStorage.setItem('forgex_download_url', u); }

function openTerminal(){
  overlay.classList.add('show');
  overlay.setAttribute('aria-hidden','false');
  termResult.style.display = 'none';
  termLines.forEach((ln)=> ln.classList.remove('show'));
  termLines.forEach((ln, i)=> setTimeout(()=> ln.classList.add('show'), 600*(i+1)));
  setTimeout(()=>{
    const stored = getStoredURL();
    if (stored){
      finalLink.href = stored;
      finalLink.textContent = 'Abrir enlace (tu sitio)';
    } else {
      finalLink.href = '#';
      finalLink.textContent = 'Enlace no configurado';
    }
    termResult.style.display = 'block';
    try { confirmSound.currentTime = 0; confirmSound.play(); } catch(e) {}
  }, 600*(termLines.length+1));
}

// close on outside click or ESC
overlay.addEventListener('click', (e)=> { if (e.target === overlay) closeTerminal(); });
document.addEventListener('keydown', (e)=> { if (e.key === 'Escape') closeTerminal(); });
function closeTerminal(){ overlay.classList.remove('show'); overlay.setAttribute('aria-hidden','true'); }

setLink.addEventListener('click', ()=>{
  const current = getStoredURL() || 'https://';
  const url = prompt('Pega aquí la URL de descarga (tu página):', current);
  if (url){
    setStoredURL(url);
    finalLink.href = url;
    finalLink.textContent = 'Abrir enlace (tu sitio)';
    alert('Enlace guardado localmente en este navegador.');
  }
});

// final link click behaviour
finalLink.addEventListener('click', (e)=>{
  const stored = getStoredURL();
  if (!stored){ e.preventDefault(); if (confirm('No hay enlace configurado. ¿Quieres configurarlo ahora?')) setLink.click(); }
});
</script>
</body>
</html>
