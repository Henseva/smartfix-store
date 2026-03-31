<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<meta name="description" content="CelularPro — Acessórios premium e assistência técnica especializada.">
<meta name="theme-color" content="#060810">
<title>CelularPro — Acessórios & Assistência Técnica</title>
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,300&display=swap" rel="stylesheet">

<style>
/* ─── TOKENS ─────────────────────────────────────── */
:root{
  --bg:       #060810;
  --bg2:      #0c0f1c;
  --card:     #10142a;
  --card2:    #141830;
  --border:   rgba(255,255,255,.07);
  --border2:  rgba(255,255,255,.12);
  --blue:     #3b82f6;
  --blue-d:   #2563eb;
  --cyan:     #06b6d4;
  --gold:     #f59e0b;
  --green:    #10b981;
  --red:      #ef4444;
  --white:    #f8fafc;
  --muted:    rgba(248,250,252,.42);
  --muted2:   rgba(248,250,252,.22);
  --radius:   16px;
  --radius-sm:10px;
}

/* ─── RESET ─────────────────────────────────────── */
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;font-size:16px}
body{background:var(--bg);color:var(--white);font-family:'DM Sans',sans-serif;overflow-x:hidden;-webkit-tap-highlight-color:transparent}
img{display:block;max-width:100%}
a{text-decoration:none;color:inherit}
button{cursor:pointer;font-family:inherit;border:none;outline:none}
input,textarea,select{font-family:inherit;outline:none}
ul{list-style:none}

/* ─── SCROLLBAR ──────────────────────────────────── */
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--blue);border-radius:99px}

/* ─── CURSOR (desktop) ───────────────────────────── */
@media(min-width:769px){
  body{cursor:none}
  #cur{width:8px;height:8px;background:var(--blue);border-radius:50%;position:fixed;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:transform .12s,background .18s}
  #cur-r{width:30px;height:30px;border:1.5px solid rgba(59,130,246,.5);border-radius:50%;position:fixed;pointer-events:none;z-index:9997;transform:translate(-50%,-50%);transition:width .22s,height .22s,border-color .22s}
  body.hov #cur{transform:translate(-50%,-50%) scale(2);background:var(--cyan)}
  body.hov #cur-r{width:44px;height:44px;border-color:rgba(6,182,212,.4)}
}
@media(max-width:768px){#cur,#cur-r{display:none}}

/* ─── PROGRESS BAR ───────────────────────────────── */
#prog{position:fixed;top:0;left:0;height:2px;background:linear-gradient(90deg,var(--blue),var(--cyan));z-index:9999;width:0;transition:width .08s linear}

/* ─── LOADER ─────────────────────────────────────── */
#ldr{position:fixed;inset:0;z-index:99999;background:var(--bg);display:flex;flex-direction:column;align-items:center;justify-content:center;transition:opacity .8s,visibility .8s}
#ldr.out{opacity:0;visibility:hidden;pointer-events:none}
.ldr-icon{font-size:52px;animation:ldrPop .6s cubic-bezier(.22,1,.36,1) both}
.ldr-name{font-family:'Syne',sans-serif;font-size:clamp(28px,6vw,48px);font-weight:800;margin-top:16px;letter-spacing:-1.5px;background:linear-gradient(135deg,var(--white) 40%,var(--blue));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:ldrFade .7s .2s both}
.ldr-sub{font-size:11px;letter-spacing:.22em;text-transform:uppercase;color:var(--muted);margin-top:10px;animation:ldrFade .7s .35s both}
.ldr-bar{width:120px;height:1px;background:var(--border);margin-top:36px;overflow:hidden;animation:ldrFade .5s .5s both}
.ldr-fill{height:100%;background:linear-gradient(90deg,var(--blue),var(--cyan));animation:ldrFill 1.6s ease forwards}
@keyframes ldrPop{from{opacity:0;transform:scale(.5)}to{opacity:1;transform:scale(1)}}
@keyframes ldrFade{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:none}}
@keyframes ldrFill{to{width:100%}}

/* ─── NAV ────────────────────────────────────────── */
nav{position:fixed;top:0;left:0;right:0;z-index:900;padding:18px 24px;display:flex;align-items:center;justify-content:space-between;transition:all .3s;border-bottom:1px solid transparent}
nav.scrolled{background:rgba(6,8,16,.85);backdrop-filter:blur(20px);border-bottom-color:var(--border)}
.nav-logo{display:flex;align-items:center;gap:10px;font-family:'Syne',sans-serif;font-weight:800;font-size:20px;letter-spacing:-.5px}
.nav-logo span.icon{width:34px;height:34px;background:linear-gradient(135deg,var(--blue),var(--cyan));border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:16px}
.nav-links{display:flex;align-items:center;gap:8px}
.nav-links a{font-size:13px;font-weight:500;color:var(--muted);padding:7px 14px;border-radius:99px;transition:all .2s}
.nav-links a:hover{color:var(--white);background:var(--border)}
.nav-cta{background:var(--blue);color:#fff!important;padding:8px 20px!important;border-radius:99px!important;font-weight:600!important;transition:all .25s!important}
.nav-cta:hover{background:var(--blue-d)!important;transform:translateY(-1px);box-shadow:0 6px 24px rgba(59,130,246,.4)!important}
.nav-burger{display:none;flex-direction:column;gap:5px;width:26px;cursor:pointer;padding:4px}
.nav-burger span{height:2px;background:var(--white);border-radius:2px;transition:all .3s}
@media(max-width:768px){
  .nav-links{display:none}
  .nav-burger{display:flex}
}

/* ─── MOBILE MENU ────────────────────────────────── */
#mob-menu{position:fixed;inset:0;background:rgba(6,8,16,.97);backdrop-filter:blur(30px);z-index:800;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:8px;opacity:0;pointer-events:none;transition:opacity .3s}
#mob-menu.open{opacity:1;pointer-events:all}
#mob-menu a{font-family:'Syne',sans-serif;font-size:clamp(22px,6vw,32px);font-weight:700;color:var(--muted);padding:10px 28px;border-radius:12px;transition:all .2s;text-align:center}
#mob-menu a:hover,#mob-menu a:active{color:var(--white);background:var(--border)}
#mob-menu .mob-cta{background:var(--blue);color:#fff!important;margin-top:16px}
#mob-close{position:absolute;top:22px;right:24px;font-size:28px;color:var(--muted);background:none;border:none;cursor:pointer;padding:4px}

/* ─── HERO ───────────────────────────────────────── */
.hero{min-height:100svh;display:flex;align-items:center;padding:100px 24px 60px;position:relative;overflow:hidden}
.hero-bg{position:absolute;inset:0;pointer-events:none}
.hero-orb{position:absolute;border-radius:50%;filter:blur(80px);opacity:.25}
.hero-orb.o1{width:500px;height:500px;background:var(--blue);top:-100px;right:-150px;animation:orbDrift 8s ease-in-out infinite}
.hero-orb.o2{width:350px;height:350px;background:var(--cyan);bottom:-60px;left:-80px;animation:orbDrift 11s ease-in-out infinite reverse}
.hero-grid{position:absolute;inset:0;background-image:linear-gradient(var(--border) 1px,transparent 1px),linear-gradient(90deg,var(--border) 1px,transparent 1px);background-size:50px 50px;mask-image:radial-gradient(ellipse 80% 80% at 50% 50%,black 0%,transparent 100%)}
@keyframes orbDrift{0%,100%{transform:translate(0,0)}50%{transform:translate(20px,-18px)}}

.hero-inner{max-width:1100px;margin:0 auto;width:100%;display:grid;grid-template-columns:1fr 1fr;align-items:center;gap:60px;position:relative}
.hero-badge{display:inline-flex;align-items:center;gap:8px;background:rgba(59,130,246,.12);border:1px solid rgba(59,130,246,.3);border-radius:99px;padding:6px 16px;font-size:12px;font-weight:500;color:var(--blue);letter-spacing:.05em;margin-bottom:24px}
.hero-badge::before{content:'';width:6px;height:6px;background:var(--blue);border-radius:50%;animation:pulse 1.8s ease infinite}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.4;transform:scale(.6)}}
.hero h1{font-family:'Syne',sans-serif;font-size:clamp(36px,5.5vw,68px);font-weight:800;line-height:1.05;letter-spacing:-2px;margin-bottom:20px}
.hero h1 .hl{background:linear-gradient(90deg,var(--blue),var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-sub{font-size:clamp(15px,2vw,18px);color:var(--muted);font-weight:300;line-height:1.65;max-width:440px;margin-bottom:36px}
.hero-btns{display:flex;gap:12px;flex-wrap:wrap}
.btn-primary{background:linear-gradient(135deg,var(--blue),var(--blue-d));color:#fff;padding:14px 28px;border-radius:99px;font-weight:600;font-size:15px;display:inline-flex;align-items:center;gap:8px;transition:all .28s;box-shadow:0 6px 32px rgba(59,130,246,.35)}
.btn-primary:hover{transform:translateY(-2px);box-shadow:0 12px 40px rgba(59,130,246,.5)}
.btn-ghost{background:var(--border);color:var(--white);padding:14px 28px;border-radius:99px;font-weight:500;font-size:15px;display:inline-flex;align-items:center;gap:8px;transition:all .28s;border:1px solid var(--border2)}
.btn-ghost:hover{background:var(--border2);transform:translateY(-2px)}

.hero-stats{display:flex;gap:32px;margin-top:44px;flex-wrap:wrap}
.hero-stat{display:flex;flex-direction:column}
.hero-stat strong{font-family:'Syne',sans-serif;font-size:28px;font-weight:800;color:var(--white)}
.hero-stat span{font-size:12px;color:var(--muted);margin-top:2px}

/* hero right: phone mockup */
.hero-visual{position:relative;display:flex;align-items:center;justify-content:center}
.phone-mock{width:220px;height:440px;background:linear-gradient(160deg,#1a1f3a,#0c0f1c);border-radius:38px;border:2px solid rgba(255,255,255,.12);position:relative;box-shadow:0 40px 80px rgba(0,0,0,.7),0 0 0 1px rgba(255,255,255,.04);display:flex;flex-direction:column;overflow:hidden;animation:floatY 4s ease-in-out infinite}
@keyframes floatY{0%,100%{transform:translateY(0)}50%{transform:translateY(-14px)}}
.phone-notch{width:90px;height:26px;background:#060810;border-radius:0 0 18px 18px;margin:0 auto;margin-top:0}
.phone-screen{flex:1;padding:14px 12px;display:flex;flex-direction:column;gap:8px}
.phone-row{display:flex;gap:8px}
.phone-card-mini{flex:1;border-radius:12px;overflow:hidden;position:relative}
.phone-card-mini.big{height:110px;background:linear-gradient(135deg,#1e3a8a,#1d4ed8)}
.phone-card-mini.sm{height:70px}
.phone-card-mini.sm1{background:linear-gradient(135deg,#065f46,#047857)}
.phone-card-mini.sm2{background:linear-gradient(135deg,#78350f,#92400e)}
.phone-inner-tag{position:absolute;bottom:6px;left:8px;font-size:7px;font-weight:600;color:rgba(255,255,255,.8);font-family:'Syne',sans-serif;letter-spacing:.5px}
.phone-shine{position:absolute;top:-40%;left:-40%;width:180%;height:180%;background:conic-gradient(from 180deg at 50% 50%,transparent 60%,rgba(59,130,246,.08) 100%);pointer-events:none;animation:spinSlow 12s linear infinite}
@keyframes spinSlow{to{transform:rotate(360deg)}}
.phone-home{width:90px;height:4px;background:rgba(255,255,255,.2);border-radius:2px;margin:10px auto}

.float-badge{position:absolute;background:var(--card2);border:1px solid var(--border2);border-radius:12px;padding:10px 14px;font-size:11px;font-weight:600;display:flex;align-items:center;gap:8px;box-shadow:0 8px 32px rgba(0,0,0,.5);animation:floatY 3.5s ease-in-out infinite}
.float-badge.f1{top:20px;left:-40px;animation-delay:.5s}
.float-badge.f2{bottom:40px;right:-35px;animation-delay:1.2s}
.float-badge .fb-icon{width:28px;height:28px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:14px}
.float-badge.f1 .fb-icon{background:rgba(16,185,129,.2);color:#10b981}
.float-badge.f2 .fb-icon{background:rgba(245,158,11,.2);color:#f59e0b}
.float-badge div{display:flex;flex-direction:column}
.float-badge strong{font-size:13px;color:var(--white)}
.float-badge small{font-size:10px;color:var(--muted)}

@media(max-width:900px){
  .hero-inner{grid-template-columns:1fr;text-align:center}
  .hero-sub{margin:0 auto 36px}
  .hero-btns{justify-content:center}
  .hero-stats{justify-content:center}
  .hero-visual{display:none}
}

/* ─── SECTION WRAPPER ────────────────────────────── */
.section{padding:90px 24px}
.section-inner{max-width:1100px;margin:0 auto}
.section-header{margin-bottom:48px}
.section-eyebrow{display:inline-flex;align-items:center;gap:6px;font-size:11px;font-weight:600;letter-spacing:.18em;text-transform:uppercase;color:var(--blue);margin-bottom:14px}
.section-eyebrow::before{content:'';display:block;width:20px;height:1px;background:var(--blue)}
.section-title{font-family:'Syne',sans-serif;font-size:clamp(28px,4vw,44px);font-weight:800;letter-spacing:-1.5px;line-height:1.1}
.section-sub{font-size:16px;color:var(--muted);font-weight:300;margin-top:12px;max-width:500px}

/* ─── CATEGORIES TABS ────────────────────────────── */
.cat-tabs{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:36px}
.cat-tab{padding:8px 18px;border-radius:99px;font-size:13px;font-weight:500;background:var(--border);color:var(--muted);border:1px solid var(--border);transition:all .22s;cursor:pointer}
.cat-tab.active,.cat-tab:hover{background:var(--blue);color:#fff;border-color:var(--blue);box-shadow:0 4px 20px rgba(59,130,246,.35)}

/* ─── PRODUCT GRID ───────────────────────────────── */
.prod-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:20px}
.prod-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;transition:all .3s;position:relative;display:flex;flex-direction:column}
.prod-card:hover{border-color:rgba(59,130,246,.35);transform:translateY(-4px);box-shadow:0 20px 50px rgba(0,0,0,.5)}
.prod-img{height:200px;display:flex;align-items:center;justify-content:center;font-size:72px;position:relative;overflow:hidden}
.prod-img::after{content:'';position:absolute;inset:0;background:linear-gradient(180deg,transparent 50%,rgba(10,14,32,.8));pointer-events:none}
.prod-badge{position:absolute;top:12px;left:12px;padding:4px 10px;border-radius:99px;font-size:10px;font-weight:700;letter-spacing:.05em;z-index:1}
.badge-hot{background:rgba(239,68,68,.9);color:#fff}
.badge-sale{background:rgba(245,158,11,.9);color:#000}
.badge-new{background:rgba(16,185,129,.9);color:#fff}
.prod-body{padding:18px;flex:1;display:flex;flex-direction:column}
.prod-name{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;margin-bottom:6px;line-height:1.3}
.prod-desc{font-size:12px;color:var(--muted);line-height:1.55;flex:1}
.prod-footer{display:flex;align-items:center;justify-content:space-between;margin-top:16px;gap:10px}
.prod-price{display:flex;flex-direction:column}
.prod-price .old{font-size:11px;color:var(--muted2);text-decoration:line-through;line-height:1}
.prod-price .cur{font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--white)}
.prod-price .cur small{font-size:12px;font-weight:400;color:var(--muted)}
.btn-buy{background:linear-gradient(135deg,var(--blue),var(--blue-d));color:#fff;padding:10px 18px;border-radius:99px;font-size:13px;font-weight:600;display:flex;align-items:center;gap:6px;transition:all .25s;white-space:nowrap;flex-shrink:0}
.btn-buy:hover{transform:scale(1.05);box-shadow:0 6px 20px rgba(59,130,246,.45)}
.btn-buy svg{width:14px;height:14px;fill:#fff}

/* ─── SERVICES ───────────────────────────────────── */
.svc-section{background:var(--bg2)}
.svc-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:20px}
.svc-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:28px;transition:all .3s;position:relative;overflow:hidden;cursor:pointer}
.svc-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--blue),var(--cyan));opacity:0;transition:opacity .3s}
.svc-card:hover{border-color:rgba(59,130,246,.3);transform:translateY(-3px);box-shadow:0 16px 44px rgba(0,0,0,.45)}
.svc-card:hover::before{opacity:1}
.svc-icon{width:52px;height:52px;background:rgba(59,130,246,.1);border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:24px;margin-bottom:18px;border:1px solid rgba(59,130,246,.2)}
.svc-name{font-family:'Syne',sans-serif;font-size:18px;font-weight:700;margin-bottom:10px}
.svc-desc{font-size:13px;color:var(--muted);line-height:1.65;margin-bottom:20px}
.svc-footer{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:12px}
.svc-price{display:flex;flex-direction:column}
.svc-price .label{font-size:10px;text-transform:uppercase;letter-spacing:.1em;color:var(--muted2)}
.svc-price .val{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;color:var(--green)}
.btn-svc{background:rgba(59,130,246,.1);border:1px solid rgba(59,130,246,.3);color:var(--blue);padding:9px 18px;border-radius:99px;font-size:13px;font-weight:600;transition:all .25s;display:flex;align-items:center;gap:6px}
.btn-svc:hover{background:var(--blue);color:#fff;border-color:var(--blue)}

/* ─── WHY US ─────────────────────────────────────── */
.why-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:20px}
.why-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:24px;text-align:center;transition:all .3s}
.why-card:hover{border-color:rgba(59,130,246,.25);transform:translateY(-3px)}
.why-icon{font-size:36px;margin-bottom:16px}
.why-title{font-family:'Syne',sans-serif;font-size:16px;font-weight:700;margin-bottom:8px}
.why-desc{font-size:13px;color:var(--muted);line-height:1.6}

/* ─── REPAIR FORM ────────────────────────────────── */
.form-section{background:var(--bg2)}
.form-wrap{max-width:700px;margin:0 auto}
.form-card{background:var(--card);border:1px solid var(--border);border-radius:20px;padding:clamp(28px,5vw,48px);position:relative;overflow:hidden}
.form-card::before{content:'';position:absolute;top:-1px;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--blue),var(--cyan),var(--blue))}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px}
@media(max-width:600px){.form-grid{grid-template-columns:1fr}}
.field{display:flex;flex-direction:column;gap:7px}
.field.full{grid-column:1/-1}
.field label{font-size:12px;font-weight:600;color:var(--muted);letter-spacing:.05em;text-transform:uppercase}
.field input,.field select,.field textarea{background:rgba(255,255,255,.04);border:1px solid var(--border2);border-radius:10px;padding:12px 16px;font-size:14px;color:var(--white);transition:all .2s}
.field input::placeholder,.field textarea::placeholder{color:var(--muted2)}
.field input:focus,.field select:focus,.field textarea:focus{border-color:var(--blue);box-shadow:0 0 0 3px rgba(59,130,246,.15);background:rgba(59,130,246,.04)}
.field select{cursor:pointer}
.field select option{background:#0c0f1c;color:var(--white)}
.field textarea{resize:vertical;min-height:100px;line-height:1.6}
.form-submit{width:100%;background:linear-gradient(135deg,var(--blue),var(--blue-d));color:#fff;padding:16px;border-radius:12px;font-size:16px;font-weight:700;display:flex;align-items:center;justify-content:center;gap:10px;margin-top:20px;transition:all .3s;box-shadow:0 8px 32px rgba(59,130,246,.35)}
.form-submit:hover{transform:translateY(-2px);box-shadow:0 14px 48px rgba(59,130,246,.5)}
.form-note{text-align:center;font-size:12px;color:var(--muted);margin-top:14px;line-height:1.6}
.form-note span{color:var(--green)}

/* ─── TESTIMONIALS ───────────────────────────────── */
.reviews-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:20px}
.review-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:24px;transition:all .3s}
.review-card:hover{border-color:var(--border2);transform:translateY(-2px)}
.review-stars{color:var(--gold);font-size:14px;margin-bottom:14px}
.review-text{font-size:14px;color:rgba(248,250,252,.75);line-height:1.7;margin-bottom:18px;font-style:italic}
.review-author{display:flex;align-items:center;gap:12px}
.review-avatar{width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:16px;font-weight:700;font-family:'Syne',sans-serif}
.review-name{font-weight:600;font-size:14px}
.review-role{font-size:11px;color:var(--muted)}

/* ─── FOOTER ─────────────────────────────────────── */
footer{background:var(--bg2);border-top:1px solid var(--border);padding:60px 24px 30px}
.footer-inner{max-width:1100px;margin:0 auto}
.footer-top{display:grid;grid-template-columns:1.5fr 1fr 1fr;gap:48px;margin-bottom:48px}
@media(max-width:768px){.footer-top{grid-template-columns:1fr;gap:32px}}
.footer-brand .logo{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;letter-spacing:-.5px;margin-bottom:14px;display:flex;align-items:center;gap:10px}
.footer-brand .logo-icon{width:32px;height:32px;background:linear-gradient(135deg,var(--blue),var(--cyan));border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:14px}
.footer-brand p{font-size:13px;color:var(--muted);line-height:1.7;max-width:280px}
.footer-social{display:flex;gap:10px;margin-top:20px}
.social-btn{width:38px;height:38px;background:var(--border);border:1px solid var(--border2);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:16px;transition:all .25s;cursor:pointer}
.social-btn:hover{background:rgba(59,130,246,.15);border-color:rgba(59,130,246,.4);transform:translateY(-2px)}
.footer-col h4{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:18px;color:var(--white)}
.footer-col ul li{margin-bottom:10px}
.footer-col ul li a{font-size:13px;color:var(--muted);transition:color .2s;display:flex;align-items:center;gap:6px}
.footer-col ul li a:hover{color:var(--white)}
.footer-hours li{display:flex;justify-content:space-between;font-size:12px;color:var(--muted);padding:6px 0;border-bottom:1px solid var(--border)}
.footer-hours li.today{color:var(--green);font-weight:600}
.footer-bottom{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:16px;padding-top:28px;border-top:1px solid var(--border)}
.footer-bottom p{font-size:12px;color:var(--muted2)}
.footer-wpp{background:linear-gradient(135deg,#25d366,#128c7e);color:#fff;padding:10px 22px;border-radius:99px;font-size:13px;font-weight:700;display:inline-flex;align-items:center;gap:8px;transition:all .28s}
.footer-wpp:hover{transform:translateY(-2px);box-shadow:0 8px 28px rgba(37,211,102,.4)}

/* ─── SCROLL REVEAL ─────────────────────────────── */
.reveal{opacity:0;transform:translateY(36px);transition:opacity .7s cubic-bezier(.22,1,.36,1),transform .7s cubic-bezier(.22,1,.36,1)}
.reveal.visible{opacity:1;transform:none}

/* ─── BACK TO TOP ─────────────────────────────────── */
#btt{position:fixed;bottom:90px;right:20px;width:44px;height:44px;background:var(--card2);border:1px solid var(--border2);border-radius:50%;display:flex;align-items:center;justify-content:center;z-index:600;opacity:0;transform:scale(.8) translateY(12px);pointer-events:none;transition:all .3s;box-shadow:0 4px 20px rgba(0,0,0,.4)}
#btt.show{opacity:1;transform:scale(1) translateY(0);pointer-events:all}
#btt:hover{background:var(--blue);border-color:var(--blue)}
#btt svg{width:18px;height:18px;stroke:var(--white);fill:none;stroke-width:2.5;stroke-linecap:round;stroke-linejoin:round}

/* ─── WHATSAPP FAB ─────────────────────────────────── */
#wpp-fab{position:fixed;bottom:24px;right:20px;width:52px;height:52px;background:#25d366;border-radius:50%;display:flex;align-items:center;justify-content:center;z-index:600;box-shadow:0 6px 24px rgba(37,211,102,.5);transition:all .3s;text-decoration:none}
#wpp-fab:hover{transform:scale(1.1);box-shadow:0 10px 36px rgba(37,211,102,.65)}
#wpp-fab svg{width:26px;height:26px;fill:#fff}

/* ─── DIVIDER ─────────────────────────────────────── */
.divider{height:1px;background:linear-gradient(90deg,transparent,var(--border2),transparent);margin:0}

/* ─── TOAST ──────────────────────────────────────── */
#toast{position:fixed;bottom:90px;left:50%;transform:translateX(-50%) translateY(20px);background:var(--card2);border:1px solid var(--border2);border-radius:12px;padding:14px 22px;font-size:14px;font-weight:500;z-index:9000;opacity:0;pointer-events:none;transition:all .35s;white-space:nowrap;box-shadow:0 8px 32px rgba(0,0,0,.5)}
#toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* ─── RESPONSIVE TWEAKS ──────────────────────────── */
@media(max-width:480px){
  .prod-grid{grid-template-columns:1fr 1fr}
  .prod-img{height:150px;font-size:52px}
  .prod-name{font-size:13px}
  .prod-price .cur{font-size:17px}
  .btn-buy{padding:8px 12px;font-size:12px}
}
@media(max-width:360px){
  .prod-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<!-- ═══ LOADER ═══════════════════════════════════════ -->
<div id="ldr">
  <div class="ldr-icon">📱</div>
  <div class="ldr-name">CelularPro</div>
  <div class="ldr-sub">Acessórios & Assistência Técnica</div>
  <div class="ldr-bar"><div class="ldr-fill"></div></div>
</div>

<!-- ═══ PROGRESS ═════════════════════════════════════ -->
<div id="prog"></div>

<!-- ═══ CURSOR ═══════════════════════════════════════ -->
<div id="cur"></div>
<div id="cur-r"></div>

<!-- ═══ TOAST ════════════════════════════════════════ -->
<div id="toast">✅ Abrindo WhatsApp...</div>

<!-- ═══ NAV ══════════════════════════════════════════ -->
<nav id="nav">
  <a href="#" class="nav-logo" data-h>
    <span class="icon">📱</span>
    CelularPro
  </a>
  <div class="nav-links">
    <a href="#produtos" data-h>Produtos</a>
    <a href="#servicos" data-h>Serviços</a>
    <a href="#sobre" data-h>Por que nós</a>
    <a href="#depoimentos" data-h>Avaliações</a>
    <a href="#conserto" class="nav-cta" data-h>Solicitar Conserto</a>
  </div>
  <div class="nav-burger" id="burger" onclick="toggleMenu()" data-h>
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- ═══ MOBILE MENU ═══════════════════════════════════ -->
<div id="mob-menu">
  <button id="mob-close" onclick="toggleMenu()">✕</button>
  <a href="#produtos" onclick="toggleMenu()" data-h>🛒 Produtos</a>
  <a href="#servicos" onclick="toggleMenu()" data-h>🔧 Serviços</a>
  <a href="#sobre" onclick="toggleMenu()" data-h>⭐ Por que nós</a>
  <a href="#depoimentos" onclick="toggleMenu()" data-h>💬 Avaliações</a>
  <a href="#conserto" class="mob-cta" onclick="toggleMenu()" data-h>Solicitar Conserto</a>
</div>

<!-- ═══ HERO ══════════════════════════════════════════ -->
<section class="hero" id="inicio">
  <div class="hero-bg">
    <div class="hero-orb o1"></div>
    <div class="hero-orb o2"></div>
    <div class="hero-grid"></div>
  </div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="hero-badge">
        <span>Assistência técnica autorizada</span>
      </div>
      <h1>Seu celular<br>em <span class="hl">perfeito estado</span><br>merece isso.</h1>
      <p class="hero-sub">Acessórios premium, consertos rápidos e garantia real. Atendemos você do diagnóstico até a entrega.</p>
      <div class="hero-btns">
        <a href="#produtos" class="btn-primary" data-h>
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>
          Ver Produtos
        </a>
        <a href="#conserto" class="btn-ghost" data-h>
          🔧 Solicitar Conserto
        </a>
      </div>
      <div class="hero-stats">
        <div class="hero-stat">
          <strong>+2.400</strong>
          <span>Clientes atendidos</span>
        </div>
        <div class="hero-stat">
          <strong>98%</strong>
          <span>Satisfação</span>
        </div>
        <div class="hero-stat">
          <strong>1 ano</strong>
          <span>Garantia</span>
        </div>
      </div>
    </div>

    <div class="hero-visual">
      <div class="phone-mock">
        <div class="phone-notch"></div>
        <div class="phone-screen">
          <div class="phone-row">
            <div class="phone-card-mini big">
              <div class="phone-inner-tag">CAPINHA PRO</div>
              <div class="phone-shine"></div>
            </div>
          </div>
          <div class="phone-row">
            <div class="phone-card-mini sm sm1"><div class="phone-inner-tag">PELÍCULA</div></div>
            <div class="phone-card-mini sm sm2"><div class="phone-inner-tag">CARREGADOR</div></div>
          </div>
          <div class="phone-row">
            <div class="phone-card-mini sm" style="background:linear-gradient(135deg,#4c1d95,#5b21b6)"><div class="phone-inner-tag">FONE BT</div></div>
            <div class="phone-card-mini sm" style="background:linear-gradient(135deg,#164e63,#0e7490)"><div class="phone-inner-tag">CABO 3M</div></div>
          </div>
        </div>
        <div class="phone-home"></div>
      </div>

      <div class="float-badge f1">
        <div class="fb-icon">✅</div>
        <div>
          <strong>Conserto concluído</strong>
          <small>Tela trocada · 45 min</small>
        </div>
      </div>
      <div class="float-badge f2">
        <div class="fb-icon">⭐</div>
        <div>
          <strong>4.9 / 5.0</strong>
          <small>312 avaliações</small>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══ PRODUTOS ══════════════════════════════════════ -->
<section class="section" id="produtos">
  <div class="section-inner">
    <div class="section-header reveal">
      <div class="section-eyebrow">Loja</div>
      <h2 class="section-title">Acessórios para o seu celular</h2>
      <p class="section-sub">Seleção premium com entrega rápida ou retirada na loja.</p>
    </div>

    <div class="cat-tabs reveal" id="cat-tabs">
      <button class="cat-tab active" data-cat="todos" onclick="filterCat('todos',this)">Todos</button>
      <button class="cat-tab" data-cat="capinha" onclick="filterCat('capinha',this)">Capinhas</button>
      <button class="cat-tab" data-cat="protecao" onclick="filterCat('protecao',this)">Proteção</button>
      <button class="cat-tab" data-cat="carregador" onclick="filterCat('carregador',this)">Carregadores</button>
      <button class="cat-tab" data-cat="cabo" onclick="filterCat('cabo',this)">Cabos</button>
      <button class="cat-tab" data-cat="audio" onclick="filterCat('audio',this)">Áudio</button>
      <button class="cat-tab" data-cat="outro" onclick="filterCat('outro',this)">Outros</button>
    </div>

    <div class="prod-grid" id="prod-grid"></div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══ SERVIÇOS ══════════════════════════════════════ -->
<section class="section svc-section" id="servicos">
  <div class="section-inner">
    <div class="section-header reveal">
      <div class="section-eyebrow">Assistência Técnica</div>
      <h2 class="section-title">Consertamos o seu celular</h2>
      <p class="section-sub">Diagnóstico gratuito, peças originais e garantia em todos os serviços.</p>
    </div>
    <div class="svc-grid" id="svc-grid"></div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══ POR QUE NÓS ═══════════════════════════════════ -->
<section class="section" id="sobre">
  <div class="section-inner">
    <div class="section-header reveal">
      <div class="section-eyebrow">Diferenciais</div>
      <h2 class="section-title">Por que a CelularPro?</h2>
    </div>
    <div class="why-grid">
      <div class="why-card reveal">
        <div class="why-icon">⚡</div>
        <div class="why-title">Rapidez</div>
        <p class="why-desc">Maioria dos consertos em até 2 horas. Você não precisa ficar sem celular por dias.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">🔒</div>
        <div class="why-title">Garantia Real</div>
        <p class="why-desc">Todo serviço tem garantia de 90 dias. Produtos com garantia de até 1 ano.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">🧩</div>
        <div class="why-title">Peças Originais</div>
        <p class="why-desc">Utilizamos componentes originais ou compatíveis de alta qualidade, sem gambiarras.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">💬</div>
        <div class="why-title">Atendimento Humano</div>
        <p class="why-desc">WhatsApp com resposta rápida. Você sempre sabe o que está acontecendo com o seu aparelho.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">📍</div>
        <div class="why-title">Fácil de Chegar</div>
        <p class="why-desc">Localização central com estacionamento. Também buscamos e entregamos em domicílio.</p>
      </div>
      <div class="why-card reveal">
        <div class="why-icon">💳</div>
        <div class="why-title">Parcelamos</div>
        <p class="why-desc">Aceitamos cartão, Pix, dinheiro. Parcelamos em até 12x sem juros no cartão de crédito.</p>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══ FORMULÁRIO DE CONSERTO ════════════════════════ -->
<section class="section form-section" id="conserto">
  <div class="section-inner">
    <div class="section-header reveal" style="text-align:center">
      <div class="section-eyebrow" style="justify-content:center">Solicitar Serviço</div>
      <h2 class="section-title">Precisa consertar seu celular?</h2>
      <p class="section-sub" style="margin:12px auto 0">Preencha o formulário e já te enviamos um orçamento pelo WhatsApp.</p>
    </div>

    <div class="form-wrap reveal">
      <div class="form-card">
        <div class="form-grid">
          <div class="field">
            <label>Seu nome</label>
            <input type="text" id="f-nome" placeholder="Ex: João Silva">
          </div>
          <div class="field">
            <label>Modelo do celular</label>
            <input type="text" id="f-modelo" placeholder="Ex: iPhone 14, Samsung S23...">
          </div>
          <div class="field">
            <label>Tipo de problema</label>
            <select id="f-tipo">
              <option value="">Selecione o problema</option>
              <option value="Troca de tela">Troca de tela</option>
              <option value="Troca de bateria">Troca de bateria</option>
              <option value="Conector de carga">Conector de carga</option>
              <option value="Câmera com defeito">Câmera com defeito</option>
              <option value="Não liga / não carrega">Não liga / não carrega</option>
              <option value="Queda na água">Queda na água</option>
              <option value="Botão quebrado">Botão quebrado</option>
              <option value="Limpeza interna">Limpeza interna</option>
              <option value="Diagnóstico">Diagnóstico geral</option>
              <option value="Outro problema">Outro problema</option>
            </select>
          </div>
          <div class="field">
            <label>Urgência</label>
            <select id="f-urgencia">
              <option value="Normal">Normal (1–2 dias)</option>
              <option value="Urgente">Urgente (mesmo dia)</option>
              <option value="Sem pressa">Sem pressa</option>
            </select>
          </div>
          <div class="field full">
            <label>Descrição do problema (opcional)</label>
            <textarea id="f-desc" placeholder="Descreva o que aconteceu com o aparelho..."></textarea>
          </div>
        </div>
        <button class="form-submit" onclick="sendRepairForm()" data-h>
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.127.558 4.126 1.528 5.858L.057 23.428a.75.75 0 0 0 .92.921l5.684-1.461A11.945 11.945 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.75a9.708 9.708 0 0 1-4.953-1.355l-.355-.212-3.679.945.974-3.58-.232-.368A9.709 9.709 0 0 1 2.25 12C2.25 6.615 6.615 2.25 12 2.25S21.75 6.615 21.75 12 17.385 21.75 12 21.75z"/></svg>
          Enviar via WhatsApp
        </button>
        <p class="form-note"><span>✓</span> Sem compromisso · Orçamento gratuito · Respondemos em minutos</p>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══ DEPOIMENTOS ═══════════════════════════════════ -->
<section class="section" id="depoimentos">
  <div class="section-inner">
    <div class="section-header reveal">
      <div class="section-eyebrow">Avaliações</div>
      <h2 class="section-title">O que nossos clientes dizem</h2>
    </div>
    <div class="reviews-grid" id="reviews-grid"></div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══ FOOTER ════════════════════════════════════════ -->
<footer>
  <div class="footer-inner">
    <div class="footer-top">
      <div class="footer-brand">
        <div class="logo">
          <span class="logo-icon">📱</span>
          CelularPro
        </div>
        <p>Assistência técnica especializada e acessórios premium para o seu celular. Qualidade e agilidade em cada atendimento.</p>
        <div class="footer-social">
          <a class="social-btn" href="https://instagram.com" target="_blank" title="Instagram">📸</a>
          <a class="social-btn" href="https://facebook.com" target="_blank" title="Facebook">👥</a>
          <a class="social-btn" href="https://wa.me/5569981133218" target="_blank" title="WhatsApp">💬</a>
        </div>
      </div>

      <div class="footer-col">
        <h4>Links Rápidos</h4>
        <ul>
          <li><a href="#produtos">🛒 Produtos</a></li>
          <li><a href="#servicos">🔧 Serviços</a></li>
          <li><a href="#sobre">⭐ Por que nós</a></li>
          <li><a href="#conserto">📋 Solicitar conserto</a></li>
          <li><a href="#depoimentos">💬 Avaliações</a></li>
        </ul>
      </div>

      <div class="footer-col">
        <h4>Horários</h4>
        <ul class="footer-hours" id="footer-hours"></ul>
        <div style="margin-top:18px;font-size:12px;color:var(--muted)">
          📍 Porto Velho, RO<br>
          <a href="https://wa.me/5569981133218" style="color:var(--green);margin-top:6px;display:block" data-h>💬 (69) 98113-3218</a>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <p>© <span id="yr"></span> CelularPro · Todos os direitos reservados</p>
      <a href="https://wa.me/5569981133218?text=Olá%2C%20vim%20pelo%20site%20e%20preciso%20de%20ajuda%21" target="_blank" class="footer-wpp" data-h>
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.127.558 4.126 1.528 5.858L.057 23.428a.75.75 0 0 0 .92.921l5.684-1.461A11.945 11.945 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.75a9.708 9.708 0 0 1-4.953-1.355l-.355-.212-3.679.945.974-3.58-.232-.368A9.709 9.709 0 0 1 2.25 12C2.25 6.615 6.615 2.25 12 2.25S21.75 6.615 21.75 12 17.385 21.75 12 21.75z"/></svg>
        Falar no WhatsApp
      </a>
    </div>
  </div>
</footer>

<!-- ═══ FABs ═══════════════════════════════════════════ -->
<a id="wpp-fab" href="https://wa.me/5569981133218?text=Olá%2C%20vim%20pelo%20site%20e%20preciso%20de%20ajuda%21" target="_blank" title="WhatsApp" data-h>
  <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.127.558 4.126 1.528 5.858L.057 23.428a.75.75 0 0 0 .92.921l5.684-1.461A11.945 11.945 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.75a9.708 9.708 0 0 1-4.953-1.355l-.355-.212-3.679.945.974-3.58-.232-.368A9.709 9.709 0 0 1 2.25 12C2.25 6.615 6.615 2.25 12 2.25S21.75 6.615 21.75 12 17.385 21.75 12 21.75z"/></svg>
</a>

<button id="btt" onclick="window.scrollTo({top:0,behavior:'smooth'})" title="Voltar ao topo">
  <svg viewBox="0 0 24 24"><polyline points="18 15 12 9 6 15"/></svg>
</button>

<!-- ═══ SCRIPT ═════════════════════════════════════════ -->
<script>
/* ── DATA ── */
const WPP = '5569981133218';

const PRODUCTS = [
  { id:1, name:'Capinha MagSafe iPhone 15 Pro', cat:'capinha', emoji:'🔵', price:89.90, old:119.90, badge:'hot', badgeLabel:'Mais Vendido', desc:'Compatível MagSafe. Material premium, proteção military grade.' },
  { id:2, name:'Capinha Samsung S24 Ultra Fosca', cat:'capinha', emoji:'🟣', price:79.90, old:null, badge:'new', badgeLabel:'Novo', desc:'Acabamento fosco anti-impressão digital. Encaixe perfeito.' },
  { id:3, name:'Capinha iPhone 14 Transparente', cat:'capinha', emoji:'⚪', price:49.90, old:null, badge:null, badgeLabel:null, desc:'Crystal clear premium, resistente a amarelamento. Anti-impacto.' },
  { id:4, name:'Película 3D Vidro Temperado', cat:'protecao', emoji:'🛡️', price:49.90, old:69.90, badge:'sale', badgeLabel:'Promoção', desc:'Vidro 9H, cobertura total, instalação gratuita na loja.' },
  { id:5, name:'Película Privacidade 360°', cat:'protecao', emoji:'🔏', price:59.90, old:null, badge:null, badgeLabel:null, desc:'Anti-espionagem. Protege sua tela de olhares curiosos.' },
  { id:6, name:'Carregador 65W GaN Ultra', cat:'carregador', emoji:'⚡', price:129.90, old:169.90, badge:'hot', badgeLabel:'Mais Vendido', desc:'Carrega 3 dispositivos simultâneos. Tecnologia GaN segura e rápida.' },
  { id:7, name:'Carregador 20W USB-C iPhone', cat:'carregador', emoji:'🍎', price:69.90, old:null, badge:null, badgeLabel:null, desc:'Compatível iPhone 12 em diante. Carga rápida original.' },
  { id:8, name:'Cabo USB-C para USB-C 2m', cat:'cabo', emoji:'🔌', price:39.90, old:null, badge:null, badgeLabel:null, desc:'Suporta 100W e dados 480Mbps. Nylon trançado reforçado.' },
  { id:9, name:'Cabo Lightning Reforçado 3m', cat:'cabo', emoji:'📏', price:44.90, old:59.90, badge:'sale', badgeLabel:'Promoção', desc:'3 metros de alcance. Revestimento anti-quebra nas pontas.' },
  { id:10, name:'Fone Bluetooth TWS Pro', cat:'audio', emoji:'🎧', price:189.90, old:249.90, badge:'hot', badgeLabel:'Mais Vendido', desc:'Cancelamento de ruído ativo, 30h de bateria, case carregador.' },
  { id:11, name:'Suporte Veicular Magnético', cat:'outro', emoji:'🚗', price:69.90, old:null, badge:null, badgeLabel:null, desc:'Fixação forte, 360°, compatível com qualquer celular.' },
  { id:12, name:'Powerbank 20.000mAh 65W', cat:'outro', emoji:'🔋', price:159.90, old:199.90, badge:'new', badgeLabel:'Novo', desc:'Carrega notebook e celular ao mesmo tempo. Display LED.' },
];

const SERVICES = [
  { icon:'📱', name:'Troca de Tela', desc:'Substituição completa do display com peça original ou compatível premium. Testamos tudo antes de entregar.', price:'A partir de R$ 199', priceVal:'R$ 199', svc:'Troca de tela' },
  { icon:'🔋', name:'Troca de Bateria', desc:'Bateria nova com desempenho original restaurado. Diagnóstico de ciclos incluso.', price:'A partir de R$ 149', priceVal:'R$ 149', svc:'Troca de bateria' },
  { icon:'🔍', name:'Diagnóstico Gratuito', desc:'Avaliamos seu aparelho completamente, sem custo. Você decide se quer seguir com o conserto.', price:'Grátis', priceVal:'Grátis', svc:'Diagnóstico gratuito' },
  { icon:'🔌', name:'Troca de Conector', desc:'Conector USB-C, Lightning ou micro-USB. Resolvemos problemas de carga lenta ou falha de conexão.', price:'A partir de R$ 120', priceVal:'R$ 120', svc:'Troca de conector de carga' },
  { icon:'🧹', name:'Limpeza Interna', desc:'Limpeza profissional de componentes, remoção de poeira e correção de superaquecimento.', price:'R$ 89', priceVal:'R$ 89', svc:'Limpeza interna' },
  { icon:'💧', name:'Recuperação Dano por Água', desc:'Tratamento especializado para aparelhos que caíram na água. Quanto antes, maiores as chances.', price:'A partir de R$ 199', priceVal:'R$ 199', svc:'Recuperação de dano por água' },
];

const REVIEWS = [
  { stars:5, text:'Troquei a tela do meu iPhone em menos de 1 hora. Ficou perfeita, sem nenhuma diferença da original. Super recomendo!', name:'Ana Claudia', role:'Cliente desde 2023', avatar:'AC', color:'#1d4ed8' },
  { stars:5, text:'Comprei uma capinha e uma película, instalaram na hora e ainda me deram uma dica de como conservar melhor. Atendimento excelente.', name:'Marcos Vinicius', role:'Cliente fidelizado', avatar:'MV', color:'#065f46' },
  { stars:5, text:'Meu celular caiu na água, achei que tinha perdido. Trouxe aqui e eles recuperaram tudo! Recomendo demais.', name:'Juliana Ferreira', role:'Cliente satisfeita', avatar:'JF', color:'#7c2d12' },
  { stars:5, text:'Atendimento rápido, preço justo e garantia real. Não levo mais meu celular em outro lugar.', name:'Roberto Santos', role:'Cliente há 2 anos', avatar:'RS', color:'#4c1d95' },
  { stars:4, text:'Bateria trocada em 40 minutos, celular voltou a durar o dia inteiro. Só ponto positivo.', name:'Fernanda Lima', role:'Cliente nova', avatar:'FL', color:'#164e63' },
  { stars:5, text:'Comprei o carregador GaN 65W e é incrível. Carrega meu notebook e celular ao mesmo tempo. Entrega rápida!', name:'Carlos Eduardo', role:'Compra online', avatar:'CE', color:'#78350f' },
];

const HOURS = [
  { day:'Segunda-feira', range:'08:00 – 18:00' },
  { day:'Terça-feira',   range:'08:00 – 18:00' },
  { day:'Quarta-feira',  range:'08:00 – 18:00' },
  { day:'Quinta-feira',  range:'08:00 – 18:00' },
  { day:'Sexta-feira',   range:'08:00 – 18:00' },
  { day:'Sábado',        range:'08:00 – 13:00' },
  { day:'Domingo',       range:'Fechado' },
];

/* ── HELPERS ── */
function wppLink(msg){ return `https://wa.me/${WPP}?text=${encodeURIComponent(msg)}`; }

function showToast(){
  const t = document.getElementById('toast');
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'), 2200);
}

function buyProduct(name, price){
  const msg = `Olá! Vim pelo site da CelularPro e tenho interesse em comprar:\n\n🛒 *${name}*\n💰 R$ ${price.toFixed(2).replace('.',',')}\n\nPoderia me dar mais informações?`;
  showToast();
  setTimeout(()=>window.open(wppLink(msg),'_blank'), 400);
}

function requestService(svc, price){
  const msg = `Olá! Vim pelo site da CelularPro e preciso de:\n\n🔧 *${svc}*\n💰 ${price}\n\nPoderia me dar mais informações e agendar?`;
  showToast();
  setTimeout(()=>window.open(wppLink(msg),'_blank'), 400);
}

function sendRepairForm(){
  const nome    = document.getElementById('f-nome').value.trim();
  const modelo  = document.getElementById('f-modelo').value.trim();
  const tipo    = document.getElementById('f-tipo').value;
  const urgencia= document.getElementById('f-urgencia').value;
  const desc    = document.getElementById('f-desc').value.trim();

  if(!nome){ alert('Por favor, informe seu nome.'); return; }
  if(!modelo){ alert('Por favor, informe o modelo do celular.'); return; }
  if(!tipo){ alert('Por favor, selecione o tipo de problema.'); return; }

  let msg = `Olá! Vim pelo site da CelularPro e preciso de assistência:\n\n`;
  msg += `👤 *Nome:* ${nome}\n`;
  msg += `📱 *Aparelho:* ${modelo}\n`;
  msg += `🔧 *Problema:* ${tipo}\n`;
  msg += `⚡ *Urgência:* ${urgencia}\n`;
  if(desc) msg += `📝 *Detalhes:* ${desc}\n`;
  msg += `\nAguardo o orçamento. Obrigado!`;

  showToast();
  setTimeout(()=>window.open(wppLink(msg),'_blank'), 400);
}

/* ── RENDER PRODUCTS ── */
function renderProducts(cat){
  const grid = document.getElementById('prod-grid');
  const items = cat === 'todos' ? PRODUCTS : PRODUCTS.filter(p=>p.cat===cat);
  grid.innerHTML = items.map(p=>`
    <div class="prod-card reveal">
      <div class="prod-img" style="background:linear-gradient(135deg,#0f172a,#1e293b)">
        <span>${p.emoji}</span>
        ${p.badge ? `<span class="prod-badge badge-${p.badge}">${p.badgeLabel}</span>` : ''}
      </div>
      <div class="prod-body">
        <div class="prod-name">${p.name}</div>
        <div class="prod-desc">${p.desc}</div>
        <div class="prod-footer">
          <div class="prod-price">
            ${p.old ? `<span class="old">R$ ${p.old.toFixed(2).replace('.',',')}</span>` : ''}
            <span class="cur">R$ ${p.price.toFixed(2).replace('.',',')}<small></small></span>
          </div>
          <button class="btn-buy" onclick="buyProduct('${p.name}',${p.price})">
            <svg viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.127.558 4.126 1.528 5.858L.057 23.428a.75.75 0 0 0 .92.921l5.684-1.461A11.945 11.945 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.75a9.708 9.708 0 0 1-4.953-1.355l-.355-.212-3.679.945.974-3.58-.232-.368A9.709 9.709 0 0 1 2.25 12C2.25 6.615 6.615 2.25 12 2.25S21.75 6.615 21.75 12 17.385 21.75 12 21.75z"/></svg>
            Comprar
          </button>
        </div>
      </div>
    </div>
  `).join('');
  observeReveal();
}

function filterCat(cat, btn){
  document.querySelectorAll('.cat-tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderProducts(cat);
}

/* ── RENDER SERVICES ── */
function renderServices(){
  document.getElementById('svc-grid').innerHTML = SERVICES.map(s=>`
    <div class="svc-card reveal" onclick="requestService('${s.svc}','${s.priceVal}')">
      <div class="svc-icon">${s.icon}</div>
      <div class="svc-name">${s.name}</div>
      <p class="svc-desc">${s.desc}</p>
      <div class="svc-footer">
        <div class="svc-price">
          <span class="label">Preço</span>
          <span class="val">${s.priceVal}</span>
        </div>
        <button class="btn-svc">
          Solicitar
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
        </button>
      </div>
    </div>
  `).join('');
}

/* ── RENDER REVIEWS ── */
function renderReviews(){
  document.getElementById('reviews-grid').innerHTML = REVIEWS.map(r=>`
    <div class="review-card reveal">
      <div class="review-stars">${'★'.repeat(r.stars)}${'☆'.repeat(5-r.stars)}</div>
      <p class="review-text">"${r.text}"</p>
      <div class="review-author">
        <div class="review-avatar" style="background:${r.color}22;color:${r.color};border:1px solid ${r.color}44">${r.avatar}</div>
        <div>
          <div class="review-name">${r.name}</div>
          <div class="review-role">${r.role}</div>
        </div>
      </div>
    </div>
  `).join('');
}

/* ── RENDER HOURS ── */
function renderHours(){
  const day = new Date().getDay(); // 0=sun
  const map = [6,0,1,2,3,4,5]; // map JS day to HOURS index
  const todayI = map[day];
  document.getElementById('footer-hours').innerHTML = HOURS.map((h,i)=>`
    <li class="${i===todayI?'today':''}">
      <span>${h.day}</span><span>${h.range}</span>
    </li>
  `).join('');
}

/* ── SCROLL REVEAL ── */
function observeReveal(){
  const obs = new IntersectionObserver(entries=>{
    entries.forEach(e=>{
      if(e.isIntersecting){ e.target.classList.add('visible'); obs.unobserve(e.target); }
    });
  },{threshold:.12});
  document.querySelectorAll('.reveal:not(.visible)').forEach(el=>obs.observe(el));
}

/* ── NAV SCROLL ── */
window.addEventListener('scroll',()=>{
  const s = window.scrollY;
  document.getElementById('nav').classList.toggle('scrolled', s>40);
  document.getElementById('btt').classList.toggle('show', s>400);
  // progress bar
  const doc = document.documentElement;
  const pct = (s/(doc.scrollHeight-doc.clientHeight))*100;
  document.getElementById('prog').style.width = pct+'%';
});

/* ── MOBILE MENU ── */
function toggleMenu(){
  document.getElementById('mob-menu').classList.toggle('open');
}

/* ── CURSOR ── */
(function(){
  const cur = document.getElementById('cur');
  const curR = document.getElementById('cur-r');
  if(!cur) return;
  let mx=0,my=0,rx=0,ry=0;
  document.addEventListener('mousemove',e=>{ mx=e.clientX; my=e.clientY; cur.style.left=mx+'px'; cur.style.top=my+'px'; });
  function animR(){ rx+=(mx-rx)*.12; ry+=(my-ry)*.12; curR.style.left=rx+'px'; curR.style.top=ry+'px'; requestAnimationFrame(animR); }
  animR();
  document.querySelectorAll('[data-h]').forEach(el=>{
    el.addEventListener('mouseenter',()=>document.body.classList.add('hov'));
    el.addEventListener('mouseleave',()=>document.body.classList.remove('hov'));
  });
})();

/* ── LOADER ── */
window.addEventListener('load',()=>{
  setTimeout(()=>document.getElementById('ldr').classList.add('out'), 1800);
});

/* ── INIT ── */
document.getElementById('yr').textContent = new Date().getFullYear();
renderProducts('todos');
renderServices();
renderReviews();
renderHours();
observeReveal();
</script>
</body>
</html>
