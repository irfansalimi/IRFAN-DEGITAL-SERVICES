<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>IRFAN DIGITAL SERVICES — Smart Tech for Schools & Coachings</title>
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Bricolage+Grotesque:opsz,wght@12..96,400;12..96,600;12..96,700;12..96,800&display=swap" rel="stylesheet">
<style>
/* ─── CSS VARIABLES ─────────────────────────────────── */
:root {
  --bg:    #C9DDF1;
  --bg2:   #B8D0E8;
  --teal:  #0F7B9A;
  --tealb: #139CBA;
  --amber: #D97706;
  --white: #FFFFFF;
  --off:   #EAF2F8;
  --muted: rgba(255,255,255,0.75);
  --card:  rgba(15,123,154,0.12);
  --bdr:   rgba(255,255,255,0.6);
  --bdrs:  rgba(255,255,255,1);
  --fh:    'Bricolage Grotesque', sans-serif;
  --fb:    'Plus Jakarta Sans', sans-serif;
}

/* ─── RESET ─────────────────────────────────────────── */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body { background: var(--bg); color: var(--white); font-family: var(--fb); overflow-x: hidden; line-height: 1.6; }
img  { max-width: 100%; display: block; }
::-webkit-scrollbar       { width: 4px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--teal); border-radius: 4px; }
::selection               { background: var(--teal); color: #000; }

/* ─── ANIMATED BACKGROUND BLOBS ─────────────────────── */
.glass-bg {
  position: fixed; inset: 0; z-index: -1;
  overflow: hidden; pointer-events: none;
  background: var(--bg);
}
.blob {
  position: absolute; border-radius: 50%;
  filter: blur(87px); opacity: 0.25;
  animation: floatBlob 25s infinite alternate cubic-bezier(0.4,0,0.2,1);
}
.blob1 { width: 450px; height: 450px; background: #FF3366; top: -10%; left: -10%; animation-delay: 0s; }
.blob2 { width: 550px; height: 550px; background: #00C8F0; bottom: -20%; right: -10%; animation-duration: 30s; }
.blob3 { width: 350px; height: 350px; background: #F9A820; top: 40%; left: 30%; animation-duration: 22s; animation-delay: -5s; }
.blob4 { width: 400px; height: 400px; background: #8B5CF6; top: 10%; right: 20%; animation-duration: 28s; animation-delay: -10s; }
@keyframes floatBlob {
  0%   { transform: translate(0,0) scale(1); }
  33%  { transform: translate(25vw,20vh) scale(1.2); }
  66%  { transform: translate(-20vw,35vh) scale(0.8); }
  100% { transform: translate(15vw,-15vh) scale(1.1); }
}

/* ─── NAVBAR ─────────────────────────────────────────── */
#navbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  padding: 0 max(1.25rem,2vw);
  transition: background .4s, border .4s;
}
#navbar.scrolled {
  background: rgba(255,255,255,0.65);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255,255,255,0.8);
  box-shadow: 0 4px 20px rgba(0,0,0,0.05);
}
#navbar.scrolled .logo,
#navbar.scrolled .nav-links a { color: #111B29 !important; }
#navbar.scrolled .nav-links a:hover { color: var(--teal) !important; }
#navbar.scrolled .hamburger span { background: #111B29; }

.nav-inner {
  max-width: 1260px; margin: 0 auto; height: 68px;
  display: flex; align-items: center; justify-content: space-between; gap: 1rem;
}
.logo {
  font-family: var(--fh); font-weight: 800;
  font-size: clamp(.8rem,2.2vw,1rem); letter-spacing: .05em;
  color: var(--white); text-decoration: none;
  display: flex; align-items: center; gap: .5rem;
  white-space: nowrap; flex-shrink: 0;
}
.logo-mark {
  width: 28px; height: 28px; border-radius: 7px;
  background: linear-gradient(135deg,#0A5E78,var(--teal));
  border: 1px solid rgba(255,255,255,0.15);
  display: flex; align-items: center; justify-content: center;
  font-size: .65rem; font-weight: 800; color: #fff !important;
  flex-shrink: 0; box-shadow: 0 4px 12px rgba(15,123,154,0.25);
}
.nav-links { display: flex; align-items: center; gap: 1.7rem; list-style: none; }
.nav-links a {
  color: var(--muted); text-decoration: none;
  font-size: .875rem; font-weight: 500;
  transition: color .2s; white-space: nowrap;
}
.nav-links a:hover { color: var(--white); }

.btn-nav {
  background: linear-gradient(135deg,var(--teal),#0A5E78) !important;
  color: #fff !important;
  border: 1px solid rgba(255,255,255,0.25) !important;
  padding: .52rem 1.15rem; border-radius: 6px;
  font-family: var(--fb); font-size: .82rem; font-weight: 700;
  cursor: pointer; text-decoration: none; white-space: nowrap;
  transition: all .25s; flex-shrink: 0;
  box-shadow: 0 4px 15px rgba(15,123,154,0.3) !important;
}
.btn-nav:hover {
  background: var(--tealb) !important;
  transform: translateY(-1px);
  box-shadow: 0 6px 22px rgba(15,123,154,0.5) !important;
}

.hamburger {
  display: none; flex-direction: column; gap: 5px;
  cursor: pointer; padding: 6px; background: none;
  border: none; flex-shrink: 0; z-index: 1001;
}
.hamburger span {
  display: block; width: 22px; height: 2px;
  background: var(--white); border-radius: 2px;
  transition: all .35s cubic-bezier(.68,-.55,.27,1.55);
}
.hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; transform: scaleX(0); }
.hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

/* ─── MOBILE MENU ────────────────────────────────────── */
.mobile-menu {
  display: flex; flex-direction: column;
  position: fixed; top: 68px; left: 0; right: 0;
  background: rgba(255,255,255,0.55) !important;
  backdrop-filter: blur(25px) !important;
  -webkit-backdrop-filter: blur(25px) !important;
  padding: 0 1.5rem;
  border-bottom: 1px solid rgba(15,123,154,0.2);
  box-shadow: 0 10px 30px rgba(0,0,0,0.08);
  z-index: 999; gap: 0;
  max-height: 0; overflow: hidden; opacity: 0;
  pointer-events: none;
  transition: max-height .42s cubic-bezier(.4,0,.2,1), opacity .32s ease, padding .42s cubic-bezier(.4,0,.2,1);
}
.mobile-menu.open { max-height: 450px; opacity: 1; padding: 1.2rem 1.5rem 1.5rem; pointer-events: all; }
.mobile-menu a {
  color: #111B29 !important; text-decoration: none;
  font-weight: 600; font-size: .95rem;
  padding: .85rem 0; border-bottom: 1px solid rgba(0,0,0,0.08);
  display: block; opacity: 0; transform: translateX(-18px);
  transition: color .2s, transform .35s ease, opacity .35s ease;
}
.mobile-menu a:last-child { border-bottom: none; padding-bottom: 0; }
.mobile-menu a:hover { color: var(--teal) !important; }
.mobile-menu a.btn-nav { color: #fff !important; border-bottom: none !important; }
.mobile-menu.open a:nth-child(1) { transform: translateX(0); opacity: 1; transition-delay: .05s; }
.mobile-menu.open a:nth-child(2) { transform: translateX(0); opacity: 1; transition-delay: .10s; }
.mobile-menu.open a:nth-child(3) { transform: translateX(0); opacity: 1; transition-delay: .15s; }
.mobile-menu.open a:nth-child(4) { transform: translateX(0); opacity: 1; transition-delay: .20s; }
.mobile-menu.open a:nth-child(5) { transform: translateX(0); opacity: 1; transition-delay: .25s; }
.mobile-menu.open a:nth-child(6) { transform: translateX(0); opacity: 1; transition-delay: .30s; }

/* ─── SHARED LAYOUT ──────────────────────────────────── */
section { padding: 5.5rem max(1.25rem,3vw); position: relative; background: transparent !important; }
.container { max-width: 1260px; margin: 0 auto; width: 100%; }
.sdiv { width: 100%; height: 1px; background: linear-gradient(90deg,transparent,var(--bdr),transparent); }

.slbl {
  display: inline-flex; align-items: center; gap: .5rem;
  font-size: .7rem; font-weight: 700; letter-spacing: .14em;
  text-transform: uppercase; color: var(--teal); margin-bottom: .9rem;
}
.slbl::before { content: ''; width: 14px; height: 2px; background: var(--teal); flex-shrink: 0; }
.stitle {
  font-family: var(--fh); font-size: clamp(1.7rem,3.5vw,2.75rem);
  font-weight: 800; line-height: 1.15; letter-spacing: -.02em; margin-bottom: .9rem;
}
.ssub { font-size: .93rem; color: var(--muted); line-height: 1.75; max-width: 540px; }

/* ─── SCROLL ANIMATIONS ──────────────────────────────── */
.au  { opacity: 0; transform: translateY(35px);   transition: opacity .9s cubic-bezier(0.16,1,0.3,1), transform .9s cubic-bezier(0.16,1,0.3,1); }
.asc { opacity: 0; transform: scale(.92);          transition: opacity .9s cubic-bezier(0.16,1,0.3,1), transform .9s cubic-bezier(0.16,1,0.3,1); }
.al  { opacity: 0; transform: translateX(-40px);   transition: opacity .9s cubic-bezier(0.16,1,0.3,1), transform .9s cubic-bezier(0.16,1,0.3,1); }
.ar  { opacity: 0; transform: translateX(40px);    transition: opacity .9s cubic-bezier(0.16,1,0.3,1), transform .9s cubic-bezier(0.16,1,0.3,1); }
.af  { opacity: 0; transform: perspective(500px) rotateX(12deg) translateY(20px); transition: opacity 1s cubic-bezier(0.16,1,0.3,1), transform 1s cubic-bezier(0.16,1,0.3,1); }
.ab  { opacity: 0; filter: blur(12px);             transition: opacity 1s cubic-bezier(0.16,1,0.3,1), filter 1s cubic-bezier(0.16,1,0.3,1); }
.au.in, .asc.in { opacity: 1; transform: none; }
.al.in { opacity: 1; transform: translateX(0); }
.ar.in { opacity: 1; transform: translateX(0); }
.af.in { opacity: 1; transform: perspective(500px) rotateX(0) translateY(0); }
.ab.in { opacity: 1; filter: blur(0); }

/* ─── HERO ───────────────────────────────────────────── */
#hero {
  min-height: 100svh; display: flex; align-items: center;
  position: relative; overflow: hidden;
  padding: calc(68px + 3rem) max(1.25rem,3vw) 4rem;
}
#hero::before {
  content: ''; position: absolute; inset: 0;
  background-image: linear-gradient(rgba(0,200,240,.04) 1px,transparent 1px),
                    linear-gradient(90deg,rgba(0,200,240,.04) 1px,transparent 1px);
  background-size: 55px 55px;
  mask-image: radial-gradient(ellipse 80% 80% at 50% 40%,black 20%,transparent 80%);
}
.orb { position: absolute; border-radius: 50%; filter: blur(90px); pointer-events: none; }
.orb1 { width: min(520px,80vw); height: min(520px,80vw); background: rgba(0,160,200,.22); top: -150px; left: -100px; }
.orb2 { width: min(320px,60vw); height: min(320px,60vw); background: rgba(249,168,32,.1);  bottom: 0;     right: -80px; }
.orb3 { width: min(260px,50vw); height: min(260px,50vw); background: rgba(0,200,240,.12); top: 40%;     right: 15%; }

.hero-inner {
  max-width: 1260px; margin: 0 auto; width: 100%;
  position: relative; z-index: 1;
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 3rem; align-items: center;
}
.hero-badge {
  display: inline-flex; align-items: center; gap: .5rem;
  background: rgba(0,200,240,.12); border: 1px solid rgba(0,200,240,.35);
  border-radius: 100px; padding: .28rem .9rem;
  font-size: .72rem; font-weight: 700; letter-spacing: .1em;
  text-transform: uppercase; color: var(--teal); margin-bottom: 1.3rem;
}
.pdot {
  width: 6px; height: 6px; background: var(--teal); border-radius: 50%;
  animation: pdot 2s infinite;
}
@keyframes pdot { 0%,100% { opacity:1; transform:scale(1); } 50% { opacity:.4; transform:scale(1.6); } }

.hero-headline {
  font-family: var(--fh); font-size: clamp(1.9rem,4.5vw,3.5rem);
  font-weight: 800; line-height: 1.1; letter-spacing: -.025em; margin-bottom: 1.4rem;
}
.hero-headline .tc { color: var(--teal); }
.hero-headline .ac { color: var(--amber); }
.hero-sub { font-size: clamp(.87rem,1.4vw,1.02rem); color: var(--muted); line-height: 1.75; max-width: 480px; margin-bottom: 2.2rem; }

.hero-ctas { display: flex; gap: .9rem; flex-wrap: wrap; }
.btn-p {
  background: linear-gradient(135deg,var(--teal),#0A5E78);
  color: #fff !important; border: 1px solid rgba(255,255,255,0.25);
  padding: .85rem 1.55rem; border-radius: 8px;
  font-family: var(--fb); font-size: .9rem; font-weight: 700;
  cursor: pointer; text-decoration: none;
  display: inline-flex; align-items: center; gap: .45rem;
  transition: all .3s; box-shadow: 0 8px 25px rgba(15,123,154,0.35);
}
.btn-p:hover { background: var(--tealb); transform: translateY(-3px); box-shadow: 0 12px 30px rgba(15,123,154,0.5); }
.btn-s {
  background: rgba(255,255,255,0.1); color: var(--teal) !important;
  border: 1px solid rgba(15,123,154,0.4);
  padding: .85rem 1.55rem; border-radius: 8px;
  font-family: var(--fb); font-size: .9rem; font-weight: 600;
  cursor: pointer; text-decoration: none;
  display: inline-flex; align-items: center; gap: .45rem; transition: all .3s;
}
.btn-s:hover {
  border-color: var(--teal); color: #fff !important;
  background: linear-gradient(135deg,var(--teal),#0A5E78);
  box-shadow: 0 8px 25px rgba(15,123,154,0.35); transform: translateY(-3px);
}

/* Mobile typewriter */
.hero-typewriter-mobile { display: none; margin-bottom: 1.4rem; min-height: 2.8rem; align-items: center; }
.tw-text {
  font-family: var(--fh); font-size: clamp(1.25rem,5vw,1.7rem);
  font-weight: 800; color: var(--teal); letter-spacing: -.01em;
  border-right: 3px solid var(--teal); padding-right: 3px;
  white-space: nowrap; overflow: hidden;
  animation: blink .75s step-end infinite;
}
@keyframes blink { 0%,100% { border-color: var(--teal); } 50% { border-color: transparent; } }

/* Hero fan cards */
.hero-visual { position: relative; display: flex; align-items: center; justify-content: center; perspective: 1000px; }
.hcs-fan {
  position: relative; width: 100%; max-width: 380px; height: 420px;
  display: flex; align-items: center; justify-content: center;
  animation: floatGroup 6s ease-in-out infinite;
}
@keyframes floatGroup { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-12px); } }

.hcs-fan .hc {
  position: absolute; width: 250px;
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 16px; padding: 1.2rem;
  backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
  box-shadow: 0 15px 35px rgba(0,0,0,0.08);
  transform-origin: bottom center;
  opacity: 0; transform: translateY(150px) scale(0.5);
  transition: box-shadow .3s, border-color .3s;
}
.hcs-fan .hc:hover { border-color: var(--bdrs); box-shadow: 0 20px 40px rgba(15,123,154,0.25); z-index: 10 !important; }
.hcs-fan .hc h3 { font-family: var(--fh); font-size: 1rem; font-weight: 700; margin-bottom: .3rem; }
.hcs-fan .hc p  { font-size: .75rem; color: var(--muted); line-height: 1.5; }
.hci {
  width: 38px; height: 38px; border-radius: 10px;
  background: rgba(15,123,154,0.15); border: 1px solid rgba(15,123,154,0.35);
  display: flex; align-items: center; justify-content: center;
  color: var(--teal); margin-bottom: .9rem;
}

.hc1 { z-index:1; animation: fan1 1.2s cubic-bezier(0.16,1,0.3,1) .2s forwards; }
.hc2 { z-index:2; animation: fan2 1.2s cubic-bezier(0.16,1,0.3,1) .3s forwards; }
.hc3 { z-index:3; animation: fan3 1.2s cubic-bezier(0.16,1,0.3,1) .4s forwards; }
.hc4 { z-index:4; animation: fan4 1.2s cubic-bezier(0.16,1,0.3,1) .5s forwards; }
@keyframes fan1 { 100% { opacity:1; transform: translateX(-60%) translateY(45px) rotate(-22deg) scale(0.9); } }
@keyframes fan2 { 100% { opacity:1; transform: translateX(-22%) translateY(10px) rotate(-7deg)  scale(0.95); } }
@keyframes fan3 { 100% { opacity:1; transform: translateX(22%)  translateY(10px) rotate(7deg)   scale(0.95); } }
@keyframes fan4 { 100% { opacity:1; transform: translateX(60%)  translateY(45px) rotate(22deg)  scale(0.9); } }

/* ─── ABOUT ──────────────────────────────────────────── */
.about-grid { display: grid; grid-template-columns: 1fr 1.35fr; gap: 4.5rem; align-items: center; }
.fc {
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 20px; padding: 2.2rem;
  backdrop-filter: blur(12px); position: relative; overflow: hidden;
  transition: transform .35s, box-shadow .35s, border-color .35s;
}
.fc:hover { transform: translateY(-6px) scale(1.01); border-color: var(--bdrs); box-shadow: 0 20px 50px rgba(0,0,0,.4), 0 0 40px rgba(0,200,240,.08); }
.fc::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg,var(--teal),var(--amber)); }

.fav {
  width: 88px; height: 88px; border-radius: 50%; overflow: hidden;
  margin-bottom: 1.1rem; border: 2.5px solid rgba(0,200,240,.5);
  box-shadow: 0 0 0 5px rgba(0,200,240,.1);
  background: linear-gradient(135deg,var(--teal),#0077A8);
  display: flex; align-items: center; justify-content: center; flex-shrink: 0;
  transition: transform .35s, box-shadow .35s;
}
.fav img { width: 100%; height: 100%; object-fit: cover; object-position: center; }
.fc:hover .fav { transform: scale(1.05); box-shadow: 0 0 0 8px rgba(0,200,240,.15), 0 8px 24px rgba(0,200,240,.2); }

.fn { font-family: var(--fh); font-size: 1.3rem; font-weight: 700; margin-bottom: .2rem; }
.fr { font-size: .74rem; color: var(--teal); font-weight: 700; letter-spacing: .07em; text-transform: uppercase; margin-bottom: 1.1rem; }
.fq { font-size: .85rem; color: var(--muted); line-height: 1.7; font-style: italic; border-left: 2px solid var(--teal); padding-left: .9rem; }

.mlist { list-style: none; margin-top: 1.5rem; display: flex; flex-direction: column; gap: .85rem; }
.mi { display: flex; align-items: flex-start; gap: .82rem; transition: transform .25s; }
.mi:hover { transform: translateX(4px); }
.mic {
  width: 36px; height: 36px; min-width: 36px; border-radius: 9px;
  background: rgba(0,200,240,.1); border: 1px solid rgba(0,200,240,.22);
  display: flex; align-items: center; justify-content: center; color: var(--teal);
  transition: background .25s, border-color .25s, transform .25s;
}
.mi:hover .mic { background: rgba(0,200,240,.2); border-color: rgba(0,200,240,.5); transform: rotate(-5deg) scale(1.08); }
.mit strong { display: block; font-size: .88rem; font-weight: 600; margin-bottom: .1rem; }
.mit span   { font-size: .8rem; color: var(--muted); }

/* ─── EXPERTISE ──────────────────────────────────────── */
#expertise::before {
  content: ''; position: absolute; top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  width: min(800px,90vw); height: min(800px,90vw);
  background: radial-gradient(circle,rgba(0,200,240,.07) 0%,transparent 65%);
  pointer-events: none;
}
.exp-header { text-align: center; margin-bottom: 3.5rem; }
.exp-header .slbl { margin: 0 auto .9rem; justify-content: center; }
.exp-header .ssub { margin: 0 auto; }
.exp-grid { display: grid; grid-template-columns: repeat(2,1fr); gap: 1.4rem; }

.ec {
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 18px; padding: 2rem; backdrop-filter: blur(12px);
  transition: transform .35s, border-color .35s, box-shadow .35s;
  cursor: default; position: relative; overflow: hidden;
}
.ec::after { content: ''; position: absolute; inset: 0; border-radius: 18px; background: linear-gradient(135deg,rgba(0,200,240,.06),transparent); opacity: 0; transition: opacity .35s; }
.ec:hover { transform: translateY(-6px); border-color: var(--bdrs); box-shadow: 0 18px 44px rgba(0,0,0,.38), 0 0 30px rgba(0,200,240,.06); }
.ec:hover::after { opacity: 1; }
.ec h3 { font-family: var(--fh); font-size: 1.12rem; font-weight: 700; margin-bottom: .6rem; line-height: 1.3; transition: color .3s; }
.ec:hover h3 { color: var(--teal); }
.ec p  { font-size: .86rem; color: var(--muted); line-height: 1.65; margin-bottom: 1.2rem; transition: color .3s; }
.ec:hover p { color: var(--off); }

.etop { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 1.1rem; }
.ei {
  width: 52px; height: 52px; border-radius: 13px;
  display: flex; align-items: center; justify-content: center;
  transition: transform .35s cubic-bezier(.34,1.56,.64,1);
}
.ec:hover .ei { transform: scale(1.12) rotate(-5deg); }
.ei.t { background: rgba(0,200,240,.12); border: 1px solid rgba(0,200,240,.28); color: var(--teal); }
.ei.a { background: rgba(249,168,32,.1);  border: 1px solid rgba(249,168,32,.28); color: var(--amber); }
.ei.g { background: rgba(74,222,128,.08); border: 1px solid rgba(74,222,128,.22); color: #4ADE80; }
.ei.v { background: rgba(167,139,250,.1); border: 1px solid rgba(167,139,250,.25); color: #A78BFA; }

.etag { font-size: .65rem; font-weight: 700; letter-spacing: .08em; text-transform: uppercase; padding: .23rem .62rem; border-radius: 100px; background: rgba(0,200,240,.1); color: var(--teal); border: 1px solid rgba(0,200,240,.2); }
.tpills { display: flex; flex-wrap: wrap; gap: .32rem; }
.tp { font-size: .68rem; font-weight: 600; padding: .2rem .58rem; border-radius: 100px; background: rgba(255,255,255,.05); border: 1px solid rgba(255,255,255,.09); color: var(--off); transition: background .25s, border-color .25s, color .25s; }
.ec:hover .tp { background: rgba(0,200,240,.08); border-color: rgba(0,200,240,.2); color: var(--teal); }

/* Flagship card */
.ec.feat {
  grid-column: span 2; display: grid; grid-template-columns: 1fr 1fr;
  gap: 2rem; align-items: center;
  background: linear-gradient(135deg,rgba(30,32,42,.95),rgba(0,160,200,.12));
  border-color: rgba(0,200,240,.28);
}
.ec.feat::before {
  content: 'FLAGSHIP'; position: absolute; top: 1.1rem; right: 1.3rem;
  font-size: .6rem; font-weight: 800; letter-spacing: .15em;
  color: var(--amber); background: rgba(249,168,32,.1);
  border: 1px solid rgba(249,168,32,.28); border-radius: 100px; padding: .2rem .62rem;
}
.fvis { background: rgba(0,200,240,.05); border: 1px solid rgba(0,200,240,.12); border-radius: 12px; padding: 1.3rem; display: flex; flex-direction: column; gap: .55rem; }
.mb { height: 7px; border-radius: 4px; background: rgba(0,200,240,.28); transition: width .4s; }
.mb.s  { width: 55%; } .mb.m  { width: 75%; } .mb.f  { width: 100%; } .mb.gd { background: rgba(249,168,32,.3); width: 42%; }
.ec:hover .mb.s { width: 68%; } .ec:hover .mb.m { width: 88%; }
.mr { display: flex; gap: .5rem; }
.mx { flex: 1; height: 36px; border-radius: 6px; background: rgba(0,200,240,.08); border: 1px solid rgba(0,200,240,.12); transition: background .35s; }
.ec:hover .mx { background: rgba(0,200,240,.13); }

/* ─── DTP ────────────────────────────────────────────── */
.dtp-lay { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; margin-bottom: 2.8rem; }
.dtp-grid { display: grid; grid-template-columns: repeat(2,1fr); gap: 1.4rem; }

.dc {
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 16px; padding: 1.8rem;
  transition: transform .35s, border-color .35s, box-shadow .35s;
  overflow: hidden; position: relative;
}
.dc::after { content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg,var(--teal),var(--amber)); transform: scaleX(0); transition: transform .35s; transform-origin: left; }
.dc:hover { transform: translateY(-5px); border-color: var(--bdrs); box-shadow: 0 16px 40px rgba(0,0,0,.3); }
.dc:hover::after { transform: scaleX(1); }
.dc h3 { font-family: var(--fh); font-size: 1.05rem; font-weight: 700; margin-bottom: .55rem; line-height: 1.3; transition: color .3s; }
.dc:hover h3 { color: var(--amber); }
.dc p  { font-size: .85rem; color: var(--muted); line-height: 1.65; transition: color .3s; }
.dc:hover p { color: var(--off); }

.di {
  width: 48px; height: 48px; border-radius: 12px;
  background: rgba(249,168,32,.1); border: 1px solid rgba(249,168,32,.25);
  display: flex; align-items: center; justify-content: center;
  color: var(--amber); margin-bottom: 1.1rem;
  transition: transform .35s cubic-bezier(.34,1.56,.64,1);
}
.dc:hover .di { transform: scale(1.12) rotate(-6deg); }
.dchips { display: flex; flex-wrap: wrap; gap: .38rem; margin-top: .9rem; }
.dchip { font-size: .68rem; color: var(--amber); background: rgba(249,168,32,.07); border: 1px solid rgba(249,168,32,.2); border-radius: 100px; padding: .17rem .62rem; font-weight: 500; transition: background .25s, border-color .25s; }
.dc:hover .dchip { background: rgba(249,168,32,.14); border-color: rgba(249,168,32,.4); }

/* ─── TECH STACK MARQUEE ─────────────────────────────── */
#techstack { padding: 2.8rem 0; border-top: 1px solid var(--bdr); border-bottom: 1px solid var(--bdr); overflow: hidden; }
.mlbl { text-align: center; font-size: .67rem; letter-spacing: .15em; text-transform: uppercase; color: var(--muted); margin-bottom: 1.8rem; font-weight: 600; }
.mwrap { overflow: hidden; position: relative; }
.mwrap::before, .mwrap::after { content: ''; position: absolute; top: 0; bottom: 0; width: 100px; z-index: 2; }
.mwrap::before { left: 0;  background: linear-gradient(90deg,var(--bg),transparent); }
.mwrap::after  { right: 0; background: linear-gradient(-90deg,var(--bg),transparent); }
.mtrack { display: flex; gap: 1.2rem; animation: mq 22s linear infinite; width: max-content; }
@keyframes mq { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }
.ti {
  display: flex; align-items: center; gap: .62rem;
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 10px; padding: .62rem 1.2rem;
  white-space: nowrap; transition: all .3s; cursor: default;
}
.ti:hover { border-color: var(--bdrs); background: rgba(0,200,240,.08); }
.tic { color: var(--teal); display: flex; align-items: center; flex-shrink: 0; }
.tin { font-family: var(--fh); font-size: .83rem; font-weight: 700; }

/* ─── WHY US ─────────────────────────────────────────── */
#why::after {
  content: ''; position: absolute; bottom: -200px; left: 50%; transform: translateX(-50%);
  width: 600px; height: 400px;
  background: radial-gradient(circle,rgba(0,200,240,.06) 0%,transparent 70%); pointer-events: none;
}
.why-hdr { text-align: center; margin-bottom: 3.5rem; }
.why-hdr .slbl { justify-content: center; margin: 0 auto .9rem; }
.why-hdr .ssub { margin: 0 auto; }
.why-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.4rem; }

.wc {
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 18px; padding: 2.2rem 1.8rem;
  text-align: center;
  transition: transform .35s, border-color .35s, box-shadow .35s;
  position: relative; overflow: hidden;
}
.wc::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; opacity: 0; transition: opacity .35s; }
.wc:nth-child(1)::before { background: var(--teal); }
.wc:nth-child(2)::before { background: var(--amber); }
.wc:nth-child(3)::before { background: #4ADE80; }
.wc:hover { transform: translateY(-6px); border-color: rgba(255,255,255,.12); box-shadow: 0 18px 44px rgba(0,0,0,.3); }
.wc:hover::before { opacity: 1; }

.wi {
  width: 68px; height: 68px; border-radius: 17px;
  margin: 0 auto 1.3rem;
  display: flex; align-items: center; justify-content: center;
  transition: transform .35s cubic-bezier(.34,1.56,.64,1);
}
.wc:hover .wi { transform: scale(1.12) rotate(-6deg); }
.wc:nth-child(1) .wi { background: rgba(0,200,240,.1);  border: 1px solid rgba(0,200,240,.22); color: var(--teal); }
.wc:nth-child(2) .wi { background: rgba(249,168,32,.08); border: 1px solid rgba(249,168,32,.22); color: var(--amber); }
.wc:nth-child(3) .wi { background: rgba(74,222,128,.07); border: 1px solid rgba(74,222,128,.18); color: #4ADE80; }
.wc h3 { font-family: var(--fh); font-size: 1.12rem; font-weight: 700; margin-bottom: .72rem; }
.wc:nth-child(1) h3 { color: var(--teal); }
.wc:nth-child(2) h3 { color: var(--amber); }
.wc:nth-child(3) h3 { color: #4ADE80; }
.wc p { font-size: .86rem; color: var(--muted); line-height: 1.65; transition: color .3s; }
.wc:hover p { color: var(--off); }

/* ─── CONTACT ────────────────────────────────────────── */
#contact { border-top: 1px solid var(--bdr); }
.cgrid { display: grid; grid-template-columns: 1fr 1.45fr; gap: 5rem; align-items: start; }
.ci h2 { font-family: var(--fh); font-size: clamp(1.7rem,3vw,2.3rem); font-weight: 800; line-height: 1.2; margin-bottom: 1.1rem; letter-spacing: -.02em; }
.ci > p { color: var(--muted); font-size: .88rem; line-height: 1.75; margin-bottom: 2rem; }
.cdet { display: flex; flex-direction: column; gap: .82rem; }
.cit { display: flex; align-items: center; gap: .75rem; font-size: .86rem; color: var(--off); transition: transform .25s; }
.cit:hover { transform: translateX(4px); }
.cic {
  width: 36px; height: 36px; border-radius: 8px;
  background: rgba(0,200,240,.08); border: 1px solid rgba(0,200,240,.18);
  display: flex; align-items: center; justify-content: center;
  color: var(--teal); flex-shrink: 0; transition: background .25s, border-color .25s;
}
.cit:hover .cic { background: rgba(0,200,240,.18); border-color: rgba(0,200,240,.4); }

.cform {
  background: var(--card); border: 1px solid var(--bdr);
  border-radius: 20px; padding: 2.2rem; backdrop-filter: blur(12px);
  transition: border-color .35s;
}
.cform:hover { border-color: rgba(0,200,240,.25); }
.cform h3 { font-family: var(--fh); font-size: 1.2rem; font-weight: 700; margin-bottom: 1.4rem; }
.frow { display: grid; grid-template-columns: 1fr 1fr; gap: .9rem; }
.fg { display: flex; flex-direction: column; gap: .33rem; margin-bottom: .85rem; }
.fg label { font-size: .7rem; font-weight: 700; color: var(--muted); letter-spacing: .07em; text-transform: uppercase; }
.fg input, .fg select, .fg textarea {
  background: rgba(255,255,255,.05); border: 1px solid rgba(255,255,255,.1);
  border-radius: 8px; padding: .73rem .88rem;
  color: var(--white); font-family: var(--fb); font-size: .875rem;
  outline: none; transition: all .25s; width: 100%;
}
.fg input::placeholder, .fg textarea::placeholder { color: rgba(154,175,196,.4); }
.fg select { appearance: none; cursor: pointer; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='7' fill='none'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%239AAFC4' stroke-width='1.5' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right .88rem center; padding-right: 2.1rem; }
.fg select option { background: var(--bg2); color: var(--white); }
.fg input:focus, .fg select:focus, .fg textarea:focus { border-color: var(--teal); box-shadow: 0 0 0 3px rgba(0,200,240,.14); background: rgba(0,200,240,.05); }
.fg textarea { resize: vertical; min-height: 92px; }

.bsub {
  width: 100%; background: linear-gradient(135deg,var(--teal),#0A5E78) !important;
  color: #fff !important; border: 1px solid rgba(255,255,255,0.25) !important;
  padding: .93rem; border-radius: 8px;
  font-family: var(--fh); font-size: .93rem; font-weight: 800;
  cursor: pointer; transition: all .3s; margin-top: .4rem; letter-spacing: .02em;
  box-shadow: 0 8px 25px rgba(15,123,154,0.35) !important;
}
.bsub:hover { transform: translateY(-2px); box-shadow: 0 12px 30px rgba(15,123,154,0.5) !important; }

/* ─── FOOTER ─────────────────────────────────────────── */
.fbot { border-top: 1px solid var(--bdr); padding: 1.4rem max(1.25rem,3vw); margin-top: 4rem; }
.fin { max-width: 1260px; margin: 0 auto; display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: .9rem; }
.fcopy { font-size: .76rem; color: var(--muted); }
.flinks { display: flex; gap: 1.4rem; }
.flinks a { font-size: .76rem; color: var(--muted); text-decoration: none; transition: color .2s; }
.flinks a:hover { color: var(--teal); }

/* ─── SCROLL-TO-TOP BUTTON ───────────────────────────── */
#stt {
  position: fixed; bottom: 1.8rem; right: 1.8rem;
  width: 42px; height: 42px; background: var(--teal);
  border: none; border-radius: 10px; cursor: pointer;
  display: flex; align-items: center; justify-content: center;
  color: #000; opacity: 0; transform: translateY(16px);
  transition: all .3s; box-shadow: 0 4px 16px rgba(0,200,240,.35); z-index: 500;
}
#stt.vis { opacity: 1; transform: translateY(0); }
#stt:hover { background: var(--tealb); transform: translateY(-2px); }

/* ─── RESPONSIVE ─────────────────────────────────────── */
@media (max-width: 1024px) {
  .hero-inner, .about-grid { grid-template-columns: 1fr; gap: 2.5rem; }
  .hero-visual { display: none !important; }
  .hero-typewriter-mobile { display: flex; }
  .exp-grid { grid-template-columns: 1fr; }
  .ec.feat { grid-column: span 1; grid-template-columns: 1fr; }
  .fvis { display: none; }
  .dtp-lay { grid-template-columns: 1fr; }
  .cgrid { grid-template-columns: 1fr; gap: 2.5rem; }
  .why-grid { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 768px) {
  .nav-links, .btn-nav { display: none; }
  .hamburger { display: flex; }
  section { padding: 4rem 1.25rem; }
  .dtp-grid, .why-grid, .frow { grid-template-columns: 1fr; }
  .fbot { padding: 1.2rem 1.25rem; }
  .fin { flex-direction: column; align-items: flex-start; gap: .6rem; }
  .hero-ctas { flex-direction: column; }
  .btn-p, .btn-s { justify-content: center; text-align: center; }
}
@media (max-width: 480px) {
  .cform { padding: 1.4rem; }
  .logo { font-size: .78rem; }
  .logo-mark { width: 24px; height: 24px; font-size: .6rem; }
}
</style>
</head>
<body>

<!-- Background blobs -->
<div class="glass-bg">
  <div class="blob blob1"></div>
  <div class="blob blob2"></div>
  <div class="blob blob3"></div>
  <div class="blob blob4"></div>
</div>

<!-- NAVBAR -->
<nav id="navbar">
  <div class="nav-inner">
    <a href="#hero" class="logo">
      <div class="logo-mark">IDS</div>
      IRFAN DIGITAL SERVICES
    </a>
    <ul class="nav-links">
      <li><a href="#hero">Home</a></li>
      <li><a href="#expertise">Expertise</a></li>
      <li><a href="#dtp">DTP Services</a></li>
      <li><a href="#techstack">Tech Stack</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="btn-nav">Get a Free Consultation</a>
    <button class="hamburger" id="hbtn" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mmenu">
  <a href="#hero"       onclick="closeMenu()">Home</a>
  <a href="#expertise"  onclick="closeMenu()">Expertise</a>
  <a href="#dtp"        onclick="closeMenu()">DTP Services</a>
  <a href="#techstack"  onclick="closeMenu()">Tech Stack</a>
  <a href="#contact"    onclick="closeMenu()">Contact</a>
  <a href="#contact" class="btn-nav" style="text-align:center;margin-top:.4rem;border-radius:8px;padding:.7rem" onclick="closeMenu()">Get a Free Consultation</a>
</div>

<!-- HERO -->
<section id="hero">
  <div class="orb orb1"></div>
  <div class="orb orb2"></div>
  <div class="orb orb3"></div>
  <div class="hero-inner">
    <div>
      <div class="hero-typewriter-mobile" style="margin-bottom:1.5rem;margin-top:-6.5rem">
        <span class="tw-text" id="twText"></span>
      </div>
      <div class="hero-badge"><span class="pdot"></span>B2B Tech Partner for Education</div>
      <h1 class="hero-headline">
        Automating Education:<br>
        <span class="tc">Smart Tech Solutions</span><br>
        for Schools &amp; <span class="ac">Coachings.</span>
      </h1>
      <p class="hero-sub">We eliminate manual administrative burdens with advanced software, custom automation, and high-speed data processing — saving you significant time and operational cost.</p>
      <div class="hero-ctas">
        <a href="#expertise" class="btn-p">
          <svg width="15" height="15" fill="none" viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/></svg>
          Explore Automation
        </a>
        <a href="#dtp" class="btn-s">
          <svg width="15" height="15" fill="none" viewBox="0 0 24 24"><path d="M9 12h6M9 16h6M7 4H5a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2V6a2 2 0 00-2-2h-2M9 4a2 2 0 012-2h2a2 2 0 012 2v0a2 2 0 01-2 2h-2a2 2 0 01-2-2z" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg>
          View DTP Services
        </a>
      </div>
    </div>

    <div class="hero-visual">
      <div class="hcs-fan">
        <div class="hc hc1">
          <div class="hci"><svg width="18" height="18" fill="none" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8l-6-6z" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/></svg></div>
          <h3>Automated DTP</h3>
          <p>High-speed exam paper formatting.</p>
        </div>
        <div class="hc hc2">
          <div class="hci"><svg width="18" height="18" fill="none" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/><rect x="14" y="3" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/><rect x="3" y="14" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/><rect x="14" y="14" width="7" height="7" rx="1" stroke="currentColor" stroke-width="2"/></svg></div>
          <h3>Live Results Bot</h3>
          <p>Board data compiled instantly.</p>
        </div>
        <div class="hc hc3">
          <div class="hci"><svg width="18" height="18" fill="none" viewBox="0 0 24 24"><rect x="2" y="7" width="20" height="14" rx="2" stroke="currentColor" stroke-width="2"/><circle cx="12" cy="14" r="2" stroke="currentColor" stroke-width="2"/></svg></div>
          <h3>Bulk ID Generation</h3>
          <p>1000+ IDs &amp; Admit cards in minutes.</p>
        </div>
        <div class="hc hc4">
          <div class="hci"><svg width="18" height="18" fill="none" viewBox="0 0 24 24"><rect x="5" y="2" width="14" height="20" rx="2" stroke="currentColor" stroke-width="2"/><path d="M9 7h6M9 11h6" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg></div>
          <h3>School Management App</h3>
          <p>Custom FlutterFlow &amp; Firebase app.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="sdiv"></div>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <div class="about-grid">
      <div class="al">
        <div class="fc">
          <div class="fav">
            <img src="https://drive.google.com/thumbnail?id=1HPj9UGPyZJxUWRt0Dxfs4LGKy6TWn6B-&sz=w400" alt="Irfan Salimi"
              onerror="this.style.display='none';this.parentElement.innerHTML='<span style=\'font-family:var(--fh);font-size:2rem;font-weight:800;color:#000\'>IS</span>'">
          </div>
          <div class="fn">Irfan Salimi</div>
          <div class="fr">Founder &amp; Lead Tech Architect</div>
          <div class="fq">"Educational institutions deserve the same technological edge as Fortune 500 companies. My mission is to bridge that gap — one automation at a time."</div>
        </div>
      </div>
      <div>
        <span class="slbl ab">About The Founder</span>
        <h2 class="stitle af">Your Dedicated <span style="color:var(--teal)">Tech &amp; Admin Partner</span> — Not Just a Service Provider</h2>
        <p class="ssub af">Irfan Salimi founded IRFAN DIGITAL SERVICES with a singular vision: to bridge the critical gap between educational administration and modern technology. With deep expertise in software automation, app development, and data processing, Irfan works alongside school principals, directors, and coaching owners — not as a vendor, but as a committed technology partner invested in their institutional growth.</p>
        <ul class="mlist">
          <li class="mi au">
            <div class="mic"><svg width="15" height="15" fill="none" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3" stroke="currentColor" stroke-width="2"/><path d="M12 2v3M12 19v3M4.22 4.22l2.12 2.12M17.66 17.66l2.12 2.12M2 12h3M19 12h3M4.22 19.78l2.12-2.12M17.66 6.34l2.12-2.12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg></div>
            <div class="mit"><strong>Purpose-Built for Education</strong><span>Every solution is designed exclusively for the workflows, challenges, and compliance requirements of educational institutions.</span></div>
          </li>
          <li class="mi au">
            <div class="mic"><svg width="15" height="15" fill="none" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2M9 7a4 4 0 100 8 4 4 0 000-8zM23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></div>
            <div class="mit"><strong>End-to-End Ownership</strong><span>From concept to deployment, we own every deliverable — no hand-offs, no outsourcing, full accountability.</span></div>
          </li>
          <li class="mi au">
            <div class="mic"><svg width="15" height="15" fill="none" viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/></svg></div>
            <div class="mit"><strong>Technology That Scales With You</strong><span>Whether you manage 200 or 2,000 students, our solutions adapt and grow alongside your institution.</span></div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</section>

<div class="sdiv"></div>

<!-- EXPERTISE -->
<section id="expertise">
  <div class="container">
    <div class="exp-header">
      <span class="slbl ab">Core Expertise</span>
      <h2 class="stitle asc">Software &amp; Automation <span style="color:var(--teal)">Built for Education</span></h2>
      <p class="ssub asc">Advanced, code-driven solutions that transform the way your institution operates — eliminating inefficiency and replacing it with precision-engineered automation.</p>
    </div>
    <div class="exp-grid">
      <!-- Flagship -->
      <div class="ec feat af">
        <div>
          <div class="ei t" style="width:60px;height:60px;margin-bottom:1.1rem">
            <svg width="26" height="26" fill="none" viewBox="0 0 24 24"><rect x="5" y="2" width="14" height="20" rx="2" stroke="currentColor" stroke-width="2"/><path d="M9 7h6M9 11h6M9 15h3" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg>
          </div>
          <h3 style="font-size:1.3rem;margin-bottom:.7rem">Custom School Management Apps</h3>
          <p style="margin-bottom:1.2rem">A fully tailored, cross-platform mobile application built with FlutterFlow and Firebase — with separate, role-based access for Administrators, Teachers, and Students. Manage attendance, results, notices, fees, and more from a single, secure dashboard.</p>
          <div class="tpills">
            <span class="tp">FlutterFlow</span><span class="tp">Firebase</span><span class="tp">Real-time DB</span><span class="tp">Cloud Functions</span><span class="tp">Role-Based Auth</span>
          </div>
        </div>
        <div class="fvis">
          <div class="mb f"></div><div class="mb m"></div>
          <div class="mr"><div class="mx"></div><div class="mx"></div></div>
          <div class="mb gd"></div><div class="mb s"></div>
          <div class="mr"><div class="mx"></div><div class="mx"></div><div class="mx"></div></div>
          <div class="mb m"></div>
        </div>
      </div>
      <!-- Card 2 -->
      <div class="ec ar">
        <div class="etop">
          <div class="ei a"><svg width="22" height="22" fill="none" viewBox="0 0 24 24"><path d="M12 2a10 10 0 100 20A10 10 0 0012 2z" stroke="currentColor" stroke-width="2"/><path d="M12 8v4l3 3" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></div>
          <span class="etag">Automation</span>
        </div>
        <h3>Data Automation &amp; Web Scraping</h3>
        <p>Python and Selenium-powered bots that automatically fetch, compile, and structure board exam results and institutional data — in minutes, not days. No manual copying, no human error.</p>
        <div class="tpills"><span class="tp">Python</span><span class="tp">Selenium</span><span class="tp">BeautifulSoup</span><span class="tp">Pandas</span></div>
      </div>
      <!-- Card 3 -->
      <div class="ec ar">
        <div class="etop">
          <div class="ei g"><svg width="22" height="22" fill="none" viewBox="0 0 24 24"><path d="M3 3h7v7H3zM14 3h7v7h-7zM3 14h7v7H3zM14 14h7v7h-7z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
          <span class="etag">Workflow</span>
        </div>
        <h3>Google Workspace Automation</h3>
        <p>Custom Google Apps Script solutions that connect your Sheets, Forms, Gmail, and Drive into seamless automated workflows — eliminating repetitive data entry and manual cross-checking for good.</p>
        <div class="tpills"><span class="tp">Apps Script</span><span class="tp">Google Sheets</span><span class="tp">Gmail API</span><span class="tp">Google Forms</span></div>
      </div>
      <!-- Card 4 -->
      <div class="ec ar">
        <div class="etop">
          <div class="ei v"><svg width="22" height="22" fill="none" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8l-6-6z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/><path d="M14 2v6h6M16 13H8M16 17H8M10 9H8" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></div>
          <span class="etag">Bulk Processing</span>
        </div>
        <h3>Bulk Document Generation</h3>
        <p>Generate hundreds of personalized admit cards, marksheets, and certificates directly from raw data — automatically formatted, accurately populated, and print-ready in a single click.</p>
        <div class="tpills"><span class="tp">Python</span><span class="tp">ReportLab</span><span class="tp">Apps Script</span><span class="tp">Mail Merge</span></div>
      </div>
    </div>
  </div>
</section>

<div class="sdiv"></div>

<!-- DTP -->
<section id="dtp">
  <div class="container">
    <div class="dtp-lay">
      <div>
        <span class="slbl ab">DTP &amp; Formatting</span>
        <h2 class="stitle al">Premium Design &amp;<br><span style="color:var(--amber)">Document Solutions</span></h2>
      </div>
      <p class="ssub ar" style="margin-top:3rem">Precision-formatted academic documents and high-impact visual assets — crafted with professional tools and delivered with guaranteed quality at speed.</p>
    </div>
    <div class="dtp-grid">
      <div class="dc asc">
        <div class="di"><svg width="22" height="22" fill="none" viewBox="0 0 24 24"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7" stroke="currentColor" stroke-width="2" stroke-linecap="round"/><path d="M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4 9.5-9.5z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
        <h3>High-Speed Exam Paper Typesetting</h3>
        <p>Professionally structured question papers that precisely match official board patterns and mock test formats. Flawless typography, correct section layouts, and print-ready output every time.</p>
        <div class="dchips">
          <span class="dchip">Board-Pattern Compliant</span>
          <span class="dchip">Quick Turnaround</span>
          <span class="dchip">Print-Ready PDF</span>
        </div>
      </div>
      <div class="dc asc">
        <div class="di"><svg width="22" height="22" fill="none" viewBox="0 0 24 24"><rect x="2" y="7" width="20" height="14" rx="2" stroke="currentColor" stroke-width="2"/><path d="M16 7V5a2 2 0 00-2-2h-4a2 2 0 00-2 2v2" stroke="currentColor" stroke-width="2"/><circle cx="12" cy="14" r="2" stroke="currentColor" stroke-width="2"/></svg></div>
        <h3>Smart ID Cards &amp; Result Processing</h3>
        <p>Premium, data-driven student ID card designs and eye-catching Result Posters featuring your institution's toppers — formatted from raw data in bulk, with photo integration and brand consistency.</p>
        <div class="dchips">
          <span class="dchip">Bulk from Data</span>
          <span class="dchip">Toppers Poster</span>
          <span class="dchip">Brand Consistent</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TECH STACK -->
<section id="techstack">
  <div class="mlbl">Powered by Industry-Leading Technologies</div>
  <div class="mwrap">
    <div class="mtrack" id="mtr">
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z" stroke="currentColor" stroke-width="1.8"/><text x="7.5" y="16" font-size="7" fill="currentColor" font-weight="bold" font-family="monospace">Py</text></svg></span><span class="tin">Python</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M3 3h7v7H3zM14 3h7v7h-7zM3 14h7v7H3zM14 14h7v7h-7z" stroke="currentColor" stroke-width="1.8"/></svg></span><span class="tin">Google Apps Script</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><rect x="5" y="2" width="14" height="20" rx="2" stroke="currentColor" stroke-width="1.8"/><path d="M9 7h6M9 11h6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg></span><span class="tin">FlutterFlow</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/></svg></span><span class="tin">Firebase</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3" stroke="currentColor" stroke-width="1.8"/><path d="M12 2v2M12 20v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M2 12h2M20 12h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg></span><span class="tin">Selenium</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M3 12h18M3 6h18M3 18h18" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg></span><span class="tin">HTML / CSS / JS</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8l-6-6z" stroke="currentColor" stroke-width="1.8"/><path d="M14 2v6h6" stroke="currentColor" stroke-width="1.8"/></svg></span><span class="tin">ReportLab</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M18 10h-4V6h-4v4H6l6 6 6-6z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/><path d="M6 18h12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg></span><span class="tin">Google Cloud</span></div>
      <!-- Duplicate set for infinite loop -->
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z" stroke="currentColor" stroke-width="1.8"/><text x="7.5" y="16" font-size="7" fill="currentColor" font-weight="bold" font-family="monospace">Py</text></svg></span><span class="tin">Python</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M3 3h7v7H3zM14 3h7v7h-7zM3 14h7v7H3zM14 14h7v7h-7z" stroke="currentColor" stroke-width="1.8"/></svg></span><span class="tin">Google Apps Script</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><rect x="5" y="2" width="14" height="20" rx="2" stroke="currentColor" stroke-width="1.8"/><path d="M9 7h6M9 11h6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg></span><span class="tin">FlutterFlow</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/></svg></span><span class="tin">Firebase</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3" stroke="currentColor" stroke-width="1.8"/><path d="M12 2v2M12 20v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M2 12h2M20 12h2" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/></svg></span><span class="tin">Selenium</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M3 12h18M3 6h18M3 18h18" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg></span><span class="tin">HTML / CSS / JS</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8l-6-6z" stroke="currentColor" stroke-width="1.8"/></svg></span><span class="tin">ReportLab</span></div>
      <div class="ti"><span class="tic"><svg width="16" height="16" fill="none" viewBox="0 0 24 24"><path d="M18 10h-4V6h-4v4H6l6 6 6-6z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/><path d="M6 18h12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg></span><span class="tin">Google Cloud</span></div>
    </div>
  </div>
</section>

<!-- WHY US -->
<section id="why">
  <div class="container">
    <div class="why-hdr">
      <span class="slbl ab">Why Us</span>
      <h2 class="stitle asc">The Standard Your Institution <span style="color:var(--teal)">Deserves</span></h2>
      <p class="ssub asc">Three core commitments that define every engagement — setting us apart from conventional service providers.</p>
    </div>
    <div class="why-grid">
      <div class="wc af">
        <div class="wi"><svg width="28" height="28" fill="none" viewBox="0 0 24 24"><path d="M22 11.08V12a10 10 0 11-5.93-9.14" stroke="currentColor" stroke-width="2" stroke-linecap="round"/><path d="M22 4L12 14.01l-3-3" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
        <h3>100% Accuracy</h3>
        <p>Code-driven, automated workflows eliminate the risk of human error entirely. Every record, every admit card, every compiled result is processed with programmatic precision — verified and reliable.</p>
      </div>
      <div class="wc af">
        <div class="wi"><svg width="28" height="28" fill="none" viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z" stroke="currentColor" stroke-width="2" stroke-linejoin="round"/></svg></div>
        <h3>Massive Time Savings</h3>
        <p>Tasks that consume your staff for days — compiling board results, generating admit cards, formatting exam papers — are completed in minutes. We give your team their time back.</p>
      </div>
      <div class="wc af">
        <div class="wi"><svg width="28" height="28" fill="none" viewBox="0 0 24 24"><path d="M21 16V8a2 2 0 00-1-1.73l-7-4a2 2 0 00-2 0l-7 4A2 2 0 003 8v8a2 2 0 001 1.73l7 4a2 2 0 002 0l7-4A2 2 0 0021 16z" stroke="currentColor" stroke-width="2"/><path d="M3.27 6.96L12 12.01l8.73-5.05M12 22.08V12" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></div>
        <h3>All-in-One Tech Partner</h3>
        <p>From premium DTP and formatting to fully functional mobile applications — you don't need five vendors. One partner, one point of contact, complete institutional technology coverage.</p>
      </div>
    </div>
  </div>
</section>

<div class="sdiv"></div>

<!-- CONTACT -->
<section id="contact">
  <div class="container">
    <div class="cgrid">
      <div class="ci">
        <span class="slbl ab">Get In Touch</span>
        <h2 class="al">Ready to Transform<br>Your Institution?</h2>
        <p class="al">Schedule a free, no-obligation consultation. Tell us about your biggest administrative challenge and we will show you exactly how to solve it — with a clear timeline and transparent pricing.</p>
        <div class="cdet al">
          <div class="cit"><div class="cic"><svg width="14" height="14" fill="none" viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z" stroke="currentColor" stroke-width="2"/><circle cx="12" cy="9" r="2.5" stroke="currentColor" stroke-width="2"/></svg></div><span>Araria, Bihar, India</span></div>
          <div class="cit"><div class="cic"><svg width="14" height="14" fill="none" viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z" stroke="currentColor" stroke-width="2"/><path d="M22 6l-10 7L2 6" stroke="currentColor" stroke-width="2"/></svg></div><span>irfandigitalservices@gmail.com</span></div>
          <div class="cit"><div class="cic"><svg width="14" height="14" fill="none" viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.8 19.79 19.79 0 01.09 1.23 2 2 0 012.06.04h3a2 2 0 012 1.72 12.84 12.84 0 00.7 2.81 2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45 12.84 12.84 0 002.81.7A2 2 0 0122 16.92z" stroke="currentColor" stroke-width="2"/></svg></div><span>Available on WhatsApp &amp; Call</span></div>
          <div class="cit"><div class="cic"><svg width="14" height="14" fill="none" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/><path d="M12 6v6l4 2" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></div><span>Mon – Sat: 9:00 AM – 7:00 PM IST</span></div>
        </div>
      </div>
      <div class="cform ar">
        <h3>Send Us a Message</h3>
        <div class="frow">
          <div class="fg"><label>Your Name</label><input type="text" placeholder="e.g. Rajesh Kumar"></div>
          <div class="fg"><label>Institute Name</label><input type="text" placeholder="e.g. Sunrise Public School"></div>
        </div>
        <div class="fg"><label>Email Address</label><input type="email" placeholder="your@email.com"></div>
        <div class="fg">
          <label>Service Required</label>
          <select>
            <option value="" disabled selected>Select a service...</option>
            <option>Custom School Management App</option>
            <option>Data Automation &amp; Web Scraping</option>
            <option>Google Workspace Automation</option>
            <option>Bulk Document Generation</option>
            <option>Exam Paper Typesetting</option>
            <option>ID Cards &amp; Result Processing</option>
            <option>Full Tech Partnership</option>
            <option>Other / Not Sure Yet</option>
          </select>
        </div>
        <div class="fg"><label>Your Message</label><textarea placeholder="Briefly describe your challenge or requirement..."></textarea></div>
        <button class="bsub" onclick="handleSubmit(this)">Send Message &rarr;</button>
      </div>
    </div>
  </div>
  <div class="fbot">
    <div class="fin">
      <span class="fcopy">&copy; 2025 IRFAN DIGITAL SERVICES. All rights reserved. Irfan Salimi, Araria, Bihar, India.</span>
      <div class="flinks">
        <a href="#hero">Home</a>
        <a href="#expertise">Expertise</a>
        <a href="#dtp">DTP</a>
        <a href="#contact">Contact</a>
      </div>
    </div>
  </div>
</section>

<!-- Scroll to top -->
<button id="stt" aria-label="Back to top">
  <svg width="14" height="14" fill="none" viewBox="0 0 24 24"><path d="M18 15l-6-6-6 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
</button>

<script>
// ─── NAVBAR + SCROLL-TO-TOP ───────────────────────────
const navbar = document.getElementById('navbar');
const stt    = document.getElementById('stt');

stt.addEventListener('click', () => {
  document.documentElement.scrollTop = 0;
  document.body.scrollTop = 0;
});

window.addEventListener('scroll', () => {
  navbar.classList.toggle('scrolled', scrollY > 40);
  stt.classList.toggle('vis', scrollY > 400);

  // Active nav link highlight
  let current = '';
  document.querySelectorAll('section[id]').forEach(s => {
    if (scrollY >= s.offsetTop - 100) current = s.id;
  });
  document.querySelectorAll('.nav-links a').forEach(a => {
    a.style.color = a.getAttribute('href') === '#' + current ? '#fff' : '';
  });
});

// ─── HAMBURGER MENU ───────────────────────────────────
const hbtn  = document.getElementById('hbtn');
const mmenu = document.getElementById('mmenu');
let menuOpen = false;

hbtn.addEventListener('click', e => {
  e.stopPropagation();
  menuOpen = !menuOpen;
  hbtn.classList.toggle('open', menuOpen);
  mmenu.classList.toggle('open', menuOpen);
});

function closeMenu() {
  menuOpen = false;
  hbtn.classList.remove('open');
  mmenu.classList.remove('open');
}

document.addEventListener('click', e => {
  if (!navbar.contains(e.target) && !mmenu.contains(e.target)) closeMenu();
});

// ─── SCROLL REVEAL ────────────────────────────────────
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('in'); });
}, { threshold: 0.15, rootMargin: '0px 0px -60px 0px' });

document.querySelectorAll('.au,.asc,.al,.ar,.af,.ab').forEach(el => observer.observe(el));

// ─── HERO ENTRANCE ────────────────────────────────────
['.hero-badge', '.hero-headline', '.hero-sub', '.hero-ctas'].forEach((sel, i) => {
  const el = document.querySelector(sel);
  if (!el) return;
  el.style.cssText = `opacity:0;transform:translateY(16px);transition:opacity .65s ease,transform .65s ease;transition-delay:${0.15 + i * 0.13}s`;
  setTimeout(() => { el.style.opacity = '1'; el.style.transform = 'translateY(0)'; }, 60);
});

// ─── MARQUEE PAUSE ON HOVER ───────────────────────────
const mtrack = document.getElementById('mtr');
if (mtrack) {
  mtrack.addEventListener('mouseenter', () => mtrack.style.animationPlayState = 'paused');
  mtrack.addEventListener('mouseleave', () => mtrack.style.animationPlayState = 'running');
}

// ─── FORM SUBMIT ─────────────────────────────────────
function handleSubmit(btn) {
  btn.textContent = 'Message Sent!';
  btn.style.cssText = 'background:linear-gradient(135deg,#16A34A,#15803D)!important;color:#fff!important;width:100%;border:none;padding:.93rem;border-radius:8px;font-family:var(--fh);font-size:.93rem;font-weight:800;cursor:default;margin-top:.4rem';
  btn.disabled = true;
  setTimeout(() => {
    btn.textContent = 'Send Message →';
    btn.style.cssText = '';
    btn.disabled = false;
  }, 4000);
}

// ─── TYPEWRITER ANIMATION (mobile) ───────────────────
(function () {
  const words = [
    'WELCOME TO IRFAN DIGITAL SERVICES',
    'DATA AUTOMATION',
    'GOOGLE WORKSPACE AUTOMATION',
    'BULK DOCUMENT GENERATION',
    'SCHOOL MANAGEMENT APPS',
    'WEB SCRAPING EXPERTS',
    'SMART TECH FOR SCHOOLS',
  ];
  const el = document.getElementById('twText');
  if (!el) return;

  let wi = 0, ci = 0, deleting = false;
  const TYPE_SPEED = 65, DELETE_SPEED = 35, PAUSE_AFTER = 1400, PAUSE_BEFORE = 300;

  function tick() {
    const word = words[wi];
    if (!deleting) {
      el.textContent = word.slice(0, ++ci);
      if (ci === word.length) { deleting = true; setTimeout(tick, PAUSE_AFTER); return; }
    } else {
      el.textContent = word.slice(0, --ci);
      if (ci === 0) { deleting = false; wi = (wi + 1) % words.length; setTimeout(tick, PAUSE_BEFORE); return; }
    }
    setTimeout(tick, deleting ? DELETE_SPEED : TYPE_SPEED);
  }
  setTimeout(tick, 900);
})();
</script>
</body>
</html>
