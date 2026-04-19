<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Anas Mahmoud</title>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;700;900&family=Playfair+Display:ital,wght@1,400;1,700&family=Fira+Code:wght@300;400&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}

:root{
  --bg: #0d0f1a;
  --violet: #7c3aed;
  --indigo: #4f46e5;
  --pink: #ec4899;
  --teal: #14b8a6;
  --amber: #f59e0b;
  --white: #f8fafc;
  --muted: rgba(248,250,252,0.5);
  --card: rgba(255,255,255,0.05);
  --border: rgba(255,255,255,0.1);
}

html,body{width:100%;height:100%;overflow:hidden;background:var(--bg);}

/* ── ANIMATED MESH BACKGROUND ── */
.mesh{
  position:fixed;inset:0;z-index:0;
  background:
    radial-gradient(ellipse 70% 60% at 15% 20%, rgba(124,58,237,0.4) 0%, transparent 55%),
    radial-gradient(ellipse 55% 55% at 85% 75%, rgba(20,184,166,0.35) 0%, transparent 55%),
    radial-gradient(ellipse 50% 50% at 80% 15%, rgba(236,72,153,0.28) 0%, transparent 55%),
    radial-gradient(ellipse 60% 40% at 50% 100%, rgba(79,70,229,0.3) 0%, transparent 60%),
    radial-gradient(ellipse 40% 40% at 10% 80%, rgba(245,158,11,0.15) 0%, transparent 50%);
  animation: meshShift 12s ease-in-out infinite alternate;
}
@keyframes meshShift{
  0%  {filter:hue-rotate(0deg) brightness(1);}
  100%{filter:hue-rotate(18deg) brightness(1.08);}
}

/* ── NOISE TEXTURE ── */
.noise{
  position:fixed;inset:0;z-index:1;pointer-events:none;opacity:.04;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  background-size:180px;
}

/* ── FLOATING ORBS ── */
.orb{position:fixed;border-radius:50%;filter:blur(90px);z-index:1;pointer-events:none;}
.o1{width:500px;height:500px;background:rgba(124,58,237,.22);top:-120px;left:-80px;animation:floatA 14s ease-in-out infinite;}
.o2{width:400px;height:400px;background:rgba(20,184,166,.2);bottom:-100px;right:-60px;animation:floatA 11s ease-in-out infinite reverse;}
.o3{width:280px;height:280px;background:rgba(236,72,153,.18);top:30%;right:5%;animation:floatB 9s ease-in-out infinite;}
@keyframes floatA{0%,100%{transform:translateY(0);}50%{transform:translateY(-30px);}}
@keyframes floatB{0%,100%{transform:translateY(0) scale(1);}50%{transform:translateY(20px) scale(1.07);}}

/* ── GRID ── */
.grid{
  position:fixed;inset:0;z-index:2;pointer-events:none;
  background-image:
    linear-gradient(rgba(255,255,255,.032) 1px,transparent 1px),
    linear-gradient(90deg,rgba(255,255,255,.032) 1px,transparent 1px);
  background-size:72px 72px;
}

/* ── VIGNETTE ── */
.vig{
  position:fixed;inset:0;z-index:3;pointer-events:none;
  background:radial-gradient(ellipse 90% 90% at 50% 50%,transparent 45%,rgba(13,15,26,.65) 100%);
}

/* ── STAGE ── */
.stage{
  position:fixed;inset:0;z-index:20;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  padding:40px 32px;
}

/* ── LOCATION PILL ── */
.location{
  display:flex;align-items:center;gap:7px;
  padding:6px 18px;border-radius:40px;
  border:1px solid rgba(20,184,166,.35);
  background:rgba(20,184,166,.08);
  margin-bottom:28px;
  opacity:0;animation:up .6s cubic-bezier(.22,1,.36,1) forwards .1s;
}
.loc-dot{
  width:7px;height:7px;border-radius:50%;
  background:var(--teal);
  box-shadow:0 0 8px var(--teal);
  animation:blink 2s ease-in-out infinite;
}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:.4;}}
.loc-text{
  font-family:'Fira Code',monospace;
  font-size:11px;font-weight:300;letter-spacing:.22em;text-transform:uppercase;
  color:rgba(20,184,166,.85);
}

/* ── NAME ── */
.name-wrap{
  text-align:center;margin-bottom:10px;
  opacity:0;animation:up .8s cubic-bezier(.22,1,.36,1) forwards .35s;
}
.first{
  display:block;
  font-family:'Outfit',sans-serif;font-weight:900;
  font-size:clamp(64px,10vw,130px);
  letter-spacing:-.02em;line-height:1;
  color:var(--white);
  text-shadow:0 0 80px rgba(124,58,237,.4),0 2px 40px rgba(0,0,0,.5);
}
.last{
  display:block;
  font-family:'Outfit',sans-serif;font-weight:300;
  font-size:clamp(38px,6vw,78px);
  letter-spacing:.18em;line-height:1.1;
  background:linear-gradient(100deg,#a78bfa,#ec4899,#14b8a6);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-clip:text;
  filter:drop-shadow(0 0 24px rgba(167,139,250,.4));
  background-size:200%;
  animation:gradShift 5s ease-in-out infinite alternate;
}
@keyframes gradShift{
  from{background-position:0%;}
  to{background-position:100%;}
}

/* ── ROLE ── */
.role{
  font-family:'Playfair Display',serif;
  font-style:italic;font-weight:400;
  font-size:clamp(17px,2.2vw,26px);
  letter-spacing:.06em;
  color:rgba(248,250,252,.62);
  margin-bottom:36px;
  opacity:0;animation:up .6s cubic-bezier(.22,1,.36,1) forwards .6s;
}

/* ── QUOTE CARD ── */
.quote-card{
  position:relative;
  padding:18px 32px;
  border-radius:14px;
  border:1px solid var(--border);
  background:var(--card);
  backdrop-filter:blur(16px);
  -webkit-backdrop-filter:blur(16px);
  max-width:620px;text-align:center;
  margin-bottom:36px;
  overflow:hidden;
  opacity:0;animation:up .7s cubic-bezier(.22,1,.36,1) forwards .8s;
}
.quote-card::before{
  content:'';position:absolute;inset:0;border-radius:14px;
  background:linear-gradient(135deg,rgba(124,58,237,.12),rgba(20,184,166,.06));
  pointer-events:none;
}
/* animated border glow */
.quote-card::after{
  content:'';position:absolute;inset:-1px;border-radius:14px;z-index:-1;
  background:linear-gradient(135deg,rgba(124,58,237,.5),rgba(236,72,153,.4),rgba(20,184,166,.5));
  opacity:.5;
  animation:borderGlow 4s ease-in-out infinite;
}
@keyframes borderGlow{
  0%,100%{opacity:.3;}
  50%{opacity:.7;}
}
.quote-icon{
  font-size:20px;margin-bottom:6px;display:block;
  filter:drop-shadow(0 0 8px rgba(245,158,11,.6));
}
.quote-text{
  font-family:'Outfit',sans-serif;font-weight:300;
  font-size:clamp(13px,1.6vw,17px);
  letter-spacing:.04em;line-height:1.7;
  color:rgba(248,250,252,.8);
}
.quote-text em{
  font-style:normal;font-weight:600;
  background:linear-gradient(90deg,var(--amber),var(--pink));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-clip:text;
}

/* ── TOOLS ── */
.tools{
  display:flex;gap:12px;flex-wrap:wrap;justify-content:center;
  opacity:0;animation:up .7s cubic-bezier(.22,1,.36,1) forwards 1.05s;
}
.tool{
  display:flex;align-items:center;gap:8px;
  padding:10px 20px;border-radius:12px;
  border:1px solid var(--border);
  background:var(--card);
  backdrop-filter:blur(10px);
  transition:transform .25s,border-color .25s,box-shadow .25s;
  position:relative;overflow:hidden;
}
.tool::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,var(--c1),var(--c2));
  opacity:0;transition:opacity .25s;
}
.tool:hover{transform:translateY(-5px) scale(1.04);}
.tool:hover::before{opacity:.12;}
.tool:hover{border-color:rgba(255,255,255,.25);box-shadow:0 12px 40px rgba(0,0,0,.35);}

.tool-bi  {--c1:#7c3aed;--c2:#ec4899;}
.tool-sql {--c1:#4f46e5;--c2:#14b8a6;}
.tool-xl  {--c1:#14b8a6;--c2:#22d3ee;}
.tool-ss  {--c1:#f59e0b;--c2:#ef4444;}

.t-icon{font-size:18px;position:relative;z-index:1;}
.t-name{
  font-family:'Outfit',sans-serif;font-weight:600;font-size:13px;
  letter-spacing:.05em;color:var(--white);
  position:relative;z-index:1;
}

/* ── BOTTOM STRIP ── */
.strip{
  position:fixed;bottom:0;left:0;right:0;z-index:25;
  height:3px;
  background:linear-gradient(90deg,var(--violet),var(--pink),var(--teal),var(--amber),var(--violet));
  background-size:300%;
  animation:stripMove 4s linear infinite;
}
@keyframes stripMove{
  from{background-position:0%;}
  to{background-position:300%;}
}

/* ── TOP STRIP ── */
.strip-top{
  position:fixed;top:0;left:0;right:0;z-index:25;
  height:3px;
  background:linear-gradient(90deg,var(--teal),var(--indigo),var(--pink),var(--amber),var(--teal));
  background-size:300%;
  animation:stripMove 6s linear infinite reverse;
}

/* ── CORNER MARKS ── */
.cm{position:fixed;z-index:30;width:22px;height:22px;border-style:solid;opacity:0;animation:fadeIn .5s ease forwards 1.5s;}
.cm-tl{top:16px;left:16px;border-width:2px 0 0 2px;border-color:rgba(167,139,250,.5);}
.cm-tr{top:16px;right:16px;border-width:2px 2px 0 0;border-color:rgba(167,139,250,.5);}
.cm-bl{bottom:16px;left:16px;border-width:0 0 2px 2px;border-color:rgba(20,184,166,.5);}
.cm-br{bottom:16px;right:16px;border-width:0 2px 2px 0;border-color:rgba(20,184,166,.5);}

/* ── SHARED ── */
@keyframes up{
  from{opacity:0;transform:translateY(20px);}
  to{opacity:1;transform:translateY(0);}
}
@keyframes fadeIn{to{opacity:1;}}

/* ── FLOATING PARTICLES ── */
.pt{position:fixed;border-radius:50%;pointer-events:none;z-index:4;animation:ptRise linear infinite;}
@keyframes ptRise{
  0%{opacity:0;transform:translateY(0) scale(1);}
  10%{opacity:.8;}
  90%{opacity:.2;}
  100%{opacity:0;transform:translateY(-100vh) scale(.3);}
}
</style>
</head>
<body>

<div class="mesh"></div>
<div class="noise"></div>
<div class="orb o1"></div>
<div class="orb o2"></div>
<div class="orb o3"></div>
<div class="grid"></div>
<div class="vig"></div>

<div class="strip-top"></div>
<div class="strip"></div>

<div class="cm cm-tl"></div>
<div class="cm cm-tr"></div>
<div class="cm cm-bl"></div>
<div class="cm cm-br"></div>

<div id="particles"></div>

<div class="stage">

  <div class="location">
    <div class="loc-dot"></div>
    <span class="loc-text">Riyadh, Saudi Arabia</span>
  </div>

  <div class="name-wrap">
    <span class="first">ANAS</span>
    <span class="last">MAHMOUD</span>
  </div>

  <div class="role">Data Analyst</div>

  <div class="quote-card">
    <span class="quote-icon">✦</span>
    <p class="quote-text">
      The data doesn't lie — it just waits for someone who knows<br>
      how to ask the right questions. I <em>turn raw numbers</em><br>
      into <em>decisions that move businesses forward.</em>
    </p>
  </div>

  <div class="tools">
    <div class="tool tool-bi"><span class="t-icon">📊</span><span class="t-name">Power BI</span></div>
    <div class="tool tool-sql"><span class="t-icon">🗄️</span><span class="t-name">SQL Server</span></div>
    <div class="tool tool-xl"><span class="t-icon">📗</span><span class="t-name">Excel</span></div>
    <div class="tool tool-ss"><span class="t-icon">⚙️</span><span class="t-name">SSAS</span></div>
  </div>

</div>

<script>
/* PARTICLES */
const pc = document.getElementById('particles');
const colors = ['#a78bfa','#ec4899','#14b8a6','#f59e0b','#818cf8'];
for(let i=0;i<30;i++){
  const p=document.createElement('div');
  p.className='pt';
  const s=Math.random()*3+1;
  const dur=10+Math.random()*16;
  p.style.cssText=`
    width:${s}px;height:${s}px;
    left:${Math.random()*100}%;
    bottom:-10px;
    background:${colors[Math.floor(Math.random()*colors.length)]};
    box-shadow:0 0 ${s*3}px ${colors[Math.floor(Math.random()*colors.length)]};
    animation-duration:${dur}s;
    animation-delay:${Math.random()*15}s;
  `;
  pc.appendChild(p);
}

/* SMOOTH PARALLAX */
let mx=0,my=0,tx=0,ty=0;
document.addEventListener('mousemove',e=>{
  mx=(e.clientX/window.innerWidth-.5)*2;
  my=(e.clientY/window.innerHeight-.5)*2;
});
(function loop(){
  tx+=(mx-tx)*.06; ty+=(my-ty)*.06;
  document.querySelector('.stage').style.transform=
    `perspective(1100px) rotateY(${tx*3.5}deg) rotateX(${-ty*2.5}deg)`;
  document.querySelector('.o1').style.transform=`translateY(${ty*20}px) translateX(${tx*15}px)`;
  document.querySelector('.o2').style.transform=`translateY(${-ty*18}px) translateX(${-tx*12}px)`;
  document.querySelector('.o3').style.transform=`translateY(${ty*10}px) scale(1)`;
  requestAnimationFrame(loop);
})();

/* LETTER ENTRANCE — first name */
window.addEventListener('load',()=>{
  const el=document.querySelector('.first');
  const letters=[...el.textContent];
  el.textContent='';
  letters.forEach((ch,i)=>{
    const s=document.createElement('span');
    s.textContent=ch;
    s.style.cssText=`display:inline-block;opacity:0;transform:translateY(28px) scale(.8);
      transition:opacity .5s ${.35+i*.08}s cubic-bezier(.22,1,.36,1),
                 transform .55s ${.35+i*.08}s cubic-bezier(.22,1,.36,1);`;
    el.appendChild(s);
  });
  setTimeout(()=>{
    el.querySelectorAll('span').forEach(s=>{
      s.style.opacity='1';
      s.style.transform='translateY(0) scale(1)';
    });
  },80);
});
</script>
</body>
</html>
