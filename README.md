<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Urooj – Developer Banner</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Sora:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root{--bg:#070614;--bg2:#0d0b2a;--cyan:#22d3ee;--violet:#a855f7;--pink:#f472b6;--text:#e9e7ff;--muted:#a9a4d6}
  *{box-sizing:border-box;margin:0}
  body{min-height:100vh;background:#04030c;display:grid;place-items:center;padding:16px;font-family:'Sora',system-ui,sans-serif}

  .banner{
    container-type:inline-size;position:relative;width:100%;max-width:1200px;aspect-ratio:16/8.2;min-height:300px;
    border-radius:22px;overflow:hidden;isolation:isolate;
    background:radial-gradient(120% 120% at 50% 0%,var(--bg2),var(--bg) 70%);
    box-shadow:0 0 0 1px rgba(168,85,247,.25),0 30px 80px -20px rgba(168,85,247,.45);
    display:grid;place-items:center;text-align:center;
  }

  /* glows (move with mouse) */
  .glow{position:absolute;border-radius:50%;filter:blur(70px);opacity:.5;z-index:-3;transition:transform .5s ease-out}
  .g1{width:44%;aspect-ratio:1;left:-8%;top:-30%;background:var(--cyan)}
  .g2{width:48%;aspect-ratio:1;right:-10%;top:-20%;background:var(--violet)}
  .g3{width:40%;aspect-ratio:1;left:30%;bottom:-48%;background:var(--pink);opacity:.35}
  .glow i{display:block;width:100%;height:100%;border-radius:50%;background:inherit;animation:drift 15s ease-in-out infinite alternate}
  @keyframes drift{to{transform:translate(14%,10%) scale(1.12)}}

  /* orbit rings behind name */
  .ring{position:absolute;left:50%;top:44%;border-radius:50%;border:1px solid rgba(168,85,247,.25);z-index:-2;transform:translate(-50%,-50%)}
  .r1{width:46cqw;height:22cqw;animation:spin 22s linear infinite}
  .r2{width:62cqw;height:30cqw;border-color:rgba(34,211,238,.18);animation:spin 34s linear infinite reverse}
  .ring::after{content:"";position:absolute;top:-4px;left:50%;width:8px;height:8px;border-radius:50%;background:var(--cyan);box-shadow:0 0 12px 2px var(--cyan)}
  .r2::after{background:var(--pink);box-shadow:0 0 12px 2px var(--pink)}
  @keyframes spin{to{transform:translate(-50%,-50%) rotate(360deg)}}

  /* moving grid floor */
  .grid{position:absolute;left:-25%;right:-25%;bottom:-2%;height:40%;z-index:-2;
    background:linear-gradient(rgba(168,85,247,.5) 1px,transparent 1px) 0 0/100% 32px,
               linear-gradient(90deg,rgba(34,211,238,.4) 1px,transparent 1px) 0 0/46px 100%;
    transform:perspective(380px) rotateX(62deg);transform-origin:50% 100%;
    -webkit-mask-image:linear-gradient(transparent,#000 70%);mask-image:linear-gradient(transparent,#000 70%);
    animation:scroll 3.2s linear infinite;opacity:.45}
  @keyframes scroll{to{background-position:0 32px,0 0}}

  /* floating symbols */
  .sym{position:absolute;z-index:-1;font-family:'Sora',monospace;font-weight:600;color:var(--c);opacity:.5;
    text-shadow:0 0 12px var(--c);left:var(--x);top:var(--y);font-size:var(--s);animation:bob var(--d) ease-in-out infinite alternate}
  @keyframes bob{to{transform:translateY(-14px) rotate(8deg);opacity:.85}}

  /* side code cards */
  .card{position:absolute;top:50%;width:21cqw;padding:1.3cqw 1.5cqw;text-align:left;border-radius:1.2cqw;
    background:rgba(14,11,40,.6);border:1px solid rgba(168,85,247,.35);backdrop-filter:blur(8px);
    font:400 1.05cqw/1.6 ui-monospace,'SF Mono',Menlo,Consolas,monospace;color:#cfd0ff;
    box-shadow:0 10px 40px -10px rgba(34,211,238,.35);transition:transform .5s ease-out}
  .card.left{left:3.5cqw;--ty:-50%;transform:translateY(-50%)}
  .card.right{right:3.5cqw;--ty:-50%;transform:translateY(-50%)}
  .dotsbar{display:flex;gap:.45cqw;margin-bottom:.9cqw}
  .dotsbar b{width:.8cqw;height:.8cqw;border-radius:50%;background:#ff6b8b}
  .dotsbar b:nth-child(2){background:#ffd166}.dotsbar b:nth-child(3){background:#4ade80}
  .card .ln{white-space:nowrap;overflow:hidden;opacity:0;max-width:0;animation:type .9s steps(26) forwards}
  .k{color:#c084fc}.f{color:#22d3ee}.s{color:#f9a8d4}.c{color:#7c7aa8}
  .card .ln:nth-of-type(1){animation-delay:2.6s}.card .ln:nth-of-type(2){animation-delay:3.4s}
  .card .ln:nth-of-type(3){animation-delay:4.2s}.card .ln:nth-of-type(4){animation-delay:5s}
  @keyframes type{from{opacity:1;max-width:0}to{opacity:1;max-width:100%}}
  .blink{display:inline-block;width:.5cqw;height:1.1cqw;background:var(--cyan);vertical-align:middle;animation:bl 1s steps(1) infinite}
  @keyframes bl{50%{opacity:0}}

  .content{display:flex;flex-direction:column;align-items:center;gap:1.5cqw;padding:0 3cqw}

  /* name: written from left to right with a glowing pen */
  .nameWrap{position:relative;display:inline-block}
  .name{
    font-family:'Pacifico','Brush Script MT',cursive;font-weight:400;font-size:12.5cqw;line-height:1.15;padding:0 .1em .1em;
    background:linear-gradient(100deg,var(--cyan),#7aa2ff 28%,var(--violet) 55%,var(--pink) 80%,var(--cyan));
    background-size:220% 100%;-webkit-background-clip:text;background-clip:text;color:transparent;
    filter:drop-shadow(0 0 1cqw rgba(168,85,247,.65)) drop-shadow(0 0 .3cqw rgba(34,211,238,.6));
    animation:write 2.2s cubic-bezier(.45,.05,.35,1) .3s both, flow 7s linear 2.5s infinite;
  }
  @keyframes write{from{clip-path:inset(-20% 100% -20% -5%)}to{clip-path:inset(-20% -5% -20% -5%)}}
  @keyframes flow{to{background-position:-220% 0}}
  .pen{position:absolute;top:12%;bottom:18%;left:0;width:.28cqw;border-radius:2px;background:#fff;
    box-shadow:0 0 .8cqw .3cqw var(--cyan),0 0 1.8cqw .6cqw var(--violet);
    animation:pen 2.2s cubic-bezier(.45,.05,.35,1) .3s both}
  @keyframes pen{0%{left:0;opacity:1}94%{opacity:1}100%{left:100%;opacity:0}}

  /* role typing line */
  .role{display:flex;align-items:center;gap:1.6cqw;opacity:0;animation:rise .7s ease 2.2s forwards}
  .role i{display:block;width:7cqw;height:2px;border-radius:2px;background:linear-gradient(90deg,transparent,var(--cyan));box-shadow:0 0 8px var(--cyan)}
  .role i:last-child{background:linear-gradient(90deg,var(--pink),transparent);box-shadow:0 0 8px var(--pink)}
  .role b{display:block;min-width:30cqw;font-weight:600;font-size:2.2cqw;letter-spacing:.32em;color:var(--text);text-shadow:0 0 14px rgba(168,85,247,.8);white-space:nowrap}
  .role .caret{display:inline-block;width:.22cqw;height:2cqw;background:var(--pink);margin-left:.3em;vertical-align:-.25cqw;animation:bl .9s steps(1) infinite}

  .skills{display:flex;gap:2cqw;align-items:center;opacity:0;animation:rise .8s ease 2.5s forwards}
  .skill{display:flex;align-items:center;gap:.8cqw;font-size:1.5cqw;color:var(--text);padding:.6cqw 1.3cqw;border-radius:99px;
    background:rgba(255,255,255,.04);border:1px solid rgba(168,85,247,.35);backdrop-filter:blur(6px);
    transition:transform .25s,border-color .25s,box-shadow .25s}
  .skill:hover{transform:translateY(-3px);border-color:var(--cyan);box-shadow:0 0 18px rgba(34,211,238,.35)}
  .skill svg{width:2.1cqw;height:2.1cqw;flex:none}
  .ai{display:grid;place-items:center;width:2.1cqw;height:2.1cqw;border-radius:.5cqw;border:1.5px solid var(--pink);color:var(--pink);font-size:1cqw;font-weight:600}

  .tag{min-height:2.4cqw;font-weight:300;font-style:italic;font-size:1.55cqw;color:var(--muted);letter-spacing:.04em;opacity:0;animation:rise .6s ease 2.8s forwards}
  .tag::before,.tag::after{content:"";display:inline-block;width:4cqw;height:1px;vertical-align:middle;margin:0 1cqw;background:linear-gradient(90deg,transparent,rgba(169,164,214,.7))}
  .tag::after{transform:scaleX(-1)}

  .social{display:flex;gap:1.2cqw;opacity:0;animation:rise .8s ease 3.2s forwards}
  .social a{display:grid;place-items:center;width:3.2cqw;height:3.2cqw;border-radius:50%;color:var(--text);
    background:rgba(255,255,255,.05);border:1px solid rgba(168,85,247,.4);transition:transform .25s,box-shadow .25s,color .25s}
  .social a:hover{transform:translateY(-3px) scale(1.08);color:var(--cyan);box-shadow:0 0 18px rgba(34,211,238,.5)}
  .social svg{width:1.5cqw;height:1.5cqw}
  a:focus-visible{outline:2px solid var(--cyan);outline-offset:3px}

  @keyframes rise{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:none}}

  @container (max-width:820px){.card{display:none}}
  @container (max-width:560px){
    .banner{aspect-ratio:auto}
    .content{padding:6cqw 3cqw;gap:3cqw}
    .name{font-size:23cqw}
    .role b{font-size:3.8cqw;min-width:50cqw}.role i{width:6cqw}.role .caret{height:3.6cqw}
    .skills{flex-wrap:wrap;justify-content:center;gap:2.5cqw}
    .skill{font-size:3.1cqw;padding:1.3cqw 3cqw}.skill svg,.ai{width:4.2cqw;height:4.2cqw}.ai{font-size:2cqw}
    .tag{font-size:3.1cqw;min-height:4cqw}
    .social a{width:8cqw;height:8cqw}.social svg{width:4cqw;height:4cqw}
    .ring{display:none}
  }
  @media (prefers-reduced-motion:reduce){
    *,*::before,*::after{animation:none!important;transition:none!important}
    .role,.skills,.tag,.social,.card .ln{opacity:1!important;max-width:100%!important}
    .pen{display:none}
  }
</style>
</head>
<body>
  <header class="banner" id="banner" aria-label="Urooj, Developer. Turning ideas into real solutions.">
    <div class="glow g1" data-m="30"><i></i></div>
    <div class="glow g2" data-m="-24"><i></i></div>
    <div class="glow g3" data-m="18"><i></i></div>
    <div class="ring r1"></div><div class="ring r2"></div>
    <div class="grid"></div>

    <span class="sym" style="--x:9%;--y:12%;--s:2.6cqw;--c:#22d3ee;--d:4s">&lt;/&gt;</span>
    <span class="sym" style="--x:88%;--y:14%;--s:2.4cqw;--c:#f472b6;--d:5s">{ }</span>
    <span class="sym" style="--x:6%;--y:80%;--s:2cqw;--c:#a855f7;--d:4.5s">✦</span>
    <span class="sym" style="--x:91%;--y:78%;--s:2.4cqw;--c:#22d3ee;--d:5.5s">AI</span>

    <aside class="card left" data-m="-10" aria-hidden="true">
      <div class="dotsbar"><b></b><b></b><b></b></div>
      <div class="ln"><span class="k">const</span> <span class="f">me</span> = {</div>
      <div class="ln">&nbsp;&nbsp;dream: <span class="s">"Developer"</span>,</div>
      <div class="ln">&nbsp;&nbsp;goal: <span class="s">"Build amazing"</span></div>
      <div class="ln">}<span class="blink"></span></div>
    </aside>

    <aside class="card right" data-m="10" aria-hidden="true">
      <div class="dotsbar"><b></b><b></b><b></b></div>
      <div class="ln"><span class="c"># keep going</span></div>
      <div class="ln"><span class="k">def</span> <span class="f">future</span>():</div>
      <div class="ln">&nbsp;&nbsp;<span class="k">print</span>(<span class="s">"You can do it!"</span>)</div>
      <div class="ln"><span class="c">&gt;&gt;&gt;</span> future()<span class="blink"></span></div>
    </aside>

    <div class="content">
      <div class="nameWrap"><h1 class="name">Urooj</h1><span class="pen" aria-hidden="true"></span></div>

      <div class="role"><i></i><b><span id="role"></span><span class="caret"></span></b><i></i></div>

      <div class="skills">
        <div class="skill">
          <svg viewBox="0 0 32 32" aria-hidden="true"><path fill="#4da3ff" d="M15.9 2C9 2 9.4 5 9.4 5v3.1H16v1H6.7S2 8.6 2 16s4.1 7.1 4.1 7.1h2.4v-3.4s-.1-4.1 4-4.1h6.5s3.9.1 3.9-3.8V5.9S23.5 2 15.9 2zm-3.6 2.2a1.3 1.3 0 110 2.6 1.3 1.3 0 010-2.6z"/><path fill="#ffd43b" d="M16.1 30c6.9 0 6.5-3 6.5-3v-3.1H16v-1h9.3S30 23.4 30 16s-4.1-7.1-4.1-7.1h-2.4v3.4s.1 4.1-4 4.1h-6.5s-3.9-.1-3.9 3.8v6S8.5 30 16.1 30zm3.6-2.2a1.3 1.3 0 110-2.6 1.3 1.3 0 010 2.6z"/></svg>
          Python
        </div>
        <div class="skill">
          <svg viewBox="0 0 32 32" fill="none" stroke="#22d3ee" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M10 8l-7 8 7 8M22 8l7 8-7 8M18.5 5l-5 22"/></svg>
          Full Stack
        </div>
        <div class="skill"><span class="ai" aria-hidden="true">AI</span>AI</div>
      </div>

      <p class="tag"><span id="tag"></span></p>

      <!-- apni links yahan daalein -->
      <nav class="social" aria-label="Social links">
        <a href="#" aria-label="GitHub"><svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 .5a11.5 11.5 0 00-3.64 22.41c.58.1.79-.25.79-.56v-2c-3.2.7-3.88-1.37-3.88-1.37-.52-1.33-1.28-1.68-1.28-1.68-1.04-.71.08-.7.08-.7 1.15.08 1.76 1.19 1.76 1.19 1.03 1.76 2.69 1.25 3.35.96.1-.75.4-1.25.73-1.54-2.55-.29-5.24-1.28-5.24-5.69 0-1.26.45-2.28 1.19-3.09-.12-.29-.52-1.46.11-3.05 0 0 .97-.31 3.17 1.18a10.9 10.9 0 015.78 0c2.2-1.49 3.17-1.18 3.17-1.18.63 1.59.23 2.76.11 3.05.74.81 1.19 1.83 1.19 3.09 0 4.42-2.69 5.39-5.25 5.68.41.36.78 1.06.78 2.14v3.17c0 .31.21.67.8.56A11.5 11.5 0 0012 .5z"/></svg></a>
        <a href="#" aria-label="LinkedIn"><svg viewBox="0 0 24 24" fill="currentColor"><path d="M4.98 3.5a2.5 2.5 0 11-.01 5 2.5 2.5 0 01.01-5zM3 9.75h4V21H3zM9.75 9.75h3.83v1.54h.05c.53-1 1.84-2.07 3.78-2.07 4.04 0 4.79 2.66 4.79 6.12V21h-4v-4.95c0-1.18-.02-2.7-1.65-2.7-1.65 0-1.9 1.29-1.9 2.62V21h-4z"/></svg></a>
        <a href="#" aria-label="Email"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="M3 7l9 6 9-6"/></svg></a>
      </nav>
    </div>
  </header>

<script>
(function(){
  var reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;
  var roleEl = document.getElementById('role'), tagEl = document.getElementById('tag');
  var roles = ['DEVELOPER','FULL STACK DEV','AI BUILDER'];
  var tagline = 'Turning Ideas Into Real Solutions';

  if (reduce){ roleEl.textContent = roles[0]; tagEl.textContent = tagline; return; }

  // tagline types once
  var ti = 0;
  function typeTag(){ if (ti <= tagline.length){ tagEl.textContent = tagline.slice(0, ti++); setTimeout(typeTag, 55); } }
  setTimeout(typeTag, 3000);

  // role types, holds, deletes, next
  var ri = 0, ci = 0, del = false;
  function loop(){
    var word = roles[ri];
    roleEl.textContent = word.slice(0, ci);
    var wait = del ? 40 : 95;
    if (!del && ci === word.length){ del = true; wait = 1700; }
    else if (del && ci === 0){ del = false; ri = (ri + 1) % roles.length; wait = 350; }
    else { ci += del ? -1 : 1; }
    setTimeout(loop, wait);
  }
  setTimeout(loop, 2400);

  // gentle mouse parallax
  var b = document.getElementById('banner');
  b.addEventListener('mousemove', function(e){
    var r = b.getBoundingClientRect(), x = (e.clientX - r.left)/r.width - .5, y = (e.clientY - r.top)/r.height - .5;
    b.querySelectorAll('[data-m]').forEach(function(el){
      var m = +el.dataset.m, base = el.classList.contains('card') ? 'translateY(-50%) ' : '';
      el.style.transform = base + 'translate(' + (x*m) + 'px,' + (y*m) + 'px)';
    });
  });
  b.addEventListener('mouseleave', function(){
    b.querySelectorAll('[data-m]').forEach(function(el){
      el.style.transform = el.classList.contains('card') ? 'translateY(-50%)' : '';
    });
  });
})();
</script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Urooj – Developer Banner</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Sora:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root{--bg:#070614;--bg2:#0d0b2a;--cyan:#22d3ee;--violet:#a855f7;--pink:#f472b6;--text:#e9e7ff;--muted:#a9a4d6}
  *{box-sizing:border-box;margin:0}
  body{min-height:100vh;background:#04030c;display:grid;place-items:center;padding:16px;font-family:'Sora',system-ui,sans-serif}

  .banner{
    container-type:inline-size;position:relative;width:100%;max-width:1200px;aspect-ratio:16/8.2;min-height:300px;
    border-radius:22px;overflow:hidden;isolation:isolate;
    background:radial-gradient(120% 120% at 50% 0%,var(--bg2),var(--bg) 70%);
    box-shadow:0 0 0 1px rgba(168,85,247,.25),0 30px 80px -20px rgba(168,85,247,.45);
    display:grid;place-items:center;text-align:center;
  }

  /* glows (move with mouse) */
  .glow{position:absolute;border-radius:50%;filter:blur(70px);opacity:.5;z-index:-3;transition:transform .5s ease-out}
  .g1{width:44%;aspect-ratio:1;left:-8%;top:-30%;background:var(--cyan)}
  .g2{width:48%;aspect-ratio:1;right:-10%;top:-20%;background:var(--violet)}
  .g3{width:40%;aspect-ratio:1;left:30%;bottom:-48%;background:var(--pink);opacity:.35}
  .glow i{display:block;width:100%;height:100%;border-radius:50%;background:inherit;animation:drift 15s ease-in-out infinite alternate}
  @keyframes drift{to{transform:translate(14%,10%) scale(1.12)}}

  /* orbit rings behind name */
  .ring{position:absolute;left:50%;top:44%;border-radius:50%;border:1px solid rgba(168,85,247,.25);z-index:-2;transform:translate(-50%,-50%)}
  .r1{width:46cqw;height:22cqw;animation:spin 22s linear infinite}
  .r2{width:62cqw;height:30cqw;border-color:rgba(34,211,238,.18);animation:spin 34s linear infinite reverse}
  .ring::after{content:"";position:absolute;top:-4px;left:50%;width:8px;height:8px;border-radius:50%;background:var(--cyan);box-shadow:0 0 12px 2px var(--cyan)}
  .r2::after{background:var(--pink);box-shadow:0 0 12px 2px var(--pink)}
  @keyframes spin{to{transform:translate(-50%,-50%) rotate(360deg)}}

  /* moving grid floor */
  .grid{position:absolute;left:-25%;right:-25%;bottom:-2%;height:40%;z-index:-2;
    background:linear-gradient(rgba(168,85,247,.5) 1px,transparent 1px) 0 0/100% 32px,
               linear-gradient(90deg,rgba(34,211,238,.4) 1px,transparent 1px) 0 0/46px 100%;
    transform:perspective(380px) rotateX(62deg);transform-origin:50% 100%;
    -webkit-mask-image:linear-gradient(transparent,#000 70%);mask-image:linear-gradient(transparent,#000 70%);
    animation:scroll 3.2s linear infinite;opacity:.45}
  @keyframes scroll{to{background-position:0 32px,0 0}}

  /* floating symbols */
  .sym{position:absolute;z-index:-1;font-family:'Sora',monospace;font-weight:600;color:var(--c);opacity:.5;
    text-shadow:0 0 12px var(--c);left:var(--x);top:var(--y);font-size:var(--s);animation:bob var(--d) ease-in-out infinite alternate}
  @keyframes bob{to{transform:translateY(-14px) rotate(8deg);opacity:.85}}

  /* side code cards */
  .card{position:absolute;top:50%;width:21cqw;padding:1.3cqw 1.5cqw;text-align:left;border-radius:1.2cqw;
    background:rgba(14,11,40,.6);border:1px solid rgba(168,85,247,.35);backdrop-filter:blur(8px);
    font:400 1.05cqw/1.6 ui-monospace,'SF Mono',Menlo,Consolas,monospace;color:#cfd0ff;
    box-shadow:0 10px 40px -10px rgba(34,211,238,.35);transition:transform .5s ease-out}
  .card.left{left:3.5cqw;--ty:-50%;transform:translateY(-50%)}
  .card.right{right:3.5cqw;--ty:-50%;transform:translateY(-50%)}
  .dotsbar{display:flex;gap:.45cqw;margin-bottom:.9cqw}
  .dotsbar b{width:.8cqw;height:.8cqw;border-radius:50%;background:#ff6b8b}
  .dotsbar b:nth-child(2){background:#ffd166}.dotsbar b:nth-child(3){background:#4ade80}
  .card .ln{white-space:nowrap;overflow:hidden;opacity:0;max-width:0;animation:type .9s steps(26) forwards}
  .k{color:#c084fc}.f{color:#22d3ee}.s{color:#f9a8d4}.c{color:#7c7aa8}
  .card .ln:nth-of-type(1){animation-delay:2.6s}.card .ln:nth-of-type(2){animation-delay:3.4s}
  .card .ln:nth-of-type(3){animation-delay:4.2s}.card .ln:nth-of-type(4){animation-delay:5s}
  @keyframes type{from{opacity:1;max-width:0}to{opacity:1;max-width:100%}}
  .blink{display:inline-block;width:.5cqw;height:1.1cqw;background:var(--cyan);vertical-align:middle;animation:bl 1s steps(1) infinite}
  @keyframes bl{50%{opacity:0}}

  .content{display:flex;flex-direction:column;align-items:center;gap:1.5cqw;padding:0 3cqw}

  /* name: written from left to right with a glowing pen */
  .nameWrap{position:relative;display:inline-block}
  .name{
    font-family:'Pacifico','Brush Script MT',cursive;font-weight:400;font-size:12.5cqw;line-height:1.15;padding:0 .1em .1em;
    background:linear-gradient(100deg,var(--cyan),#7aa2ff 28%,var(--violet) 55%,var(--pink) 80%,var(--cyan));
    background-size:220% 100%;-webkit-background-clip:text;background-clip:text;color:transparent;
    filter:drop-shadow(0 0 1cqw rgba(168,85,247,.65)) drop-shadow(0 0 .3cqw rgba(34,211,238,.6));
    animation:write 2.2s cubic-bezier(.45,.05,.35,1) .3s both, flow 7s linear 2.5s infinite;
  }
  @keyframes write{from{clip-path:inset(-20% 100% -20% -5%)}to{clip-path:inset(-20% -5% -20% -5%)}}
  @keyframes flow{to{background-position:-220% 0}}
  .pen{position:absolute;top:12%;bottom:18%;left:0;width:.28cqw;border-radius:2px;background:#fff;
    box-shadow:0 0 .8cqw .3cqw var(--cyan),0 0 1.8cqw .6cqw var(--violet);
    animation:pen 2.2s cubic-bezier(.45,.05,.35,1) .3s both}
  @keyframes pen{0%{left:0;opacity:1}94%{opacity:1}100%{left:100%;opacity:0}}

  /* role typing line */
  .role{display:flex;align-items:center;gap:1.6cqw;opacity:0;animation:rise .7s ease 2.2s forwards}
  .role i{display:block;width:7cqw;height:2px;border-radius:2px;background:linear-gradient(90deg,transparent,var(--cyan));box-shadow:0 0 8px var(--cyan)}
  .role i:last-child{background:linear-gradient(90deg,var(--pink),transparent);box-shadow:0 0 8px var(--pink)}
  .role b{display:block;min-width:30cqw;font-weight:600;font-size:2.2cqw;letter-spacing:.32em;color:var(--text);text-shadow:0 0 14px rgba(168,85,247,.8);white-space:nowrap}
  .role .caret{display:inline-block;width:.22cqw;height:2cqw;background:var(--pink);margin-left:.3em;vertical-align:-.25cqw;animation:bl .9s steps(1) infinite}

  .skills{display:flex;gap:2cqw;align-items:center;opacity:0;animation:rise .8s ease 2.5s forwards}
  .skill{display:flex;align-items:center;gap:.8cqw;font-size:1.5cqw;color:var(--text);padding:.6cqw 1.3cqw;border-radius:99px;
    background:rgba(255,255,255,.04);border:1px solid rgba(168,85,247,.35);backdrop-filter:blur(6px);
    transition:transform .25s,border-color .25s,box-shadow .25s}
  .skill:hover{transform:translateY(-3px);border-color:var(--cyan);box-shadow:0 0 18px rgba(34,211,238,.35)}
  .skill svg{width:2.1cqw;height:2.1cqw;flex:none}
  .ai{display:grid;place-items:center;width:2.1cqw;height:2.1cqw;border-radius:.5cqw;border:1.5px solid var(--pink);color:var(--pink);font-size:1cqw;font-weight:600}

  .tag{min-height:2.4cqw;font-weight:300;font-style:italic;font-size:1.55cqw;color:var(--muted);letter-spacing:.04em;opacity:0;animation:rise .6s ease 2.8s forwards}
  .tag::before,.tag::after{content:"";display:inline-block;width:4cqw;height:1px;vertical-align:middle;margin:0 1cqw;background:linear-gradient(90deg,transparent,rgba(169,164,214,.7))}
  .tag::after{transform:scaleX(-1)}

  .social{display:flex;gap:1.2cqw;opacity:0;animation:rise .8s ease 3.2s forwards}
  .social a{display:grid;place-items:center;width:3.2cqw;height:3.2cqw;border-radius:50%;color:var(--text);
    background:rgba(255,255,255,.05);border:1px solid rgba(168,85,247,.4);transition:transform .25s,box-shadow .25s,color .25s}
  .social a:hover{transform:translateY(-3px) scale(1.08);color:var(--cyan);box-shadow:0 0 18px rgba(34,211,238,.5)}
  .social svg{width:1.5cqw;height:1.5cqw}
  a:focus-visible{outline:2px solid var(--cyan);outline-offset:3px}

  @keyframes rise{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:none}}

  @container (max-width:820px){.card{display:none}}
  @container (max-width:560px){
    .banner{aspect-ratio:auto}
    .content{padding:6cqw 3cqw;gap:3cqw}
    .name{font-size:23cqw}
    .role b{font-size:3.8cqw;min-width:50cqw}.role i{width:6cqw}.role .caret{height:3.6cqw}
    .skills{flex-wrap:wrap;justify-content:center;gap:2.5cqw}
    .skill{font-size:3.1cqw;padding:1.3cqw 3cqw}.skill svg,.ai{width:4.2cqw;height:4.2cqw}.ai{font-size:2cqw}
    .tag{font-size:3.1cqw;min-height:4cqw}
    .social a{width:8cqw;height:8cqw}.social svg{width:4cqw;height:4cqw}
    .ring{display:none}
  }
  @media (prefers-reduced-motion:reduce){
    *,*::before,*::after{animation:none!important;transition:none!important}
    .role,.skills,.tag,.social,.card .ln{opacity:1!important;max-width:100%!important}
    .pen{display:none}
  }
</style>
</head>
<body>
  <header class="banner" id="banner" aria-label="Urooj, Developer. Turning ideas into real solutions.">
    <div class="glow g1" data-m="30"><i></i></div>
    <div class="glow g2" data-m="-24"><i></i></div>
    <div class="glow g3" data-m="18"><i></i></div>
    <div class="ring r1"></div><div class="ring r2"></div>
    <div class="grid"></div>

    <span class="sym" style="--x:9%;--y:12%;--s:2.6cqw;--c:#22d3ee;--d:4s">&lt;/&gt;</span>
    <span class="sym" style="--x:88%;--y:14%;--s:2.4cqw;--c:#f472b6;--d:5s">{ }</span>
    <span class="sym" style="--x:6%;--y:80%;--s:2cqw;--c:#a855f7;--d:4.5s">✦</span>
    <span class="sym" style="--x:91%;--y:78%;--s:2.4cqw;--c:#22d3ee;--d:5.5s">AI</span>

    <aside class="card left" data-m="-10" aria-hidden="true">
      <div class="dotsbar"><b></b><b></b><b></b></div>
      <div class="ln"><span class="k">const</span> <span class="f">me</span> = {</div>
      <div class="ln">&nbsp;&nbsp;dream: <span class="s">"Developer"</span>,</div>
      <div class="ln">&nbsp;&nbsp;goal: <span class="s">"Build amazing"</span></div>
      <div class="ln">}<span class="blink"></span></div>
    </aside>

    <aside class="card right" data-m="10" aria-hidden="true">
      <div class="dotsbar"><b></b><b></b><b></b></div>
      <div class="ln"><span class="c"># keep going</span></div>
      <div class="ln"><span class="k">def</span> <span class="f">future</span>():</div>
      <div class="ln">&nbsp;&nbsp;<span class="k">print</span>(<span class="s">"You can do it!"</span>)</div>
      <div class="ln"><span class="c">&gt;&gt;&gt;</span> future()<span class="blink"></span></div>
    </aside>

    <div class="content">
      <div class="nameWrap"><h1 class="name">Urooj</h1><span class="pen" aria-hidden="true"></span></div>

      <div class="role"><i></i><b><span id="role"></span><span class="caret"></span></b><i></i></div>

      <div class="skills">
        <div class="skill">
          <svg viewBox="0 0 32 32" aria-hidden="true"><path fill="#4da3ff" d="M15.9 2C9 2 9.4 5 9.4 5v3.1H16v1H6.7S2 8.6 2 16s4.1 7.1 4.1 7.1h2.4v-3.4s-.1-4.1 4-4.1h6.5s3.9.1 3.9-3.8V5.9S23.5 2 15.9 2zm-3.6 2.2a1.3 1.3 0 110 2.6 1.3 1.3 0 010-2.6z"/><path fill="#ffd43b" d="M16.1 30c6.9 0 6.5-3 6.5-3v-3.1H16v-1h9.3S30 23.4 30 16s-4.1-7.1-4.1-7.1h-2.4v3.4s.1 4.1-4 4.1h-6.5s-3.9-.1-3.9 3.8v6S8.5 30 16.1 30zm3.6-2.2a1.3 1.3 0 110-2.6 1.3 1.3 0 010 2.6z"/></svg>
          Python
        </div>
        <div class="skill">
          <svg viewBox="0 0 32 32" fill="none" stroke="#22d3ee" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M10 8l-7 8 7 8M22 8l7 8-7 8M18.5 5l-5 22"/></svg>
          Full Stack
        </div>
        <div class="skill"><span class="ai" aria-hidden="true">AI</span>AI</div>
      </div>

      <p class="tag"><span id="tag"></span></p>

      <!-- apni links yahan daalein -->
      <nav class="social" aria-label="Social links">
        <a href="#" aria-label="GitHub"><svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 .5a11.5 11.5 0 00-3.64 22.41c.58.1.79-.25.79-.56v-2c-3.2.7-3.88-1.37-3.88-1.37-.52-1.33-1.28-1.68-1.28-1.68-1.04-.71.08-.7.08-.7 1.15.08 1.76 1.19 1.76 1.19 1.03 1.76 2.69 1.25 3.35.96.1-.75.4-1.25.73-1.54-2.55-.29-5.24-1.28-5.24-5.69 0-1.26.45-2.28 1.19-3.09-.12-.29-.52-1.46.11-3.05 0 0 .97-.31 3.17 1.18a10.9 10.9 0 015.78 0c2.2-1.49 3.17-1.18 3.17-1.18.63 1.59.23 2.76.11 3.05.74.81 1.19 1.83 1.19 3.09 0 4.42-2.69 5.39-5.25 5.68.41.36.78 1.06.78 2.14v3.17c0 .31.21.67.8.56A11.5 11.5 0 0012 .5z"/></svg></a>
        <a href="#" aria-label="LinkedIn"><svg viewBox="0 0 24 24" fill="currentColor"><path d="M4.98 3.5a2.5 2.5 0 11-.01 5 2.5 2.5 0 01.01-5zM3 9.75h4V21H3zM9.75 9.75h3.83v1.54h.05c.53-1 1.84-2.07 3.78-2.07 4.04 0 4.79 2.66 4.79 6.12V21h-4v-4.95c0-1.18-.02-2.7-1.65-2.7-1.65 0-1.9 1.29-1.9 2.62V21h-4z"/></svg></a>
        <a href="#" aria-label="Email"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="M3 7l9 6 9-6"/></svg></a>
      </nav>
    </div>
  </header>

<script>
(function(){
  var reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;
  var roleEl = document.getElementById('role'), tagEl = document.getElementById('tag');
  var roles = ['DEVELOPER','FULL STACK DEV','AI BUILDER'];
  var tagline = 'Turning Ideas Into Real Solutions';

  if (reduce){ roleEl.textContent = roles[0]; tagEl.textContent = tagline; return; }

  // tagline types once
  var ti = 0;
  function typeTag(){ if (ti <= tagline.length){ tagEl.textContent = tagline.slice(0, ti++); setTimeout(typeTag, 55); } }
  setTimeout(typeTag, 3000);

  // role types, holds, deletes, next
  var ri = 0, ci = 0, del = false;
  function loop(){
    var word = roles[ri];
    roleEl.textContent = word.slice(0, ci);
    var wait = del ? 40 : 95;
    if (!del && ci === word.length){ del = true; wait = 1700; }
    else if (del && ci === 0){ del = false; ri = (ri + 1) % roles.length; wait = 350; }
    else { ci += del ? -1 : 1; }
    setTimeout(loop, wait);
  }
  setTimeout(loop, 2400);

  // gentle mouse parallax
  var b = document.getElementById('banner');
  b.addEventListener('mousemove', function(e){
    var r = b.getBoundingClientRect(), x = (e.clientX - r.left)/r.width - .5, y = (e.clientY - r.top)/r.height - .5;
    b.querySelectorAll('[data-m]').forEach(function(el){
      var m = +el.dataset.m, base = el.classList.contains('card') ? 'translateY(-50%) ' : '';
      el.style.transform = base + 'translate(' + (x*m) + 'px,' + (y*m) + 'px)';
    });
  });
  b.addEventListener('mouseleave', function(){
    b.querySelectorAll('[data-m]').forEach(function(el){
      el.style.transform = el.classList.contains('card') ? 'translateY(-50%)' : '';
    });
  });
})();
</script>
</body>
</html>
