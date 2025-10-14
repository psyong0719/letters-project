# letters-project
<!doctype html>
<html lang="ko">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Wizard Typing — spells, numbers, hold, broom, footprints, wand beam, ripple</title>
<style>
  :root{ --bg:#060a10; --panel:#0d141d; --ink:#e9edf4; }
  *{box-sizing:border-box}
  html,body{height:100%;margin:0}
  body{
    background:
      radial-gradient(1400px 900px at 70% -10%, #152335, transparent 60%),
      radial-gradient(1200px 800px at -10% 110%, #0a111a, transparent 70%),
      var(--bg);
    color:var(--ink);
    font-family: ui-serif, Georgia, "Times New Roman", serif;
    overflow:hidden;
  }
  .frame{display:grid; grid-template-rows:auto 1fr; height:100%}
  header{display:flex; align-items:center; gap:14px; padding:10px 16px; border-bottom:1px solid #182433; background:linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,0))}
  h1{margin:0; font-size:18px; letter-spacing:.04em; color:#e8f6ff; text-shadow:0 0 14px rgba(241,208,138,.45)}
  .hint{margin:0; font-size:12px; color:#b8c7da; white-space:nowrap; opacity:.95}
  .spacer{flex:1}
  .btn{appearance:none; border:1px solid #253246; background:#0f1725; color:#d5e7fb; padding:8px 12px; border-radius:10px; font-size:12px; cursor:pointer}
  .btn:hover{border-color:#37506f}

  main{position:relative}
  .pad{
    position:relative; margin:16px; height:calc(100vh - 96px); min-height:330px;
    border:1px solid #1a2736; border-radius:16px; padding:24px 26px; overflow:auto;
    background:
      radial-gradient(600px 260px at 70% 0%, rgba(255,255,255,.04), rgba(255,255,255,0)),
      linear-gradient(180deg, rgba(255,255,255,.02), rgba(255,255,255,0)),
      var(--panel);
    box-shadow: 0 30px 120px rgba(0,0,0,.55), inset 0 0 80px rgba(0,0,0,.32);
    outline:none;
  }
  .line{font-size:28px; line-height:1.58; word-wrap:break-word}
  .ch{display:inline-block; white-space:pre; transition: transform .10s linear, margin-right .14s ease, opacity .18s ease, filter .2s ease, color .2s ease; position:relative; vertical-align:baseline; user-select:none}
  .caret{display:inline-block; width:2px; height:1.2em; background:#bcd7f0; margin-left:2px; animation:blink 1s steps(1) infinite; vertical-align:text-bottom}
  @keyframes blink{50%{opacity:0}}

  .particle{position:absolute; width:6px; height:6px; border-radius:50%; pointer-events:none}
  .ring{position:absolute; border-radius:50%; border:3px solid; pointer-events:none; mix-blend-mode:screen; opacity:.9}
  .beam{position:absolute; height:2px; background:linear-gradient(90deg, rgba(255,255,255,.0), rgba(255,255,255,.95), rgba(255,255,255,.0)); box-shadow:0 0 18px rgba(255,255,255,.6); pointer-events:none; transform-origin:left center}

  .lumos{filter:brightness(4.2) saturate(1.6)}
  .nox{filter:brightness(.08) saturate(.7)}
  .float-strong .ch{animation:floatStrong 2.0s ease-in-out infinite}
  @keyframes floatStrong{0%{transform:translateY(0) rotate(0deg)}50%{transform:translateY(-46px) rotate(2deg)}100%{transform:translateY(0) rotate(0deg)}}
  .shake{animation:shake .1s linear infinite}
  @keyframes shake{0%{transform:translate(0,0)}25%{transform:translate(2px,-2px)}50%{transform:translate(-2px,1px)}75%{transform:translate(1px,2px)}100%{transform:translate(0,0)}}

  .flash{position:absolute; inset:0; pointer-events:none; background:rgba(255,255,255,.95); animation:flash .25s ease-out forwards}
  @keyframes flash{to{opacity:0}}
  .greenflash{position:absolute; inset:0; pointer-events:none; background:radial-gradient(circle at 50% 50%, rgba(0,255,150,.98), rgba(0,0,0,0) 60%); animation:flashg .55s ease-out forwards}
  @keyframes flashg{to{opacity:0}}
  .veil{position:absolute; inset:0; pointer-events:none; background:radial-gradient(circle at 50% 50%, rgba(200,245,255,.45), rgba(0,0,0,0) 70%); mix-blend-mode:screen; animation:veil .9s ease-out forwards}
  @keyframes veil{to{opacity:0}}

  .entities{position:absolute; inset:0; pointer-events:none}

  /* Broom (mirrored & refined) */
  .broom{ position:absolute; width:176px; height:28px; transform-origin:12% 50%; transform:translate(-50%,-50%) rotate(0deg); filter:drop-shadow(0 0 10px rgba(180,200,255,.35)); }
  .broomG{ position:absolute; inset:0; transform:scaleX(-1); } /* 좌우반전 */
  .shaft{ position:absolute; left:28px; top:13px; width:120px; height:2px; background:linear-gradient(90deg, #4c371b, #b99358 70%, #e6d2a8); border-radius:2px; }
  .handle{ position:absolute; left:8px; top:7px; width:28px; height:12px; border-radius:10px; background:#5b4325; box-shadow:inset 0 0 3px rgba(0,0,0,.45); }
  .collar{ position:absolute; left:146px; top:7px; width:10px; height:12px; border-radius:3px; background:linear-gradient(90deg,#8a6b1f,#ffd76a,#8a6b1f); box-shadow:0 0 6px rgba(255,220,120,.6); }
  .bristle{
    position:absolute; left:154px; top:2px; width:26px; height:22px; border-radius:0 14px 14px 0;
    background:
      repeating-linear-gradient(90deg, rgba(90,58,24,.9) 0 1px, rgba(55,34,12,.9) 1px 2px),
      radial-gradient(70% 70% at 30% 50%, #7a4f1f, #3b240e 70%);
    clip-path:polygon(0% 10%, 92% 0%, 100% 50%, 92% 100%, 0% 90%, 14% 50%);
    box-shadow:12px 0 16px rgba(125,84,35,.75);
  }

  .ball{
    position:absolute; width:14px; height:14px; border-radius:50%;
    background:radial-gradient(circle at 35% 35%, #ffd5b0, #e67e22 60%, #7a3a00 100%);
    box-shadow:0 0 12px rgba(255,200,120,.55), inset 0 0 6px rgba(255,255,255,.5);
    transform:translate(-50%,-50%); will-change:transform; opacity:0;
  }

  /* Footprints (oriented with path) */
  .footpad{position:absolute; pointer-events:none; transform-origin:center; filter:drop-shadow(0 0 2px rgba(120,95,60,.28))}
  .sole{position:absolute; width:12px; height:18px; border-radius:60% 60% 40% 40%; background:#b79658; opacity:.92; box-shadow:inset 0 -1px 2px rgba(0,0,0,.25)}
  .toe{position:absolute; border-radius:50%; background:#c9ad73; opacity:.9; box-shadow:inset 0 -1px 1px rgba(0,0,0,.2)}

  .desc{margin-top:4px; font-size:12px; color:#9fb2c9; line-height:1.35}
</style>
</head>
<body>
<div class="frame">
  <header>
    <h1>Wizard Typing</h1>
    <p class="hint">Type anything. The screen mirrors your rhythm—speed and hold time become the magic.<br>
      Spells carry power; uppercase spells add special effects.<br>
      Numbers, and some of the marks keep secrets.<br>
      Use Arrow Keys to start a Quidditch game.<br></p>
    <div class="spacer"></div>
    <button id="spellBtn" class="btn" type="button">Spell List ✨</button>
  </header>

  <main>
    <div id="pad" class="pad" tabindex="0" aria-label="Type here">
      <div id="line" class="line"></div><span id="caret" class="caret"></span>
      <div id="entities" class="entities"></div>
    </div>
  </main>
</div>

<!-- Spell list modal -->
<div id="modal" class="modal" role="dialog" aria-modal="true" aria-label="Spell list" style="display:none;place-items:center;background:rgba(0,0,0,.55);position:fixed;inset:0;z-index:1000">
  <div class="card" style="width:min(980px,92vw);max-height:80vh;overflow:auto;background:#0e1520;color:#d8e7f8;border:1px solid #223349;border-radius:16px;padding:18px 20px;box-shadow:0 30px 120px rgba(0,0,0,.55)">
    <h2 style="margin:6px 0 12px;font-size:18px">Spell Compendium</h2>
    <p style="margin:0 0 10px; font-size:12px; color:#9fb2c9">
    
    </p>
    <div id="spellGrid" class="grid" style="display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:10px"></div>
    <div style="text-align:right;margin-top:10px">
      <button id="closeModal" class="btn" type="button">Close</button>
    </div>
  </div>
</div>

<script>
(()=>{

  const pad   = document.getElementById('pad');
  const line  = document.getElementById('line');
  const caret = document.getElementById('caret');
  const entities = document.getElementById('entities');
  const modal = document.getElementById('modal');
  const spellBtn = document.getElementById('spellBtn');
  const closeModal = document.getElementById('closeModal');
  const grid = document.getElementById('spellGrid');

  function moveCaret(){ line.appendChild(caret); pad.scrollTop = pad.scrollHeight; }
  ['click','mousedown'].forEach(ev=> pad.addEventListener(ev, ()=>pad.focus()));
  window.addEventListener('load', ()=>pad.focus());

  /* ===== Tempo & Sizing ===== */
  const MIN_IV=40, MAX_IV=1600;
  const SCALE_MIN=0.6, SCALE_MAX=3.6;
  const LSPC_SLOW=34, LSPC_FAST=12;
  const LONG_PRESS_MIN=0,  LONG_PRESS_MAX=1500;
  const CURVE=8.0;

  let lastTime=0, ema=null; const EMA_ALPHA=0.25;
  const stack = [];
  const keyHolding = new Set();

  let stream = ""; const MAX_STREAM = 200;
  const ASCII = /^[\x20-\x7E]$/;
  const alpha = /[a-z]/i;

  const clamp=(v,a,b)=>Math.max(a, Math.min(b,v));
  const lerp=(a,b,t)=>a+(b-a)*t;
  const pressScale=(ms)=>{ const t=Math.max(0, Math.min(1,(ms-LONG_PRESS_MIN)/(LONG_PRESS_MAX-LONG_PRESS_MIN))); return lerp(1,3,t); };
  const withTempClass = (el, cls, ms)=>{ el.classList.add(cls); setTimeout(()=> el.classList.remove(cls), ms); };

  function overlay(node, life=1500){ node.style.pointerEvents='none'; pad.appendChild(node); setTimeout(()=>node.remove(), life); }
  function randXY(){
    const r=pad.getBoundingClientRect();
    const x = Math.random()*(r.width - 80) + 40;
    const y = Math.random()*(r.height - 80) + 40;
    return {x, y};
  }
  function ring({x,y,color='#9fe8ff',size=40,width=3,dur=700}){
    const r=document.createElement('div'); r.className='ring';
    r.style.left=(x-size/2)+'px'; r.style.top=(y-size/2)+'px';
    r.style.width=size+'px'; r.style.height=size+'px';
    r.style.borderColor=color; r.style.borderWidth=width+'px';
    pad.appendChild(r);
    r.animate([{transform:'scale(1)',opacity:.9},{transform:'scale(3.2)',opacity:0}],{duration:dur,easing:'ease-out',fill:'forwards'});
    setTimeout(()=>r.remove(), dur+60);
  }
  function beam({x,y,len=320,angle=0,color='#fff',dur=420,thick=2}){
    const b=document.createElement('div'); b.className='beam';
    b.style.left=x+'px'; b.style.top=y+'px'; b.style.width=len+'px';
    b.style.height=thick+'px';
    b.style.background = `linear-gradient(90deg, rgba(255,255,255,0), ${color}, rgba(255,255,255,0))`;
    pad.appendChild(b);
    b.animate([{transform:`rotate(${angle}rad) scaleX(0)`,opacity:.95},{transform:`rotate(${angle}rad) scaleX(1)`},{opacity:0}],{duration:dur,easing:'cubic-bezier(.2,.8,.2,1)',fill:'forwards'});
    setTimeout(()=>b.remove(), dur+40);
  }
  function makeParticles({x,y,count=120,color='#fff',spread=260,life=1700,shape='circle'}){
    for(let i=0;i<count;i++){
      const p=document.createElement('div'); p.className='particle';
      if(shape==='square') p.style.borderRadius='4px';
      p.style.background=color; p.style.left=x+'px'; p.style.top=y+'px';
      const a=Math.random()*Math.PI*2; const r=Math.random()*spread;
      const tx=Math.cos(a)*r, ty=Math.sin(a)*r;
      p.animate([{transform:'translate(0,0)',opacity:1},{transform:`translate(${tx}px,${ty}px)`,opacity:0}],{duration:600+Math.random()*900, easing:'cubic-bezier(.2,.8,.2,1)', fill:'forwards'});
      pad.appendChild(p); setTimeout(()=>p.remove(), life);
    }
  }

  function printChar(ch, iv, isUppercase=false){
    const tIv = Math.max(0, Math.min(1, ((iv??MAX_IV)-40)/(MAX_IV-40)));
    const fast = 1 - tIv;
    const f = Math.pow(fast, CURVE);
    const baseScale = lerp(SCALE_MIN, SCALE_MAX, f);
    const spacing   = lerp(LSPC_SLOW, LSPC_FAST, f);

    const span=document.createElement('span');
    span.className='ch';
    span.dataset.ch = ch;
    span.dataset.base = baseScale.toFixed(3);
    span.dataset.scale = span.dataset.base;
    span.dataset.upper = isUppercase ? '1' : '0';
    span.textContent = (ch===' ') ? '\u00A0' : ch;
    span.style.transform = `scale(${span.dataset.scale})`;
    span.style.marginRight = `${spacing}px`;
    span.style.opacity = String(lerp(1, .9, tIv));

    line.appendChild(span);
    stack.push(span);
    moveCaret();
    return span;
  }

  function removeLast(){
    const n=stack.pop();
    if(!n) return;
    const ch = n.dataset?.ch || "";
    if(alpha.test(ch)) stream = stream.slice(0, -1);
    n.remove();
    moveCaret();
  }

  function getLastScale(){
    for(let i=stack.length-1;i>=0;i--){
      const n=stack[i];
      if(n && n.classList && n.classList.contains('ch')){
        const s = parseFloat(n.dataset.scale || n.dataset.base || '1');
        if(!isNaN(s)) return s;
      }
    }
    return 1;
  }

  // Hold growth — persists
  let currentSpan=null, holdStart=0, rafId=null, holding=false;
  function startHold(){
    if(!currentSpan) return;
    if(rafId) cancelAnimationFrame(rafId);
    holding=true; holdStart = performance.now();
    const loop=()=>{
      if(!holding || !currentSpan?.isConnected){ rafId=null; return; }
      const s = parseFloat(currentSpan.dataset.base || '1') * pressScale(performance.now()-holdStart);
      currentSpan.dataset.scale = s.toFixed(3);
      currentSpan.style.transform = `scale(${currentSpan.dataset.scale})`;
      rafId = requestAnimationFrame(loop);
    };
    rafId = requestAnimationFrame(loop);
  }
  function stopHold(){
    holding=false;
    if(rafId){ cancelAnimationFrame(rafId); rafId=null; }
  }

  /* ---------- Spells ---------- */
  const PATTERN_TO_KEY = {
    'lumos':'lumos','nox':'nox','expelliarmus':'expelliarmus',
    'wingardiumleviosa':'wingardium leviosa',
    'obliviate':'obliviate',
    'expectopatronum':'expecto patronum','expectopetronum':'expecto patronum',
    'imperio':'imperio','crucio':'crucio','avadakedavra':'avada kedavra'
  };
  const PATTERNS = Object.keys(PATTERN_TO_KEY).sort((a,b)=>b.length-a.length);

  function getLastLetterSpans(n){
    const out=[];
    for(let i=stack.length-1;i>=0 && n>0;i--){
      const el=stack[i];
      if(!(el?.classList?.contains('ch'))) continue;
      const t=el.dataset.ch||'';
      if(/^[a-zA-Z]$/.test(t)){ out.unshift(el); n--; }
    }
    return out;
  }
  function strongHighlightSpans(spans){
    if(!spans.length) return;
    const k = Math.max(0, Math.min(1,(getLastScale()-SCALE_MIN)/(SCALE_MAX-SCALE_MIN)));
    spans.forEach((el,idx)=>{
      el.animate(
        [
          { transform: el.style.transform, color:'#fff', filter:'drop-shadow(0 0 0 rgba(255,240,180,0))' },
          { transform: 'scale(3.2)', color:'#ffe7b1', filter:`drop-shadow(0 0 ${28+40*k}px rgba(255,240,180,.95))`, offset:.35 },
          { transform: el.style.transform, color:'#fff', filter:'drop-shadow(0 0 0 rgba(255,240,180,0))' }
        ],
        { duration: 1200 + idx*20, easing:'cubic-bezier(.2,.8,.2,1)', fill:'none' }
      );
    });

    const first = spans[0].getBoundingClientRect();
    const last  = spans[spans.length-1].getBoundingClientRect();
    const padR  = pad.getBoundingClientRect();
    const x = first.left - padR.left;
    const y = last.bottom - padR.top + 6;
    const len = (last.right - first.left);
    const hl = document.createElement('div');
    hl.className='beam';
    hl.style.left=x+'px'; hl.style.top=y+'px'; hl.style.width=len+'px';
    hl.style.background='linear-gradient(90deg, rgba(255,220,120,0), rgba(255,220,120,1), rgba(255,220,120,0))';
    pad.appendChild(hl);
    hl.animate([{transform:'scaleX(0)',opacity:1},{transform:'scaleX(1)'},{opacity:0}],{duration:900,easing:'cubic-bezier(.2,.8,.2,1)',fill:'forwards'});
    setTimeout(()=>hl.remove(), 980);

    sfx('spell-ready', getLastScale());
  }
  function detectSpellFromStream(){
    for(const p of PATTERNS){
      if(stream.endsWith(p)){
        const spans = getLastLetterSpans(p.length);
        strongHighlightSpans(spans);
        triggerSpell(PATTERN_TO_KEY[p], spans);
        break;
      }
    }
  }

  /* ---------- KEYBOARD ---------- */
  const isPrintable = (k)=>k.length===1 && ASCII.test(k);

  window.addEventListener('keydown', (e)=>{
    if(e.key===' '||e.key==='PageDown'||e.key==='PageUp'||e.key.startsWith('Arrow')) e.preventDefault();
    if(e.isComposing) return;

    audioInit();

    if(e.key.startsWith('Arrow')){
      setArrow(e.key, true);
      ensureBroom();
      ensureBall();
      if(!q.run){ q.run=true; broomLoop(); }
      return;
    }

    const now = Date.now();
    const iv  = lastTime ? now - lastTime : MAX_IV;
    lastTime  = now;
    ema = (ema===null) ? iv : Math.round(EMA_ALPHA*iv + (1-EMA_ALPHA)*ema);

    if(e.key==='Backspace'){ e.preventDefault(); removeLast(); sfx('back'); return; }
    if(e.key==='Enter'){ e.preventDefault(); const br=document.createElement('br'); line.appendChild(br); stack.push(br); moveCaret(); return; }
    if(e.key==='Tab'){ e.preventDefault(); const s=printChar(' ', ema??MAX_IV); s.textContent='    '; s.dataset.ch='    '; s.style.marginRight='12px'; sfx('tab'); return; }
    if(e.repeat) return;

    // '!' — print AND fire straight wand beam from caret
    if(e.key==='!'){
      const span = printChar('!', ema ?? MAX_IV, false);
      currentSpan = span;
      fireWandBeam();
      sfx('beam', 1);
      return;
    }

    if(isPrintable(e.key)){
      const ch = e.key;
      const isUpper = /^[A-Z]$/.test(ch);
      const span = printChar(ch, ema ?? MAX_IV, isUpper);
      currentSpan = span;
      keyHolding.add(e.code);
      startHold();

      if(ch==='.'){ periodRipple(); sfx('period', getLastScale()); }
      if(/[0-9]/.test(ch)){ triggerNumber(ch); }
      if(ch==='?'){ spawnFootprints(); sfx('map', getLastScale()); }

      if(alpha.test(ch)){
        stream = (stream + ch.toLowerCase());
        if(stream.length > MAX_STREAM) stream = stream.slice(-MAX_STREAM);
        detectSpellFromStream();
      }
      sfx(isUpper?'keyU':'key', getLastScale());
    }
  });

  window.addEventListener('keyup', (e)=>{
    if(e.key.startsWith('Arrow')){
      setArrow(e.key, false);
      if(!anyArrowDown()){ hideBall(); }
      return;
    }
    if(keyHolding.has(e.code)){ keyHolding.delete(e.code); }
    if(keyHolding.size===0) stopHold();
  });

  /* ---------- Durations ---------- */
  const DUR = {
    default: 5000,
    'nox': 3000, 'imperio': 3000, 'crucio': 3000, 'expecto patronum': 2500
  };

  /* ---------- Spell Registry ---------- */
  const SPELLS = {
    'lumos':              { fx: castLumos, sfx:'lumos' },
    'nox':                { fx: castNox, sfx:'nox' },
    'expelliarmus':       { fx: castExpelliarmus, sfx:'expelliarmus' },
    'wingardium leviosa': { fx: castWingardiumLeviosa, sfx:'wingardium' },
    'obliviate':          { fx: castObliviate, sfx:'obliviate' },
    'expecto patronum':   { fx: castExpectoPatronum, sfx:'expecto' },
    'imperio':            { fx: castImperio, sfx:'imperio' },
    'crucio':             { fx: castCrucio, sfx:'crucio' },
    'avada kedavra':      { fx: castAvadaKedavra, sfx:'avada' }
  };

  function triggerSpell(key, spans){
    const lastScale = getLastScale();
    const baseNorm  = Math.max(0, Math.min(1,(lastScale - SCALE_MIN)/(SCALE_MAX - SCALE_MIN)));
    const sizeNorm  = baseNorm;
    const {x,y} = randXY();
    const lastWordSpans = collectLastWordSpans();
    const ms = DUR[key] ?? DUR.default;

    // Uppercase spell detection (majority uppercase)
    let upper=false;
    if(spans && spans.length){
      const up = spans.filter(s=>/^[A-Z]$/.test(s.dataset.ch||'')).length;
      upper = (up / spans.length) >= 0.6;
    }

    sfx(SPELLS[key].sfx || 'spell', lastScale);
    SPELLS[key].fx({x,y,lastWordSpans,ms,sizeNorm,sizeScale:lastScale,upper});
  }

  function collectLastWordSpans(){
    const out=[];
    for(let i=stack.length-1;i>=0;i--){
      const n=stack[i];
      if(!(n && n.classList && n.classList.contains('ch'))) break;
      const t=n.dataset.ch||'';
      if(!/[\w\-']/.test(t)) break;
      out.unshift(n);
    }
    return out;
  }

  // helpers
  function magFromSize(sizeNorm, min=0.8, max=2.5){ return lerp(min, max, sizeNorm); }
  function countFromSize(sizeNorm, base=80, extra=240){ return Math.round(base + extra*sizeNorm); }
  function spreadFromSize(sizeNorm, base=240, extra=300){ return Math.round(base + extra*sizeNorm); }

  /* ====== SPELL FX (uppercase spell → augmented visuals) ====== */
  function castLumos({ms,sizeNorm,upper}){
    const boost = magFromSize(sizeNorm, 1.2, upper?2.6:2.2);
    pad.style.filter = `brightness(${3.6*boost}) saturate(${1.3*boost})`;
    withTempClass(pad,'lumos', ms);
    if(upper){
      const {x,y}=randXY();
      ring({x,y,color:'#ffe7b1',size:70,width:4,dur:560});
      makeParticles({x,y,count:100,color:'#fff6c6',spread:200,life:900});
    }
    setTimeout(()=>{ pad.style.filter=''; }, ms+40);
  }
  function castNox({x,y,ms,upper}){
    withTempClass(pad,'nox', ms);
    ring({x,y,color: upper ? '#bdf' : '#8fd',size: upper?60:46,width: upper?3:2,dur:420});
    overlay(Object.assign(document.createElement('div'),{className:'flash'}), upper?180:120);
  }

  function castExpelliarmus({x,y,lastWordSpans,sizeNorm,upper}){
    const mag = magFromSize(sizeNorm, 1.0, upper?2.8:2.3);
    beam({x,y,angle:0,len:420+240*sizeNorm,color:'rgba(255,120,120,0.95)',dur:360,thick:upper?5:3});
    const dur=360;
    lastWordSpans.forEach((s,i)=>{
      setTimeout(()=>{
        const dx = (Math.random()*2-1)*(160*mag);
        const dy = - (90 + Math.random()*160)*mag;
        const rot= (Math.random()*2-1)*540*mag;
        s.animate(
          [{transform:s.style.transform,offset:0},
           {transform:`translate(${dx}px,${dy}px) rotate(${rot}deg)`,offset:.55},
           {transform:s.style.transform,offset:1}],
          {duration:dur, easing:'cubic-bezier(.2,.8,.2,1)', fill:'forwards'}
        );
      }, i*8);
    });
    makeParticles({x,y,count:countFromSize(sizeNorm, upper?100:60, upper?140:70),color:'#ff5a5a',spread:spreadFromSize(sizeNorm, 220, 160),life:800});
  }

  function castWingardiumLeviosa({ms,sizeNorm,upper}){
    withTempClass(pad,'float-strong', ms);
    const base=30+Math.round(100*sizeNorm)+(upper?120:0);
    for(let i=0;i<base;i++){
      const p=document.createElement('div'); p.className='particle';
      p.style.background= upper ? '#e9fbff' : '#bfe8ff';
      const {x,y}=randXY(); p.style.left=x+'px'; p.style.top=y+'px';
      const up = 120+260*sizeNorm*Math.random()*(upper?1.4:1);
      p.animate([{transform:'translate(0,0)',opacity:.25},{transform:`translate(0,-${up}px)`,opacity:0}],{duration:900+600*Math.random(),easing:'ease-out',fill:'forwards'});
      pad.appendChild(p); setTimeout(()=>p.remove(), 1600);
    }
  }

  function castObliviate({sizeNorm,upper}){
    if(upper){ overlay(Object.assign(document.createElement('div'),{className:'veil'}), 700); }
    const chars = Array.from(document.querySelectorAll('.ch'));
    let i=0;
    const iv = 32 + Math.round(24*(1-sizeNorm)); // slightly faster
    (function run(){
      if(i>=chars.length) return;
      const s=chars[i];
      s.animate([{opacity:1,filter:'blur(0px)'},{opacity:0,filter:'blur(1.4px)'}],{duration:110,fill:'forwards'});
      setTimeout(()=>{ s.remove(); i++; moveCaret(); run(); }, iv);
    })();
  }

  function castExpectoPatronum({x,y,sizeNorm,ms,upper}){
    overlay(Object.assign(document.createElement('div'),{className:'veil'}), 800);
    makeParticles({x,y,count:countFromSize(sizeNorm, upper?180:140, upper?200:160),color:'#c8f5ff',spread:spreadFromSize(sizeNorm, 300, 280),life:1100});
    const boost = magFromSize(sizeNorm, 1.3, upper?2.3:2.0);
    pad.style.filter = `brightness(${3.0*boost}) saturate(${1.35*boost})`;
    setTimeout(()=>{ pad.style.filter=''; }, ms);
  }

  let imperioTimer=null, imperioOn=false;
  function castImperio({ms,sizeNorm,upper}){
    if(imperioOn) return; imperioOn=true; withTempClass(pad,'shake', ms);
    const freq = 70 / magFromSize(sizeNorm, upper?1.6:1.2);
    imperioTimer=setInterval(()=>{
      const chars='abcdefghijklmnopqrstuvwxyz';
      const c=chars[Math.floor(Math.random()*chars.length)];
      const span=printChar(c, 100);
      span.animate([{transform:'scale(1.9)'},{transform:`scale(${span.dataset.base||1})`}],{duration:130,fill:'forwards'});
    }, Math.max(24,freq));
    setTimeout(()=>{ clearInterval(imperioTimer); imperioOn=false; pad.classList.remove('shake'); }, ms);
  }

  function castCrucio({ms,upper}){ withTempClass(pad,'shake', ms); overlay(Object.assign(document.createElement('div'),{className:'flash'}), upper?220:180); }

  function castAvadaKedavra({upper}){
    overlay(Object.assign(document.createElement('div'),{className:'greenflash'}), upper?680:520);
    document.querySelectorAll('.ch').forEach(el=> el.remove());
    stack.length = 0; stream = "";
    moveCaret();
  }

  /* ---------- Number FX (0-9) ---------- */
  function triggerNumber(d){
    const lastScale = getLastScale();
    const baseNorm  = Math.max(0, Math.min(1,(lastScale - SCALE_MIN)/(SCALE_MAX - SCALE_MIN)));
    const sizeNorm  = baseNorm;
    const pos = randXY();
    switch(d){
      case '1': numMeteors(sizeNorm); sfx('num1', lastScale); break;
      case '2': numVortex(pos,sizeNorm); sfx('num2', lastScale); break;
      case '3': numConfettiBounce(pos,sizeNorm); sfx('num3', lastScale); break;
      case '4': numQuakeCrack(sizeNorm); sfx('num4', lastScale); break;
      case '5': numBolts(pos,sizeNorm); sfx('num5', lastScale); break;
      case '6': numRockets(sizeNorm); sfx('num6', lastScale); break;
      case '7': numWindRain(sizeNorm); sfx('num7', lastScale); break;
      case '8': numLensTint(sizeNorm); sfx('num8', lastScale); break;
      case '9': numRunesConstellation(sizeNorm); sfx('num9', lastScale); break;
      case '0': numPortalPull(pos,sizeNorm); sfx('num0', lastScale); break;
    }
  }

  function numMeteors(k){
    const r=pad.getBoundingClientRect();
    const count=6+Math.round(10*k);
    for(let i=0;i<count;i++){
      const startX = -60 - Math.random()*120;
      const startY = Math.random()*r.height*0.6;
      const endX   = r.width + 120;
      const endY   = startY + 120 + 220*Math.random();
      const m=document.createElement('div');
      m.className='particle';
      m.style.width='4px'; m.style.height='4px'; m.style.borderRadius='50%';
      m.style.background='#fff';
      m.style.left=startX+'px'; m.style.top=startY+'px';
      m.style.boxShadow='0 0 12px #fff, -8px 0 14px rgba(255,255,255,.6)';
      pad.appendChild(m);
      m.animate([{transform:'translate(0,0)'},{transform:`translate(${endX-startX}px,${endY-startY}px)`}],{duration:700+400*Math.random(),easing:'linear',fill:'forwards'});
      setTimeout(()=>m.remove(), 1200);
    }
  }

  function numVortex({x,y},k){
    const arms=7, steps=70;
    for(let a=0;a<arms;a++){
      for(let s=0;s<steps;s++){
        const t=s/steps, ang = a*(Math.PI*2/arms) + t*6.2*Math.PI;
        const r=10 + t*(160+240*k);
        const px=x + Math.cos(ang)*r, py=y + Math.sin(ang)*r;
        const p=document.createElement('div'); p.className='particle';
        p.style.background=['#8df2ff','#a7b6ff','#7fffd4'][s%3]; p.style.left=x+'px'; p.style.top=y+'px';
        p.style.width='4px'; p.style.height='4px';
        p.animate([{transform:'translate(0,0)',opacity:1},{transform:`translate(${px-x}px,${py-y}px)`,opacity:0.05}],{duration:700+520*t,fill:'forwards',easing:'ease-out'});
        pad.appendChild(p); setTimeout(()=>p.remove(), 1000+520*t);
      }
    }
    document.querySelectorAll('.ch').forEach(el=>{
      el.animate([{transform:el.style.transform},{transform:el.style.transform+' perspective(400px) rotateY(18deg)'},{transform:el.style.transform}],{duration:600+300*k,fill:'none',easing:'ease-in-out'});
    });
  }

  function numConfettiBounce({x,y},k){
    const n=70+Math.round(140*k);
    const colors=['#ff6b6b','#ffd166','#06d6a0','#4cc9f0','#e0aaff'];
    for(let i=0;i<n;i++){
      const p=document.createElement('div'); p.className='particle';
      p.style.background=colors[i%colors.length];
      p.style.borderRadius='3px';
      p.style.left=x+'px'; p.style.top=y+'px';
      const a=(Math.random()*Math.PI) - Math.PI/2;
      const speed=120+220*Math.random()*(.7+k);
      const tx=Math.cos(a)*speed, ty=Math.sin(a)*speed;
      p.animate([
        {transform:'translate(0,0) rotate(0deg)',opacity:1, offset:.0},
        {transform:`translate(${tx}px,${ty}px) rotate(${360*Math.random()}deg)`,opacity:.9, offset:.45},
        {transform:`translate(${tx}px,${ty+60}px) rotate(${720*Math.random()}deg)`,opacity:.9, offset:.7},
        {transform:`translate(${tx}px,${ty+20}px)`,opacity:0, offset:1}
      ], {duration:900+600*Math.random(),easing:'cubic-bezier(.2,.9,.2,1)',fill:'forwards'});
      pad.appendChild(p); setTimeout(()=>p.remove(), 1600);
    }
  }

  function numQuakeCrack(k){
    withTempClass(pad,'shake', 420+200*k);
    const r=pad.getBoundingClientRect();
    const cracks=8+Math.round(6*k);
    for(let i=0;i<cracks;i++){
      const c=document.createElement('div');
      c.style.position='absolute'; c.style.pointerEvents='none';
      c.style.left=(Math.random()*r.width)+'px';
      c.style.top=(Math.random()*r.height)+'px';
      c.style.width='1px'; c.style.height=(80+Math.random()*200)+'px';
      c.style.background='linear-gradient(#d0e4ff, rgba(208,228,255,0))';
      c.style.transformOrigin='top center';
      c.style.filter='drop-shadow(0 0 6px rgba(160,200,255,.8))';
      const ang=(Math.random()-.5)*Math.PI;
      pad.appendChild(c);
      c.animate([{transform:`rotate(${ang}rad) scaleY(0)`,opacity:1},{transform:`rotate(${ang}rad) scaleY(1)`},{opacity:0}],{duration:420+160*Math.random(),easing:'cubic-bezier(.2,.8,.2,1)',fill:'forwards'});
      setTimeout(()=>c.remove(), 640);
    }
  }

  function numBolts({x,y},k){
    const bolts = 7 + Math.round(6*k);
    for(let i=0;i<bolts;i++){
      const b=document.createElement('div');
      const len=100+Math.random()*200*(.6+k);
      b.style.position='absolute'; b.style.left=x+'px'; b.style.top=y+'px';
      b.style.width='2px'; b.style.height=len+'px';
      b.style.background='linear-gradient(#fff, rgba(255,255,255,0))';
      b.style.filter='drop-shadow(0 0 10px #fff)';
      b.style.transformOrigin='top center';
      const ang=(Math.random()-.5)*Math.PI/1.6;
      pad.appendChild(b);
      b.animate([{transform:`rotate(${ang}rad) scaleY(0)`,opacity:1},{transform:`rotate(${ang}rad) scaleY(1)`},{opacity:0}],{duration:420+160*Math.random(),easing:'cubic-bezier(.2,.8,.2,1)',fill:'forwards'});
      setTimeout(()=>b.remove(), 600);
    }
  }

  function numRockets(k){
    const r=pad.getBoundingClientRect();
    const rockets=2+Math.round(3*k);
    for(let i=0;i<rockets;i++){
      const x=40+Math.random()*(r.width-80);
      const y=r.height+20;
      const apex=60+Math.random()*(r.height*0.5);
      const dot=document.createElement('div'); dot.className='particle';
      dot.style.left=x+'px'; dot.style.top=y+'px'; dot.style.background='#ffd166';
      pad.appendChild(dot);
      dot.animate([{transform:'translate(0,0)'},{transform:`translate(0,-${y-apex}px)`}],{duration:700+200*Math.random(),easing:'cubic-bezier(.2,.8,.2,1)',fill:'forwards'});
      setTimeout(()=>{
        const pos={x, y:apex};
        ring({x:pos.x,y:pos.y,color:'#ffe7a3',size:60+70*k,width:4,dur:420});
        makeParticles({x:pos.x,y:pos.y,count:80+Math.round(140*k),color:['#ff6b6b','#ffd166','#06d6a0','#4cc9f0'][i%4],spread:260+260*k,life:1100});
        dot.remove();
      }, 760);
    }
  }

  function numWindRain(k){
    const drops=60+Math.round(100*k);
    const r=pad.getBoundingClientRect();
    for(let i=0;i<drops;i++){
      const d=document.createElement('div'); d.className='particle';
      d.style.width='2px'; d.style.height= (14+Math.random()*26)+'px';
      d.style.borderRadius='1px'; d.style.background='#9bd9ff';
      const x=-20+Math.random()*(r.width+40);
      d.style.left=x+'px'; d.style.top='-40px';
      pad.appendChild(d);
      const y=r.height+60, dx=160+240*Math.random();
      d.animate([{transform:`translate(0,0) skewX(-20deg)`,opacity:.95},{transform:`translate(${dx}px,${y}px) skewX(-20deg)`,opacity:0}],{duration:900+500*Math.random(),easing:'linear',fill:'forwards'});
      setTimeout(()=>d.remove(), 1500);
    }
  }

  function numLensTint(k){
    const veil=document.createElement('div');
    veil.style.position='absolute'; veil.style.inset='0'; veil.style.pointerEvents='none';
    veil.style.background=`radial-gradient(circle at ${Math.random()*100}% ${Math.random()*100}%, rgba(120,200,255,${.18+.28*k}), rgba(0,0,0,0) 60%)`;
    veil.style.mixBlendMode='screen'; pad.appendChild(veil);
    veil.animate([{opacity:0},{opacity:1,offset:.25},{opacity:0}],{duration:1000+500*k, easing:'ease-in-out', fill:'forwards'});
    setTimeout(()=>veil.remove(), 1200+520*k);
  }

  function numRunesConstellation(k){
    const runes="ᚠᚢᚦᚨᚱᚲᚷᚹᛉᛊᛏᛒᛗᛟ";
    const r=pad.getBoundingClientRect();
    const pts=[];
    const count=6+Math.round(10*k);
    for(let i=0;i<count;i++){
      const s=document.createElement('div');
      s.textContent = runes[Math.floor(Math.random()*runes.length)];
      s.style.position='absolute'; s.style.pointerEvents='none';
      const px=30+Math.random()*(r.width-60), py=30+Math.random()*(r.height-60);
      s.style.left=px+'px'; s.style.top=py+'px';
      s.style.fontSize=(28+Math.random()*60*(1+k))+'px';
      s.style.color='#cfe8ff';
      s.style.textShadow='0 0 16px rgba(200,240,255,.8)';
      pad.appendChild(s);
      s.animate([{transform:'scale(.8)',opacity:0.0},{transform:'scale(1.2) rotate(3deg)',opacity:1,offset:.4},{transform:'scale(1.6) rotate(-4deg)',opacity:0}],{duration:1100+500*Math.random(),easing:'ease-in-out',fill:'forwards'});
      setTimeout(()=>s.remove(), 1600);
      pts.push({x:px,y:py});
    }
    for(let i=0;i<pts.length-1;i++){
      if(Math.random()>.6) continue;
      const a=pts[i], b=pts[i+1];
      const l=document.createElement('div'); l.className='beam';
      l.style.left=a.x+'px'; l.style.top=a.y+'px';
      const len=Math.hypot(b.x-a.x,b.y-a.y);
      const ang=Math.atan2(b.y-a.y,b.x-a.x);
      l.style.width=len+'px';
      pad.appendChild(l);
      l.animate([{transform:`rotate(${ang}rad) scaleX(0)`,opacity:.8},{transform:`rotate(${ang}rad) scaleX(1)`,opacity:.8},{opacity:0}],{duration:900,easing:'ease-out',fill:'forwards'});
      setTimeout(()=>l.remove(), 920);
    }
  }

  function numPortalPull({x,y},k){
    ring({x,y,color:'#a7b6ff',size:70+40*k,width:5,dur:620});
    ring({x,y,color:'#7fffd4',size:50+30*k,width:4,dur:540});
    const center={x,y};
    const rPad=pad.getBoundingClientRect();
    const take=Math.min(12, stack.length);
    for(let i=stack.length-1, c=0;i>=0 && c<take;i--){
      const el=stack[i]; if(!(el?.classList?.contains('ch'))) continue;
      const br=el.getBoundingClientRect();
      const px=(br.left+br.right)/2 - rPad.left, py=(br.top+br.bottom)/2 - rPad.top;
      const dx=center.x-px, dy=center.y-py;
      el.animate([{transform:el.style.transform},{transform:`translate(${dx*0.6}px,${dy*0.6}px) scale(0.8)`},{transform:el.style.transform}],{duration:600+200*Math.random(),easing:'cubic-bezier(.2,.8,.2,1)',fill:'none'});
      c++;
    }
  }

  /* ----- Spell list (no duplicates) ----- */
  const SPELL_INFO = [
    ['Lumos','Creates light at the wand tip.'],
    ['Nox','Extinguishes the light produced by Lumos.'],
    ['Expelliarmus','Disarming Charm: forces the opponent’s wand (or object) away.'],
    ['Wingardium Leviosa','Levitation Charm: makes objects rise and float.'],
    ['Obliviate','Memory Charm: erases or alters memories.'],
    ['Expecto Patronum','Patronus Charm: summons a Patronus to repel Dementors.'],
    ['Imperio','Imperius Curse: places the victim under the caster’s control.'],
    ['Crucio','Cruciatus Curse: inflicts unbearable pain.'],
    ['Avada Kedavra','Killing Curse: causes instant death.']
  ];
  SPELL_INFO.forEach(([name,desc])=>{
    const d=document.createElement('div'); d.className='spell';
    d.style.border='1px solid #223349'; d.style.borderRadius='10px'; d.style.padding='10px';
    d.innerHTML=`<b style="color:#ffe7b1">${name}</b><div class="desc">${desc}</div>`;
    grid.appendChild(d);
  });
  spellBtn.addEventListener('click', ()=>{ modal.style.display='grid'; });
  closeModal.addEventListener('click', ()=>{ modal.style.display='none'; pad.focus(); });
  modal.addEventListener('click', (e)=>{ if(e.target===modal){ modal.style.display='none'; pad.focus(); } });

  /* =======================
     WebAudio SFX
     ======================= */
  let actx=null, master=null, echo=null, echoDelay=null, echoFb=null;
  function audioInit(){
    if(actx) return;
    actx = new (window.AudioContext||window.webkitAudioContext)();
    master = actx.createGain(); master.gain.value=0.24; master.connect(actx.destination);
    echo = actx.createGain(); echo.gain.value=0.2;
    echoDelay = actx.createDelay(0.5); echoFb = actx.createGain(); echoFb.gain.value=0.3;
    echo.connect(echoDelay).connect(echoFb).connect(echoDelay);
    echoDelay.connect(master);
    document.addEventListener('click', ()=>actx.resume(), {once:true});
    document.addEventListener('keydown', ()=>actx.resume(), {once:true});
  }
  function env(node, tA=0.004, tD=0.22, g=0.9){
    const now=actx?.currentTime ?? 0;
    node.gain.setValueAtTime(0, now);
    node.gain.linearRampToValueAtTime(g, now+tA);
    node.gain.exponentialRampToValueAtTime(0.0001, now+tA+tD);
  }
  function route(g){ g.connect(master); if(echo) g.connect(echo); }
  function beep(freq=440, dur=0.15, type='sine', gain=0.25){
    if(!actx) return;
    const osc=actx.createOscillator(); osc.type=type; osc.frequency.value=freq;
    const g=actx.createGain(); g.gain.value=0; env(g, 0.004, dur, gain);
    osc.connect(g); route(g); osc.start(); osc.stop(actx.currentTime+dur+0.05);
  }
  function sweep(f1=200, f2=1200, dur=0.25, type='sawtooth', gain=0.22){
    if(!actx) return;
    const osc=actx.createOscillator(); osc.type=type; osc.frequency.setValueAtTime(f1, actx.currentTime); osc.frequency.exponentialRampToValueAtTime(f2, actx.currentTime+dur);
    const g=actx.createGain(); g.gain.value=0; env(g, 0.005, dur, gain);
    osc.connect(g); route(g); osc.start(); osc.stop(actx.currentTime+dur+0.05);
  }
  function noise(dur=0.25, type='bandpass', freq=1200, q=0.8, gain=0.28){
    if(!actx) return;
    const buffer=actx.createBuffer(1, actx.sampleRate*dur, actx.sampleRate);
    const data=buffer.getChannelData(0);
    for(let i=0;i<data.length;i++) data[i]=Math.random()*2-1;
    const src=actx.createBufferSource(); src.buffer=buffer; src.loop=false;
    const filt=actx.createBiquadFilter(); filt.type=type; filt.frequency.value=freq; filt.Q.value=q;
    const g=actx.createGain(); g.gain.value=0; env(g, 0.003, dur, gain);
    src.connect(filt).connect(g); route(g); src.start(); src.stop(actx.currentTime+dur+0.05);
  }
  function thud(dur=0.32, fStart=220, fEnd=60, gain=0.6){
    if(!actx) return;
    const osc=actx.createOscillator(); osc.type='sine'; osc.frequency.setValueAtTime(fStart, actx.currentTime); osc.frequency.exponentialRampToValueAtTime(fEnd, actx.currentTime+dur);
    const g=actx.createGain(); g.gain.value=0; env(g, 0.002, dur, gain);
    osc.connect(g); route(g); osc.start(); osc.stop(actx.currentTime+dur+0.05);
  }
  function sfx(name='key', size=1.0){
    if(!actx) return;
    switch(name){
      case 'key': noise(0.06, 'highpass', 1700, 0.9, 0.12); break;
      case 'keyU': noise(0.08, 'highpass', 2000, 1.1, 0.18); break;
      case 'back': beep(120, 0.07, 'square', 0.2); break;
      case 'tab': beep(260, 0.07, 'sine', 0.16); break;
      case 'spell-ready': sweep(500, 2400, 0.22, 'triangle', 0.26); break;

      case 'lumos': sweep(800, 2400, 0.25, 'triangle', 0.3); noise(0.14, 'bandpass', 3200, 1.1, 0.14); break;
      case 'nox':   thud(0.26, 180, 55, 0.5); break;
      case 'expelliarmus': noise(0.16, 'highpass', 1900, 1.0, 0.36); break;
      case 'wingardium': sweep(240, 720, 0.38, 'sine', 0.20); break;
      case 'obliviate':  sweep(1400, 300, 0.22, 'triangle', 0.2); break;
      case 'expecto': sweep(420, 2200, 0.3, 'sawtooth', 0.24); noise(0.2, 'bandpass', 1700, 0.9, 0.2); break;
      case 'imperio': beep(430, 0.06, 'square', 0.18); break;
      case 'crucio':  noise(0.24, 'highpass', 1600, 1.0, 0.32); break;
      case 'avada':   thud(0.38, 180, 48, 0.65); break;

      case 'num1': beep(900, 0.08, 'triangle', 0.2); break;
      case 'num2': sweep(300, 900, 0.22, 'sine', 0.2); break;
      case 'num3': noise(0.18, 'bandpass', 1600, 0.8, 0.24); break;
      case 'num4': thud(0.22, 220, 80, 0.48); break;
      case 'num5': noise(0.14, 'highpass', 2600, 1.2, 0.32); break;
      case 'num6': sweep(500, 1600, 0.24, 'sawtooth', 0.24); break;
      case 'num7': noise(0.2, 'highpass', 1400, 1.0, 0.28); break;
      case 'num8': sweep(700, 420, 0.2, 'triangle', 0.18); break;
      case 'num9': noise(0.26, 'bandpass', 1100, 0.7, 0.26); break;
      case 'num0': sweep(300, 1200, 0.28, 'triangle', 0.22); break;

      case 'beam': noise(0.12, 'highpass', 2100, 1.1, 0.28); break; // !
      case 'map':  thud(0.06, 260, 140, 0.35); break;
      case 'period': beep(520, 0.08, 'triangle', 0.2); break;
      default: beep(440,0.1);
    }
  }

  /* =======================
     '!' — straight wand beam from caret
     ======================= */
  function fireWandBeam(){
    const padR=pad.getBoundingClientRect();
    const cR=caret.getBoundingClientRect();
    const startX = (cR.left - padR.left);
    const startY = ((cR.top + cR.bottom)/2 - padR.top);
    const len = padR.width - startX + 80;
    beam({x:startX, y:startY, len, angle:0, color:'rgba(255,215,140,0.98)', dur:360, thick:4});
    ring({x:startX, y:startY, color:'#ffe7b1', size:30, width:3, dur:320});
  }

  /* '.' — ripple at caret */
  function periodRipple(){
    const padR=pad.getBoundingClientRect();
    const cR=caret.getBoundingClientRect();
    const x = (cR.left - padR.left);
    const y = ((cR.top + cR.bottom)/2 - padR.top);
    ring({x,y,color:'#bfe1ff',size:36,width:3,dur:380});
    ring({x,y,color:'#e6f5ff',size:60,width:2,dur:520});
  }

  /* =======================
     Broom + autonomous Ball (avoid broom)
     ======================= */
  let q = {
    run:false, broomEl:null, ballEl:null,
    bounds:{w:0,h:0},
    broom:{x:0,y:0,vx:0,vy:0},
    ball:{x:0,y:0,vx:0,vy:0,vis:false},
    keys:{Left:false,Right:false,Up:false,Down:false}
  };
  function ensureBroom(){
    if(q.broomEl) return;
    const br=document.createElement('div'); br.className='broom';
    br.innerHTML = '<div class="broomG"><div class="shaft"></div><div class="handle"></div><div class="collar"></div><div class="bristle"></div></div>';
    entities.appendChild(br);
    const r=pad.getBoundingClientRect();
    q.bounds={w:r.width,h:r.height};
    q.broom={x:r.width*0.5,y:r.height*0.7,vx:0,vy:0};
    q.broomEl=br;
  }
  function ensureBall(){
    if(q.ballEl) return;
    const b=document.createElement('div'); b.className='ball';
    entities.appendChild(b);
    const r=pad.getBoundingClientRect();
    q.ball={x:r.width*0.5, y:r.height*0.4, vx:0, vy:0, vis:false};
    q.ballEl=b;
  }
  function setArrow(key, on){
    if(key==='ArrowLeft') q.keys.Left=on;
    if(key==='ArrowRight') q.keys.Right=on;
    if(key==='ArrowUp') q.keys.Up=on;
    if(key==='ArrowDown') q.keys.Down=on;
    if(on){ showBall(); }
  }
  function anyArrowDown(){ return q.keys.Left||q.keys.Right||q.keys.Up||q.keys.Down; }
  function showBall(){ if(!q.ballEl) return; q.ball.vis=true; q.ballEl.style.opacity='1'; }
  function hideBall(){ if(!q.ballEl) return; q.ball.vis=false; q.ballEl.style.opacity='0'; }
  function broomLoop(){
    if(!q.run) return;
    const r=pad.getBoundingClientRect();
    q.bounds.w=r.width; q.bounds.h=r.height;

    // broom physics by arrow keys
    const acc=0.9, maxV=10, fr=0.90;
    let ax=0, ay=0;
    if(q.keys.Left) ax-=acc;
    if(q.keys.Right) ax+=acc;
    if(q.keys.Up) ay-=acc;
    if(q.keys.Down) ay+=acc;
    q.broom.vx = clamp(q.broom.vx + ax, -maxV, maxV);
    q.broom.vy = clamp(q.broom.vy + ay, -maxV, maxV);
    q.broom.vx *= fr; q.broom.vy *= fr;
    q.broom.x = clamp(q.broom.x + q.broom.vx, 20, q.bounds.w-20);
    q.broom.y = clamp(q.broom.y + q.broom.vy, 20, q.bounds.h-20);

    // ball autonomous wander + avoidance when visible
    if(q.ball.vis){
      q.ball.vx += (Math.random()*2-1)*0.4;
      q.ball.vy += (Math.random()*2-1)*0.4;
      const dx = q.ball.x - q.broom.x;
      const dy = q.ball.y - q.broom.y;
      const dist = Math.hypot(dx,dy);
      if(dist<160){
        const repel = (160 - dist)/160 * 1.6;
        q.ball.vx += (dx/dist||0)*repel;
        q.ball.vy += (dy/dist||0)*repel;
      }
      const bMax=7.5; q.ball.vx = clamp(q.ball.vx, -bMax, bMax); q.ball.vy = clamp(q.ball.vy, -bMax, bMax);
      q.ball.vx *= 0.96; q.ball.vy *= 0.96;
      q.ball.x = clamp(q.ball.x + q.ball.vx, 20, q.bounds.w-20);
      q.ball.y = clamp(q.ball.y + q.ball.vy, 20, q.bounds.h-20);
    }

    // visuals
    if(q.ballEl){
      q.ballEl.style.transform = `translate(${q.ball.x}px, ${q.ball.y}px)`;
    }
    if(q.broomEl){
      const ang = Math.atan2(q.broom.vy, q.broom.vx) || Math.atan2(q.ball.y - q.broom.y, q.ball.x - q.broom.x);
      q.broomEl.style.transform = `translate(${q.broom.x}px, ${q.broom.y}px) rotate(${ang}rad)`;
    }

    requestAnimationFrame(broomLoop);
  }

  /* =======================
     Marauder Map ( ? ) — oriented footprints
     ======================= */
  function spawnFootprints(){
    const trails = 6 + Math.floor(Math.random()*6);
    const r=pad.getBoundingClientRect();
    for(let t=0;t<trails;t++){
      let x = 30+Math.random()*(r.width-60);
      let y = 30+Math.random()*(r.height-60);
      const steps = 8 + Math.floor(Math.random()*10);
      let ang = Math.random()*Math.PI*2;

      for(let i=0;i<steps;i++){
        setTimeout(()=>{
          const stepLen = 16 + Math.random()*22;
          ang += (Math.random()-.5)*0.5;
          x = clamp(x + Math.cos(ang)*stepLen, 16, r.width-16);
          y = clamp(y + Math.sin(ang)*stepLen, 16, r.height-16);
          makeFootpad(x, y, ang, i%2===0);
          sfx('map', 1);
        }, i*80 + t*60);
      }
    }
  }
  function makeFootpad(x, y, ang, left=true){
    const g=document.createElement('div'); g.className='footpad';
    g.style.left=x+'px'; g.style.top=y+'px';
    g.style.transform=`translate(-50%,-50%) rotate(${ang + (left?0.08:-0.08)}rad)`;

    const sole=document.createElement('div'); sole.className='sole';
    sole.style.left='-6px'; sole.style.top='-9px';
    g.appendChild(sole);

    const toeSizes=[6,5,4,4,3];
    const toeOffsets=[-10,-12,-13,-12,-10];
    for(let i=0;i<5;i++){
      const toe=document.createElement('div'); toe.className='toe';
      const s=toeSizes[i]; toe.style.width=s+'px'; toe.style.height=s+'px';
      const spread = (i-2)*3.2 + (left?-0.8:0.8);
      toe.style.left= (spread-2) + 'px';
      toe.style.top = toeOffsets[i] + 'px';
      g.appendChild(toe);
    }

    pad.appendChild(g);
    g.animate([{opacity:0},{opacity:.95,offset:.25},{opacity:0}],{duration:1600,fill:'forwards'});
    setTimeout(()=>g.remove(), 1650);
  }

})();
</script>
</body>
</html>

