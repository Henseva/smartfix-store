<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<meta name="description" content="CelularPro — Assistência técnica premium e acessórios para celular em Porto Velho. Diagnóstico grátis, garantia real.">
<meta name="theme-color" content="#05060f">
<title>CelularPro — Assistência Técnica & Acessórios Premium</title>
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&display=swap" rel="stylesheet">

<style>
/* ═══════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════ */
:root{
  --bg:        #05060f;
  --bg2:       #090b18;
  --bg3:       #0c0f1f;
  --glass:     rgba(255,255,255,.038);
  --glass2:    rgba(255,255,255,.065);
  --border:    rgba(255,255,255,.07);
  --border2:   rgba(255,255,255,.13);
  --blue:      #3b82f6;
  --blue-d:    #2563eb;
  --blue-l:    #60a5fa;
  --cyan:      #22d3ee;
  --cyan-d:    #06b6d4;
  --gold:      #f59e0b;
  --green:     #34d399;
  --red:       #f87171;
  --white:     #f8fafc;
  --muted:     rgba(248,250,252,.45);
  --muted2:    rgba(248,250,252,.22);
  --radius:    18px;
  --radius-sm: 12px;
  --shadow:    0 20px 60px rgba(0,0,0,.55);
  --glow:      0 0 40px rgba(59,130,246,.25);
  --grad-main: linear-gradient(135deg,var(--blue),var(--cyan));
  --grad-text: linear-gradient(90deg,var(--white) 0%,var(--blue-l) 100%);
}

/* ═══════════════════════════════════════════
   RESET
═══════════════════════════════════════════ */
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--white);font-family:'DM Sans',sans-serif;overflow-x:hidden;-webkit-tap-highlight-color:transparent}
a{text-decoration:none;color:inherit}
button{cursor:pointer;font-family:inherit;border:none;outline:none}
input,select,textarea{font-family:inherit;outline:none}
ul{list-style:none}
img{display:block;max-width:100%}
::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--blue);border-radius:99px}

/* ═══════════════════════════════════════════
   CURSOR (desktop)
═══════════════════════════════════════════ */
@media(min-width:769px){
  body{cursor:none}
  #cur{width:7px;height:7px;background:var(--blue);border-radius:50%;position:fixed;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:transform .1s,background .18s,width .2s,height .2s}
  #cur-r{width:28px;height:28px;border:1.5px solid rgba(59,130,246,.45);border-radius:50%;position:fixed;pointer-events:none;z-index:9997;transform:translate(-50%,-50%);transition:width .22s,height .22s,border-color .22s}
  body.hov #cur{transform:translate(-50%,-50%) scale(2.5);background:var(--cyan);width:7px;height:7px}
  body.hov #cur-r{width:50px;height:50px;border-color:rgba(34,211,238,.3)}
}
@media(max-width:768px){#cur,#cur-r{display:none}}

/* ═══════════════════════════════════════════
   PROGRESS BAR
═══════════════════════════════════════════ */
#prog{position:fixed;top:0;left:0;height:2px;background:var(--grad-main);z-index:10000;width:0;transition:width .06s linear}

/* ═══════════════════════════════════════════
   LOADER
═══════════════════════════════════════════ */
#ldr{position:fixed;inset:0;z-index:99999;background:var(--bg);display:flex;flex-direction:column;align-items:center;justify-content:center;transition:opacity .9s ease,visibility .9s}
#ldr.out{opacity:0;visibility:hidden;pointer-events:none}
.ldr-ring{width:60px;height:60px;border:2px solid var(--border2);border-top-color:var(--blue);border-radius:50%;animation:spin .8s linear infinite;margin-bottom:28px}
@keyframes spin{to{transform:rotate(360deg)}}
.ldr-logo{font-family:'Syne',sans-serif;font-size:clamp(24px,5vw,36px);font-weight:800;letter-spacing:-1px;background:var(--grad-text);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.ldr-sub{font-size:11px;letter-spacing:.22em;text-transform:uppercase;color:var(--muted);margin-top:10px}
.ldr-bar{width:100px;height:1px;background:var(--border);margin-top:28px;overflow:hidden}
.ldr-fill{height:100%;background:var(--grad-main);animation:fill 2s ease forwards}
@keyframes fill{to{width:100%}}

/* ═══════════════════════════════════════════
   ANNOUNCE BAR
═══════════════════════════════════════════ */
#announce{background:var(--grad-main);color:#fff;text-align:center;padding:10px 48px;font-size:12.5px;font-weight:500;letter-spacing:.03em;position:relative;display:flex;align-items:center;justify-content:center;gap:8px}
#announce a{color:#fff;font-weight:700;text-decoration:underline;text-underline-offset:2px}
#announce-close{position:absolute;right:16px;top:50%;transform:translateY(-50%);background:none;border:none;color:rgba(255,255,255,.7);font-size:18px;cursor:pointer;line-height:1;padding:2px 6px}
#announce-close:hover{color:#fff}
#announce.gone{display:none}

/* ═══════════════════════════════════════════
   NAV
═══════════════════════════════════════════ */
nav{position:fixed;top:0;left:0;right:0;z-index:900;padding:16px 28px;display:flex;align-items:center;justify-content:space-between;transition:all .35s}
nav.with-bar{top:40px}
nav.scrolled{background:rgba(5,6,15,.82);backdrop-filter:blur(24px);-webkit-backdrop-filter:blur(24px);border-bottom:1px solid var(--border);padding:12px 28px}
nav.scrolled.with-bar{top:0}
.nav-logo{display:flex;align-items:center;gap:10px;font-family:'Syne',sans-serif;font-weight:800;font-size:19px;letter-spacing:-.5px}
.nav-logo .logo-chip{width:32px;height:32px;background:var(--grad-main);border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:15px;flex-shrink:0;box-shadow:0 4px 16px rgba(59,130,246,.4)}
.nav-links{display:flex;align-items:center;gap:4px}
.nav-links a{font-size:13px;font-weight:500;color:var(--muted);padding:7px 14px;border-radius:99px;transition:all .2s}
.nav-links a:hover{color:var(--white);background:var(--glass2)}
.nav-cta-link{background:var(--blue)!important;color:#fff!important;font-weight:600!important;box-shadow:0 4px 20px rgba(59,130,246,.35)}
.nav-cta-link:hover{background:var(--blue-d)!important;transform:translateY(-1px);box-shadow:0 8px 28px rgba(59,130,246,.5)!important}
.nav-burger{display:none;flex-direction:column;gap:5px;cursor:pointer;padding:6px}
.nav-burger span{width:22px;height:2px;background:var(--white);border-radius:2px;transition:all .3s;display:block}
@media(max-width:900px){.nav-links{display:none}.nav-burger{display:flex}}

/* ═══════════════════════════════════════════
   MOBILE MENU
═══════════════════════════════════════════ */
#mob-menu{position:fixed;inset:0;background:rgba(5,6,15,.97);backdrop-filter:blur(32px);z-index:850;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:6px;opacity:0;pointer-events:none;transition:opacity .3s}
#mob-menu.open{opacity:1;pointer-events:all}
#mob-menu a{font-family:'Syne',sans-serif;font-size:clamp(20px,5.5vw,30px);font-weight:700;color:var(--muted);padding:12px 32px;border-radius:12px;transition:all .2s;text-align:center;width:100%;max-width:320px}
#mob-menu a:hover,#mob-menu a:active{color:var(--white);background:var(--glass2)}
.mob-cta{background:var(--blue)!important;color:#fff!important;margin-top:12px;box-shadow:0 6px 24px rgba(59,130,246,.4)!important}
#mob-close{position:absolute;top:22px;right:22px;font-size:26px;color:var(--muted);background:none;border:none;cursor:pointer;padding:4px 8px}

/* ═══════════════════════════════════════════
   HERO
═══════════════════════════════════════════ */
.hero{min-height:100svh;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:130px 24px 80px;position:relative;overflow:hidden;text-align:center}
.hero-bg{position:absolute;inset:0;pointer-events:none;overflow:hidden}
.orb{position:absolute;border-radius:50%;filter:blur(90px)}
.orb1{width:600px;height:600px;background:rgba(59,130,246,.18);top:-200px;right:-200px;animation:drift 10s ease-in-out infinite}
.orb2{width:450px;height:450px;background:rgba(34,211,238,.12);bottom:-150px;left:-150px;animation:drift 13s ease-in-out infinite reverse}
.orb3{width:300px;height:300px;background:rgba(59,130,246,.1);top:40%;left:30%;animation:drift 8s ease-in-out infinite 2s}
@keyframes drift{0%,100%{transform:translate(0,0)}50%{transform:translate(22px,-16px)}}
.hero-grid{position:absolute;inset:0;background-image:linear-gradient(var(--border) 1px,transparent 1px),linear-gradient(90deg,var(--border) 1px,transparent 1px);background-size:48px 48px;mask-image:radial-gradient(ellipse 90% 90% at 50% 50%,black 0%,transparent 100%);opacity:.7}

.hero-eyebrow{display:inline-flex;align-items:center;gap:10px;background:rgba(59,130,246,.1);border:1px solid rgba(59,130,246,.25);border-radius:99px;padding:7px 18px;margin-bottom:28px;font-size:12px;font-weight:600;letter-spacing:.08em;color:var(--blue-l)}
.hero-eyebrow .dot{width:6px;height:6px;background:#34d399;border-radius:50%;animation:pulse 1.6s ease infinite;flex-shrink:0}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.3;transform:scale(.5)}}

h1.hero-title{font-family:'Syne',sans-serif;font-size:clamp(38px,7vw,80px);font-weight:800;line-height:1.03;letter-spacing:-2.5px;max-width:860px;margin:0 auto 22px}
h1.hero-title .hl{background:var(--grad-main);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-sub{font-size:clamp(15px,2.2vw,20px);color:var(--muted);font-weight:300;line-height:1.7;max-width:520px;margin:0 auto 38px}

.hero-btns{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;margin-bottom:52px}
.btn-hero-primary{background:var(--grad-main);color:#fff;padding:16px 32px;border-radius:99px;font-weight:700;font-size:15px;display:inline-flex;align-items:center;gap:9px;transition:all .3s;box-shadow:0 8px 40px rgba(59,130,246,.4)}
.btn-hero-primary:hover{transform:translateY(-3px);box-shadow:0 16px 50px rgba(59,130,246,.55)}
.btn-hero-ghost{background:var(--glass);border:1px solid var(--border2);color:var(--white);padding:16px 32px;border-radius:99px;font-weight:500;font-size:15px;display:inline-flex;align-items:center;gap:9px;transition:all .3s;backdrop-filter:blur(12px)}
.btn-hero-ghost:hover{background:var(--glass2);transform:translateY(-3px);border-color:rgba(255,255,255,.22)}

.hero-trust{display:flex;align-items:center;justify-content:center;gap:32px;flex-wrap:wrap}
.ht-item{display:flex;flex-direction:column;align-items:center;gap:4px}
.ht-item strong{font-family:'Syne',sans-serif;font-size:clamp(22px,4vw,32px);font-weight:800;background:var(--grad-text);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.ht-item span{font-size:11px;color:var(--muted);letter-spacing:.05em}
.ht-div{width:1px;height:36px;background:var(--border2)}

/* ═══════════════════════════════════════════
   TICKER
═══════════════════════════════════════════ */
.ticker-wrap{overflow:hidden;background:var(--bg2);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:14px 0}
.ticker-inner{display:flex;gap:0;white-space:nowrap;animation:tickerScroll 28s linear infinite}
.ticker-inner:hover{animation-play-state:paused}
.ticker-item{display:inline-flex;align-items:center;gap:8px;padding:0 32px;font-size:12.5px;font-weight:500;color:var(--muted);letter-spacing:.04em;white-space:nowrap}
.ticker-item .ti-icon{font-size:14px}
.ticker-dot{color:var(--blue);font-size:8px}
@keyframes tickerScroll{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ═══════════════════════════════════════════
   SECTION BASE
═══════════════════════════════════════════ */
.section{padding:96px 24px}
.section-inner{max-width:1140px;margin:0 auto}
.section-header{margin-bottom:52px}
.section-header.center{text-align:center}
.section-header.center .section-sub{margin:12px auto 0}
.section-eyebrow{display:inline-flex;align-items:center;gap:8px;font-size:11px;font-weight:700;letter-spacing:.2em;text-transform:uppercase;color:var(--blue);margin-bottom:14px}
.section-eyebrow::before{content:'';display:block;width:18px;height:1.5px;background:var(--blue)}
.center .section-eyebrow{display:flex;justify-content:center}
.center .section-eyebrow::before{display:none}
.section-title{font-family:'Syne',sans-serif;font-size:clamp(28px,4.5vw,48px);font-weight:800;letter-spacing:-1.8px;line-height:1.08}
.section-sub{font-size:16px;color:var(--muted);font-weight:300;margin-top:12px;max-width:520px;line-height:1.7}

/* ═══════════════════════════════════════════
   DIVIDERS
═══════════════════════════════════════════ */
.divider{height:1px;background:linear-gradient(90deg,transparent,var(--border2) 30%,var(--border2) 70%,transparent)}

/* ═══════════════════════════════════════════
   BUTTONS
═══════════════════════════════════════════ */
.btn-blue{background:var(--grad-main);color:#fff;padding:12px 24px;border-radius:99px;font-weight:600;font-size:14px;display:inline-flex;align-items:center;gap:7px;transition:all .28s;box-shadow:0 4px 24px rgba(59,130,246,.3)}
.btn-blue:hover{transform:translateY(-2px);box-shadow:0 10px 36px rgba(59,130,246,.5)}
.btn-outline{background:transparent;border:1px solid var(--border2);color:var(--white);padding:12px 24px;border-radius:99px;font-weight:500;font-size:14px;display:inline-flex;align-items:center;gap:7px;transition:all .28s}
.btn-outline:hover{background:var(--glass2);border-color:rgba(255,255,255,.25)}

/* ═══════════════════════════════════════════
   CATEGORY TABS
═══════════════════════════════════════════ */
.cat-tabs{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:40px}
.cat-tab{padding:9px 20px;border-radius:99px;font-size:13px;font-weight:500;background:var(--glass);color:var(--muted);border:1px solid var(--border);transition:all .22s;cursor:pointer;backdrop-filter:blur(10px)}
.cat-tab.active,.cat-tab:hover{background:var(--blue);color:#fff;border-color:var(--blue);box-shadow:0 4px 20px rgba(59,130,246,.35)}

/* ═══════════════════════════════════════════
   PRODUCT CARDS
═══════════════════════════════════════════ */
.prod-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(250px,1fr));gap:20px}

.prod-card{background:var(--glass);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;transition:all .35s;position:relative;display:flex;flex-direction:column;backdrop-filter:blur(12px);-webkit-backdrop-filter:blur(12px)}
.prod-card:hover{border-color:rgba(59,130,246,.3);transform:translateY(-6px);box-shadow:0 24px 60px rgba(0,0,0,.55),var(--glow)}

.prod-img{height:200px;display:flex;align-items:center;justify-content:center;font-size:68px;position:relative;overflow:hidden;background:var(--bg3)}
.prod-img::after{content:'';position:absolute;inset:0;background:linear-gradient(180deg,transparent 40%,rgba(5,6,15,.85));pointer-events:none}
/* category-specific gradients */
.prod-img.capinha{background:linear-gradient(135deg,#0f1740,#1e2f6e)}
.prod-img.protecao{background:linear-gradient(135deg,#0c2340,#1a4a7a)}
.prod-img.carregador{background:linear-gradient(135deg,#1a0a2e,#3b1f7a)}
.prod-img.cabo{background:linear-gradient(135deg,#0a1f20,#0f4a50)}
.prod-img.audio{background:linear-gradient(135deg,#200a2e,#5b1f7a)}
.prod-img.outro{background:linear-gradient(135deg,#1a200a,#3a500f)}

.prod-badge{position:absolute;top:12px;left:12px;padding:4px 11px;border-radius:99px;font-size:10px;font-weight:700;letter-spacing:.04em;z-index:2;backdrop-filter:blur(8px)}
.badge-hot{background:rgba(248,113,113,.9);color:#fff}
.badge-sale{background:rgba(245,158,11,.9);color:#000}
.badge-new{background:rgba(52,211,153,.9);color:#000}

.prod-body{padding:18px 18px 20px;flex:1;display:flex;flex-direction:column}
.prod-name{font-family:'Syne',sans-serif;font-size:14.5px;font-weight:700;margin-bottom:7px;line-height:1.35;color:var(--white)}
.prod-desc{font-size:12px;color:var(--muted);line-height:1.6;flex:1}
.prod-footer{display:flex;align-items:center;justify-content:space-between;margin-top:16px;gap:8px}
.prod-price{display:flex;flex-direction:column;min-width:0}
.prod-price .old{font-size:10.5px;color:var(--muted2);text-decoration:line-through;line-height:1}
.prod-price .cur{font-family:'Syne',sans-serif;font-size:21px;font-weight:800;color:var(--white);line-height:1.1}
.prod-price .cur em{font-size:11.5px;font-style:normal;font-weight:400;color:var(--muted)}
.btn-buy{background:var(--grad-main);color:#fff;padding:10px 16px;border-radius:99px;font-size:12.5px;font-weight:700;display:inline-flex;align-items:center;gap:5px;transition:all .25s;white-space:nowrap;flex-shrink:0;box-shadow:0 4px 16px rgba(59,130,246,.3)}
.btn-buy:hover{transform:scale(1.07);box-shadow:0 8px 28px rgba(59,130,246,.5)}

/* ═══════════════════════════════════════════
   SERVICES
═══════════════════════════════════════════ */
.svc-section{background:var(--bg2)}
.svc-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:22px}

.svc-card{background:var(--glass);border:1px solid var(--border);border-radius:var(--radius);padding:30px;transition:all .32s;position:relative;overflow:hidden;cursor:pointer;backdrop-filter:blur(12px)}
.svc-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--grad-main);opacity:0;transition:opacity .3s}
.svc-card::after{content:'';position:absolute;inset:0;background:radial-gradient(circle at 80% 20%,rgba(59,130,246,.06),transparent 60%);opacity:0;transition:opacity .3s}
.svc-card:hover{border-color:rgba(59,130,246,.28);transform:translateY(-4px);box-shadow:var(--shadow),var(--glow)}
.svc-card:hover::before,.svc-card:hover::after{opacity:1}

.svc-icon{width:54px;height:54px;background:rgba(59,130,246,.1);border-radius:15px;display:flex;align-items:center;justify-content:center;font-size:24px;margin-bottom:20px;border:1px solid rgba(59,130,246,.18);transition:all .3s}
.svc-card:hover .svc-icon{background:rgba(59,130,246,.18);transform:scale(1.08)}
.svc-name{font-family:'Syne',sans-serif;font-size:18px;font-weight:700;margin-bottom:10px;color:var(--white)}
.svc-desc{font-size:13px;color:var(--muted);line-height:1.65;margin-bottom:22px}
.svc-footer{display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap}
.svc-price-block .label{font-size:10px;text-transform:uppercase;letter-spacing:.1em;color:var(--muted2)}
.svc-price-block .val{font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--green)}
.btn-svc{background:rgba(59,130,246,.1);border:1px solid rgba(59,130,246,.25);color:var(--blue-l);padding:10px 20px;border-radius:99px;font-size:13px;font-weight:600;display:inline-flex;align-items:center;gap:6px;transition:all .25s}
.btn-svc:hover{background:var(--blue);color:#fff;border-color:var(--blue);transform:scale(1.03)}

/* ═══════════════════════════════════════════
   STATS BAND
═══════════════════════════════════════════ */
.stats-band{background:linear-gradient(135deg,var(--bg2) 0%,rgba(59,130,246,.06) 50%,var(--bg2) 100%);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:60px 24px;position:relative;overflow:hidden}
.stats-band::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse 60% 100% at 50% 50%,rgba(59,130,246,.08),transparent)}
.stats-band-inner{max-width:1140px;margin:0 auto;display:flex;align-items:center;justify-content:space-around;flex-wrap:wrap;gap:32px;position:relative}
.stat-item{text-align:center;display:flex;flex-direction:column;align-items:center;gap:8px}
.stat-number{font-family:'Syne',sans-serif;font-size:clamp(36px,6vw,56px);font-weight:800;background:var(--grad-main);-webkit-background-clip:text;-webkit-text-fil
