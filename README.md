# gry
gry poprostu
[index.html](https://github.com/user-attachments/files/22408814/index.html)

<!doctype html>
<html lang="pl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Borcix NML Game — PC & Mobile</title>
<meta name="description" content="Borcix NML Game — lista gier: Clicker (PC), demo 18+ i kółko-krzyżyk z AI. Wpisz frazę 'borcix nml game' i zagraj." />
<meta name="keywords" content="borcix,nml,game,borcix nml game,clicker,gra pc,gra mobilna,kółko i krzyżyk AI" />
<meta name="theme-color" content="#0b3d91" />
<style>
  :root{
    --bg1:#0f172a; --bg2:#0b3d91;
    --glass: rgba(255,255,255,.08);
    --glass2: rgba(255,255,255,.12);
    --txt:#e5edff; --muted:rgba(229,237,255,.78);
    --acc1:#38bdf8; --acc2:#60a5fa; --acc3:#a78bfa;
  }
  *{box-sizing:border-box}
  html,body{height:100%;margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,Arial;color:var(--txt);background:radial-gradient(1200px 600px at 10% -10%,#1e293b 0%,transparent 60%), linear-gradient(135deg,var(--bg1),var(--bg2));overflow-x:hidden}
  .wrap{max-width:1120px;margin:0 auto;padding:28px 18px 48px}
  /* particles canvas behind */
  #fx{position:fixed;inset:0;z-index:-1}
  header{display:flex;align-items:center;justify-content:space-between;margin-bottom:18px}
  .brand{display:flex;gap:12px;align-items:center}
  .logo{width:52px;height:52px;border-radius:14px;display:grid;place-items:center;font-weight:900;color:#06263c;background:linear-gradient(135deg,#06b6d4,#3b82f6,#a78bfa);box-shadow:0 10px 30px rgba(0,0,0,.45)}
  h1{margin:0;font-size:24px;letter-spacing:.2px}
  .type{white-space:nowrap;overflow:hidden;border-right:3px solid rgba(255,255,255,.7);width:0ch}
  .sub{color:var(--muted);font-size:13px}
  /* search */
  .search{margin-top:10px;background:var(--glass);backdrop-filter:blur(8px);border-radius:14px;padding:14px;display:flex;gap:10px;align-items:center;box-shadow:0 10px 34px rgba(0,0,0,.45)}
  .search input{flex:1;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);color:var(--txt);padding:12px 14px;border-radius:10px;outline:none}
  .btn{border:0;border-radius:10px;padding:10px 14px;font-weight:800;cursor:pointer;color:#0b2240;background:linear-gradient(90deg,var(--acc1),var(--acc2));box-shadow:0 6px 18px rgba(56,189,248,.25);transition:transform .15s ease}
  .btn:hover{transform:translateY(-1px)}
  .hint{font-size:12px;color:var(--muted);margin-top:6px}
  /* grid */
  .results{display:none;margin-top:20px;gap:16px;grid-template-columns:repeat(12,1fr)}
  .card{grid-column:span 4;background:var(--glass);border:1px solid rgba(255,255,255,.08);border-radius:16px;padding:16px;box-shadow:0 14px 34px rgba(0,0,0,.45);position:relative;transform:translateY(14px);opacity:0;transition:all .45s cubic-bezier(.2,.6,.2,1)}
  .card.show{opacity:1;transform:none}
  @media (max-width:980px){.card{grid-column:span 12}}
  .cardHeader{display:flex;align-items:center;justify-content:space-between}
  .pill{font-size:12px;padding:6px 10px;border-radius:999px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.12)}
  .title{font-size:18px;font-weight:900}
  .desc{color:var(--muted);font-size:13px;margin:6px 0 10px}
  .play{display:flex;gap:8px;align-items:center}
  .btnGhost{background:transparent;color:var(--txt);border:1px solid rgba(255,255,255,.14)}
  .float{animation:float 6s ease-in-out infinite;transform-style:preserve-3d}
  @keyframes float{0%{transform:translateY(0) rotateX(0)}50%{transform:translateY(-8px) rotateX(6deg)}100%{transform:translateY(0) rotateX(0)}}
  /* tilt hover */
  .card:hover{transform:translateY(-2px) scale(1.01)}
  /* modal */
  .modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,.6);padding:18px}
  .modal.active{display:flex}
  .win{max-width:880px;width:100%;background:#0b1224;border:1px solid rgba(255,255,255,.12);border-radius:18px;box-shadow:0 34px 80px rgba(0,0,0,.6);transform:scale(.9);opacity:0;transition:all .25s ease}
  .win.show{transform:scale(1);opacity:1}
  .winHead{display:flex;justify-content:space-between;align-items:center;padding:14px 16px;border-bottom:1px solid rgba(255,255,255,.08)}
  .close{background:transparent;border:1px solid rgba(255,255,255,.18);color:var(--txt);padding:8px 10px;border-radius:10px;cursor:pointer}
  .winBody{padding:16px;display:grid;gap:14px;grid-template-columns:2fr 1fr}
  @media (max-width:900px){.winBody{grid-template-columns:1fr}}
  .stage{background:#fff;border-radius:12px;min-height:320px;display:grid;place-items:center;color:#123}
  .downloads{background:var(--glass2);border-radius:12px;padding:12px}
  small.note{color:var(--muted)}
  /* ttt */
  .board{display:grid;grid-template-columns:repeat(3,94px);grid-template-rows:repeat(3,94px);gap:10px}
  .cell{width:94px;height:94px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,.06),rgba(255,255,255,.02));display:grid;place-items:center;font-size:42px;user-select:none;cursor:pointer;box-shadow:inset 0 -10px 24px rgba(0,0,0,.25)}
  .ctrls{display:flex;gap:8px;margin-top:8px}
  .status{font-size:13px;color:var(--muted)}
  footer{margin-top:26px;text-align:center;color:var(--muted);font-size:12px}
</style>
</head>
<body>
<canvas id="fx"></canvas>

<div class="wrap">
  <header>
    <div class="brand">
      <div class="logo">B</div>
      <div>
        <h1 class="type" id="type">Borcix NML Game — wyszukaj i graj</h1>
        <div class="sub">Wpisz dokładnie: <b>borcix nml game</b> — pokażę listę gier.</div>
      </div>
    </div>
  </header>

  <div class="search">
    <input id="q" placeholder='np. "borcix nml game"' />
    <button id="go" class="btn">Szukaj</button>
  </div>
  <div class="hint">Pro tip: dodaj tę stronę do ulubionych – adres będzie łatwy do zapamiętania.</div>

  <!-- GRID OF GAMES -->
  <div id="results" class="results" style="grid-template-columns:repeat(12,1fr)">
    <!-- Card 1 -->
    <div class="card float" id="c1">
      <div class="cardHeader">
        <div class="title">Gra #1 — Clicker (PC)</div>
        <span class="pill">PC</span>
      </div>
      <div class="desc">Turbo klikacz na Windows. Wersja offline w pliku EXE.</div>
      <div class="play">
        <button class="btn" data-open="pc">Pokaż szczegóły</button>
        <button class="btn btnGhost" id="dlBtn">Pobierz EXE</button>
      </div>
    </div>

    <!-- Card 2 -->
    <div class="card float" id="c2" style="animation-delay:.2s">
      <div class="cardHeader">
        <div class="title">Gra #2 — Demo 18+</div>
        <span class="pill">DEMO</span>
      </div>
      <div class="desc">Styl „hazard” wyłącznie jako pokaz. <b>Bez prawdziwych stawek.</b> Wymaga potwierdzenia 18+.</div>
      <div class="play">
        <button class="btn" data-open="hz">Zobacz demo</button>
        <button class="btn btnGhost" id="hzInfo">Info</button>
      </div>
    </div>

    <!-- Card 3 -->
    <div class="card float" id="c3" style="animation-delay:.4s">
      <div class="cardHeader">
        <div class="title">Gra #3 — Kółko-krzyżyk z AI</div>
        <span class="pill">WEB</span>
      </div>
      <div class="desc">Zagraj przeciw perfekcyjnej AI (minimax). Działa na PC i telefonie.</div>
      <div class="play">
        <button class="btn" data-open="ttt">Graj teraz</button>
        <button class="btn btnGhost" id="tttReset">Nowa gra</button>
      </div>
    </div>
  </div>

  <footer>© <span id="y"></span> Borcix — demo strony gier. Wersja HTML/JS bez zewnętrznych bibliotek.</footer>
</div>

<!-- MODAL -->
<div id="modal" class="modal" aria-hidden="true">
  <div class="win" id="win">
    <div class="winHead">
      <div id="winTitle" style="font-weight:900">Szczegóły</div>
      <button class="close" id="close">Zamknij</button>
    </div>
    <div class="winBody" id="winBody">
      <!-- dynamic -->
    </div>
  </div>
</div>

<script>
/* ----------------- particles background ----------------- */
const cv = document.getElementById('fx'), cx = cv.getContext('2d');
let W,H,pts=[];
function resize(){W=cv.width=innerWidth;H=cv.height=innerHeight;pts = Array.from({length:100},()=>({x:Math.random()*W,y:Math.random()*H,vx:(Math.random()-.5)*.6,vy:(Math.random()-.5)*.6}))}
addEventListener('resize',resize); resize();
(function loop(){
  cx.clearRect(0,0,W,H);
  for(const p of pts){ p.x+=p.vx; p.y+=p.vy; if(p.x<0||p.x>W)p.vx*=-1; if(p.y<0||p.y>H)p.vy*=-1;
    cx.fillStyle='rgba(96,165,250,.8)'; cx.beginPath(); cx.arc(p.x,p.y,1.5,0,Math.PI*2); cx.fill();
  }
  requestAnimationFrame(loop);
})();

/* ----------------- typewriter ----------------- */
const t = document.getElementById('type');
(function type() {
  const full = t.textContent;
  t.textContent=''; t.style.width = full.length+'ch';
  let i=0; const iv = setInterval(()=>{ t.textContent += full[i++]; if(i>=full.length) clearInterval(iv); }, 28);
})();

/* ----------------- search/show ----------------- */
const q = document.getElementById('q'), go = document.getElementById('go'), res = document.getElementById('results');
const cards = [...document.querySelectorAll('.card')];
function showResultsIfMatch(val){
  const v = (val||'').toLowerCase().trim();
  const ok = v === 'borcix nml game' || (v.includes('borcix') && v.includes('nml'));
  res.style.display = ok ? 'grid' : 'none';
  if(ok){ setTimeout(()=> cards.forEach((c,i)=> c.classList.add('show')),20); }
}
go.onclick = ()=> showResultsIfMatch(q.value);
q.addEventListener('keydown',e=>{ if(e.key==='Enter') showResultsIfMatch(q.value); });

/* ----------------- modal logic ----------------- */
const modal = document.getElementById('modal'), win = document.getElementById('win'), winBody = document.getElementById('winBody'), winTitle = document.getElementById('winTitle');
document.getElementById('close').onclick = ()=> hideModal();
modal.addEventListener('click', e=>{ if(e.target===modal) hideModal() });
function showModal(title, inner){
  winTitle.textContent = title;
  winBody.innerHTML = inner;
  modal.classList.add('active'); setTimeout(()=> win.classList.add('show'),10);
}
function hideModal(){ win.classList.remove('show'); setTimeout(()=> modal.classList.remove('active'),180); }

/* ----------------- Card buttons ----------------- */
document.querySelector('[data-open="pc"]').onclick = ()=>{
  const DL = 'REPLACE_WITH_YOUR_EXE_LINK'; // <<< PODMIEŃ na prawdziwy link do EXE (patrz instrukcja pod kodem)
  showModal('Clicker (PC) — pobieranie', `
    <div class="stage">
      <div style="text-align:center;padding:10px">
        <div style="font-weight:900;color:#0b3d91">Clicker — wersja Windows (.exe)</div>
        <p style="color:#234;margin-top:6px">Zapisz plik i uruchom. Jeśli Windows ostrzeże, wybierz „Uruchom mimo to” (bo to plik niepodpisany).</p>
        <a href="${DL}" class="btn" style="text-decoration:none;display:inline-block;margin-top:8px">Pobierz EXE</a>
      </div>
    </div>
    <div class="downloads">
      <b>Szybkie wskazówki:</b>
      <ul style="margin:8px 0 0 18px;line-height:1.6">
        <li>Najlepiej hostować EXE w <i>GitHub Releases</i> — szybki i bezpieczny link.</li>
        <li>Możesz też dodać ZIP z plikiem i README.</li>
      </ul>
    </div>
  `);
};
document.getElementById('dlBtn').onclick = ()=> document.querySelector('[data-open="pc"]').click();

document.querySelector('[data-open="hz"]').onclick = ()=>{
  showModal('Demo 18+ (tylko pokaz, bez stawek)', `
    <div class="stage" id="hzStage">
      <div style="text-align:center">
        <div style="font-weight:900;color:#0b3d91;margin-bottom:6px">Tryb pokazowy 18+</div>
        <p style="color:#234;max-width:460px">To jest demo animacji — <b>bez prawdziwych pieniędzy i stawek</b>. Nie umożliwia hazardu. Kliknij "Start demo" żeby zobaczyć animacje.</p>
        <button class="btn" id="hzStart">Start demo</button>
      </div>
    </div>
    <div class="downloads"><small class="note">Uwaga: jesteś niepełnoletni — dlatego zostawiamy to wyłącznie jako animację pokazową, bez funkcji hazardowych.</small></div>
  `);
  setTimeout(()=> {
    const st = document.getElementById('hzStage');
    const btn = document.getElementById('hzStart');
    btn.onclick = ()=>{
      // prosta animacja "slotów" (pokaz)
      st.innerHTML = '<div style="display:grid;gap:10px;text-align:center"><div style="font-weight:900;color:#0b3d91">Demo animacji</div><div id="slots" style="font-size:42px;color:#123;background:#fff;border-radius:12px;padding:10px">⏳ ⏳ ⏳</div><button class="btn" id="hzAgain">Jeszcze raz</button></div>';
      const slots = document.getElementById('slots');
      const symbols = ['🍀','⭐','💎','🍒','7️⃣'];
      let t=0; const iv = setInterval(()=>{
        t++; slots.textContent = symbols[Math.floor(Math.random()*symbols.length)]+' '+symbols[Math.floor(Math.random()*symbols.length)]+' '+symbols[Math.floor(Math.random()*symbols.length)];
        if(t>18){ clearInterval(iv); }
      },80);
      document.getElementById('hzAgain').onclick = ()=> btn.click();
    };
  },50);
};
document.getElementById('hzInfo').onclick = ()=> document.querySelector('[data-open="hz"]').click();

/* ------------- TicTacToe in modal ------------- */
document.querySelector('[data-open="ttt"]').onclick = openTTT;
document.getElementById('tttReset').onclick = openTTT;
function openTTT(){
  showModal('Kółko-krzyżyk z AI', `
    <div class="stage" style="background:linear-gradient(180deg,#f8fbff,#eef4ff);">
      <div>
        <div id="status" class="status" style="color:#123;text-align:center;margin-bottom:8px">Twoja kolej — grasz X</div>
        <div id="board" class="board" role="grid" aria-label="Plansza kółko krzyżyk">
          ${Array.from({length:9}).map((_,i)=>`<div class="cell" data-i="${i}"></div>`).join('')}
        </div>
        <div class="ctrls" style="justify-content:center;margin-top:10px">
          <button class="btn" id="new">Nowa gra</button>
          <button class="btn btnGhost" id="ai">AI: Perfekcyjne</button>
          <button class="btn btnGhost" id="mark">Ty: X</button>
        </div>
      </div>
    </div>
    <div class="downloads"><small class="note">Algorytm AI: minimax (gra optymalnie). Działa na telefonie i PC.</small></div>
  `);
  setTimeout(initTTT,30);
}
function initTTT(){
  const cells = [...document.querySelectorAll('.cell')];
  const status = document.getElementById('status');
  const newBtn = document.getElementById('new');
  const aiBtn = document.getElementById('ai');
  const markBtn = document.getElementById('mark');
  let board = Array(9).fill(null), human='X', ai='O', aiOn=true, over=false;
  const wins=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
  const winOf=b=>{for(const w of wins){const[a,b1,c]=w;if(b[a]&&b[a]===b[b1]&&b[a]===b[c])return b[a]}return b.every(v=>v!==null)?'draw':null};
  const render=()=>{cells.forEach((c,i)=>c.textContent=board[i]||'');const w=winOf(board);if(w==='draw')status.textContent='Remis 🤝';else if(w)status.textContent=(w===human?'Wygrałeś ✅':'AI wygrała 💻');else status.textContent=`Twoja kolej — grasz ${human}`;}
  const best=(bd,me)=>{
    if(bd.filter(x=>x!==null).length===0) return 4;
    let best=-1e9, mv=null;
    bd.forEach((v,i)=>{ if(v!==null) return; const cp=bd.slice(); cp[i]=me; const s=mini(cp,0,false,me); if(s>best){best=s; mv=i;} });
    return mv;
  }
  const mini=(bd,d,max,me)=>{
    const other=me==='X'?'O':'X', w=winOf(bd);
    if(w===me) return 10-d; if(w===other) return d-10; if(w==='draw') return 0;
    const avail=bd.map((v,i)=>v===null?i:null).filter(v=>v!==null);
    if(max){ let m=-1e9; for(const i of avail){const cp=bd.slice(); cp[i]=me; m=Math.max(m,mini(cp,d+1,false,me))} return m;}
    else { let m=1e9; for(const i of avail){const cp=bd.slice(); cp[i]=other; m=Math.min(m,mini(cp,d+1,true,me))} return m;}
  }
  function humanMove(i){ if(over||board[i])return; board[i]=human; step(); }
  function step(){ const w=winOf(board); if(w){over=true; render(); return;} if(aiOn){ setTimeout(()=>{ const m=best(board,ai); if(m!==null) board[m]=ai; const w2=winOf(board); if(w2) over=true; render(); },200);} else render(); }
  cells.forEach(c=>c.onclick=()=>humanMove(+c.dataset.i));
  newBtn.onclick=()=>{board=Array(9).fill(null); over=false; render(); if(aiOn&&human==='O'){ const m=best(board,ai); if(m!==null) board[m]=ai; render();}};
  aiBtn.onclick=()=>{aiOn=!aiOn; aiBtn.textContent=aiOn?'AI: Perfekcyjne':'AI: Wyłączona'; aiBtn.classList.toggle('btnGhost',!aiOn);}
  markBtn.onclick=()=>{if(human==='X'){human='O'; ai='X'; markBtn.textContent='Ty: O'} else {human='X'; ai='O'; markBtn.textContent='Ty: X'}; newBtn.click();}
  render();
}

/* year */
document.getElementById('y').textContent = new Date().getFullYear();

/* show results if ?q=... has borcix */
const params = new URLSearchParams(location.search);
if((params.get('q')||'').toLowerCase().includes('borcix')){ q.value='borcix nml game'; res.style.display='grid'; setTimeout(()=>[...document.querySelectorAll('.card')].forEach(c=>c.classList.add('show')),20); }

/* ----------------- helper: EXE link ----------------- */
document.getElementById('dlBtn').title = 'Podmień link w kodzie na własny (GitHub Releases)';

/* accessibility small */
document.addEventListener('keydown',e=>{ if(e.key==='Escape') hideModal(); });

</script>
</body>
</html>
