<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>My First English Adventure</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px);
  padding-bottom:env(safe-area-inset-bottom,0px);
  --bg:#fff6ea; --paper:#ffffff; --card:#fffdf9; --ink:#4a3f6b; --ink2:#7d7299; --line:#eadff5;
  --t-info:#fff0d9; --t-alpha:#ffe0ec; --t-num:#d8ecff; --t-ani:#d5f5de; --t-col:#e9dcfb; --t-game:#fff4bf; --t-rev:#ffe4cf;
  --dot:#b49be0; --dotfill:#f6f1fd; --shadow:0 10px 30px rgba(120,90,160,.16);
  --bar:rgba(255,255,255,.92); --ok:#d9f7df; --okline:#3fb55a; --bad:#ffe2e2; --badline:#e57373;
  --btn-ink:#3d3360; --btn-bg:#ffd93d;
  color-scheme:light;
}
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){
    --bg:#241f38; --paper:#2e2748; --card:#383058; --ink:#f1eaff; --ink2:#bdb2dd; --line:#4d4377;
    --t-info:#55422f; --t-alpha:#5a3550; --t-num:#2d4766; --t-ani:#2c5342; --t-col:#4b3a72; --t-game:#5a5230; --t-rev:#5d4132;
    --dot:#a58be0; --dotfill:#3d3560; --shadow:0 10px 30px rgba(0,0,0,.45);
    --bar:rgba(46,39,72,.94); --ok:#24523a; --bad:#5b2a35; color-scheme:dark;
  }
}
:root[data-theme="dark"]{
  --bg:#241f38; --paper:#2e2748; --card:#383058; --ink:#f1eaff; --ink2:#bdb2dd; --line:#4d4377;
  --t-info:#55422f; --t-alpha:#5a3550; --t-num:#2d4766; --t-ani:#2c5342; --t-col:#4b3a72; --t-game:#5a5230; --t-rev:#5d4132;
  --dot:#a58be0; --dotfill:#3d3560; --shadow:0 10px 30px rgba(0,0,0,.45);
  --bar:rgba(46,39,72,.94); --ok:#24523a; --bad:#5b2a35; color-scheme:dark;
}
html{scroll-padding-top:env(safe-area-inset-top,0px);height:100%}
*,*::before,*::after{box-sizing:border-box}
body{height:100%;margin:0;background:var(--bg);color:var(--ink);
  font-family:'Fredoka','Baloo 2','Nunito','Trebuchet MS','Comic Sans MS',ui-rounded,system-ui,sans-serif;
  font-size:18px;line-height:1.35;-webkit-tap-highlight-color:transparent}
button,input{font-family:inherit;color:inherit}
button{cursor:pointer}
:focus-visible{outline:4px solid #4d9de0;outline-offset:3px}
 
/* ---------- app shell ---------- */
#app{display:flex;flex-direction:column;height:100%}
.toolbar{flex:none;display:flex;align-items:center;gap:8px;padding:8px 12px;background:var(--bar);border-bottom:2px solid var(--line);position:relative;z-index:20}
.ttl{flex:1;min-width:0;font-weight:700;font-size:18px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.tbtn{font-weight:600;font-size:16px;min-height:44px;padding:0 14px;border-radius:999px;border:2px solid var(--line);background:var(--card);color:var(--ink);display:inline-flex;align-items:center;gap:6px;list-style:none}
.tbtn.static{cursor:default}
.tbtn[aria-pressed="true"]{background:var(--btn-bg);color:var(--btn-ink);border-color:#e0b800}
summary.tbtn::-webkit-details-marker{display:none}
details.pm{position:relative}
.pm .menu{position:absolute;right:0;top:52px;z-index:30;background:var(--paper);border:2px solid var(--line);border-radius:18px;padding:8px;display:grid;gap:6px;min-width:240px;box-shadow:var(--shadow)}
.pm .menu button{text-align:left;border-radius:12px;border:0;background:var(--card);padding:12px;font-size:16px;font-weight:500;min-height:44px}
#stage{flex:1;overflow:auto;padding:14px 12px 28px}
.navbar{flex:none;display:flex;align-items:center;justify-content:space-between;gap:10px;padding:8px 12px;background:var(--bar);border-top:2px solid var(--line)}
.nbtn{min-width:112px;min-height:54px;font-size:20px;font-weight:700;border:0;border-radius:999px;background:var(--btn-bg);color:var(--btn-ink);box-shadow:0 4px 0 #e0b800}
.nbtn:active{transform:translateY(3px);box-shadow:0 1px 0 #e0b800}
.nbtn[disabled]{opacity:.4;box-shadow:none;cursor:default}
.pgno{font-weight:600;text-align:center;font-size:16px}
@media (max-width:560px){.hide-s{display:none}.nbtn{min-width:92px}}
 
.drawer{position:fixed;inset:0;z-index:40;display:none}
.drawer.open{display:block}
.dback{position:absolute;inset:0;background:rgba(40,30,70,.5)}
.dpanel{position:absolute;left:0;top:0;bottom:0;width:min(400px,92vw);background:var(--paper);overflow:auto;padding:calc(14px + env(safe-area-inset-top,0px)) 14px calc(18px + env(safe-area-inset-bottom,0px))}
.dhead{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;font-size:22px}
.dsec{margin:14px 0 6px;font-weight:700;font-size:17px;color:var(--ink2)}
.ditem{display:flex;gap:10px;align-items:center;width:100%;text-align:left;border:0;background:var(--card);border-radius:14px;padding:8px 10px;margin-bottom:5px;font-size:17px;min-height:44px}
.ditem.on{background:var(--btn-bg);color:var(--btn-ink)}
.dn{min-width:30px;font-weight:700;color:var(--ink2)}
.ditem.on .dn{color:var(--btn-ink)}
 
/* ---------- page ---------- */
.page{display:none;max-width:940px;margin:0 auto;background:var(--paper);border:4px solid var(--tint);border-radius:32px;padding:18px 20px 12px;box-shadow:var(--shadow)}
.page.cur{display:block;animation:pop .3s ease-out both}
@keyframes pop{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}
.t-info{--tint:var(--t-info);--acc:#d9467f}
.t-alpha{--tint:var(--t-alpha);--acc:#d9467f}
.t-num{--tint:var(--t-num);--acc:#2c80d4}
.t-ani{--tint:var(--t-ani);--acc:#2a9f4b}
.t-col{--tint:var(--t-col);--acc:#8a52c4}
.t-game{--tint:var(--t-game);--acc:#c98e00}
.t-rev{--tint:var(--t-rev);--acc:#e0701f}
.phead{background:var(--tint);border-radius:24px;padding:12px 16px;display:flex;align-items:center;gap:12px;flex-wrap:wrap}
.phead .txt{flex:1;min-width:210px}
.chips{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:6px}
.chip{font-size:13px;font-weight:600;padding:3px 10px;border-radius:999px;background:var(--paper);color:var(--ink);border:2px solid var(--line)}
.chip.k-learn{background:#dcd0f7;color:#44307a;border-color:#dcd0f7}
.chip.k-play{background:#c9f2d4;color:#1e5a33;border-color:#c9f2d4}
.chip.k-print{background:#ffe3b8;color:#7a4300;border-color:#ffe3b8}
.ptitle{margin:0;font-size:clamp(26px,5.4vw,40px);font-weight:700;line-height:1.1}
.psub{margin:6px 0 0;font-size:20px}
.buddy{display:flex;align-items:center;gap:6px}
.bubble{background:var(--paper);border:2px solid var(--line);border-radius:16px;padding:6px 10px;font-size:15px;font-weight:600;max-width:150px;line-height:1.2}
.pbody{padding:16px 2px 4px}
.pf{display:flex;justify-content:space-between;font-size:13px;color:var(--ink2);padding-top:12px;border-top:2px dashed var(--line);margin-top:18px}
.inst{font-size:22px;font-weight:500;text-align:center;margin:2px 0 14px}
.cap{margin:6px 0 0;font-size:20px;font-weight:500}
.grid{display:grid;gap:14px}
.g2{grid-template-columns:repeat(2,1fr)}
.g3{grid-template-columns:repeat(3,1fr)}
@media (max-width:700px){.g3{grid-template-columns:1fr}}
@media (max-width:560px){.g2{grid-template-columns:1fr}.page{padding:14px 12px 10px;border-radius:26px}}
.card{background:var(--card);border:3px solid var(--tint);border-radius:26px;padding:14px;text-align:center;min-width:0}
.btn{border:0;border-radius:999px;padding:12px 26px;min-height:48px;font-size:19px;font-weight:700;background:var(--btn-bg);color:var(--btn-ink);box-shadow:0 4px 0 #e0b800}
.btn.ghost{background:var(--card);color:var(--ink);border:2px solid var(--line);box-shadow:none}
.say{min-width:44px;min-height:44px;border-radius:50%;border:2px solid var(--line);background:var(--paper);font-size:20px;line-height:1;padding:0;vertical-align:middle}
html.no-speech .say{display:none}
 
/* ---------- learning cards ---------- */
.bigl{display:flex;justify-content:center;align-items:baseline;gap:14px;font-size:68px;font-weight:700;line-height:1}
.bigl .lo{color:var(--ink)}
.bigl span:first-child{color:var(--acc)}
.pic{font-size:88px;line-height:1.15;min-height:104px;display:flex;align-items:center;justify-content:center}
.pic svg{max-width:100%;height:auto}
.word{font-size:34px;font-weight:600;line-height:1.1}
.word b{color:var(--acc);font-size:1.12em}
.bign{font-size:84px;font-weight:700;color:var(--acc);line-height:1}
.nword{font-size:34px;font-weight:600;margin-bottom:6px}
.objs{display:flex;flex-wrap:wrap;justify-content:center;gap:2px 2px;background:var(--paper);border:2px dashed var(--line);border-radius:18px;padding:8px;min-height:70px}
.obj{border:0;background:none;padding:0;line-height:1.1;border-radius:12px;position:relative;min-width:40px;min-height:40px}
.objs.sl .obj{font-size:42px}.objs.sm .obj{font-size:34px}.objs.ss .obj{font-size:26px;min-width:34px;min-height:34px}
.objs.sm .obj:nth-child(5n),.objs.ss .obj:nth-child(5n){margin-right:12px}
.obj.counted{background:#fff3a8}
.obj.counted::after{content:attr(data-k);position:absolute;right:-2px;top:-4px;min-width:22px;height:22px;border-radius:11px;background:#ff5a8a;color:#fff;font-size:14px;font-weight:700;display:flex;align-items:center;justify-content:center}
.objs.static .obj{pointer-events:none}
.apic{font-size:84px;line-height:1.1}
.aname{font-size:36px;font-weight:700;color:var(--acc);text-transform:none}
.sent{margin:4px 0;font-size:21px;font-weight:500}
.snd{margin:4px 0;font-size:19px;color:var(--ink2)}
.cring{width:112px;height:112px;margin:0 auto 8px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:64px;border:5px solid var(--c);background:var(--paper)}
.cring svg{width:80px;height:80px}
.cword{font-size:34px;font-weight:700;display:flex;align-items:center;justify-content:center;gap:8px}
.dotc{display:inline-block;width:20px;height:20px;border-radius:50%}
.sw{display:inline-block;border-radius:50%;border:3px solid rgba(60,50,90,.25);vertical-align:middle}
.shp{display:block;margin:auto}
 
/* ---------- trace pad ---------- */
.pad{position:relative;width:100%;aspect-ratio:2/1;background:var(--paper);border:3px dashed var(--line);border-radius:18px;margin-top:10px;overflow:hidden;touch-action:none}
.pad svg.guide{position:absolute;inset:0;width:100%;height:100%;pointer-events:none}
.pad canvas{position:absolute;inset:0;width:100%;height:100%;touch-action:none;cursor:crosshair}
.pad .clr{position:absolute;right:6px;bottom:6px;width:40px;height:40px;border-radius:50%;border:2px solid var(--line);background:var(--card);font-size:20px;padding:0;line-height:1}
.guide text{font-family:'Fredoka','Trebuchet MS',sans-serif;font-weight:600;fill:var(--dotfill);stroke:var(--dot);stroke-width:3.2;stroke-dasharray:.1 7;stroke-linecap:round;text-anchor:middle}
.guide .dg *{fill:var(--dotfill);stroke:var(--dot);stroke-width:3.2;stroke-dasharray:.1 7;stroke-linecap:round;stroke-linejoin:round}
.guide .base{stroke:var(--line);stroke-width:2;stroke-dasharray:6 6}
.mini{margin-top:16px;border-top:3px dotted var(--line);padding-top:12px}
.mini h3{margin:0 0 6px;font-size:22px;text-align:center}
 
/* ---------- quiz ---------- */
.quiz{max-width:720px;margin:0 auto}
.qhead{display:flex;align-items:center;gap:12px;font-weight:600;font-size:16px;color:var(--ink2);margin-bottom:8px}
.qbar{flex:1;height:12px;border-radius:6px;background:var(--line);overflow:hidden}
.qbar i{display:block;height:100%;background:var(--acc);border-radius:6px;transition:width .3s}
.qprompt{display:flex;align-items:center;justify-content:center;gap:10px;font-size:26px;font-weight:600;text-align:center;margin:8px 0}
.qbig{display:flex;justify-content:center;align-items:center;min-height:110px;margin:6px 0 14px;font-size:84px;text-align:center}
.qbig .bt{font-size:112px;font-weight:700;color:var(--acc);line-height:1}
.speech{font-size:44px;font-weight:700;background:var(--card);border:3px solid var(--line);border-radius:30px;padding:10px 28px}
.statobjs{display:flex;flex-wrap:wrap;gap:4px;justify-content:center;font-size:44px;max-width:520px;line-height:1.1}
.opts{display:grid;gap:12px;grid-template-columns:repeat(auto-fit,minmax(120px,1fr))}
.opt{min-height:92px;border-radius:24px;border:4px solid var(--line);background:var(--card);padding:8px;display:flex;align-items:center;justify-content:center;transition:transform .1s}
.opt:hover:not([disabled]){transform:scale(1.03);border-color:var(--acc)}
.opt.right{background:var(--ok);border-color:var(--okline)}
.opt.wrong{background:var(--bad);border-color:var(--badline);animation:shake .4s;opacity:.7}
.opt[disabled]:not(.right):not(.wrong){opacity:.55}
.o-t{font-size:58px;font-weight:700;color:var(--acc);line-height:1}
.o-e{font-size:62px;line-height:1}
.o-w{font-size:34px;font-weight:600}
.xl{font-size:96px}
.qfb{min-height:70px;margin-top:14px;text-align:center}
.fb{display:inline-flex;align-items:center;gap:10px;font-size:22px;font-weight:600;padding:6px 16px;border-radius:999px}
.fb.ok{background:var(--ok)}
.fb.try{background:var(--bad)}
.qfb .btn{display:block;margin:10px auto 0}
.qend{text-align:center;padding:10px 0}
.qend h3{font-size:32px;margin:6px 0}
.bigstars{font-size:54px;letter-spacing:4px}
.quiz.compact .opt{min-height:74px}
.quiz.compact .o-e{font-size:48px}
.quiz.compact .qprompt{font-size:22px}
@keyframes shake{0%,100%{transform:none}25%{transform:translateX(-7px)}75%{transform:translateX(7px)}}
 
/* ---------- matching ---------- */
.mcols{display:grid;grid-template-columns:1fr 1fr;gap:14px 26px;max-width:640px;margin:0 auto}
.mcol{display:grid;gap:12px;align-content:start}
.mitem{min-height:88px;border-radius:24px;border:4px solid var(--line);background:var(--card);font-size:50px;padding:8px;display:flex;align-items:center;justify-content:center;line-height:1.05}
.mitem.sel{border-color:var(--acc);transform:scale(1.04);background:var(--tint)}
.mitem.matched{background:var(--ok);border-color:var(--okline);cursor:default}
.mitem.shake{animation:shake .4s;border-color:var(--badline)}
.mw{font-size:32px;font-weight:600}
.mnum{font-size:54px;font-weight:700;color:var(--acc)}
.mgrp{font-size:24px;line-height:1.15;word-break:break-all}
 
/* ---------- coloring + hunt ---------- */
.crayons{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-bottom:12px}
.cray{display:flex;flex-direction:column;align-items:center;gap:2px;border:3px solid var(--line);background:var(--card);border-radius:18px;padding:6px 8px;min-width:64px;min-height:64px;font-size:13px;font-weight:600}
.cray i{display:block;width:34px;height:34px;border-radius:50%;background:var(--c);border:3px solid rgba(60,50,90,.3)}
.cray.on{border-color:var(--acc);background:var(--tint);transform:translateY(-3px)}
.sheet{background:#fff;border:3px solid var(--line);border-radius:22px;padding:6px;max-width:560px;margin:0 auto}
.scene{display:block;width:100%;height:auto}
.scene .reg{cursor:pointer}
.scene .decor{pointer-events:none}
.huntpick{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-bottom:12px}
.hgrid{display:grid;grid-template-columns:repeat(5,1fr);gap:8px;max-width:560px;margin:0 auto}
.hitem{aspect-ratio:1;font-size:clamp(30px,8vw,52px);border-radius:20px;border:4px solid var(--line);background:var(--card);padding:0;display:flex;align-items:center;justify-content:center}
.hitem.yes{background:var(--ok);border-color:var(--okline)}
.hitem.no{animation:shake .4s;border-color:var(--badline)}
 
/* ---------- rewards ---------- */
.rwtop{text-align:center}
.meter{height:20px;border-radius:10px;background:var(--line);max-width:420px;margin:8px auto;overflow:hidden}
.meter i{display:block;height:100%;background:linear-gradient(90deg,#ffd93d,#ff9f45);border-radius:10px}
.badges{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:14px;margin-top:16px}
.badge{text-align:center;border-radius:26px;padding:14px;border:3px solid var(--tint);background:var(--card)}
.badge .be{font-size:64px;line-height:1.1}
.badge.lock .be{filter:grayscale(1);opacity:.35}
.badge b{display:block;font-size:22px}
.badge small{display:block;font-size:15px;color:var(--ink2);margin:4px 0 8px}
.badge.got{background:var(--t-game)}
.cheers{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin:14px 0}
.cheers span{background:var(--tint);padding:8px 18px;border-radius:999px;font-weight:700;font-size:20px}
 
/* ---------- worksheets ---------- */
.nameline{display:flex;gap:18px;flex-wrap:wrap;font-size:18px;margin-bottom:10px}
.ln{display:inline-block;min-width:150px;border-bottom:3px solid var(--ink);height:1.3em;vertical-align:bottom}
.ln.s{min-width:100px}
.ws-row{display:flex;align-items:center;flex-wrap:wrap;gap:10px;margin:10px 0;padding:10px 12px;border:3px solid var(--line);border-radius:22px;break-inside:avoid}
.ws-row .q{flex:1 1 100%;font-size:21px;font-weight:600}
.ws-row .qn{display:inline-flex;width:34px;height:34px;border-radius:50%;background:var(--tint);align-items:center;justify-content:center;margin-right:8px;font-size:18px}
.circ{display:inline-flex;flex-direction:column;align-items:center;justify-content:center;min-width:56px;min-height:56px;padding:2px 8px;border:4px solid transparent;border-radius:50%;font-size:42px;font-weight:700;background:none;color:inherit;line-height:1.1}
.circ.pic{border-radius:26px;font-size:60px;padding:4px 12px}
.circ small{font-size:17px;font-weight:600}
.circ.on{border-color:#ff5a8a}
.blankbox{display:inline-block;width:1.15em;height:1.15em;border:3px solid var(--ink);border-radius:8px;vertical-align:middle;margin:0 3px}
.wbank{font-size:18px;color:var(--ink2);font-weight:600}
.mlines{display:flex;justify-content:space-between;max-width:420px;margin:10px auto;gap:20px}
.mlines>div{display:grid;gap:22px}
.mrow{display:flex;align-items:center;gap:10px;font-size:44px;line-height:1;min-height:56px}
.mrow.r{justify-content:flex-end;font-size:30px;font-weight:600}
.pt{display:inline-block;width:16px;height:16px;border-radius:50%;background:var(--ink)}
.numrow{font-size:30px}
.stk{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;max-width:560px;margin:10px auto}
.stk div{aspect-ratio:1;border:4px dashed var(--dot);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:clamp(30px,8vw,56px);color:var(--dot)}
.rules{list-style:none;padding:0;margin:12px auto;max-width:560px;display:grid;gap:6px;font-size:20px}
 
/* ---------- cover, welcome, certificate ---------- */
.page.raw{padding:0;overflow:hidden}
.page.raw .pf{display:none}
.cover{position:relative;min-height:min(78vh,760px);display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:38px 18px 26px;background:linear-gradient(165deg,var(--t-alpha),var(--t-num) 52%,var(--t-ani));overflow:hidden}
.cv-kicker{margin:0 0 6px;font-size:20px;font-weight:600;position:relative}
.cv-title{margin:0;font-size:clamp(40px,10vw,84px);line-height:1;font-weight:700;position:relative;text-shadow:0 4px 0 rgba(74,63,107,.18)}
.cv-title .w{display:block}
.cv-sub{font-size:clamp(22px,4.6vw,34px);font-weight:600;margin:14px 0 6px;position:relative}
.cv-pals{display:flex;align-items:flex-end;justify-content:center;gap:10px;margin:8px 0;position:relative}
.cv-animals{font-size:clamp(40px,9vw,64px);letter-spacing:6px}
.cv-brand{display:flex;flex-direction:column;align-items:center;gap:4px;margin-top:14px;position:relative;font-weight:600}
.cv-brand input{font-size:24px;text-align:center;width:min(420px,86vw);border:0;border-bottom:4px dashed var(--ink2);background:rgba(255,255,255,.6);color:#3d3360;border-radius:14px 14px 0 0;padding:8px}
.blk{position:absolute;width:clamp(46px,9vw,72px);height:clamp(46px,9vw,72px);border-radius:20px;background:var(--c);color:#fff;font-weight:700;font-size:clamp(28px,6vw,44px);display:flex;align-items:center;justify-content:center;transform:rotate(-8deg);animation:floaty 4s ease-in-out infinite;text-shadow:0 2px 0 rgba(0,0,0,.2)}
.em{position:absolute;font-size:clamp(30px,6vw,52px);animation:floaty 5s ease-in-out infinite}
@keyframes floaty{0%,100%{translate:0 0}50%{translate:0 -10px}}
.w-hero{display:flex;align-items:center;justify-content:center;flex-wrap:wrap;gap:8px 12px;margin-bottom:8px}
.bubble.big{font-size:22px;max-width:none}
.legend p{margin:6px 0 0;font-size:18px}
.legend .em2{font-size:44px}
.grown{margin-top:14px;text-align:left}
.grown h3{margin:0 0 6px;font-size:22px}
.grown ul{margin:0;padding-left:22px;display:grid;gap:5px;font-size:17px}
.toc{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:12px}
.tile{display:flex;align-items:center;gap:12px;text-align:left;border:3px solid var(--tint);background:var(--tint);border-radius:24px;padding:12px 14px;min-height:84px;font-size:22px;font-weight:700}
.tile .te{font-size:46px}
.tile small{display:block;font-weight:500;font-size:15px}
.cert{border:12px double #f0a93b;border-radius:30px;padding:22px 16px;text-align:center;background:linear-gradient(180deg,var(--t-game),var(--paper) 60%);position:relative}
.cert h3{margin:0;font-size:clamp(30px,7vw,52px);color:var(--acc)}
.cert .small{font-size:20px;margin:6px 0}
.cert-name{font-size:clamp(28px,6vw,44px);font-weight:700;text-align:center;width:min(520px,90%);border:0;border-bottom:4px solid var(--ink);background:transparent;margin:6px 0 10px;padding:4px}
.cert .bigs{font-size:46px;letter-spacing:6px}
.cert .says{display:flex;flex-wrap:wrap;justify-content:center;gap:10px;margin:10px 0;font-weight:700;font-size:22px}
.cert .says span{background:var(--tint);padding:6px 18px;border-radius:999px}
.sign{display:flex;justify-content:space-around;gap:20px;margin-top:20px;font-size:16px}
.sign div{min-width:160px;border-top:3px solid var(--ink);padding-top:4px}
.sign input{border:0;background:transparent;text-align:center;font-size:18px;width:100%;margin-bottom:-4px}
.kitem{border:2px solid var(--line);border-radius:18px;padding:8px 14px;margin:8px 0;break-inside:avoid;font-size:17px}
.kitem h3{margin:0 0 3px;font-size:19px}
.kitem small{font-weight:500;color:var(--ink2);font-size:14px}
.kp{display:inline-block;background:var(--tint);border-radius:999px;padding:0 10px;margin-right:6px;font-size:15px}
.notes{display:none;margin-top:14px;background:var(--card);border:3px dashed var(--line);border-radius:18px;padding:12px 16px;font-size:15px;line-height:1.45;text-align:left}
body.show-notes .notes{display:block}
.notes b{font-size:17px}
.notes dt{font-weight:700;margin-top:6px;color:var(--acc)}
.notes dd{margin:0}
 
@media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
 
/* ---------- print ---------- */
@media print{
  :root:root:root{--paper:#fff!important;--card:#fff!important;--ink:#3d3360!important;--ink2:#6b6190!important;--line:#d9cdee!important;
    --t-info:#fff0d9!important;--t-alpha:#ffe0ec!important;--t-num:#d8ecff!important;--t-ani:#d5f5de!important;--t-col:#e9dcfb!important;--t-game:#fff4bf!important;--t-rev:#ffe4cf!important;
    --dot:#9a85cc!important;--dotfill:#fff!important;--ok:#d9f7df!important;--bad:#ffe2e2!important;padding:0!important}
  @page{margin:10mm}
  html,body{height:auto!important;background:#fff!important;-webkit-print-color-adjust:exact;print-color-adjust:exact;font-size:16px}
  #app{display:block;height:auto}
  #stage{overflow:visible;padding:0}
  .toolbar,.navbar,.drawer,.notes,.digital-only,.clr,.say,.mini{display:none!important}
  .page{display:none!important;box-shadow:none;border-radius:0;max-width:none;margin:0;break-after:page;page-break-after:always;animation:none}
  body:not(.print-all):not(.print-one) .page:is([data-kind="cover"],[data-kind="info"],[data-kind="learn"],[data-kind="print"],[data-kind="cert"],[data-kind="key"]){display:block!important}
  body.print-all .page{display:block!important}
  body.print-one .page.print-this{display:block!important}
  input::placeholder{color:transparent}
  .cover{min-height:auto}
  .page{padding:8px 12px}
  .phead{padding:6px 12px;gap:6px}
  .ptitle{font-size:28px}.psub{font-size:16px;margin-top:2px}
  .buddy svg{width:44px;height:44px}.bubble{font-size:13px;padding:4px 8px}
  .pbody{padding:8px 0 0}.pf{margin-top:8px;padding-top:6px}
  .inst{font-size:17px;margin:0 0 8px}.cap{font-size:16px;margin:2px 0 0}
  .grid{gap:10px}.card{padding:8px;border-radius:18px}
  .bigl{font-size:46px}.pic{font-size:58px;min-height:66px}.pic svg{height:60px;width:auto}
  .word{font-size:26px}.bign{font-size:58px}.nword{font-size:26px;margin-bottom:2px}
  .objs{min-height:44px;padding:4px}
  .objs.sl .obj{font-size:30px;min-width:30px;min-height:30px}.objs.sm .obj{font-size:24px;min-width:26px;min-height:26px}.objs.ss .obj{font-size:19px;min-width:22px;min-height:22px}
  .apic{font-size:60px}.aname{font-size:28px}.sent{font-size:16px;margin:2px 0}
  .cring{width:80px;height:80px;font-size:46px}.cring svg{width:56px;height:56px}.cword{font-size:26px}
  .pad{aspect-ratio:2.7/1;margin-top:6px}
  .ws-row{margin:7px 0;padding:6px 10px}.ws-row .q{font-size:17px}
  .circ.pic{font-size:46px}.circ{font-size:34px}
  .w-hero svg{width:76px;height:76px}.legend .em2{font-size:32px}.legend p,.grown ul{font-size:14px}
  .kitem{padding:4px 10px;margin:5px 0;font-size:14px}.kitem h3{font-size:16px}
  .sheet{max-width:480px}
  .nameline{margin-bottom:4px;font-size:15px}
  .ws-row{margin:4px 0;padding:3px 8px;gap:4px 8px}.ws-row .q{font-size:15px}.ws-row .qn{width:26px;height:26px;font-size:14px}
  .circ.pic{font-size:36px;padding:0 8px;min-height:44px}.circ small{font-size:12px}.circ{font-size:28px;min-height:44px}
  .mlines>div{gap:8px}.mrow{font-size:32px;min-height:38px}.mrow.r{font-size:24px}
  .numrow{font-size:22px}
}
</style>
</head>
<body>
<div id="app">
  <div class="toolbar">
    <button class="tbtn" id="btnMenu" type="button" aria-label="Open contents">☰ <span class="hide-s">Contents</span></button>
    <div class="ttl">My First English Adventure</div>
    <div class="tbtn static" id="starCount" title="Stars you have earned in the games">⭐ 0</div>
    <button class="tbtn" id="btnNotes" type="button" aria-pressed="false" title="Show page notes for grown-ups and illustrators">📝 <span class="hide-s">Notes</span></button>
    <details class="pm" id="pm">
      <summary class="tbtn">🖨️ <span class="hide-s">Print</span></summary>
      <div class="menu">
        <button type="button" data-print="page">This page only</button>
        <button type="button" data-print="worksheets">Worksheets + learning pages</button>
        <button type="button" data-print="all">The whole book</button>
      </div>
    </details>
  </div>
  <main id="stage"></main>
  <nav class="navbar" aria-label="Page navigation">
    <button class="nbtn" id="btnPrev" type="button">◀ Back</button>
    <div class="pgno" id="pgno">1 / 45</div>
    <button class="nbtn" id="btnNext" type="button">Next ▶</button>
  </nav>
</div>
<div class="drawer" id="drawer" aria-label="Contents">
  <div class="dback" data-close></div>
  <div class="dpanel">
    <div class="dhead"><b>Contents</b><button class="tbtn" type="button" data-close>✕ Close</button></div>
    <div id="dlist"></div>
  </div>
</div>
 
<script>
(function(){
'use strict';
 
/* ================= helpers ================= */
var $=function(s,el){return (el||document).querySelector(s)};
var $$=function(s,el){return Array.prototype.slice.call((el||document).querySelectorAll(s))};
var cap=function(s){return s.charAt(0).toUpperCase()+s.slice(1)};
var art=function(w){return /^[aeiou]/i.test(w)?'an':'a'};
var esc=function(s){return String(s).replace(/"/g,'&quot;')};
var _u=0, uid=function(){return 'u'+(++_u)};
function shuffle(a){var b=a.slice();for(var i=b.length-1;i>0;i--){var j=Math.floor(Math.random()*(i+1));var t=b[i];b[i]=b[j];b[j]=t}return b}
function pick(a){return a[Math.floor(Math.random()*a.length)]}
 
/* ---- speech (uses the device's built-in voice, if there is one) ---- */
var canSpeak=('speechSynthesis' in window)&&('SpeechSynthesisUtterance' in window);
if(!canSpeak)document.documentElement.classList.add('no-speech');
function speak(t){
  if(!canSpeak)return;
  try{speechSynthesis.cancel();var u=new SpeechSynthesisUtterance(String(t).replace(/<[^>]+>/g,''));u.lang='en-US';u.rate=.8;u.pitch=1.1;speechSynthesis.speak(u)}catch(e){}
}
 
/* ---- progress ---- */
var DONE={};
try{JSON.parse(localStorage.getItem('mfea-done')||'[]').forEach(function(k){DONE[k]=1})}catch(e){}
var BADGES=[
  {n:'Letter Star',e:'🔤',ids:['find-letter','pic-letter']},
  {n:'Number Whiz',e:'🔢',ids:['howmany','num-match']},
  {n:'Animal Friend',e:'🐾',ids:['sounds','ani-match','whoami']},
  {n:'Color Artist',e:'🎨',ids:['coloring','blue']},
  {n:'Word Wizard',e:'🪄',ids:['word-match','missing','quick']},
  {n:'Little Explorer',e:'🧭',ids:['review']}
];
var ALLACT=[];BADGES.forEach(function(b){ALLACT=ALLACT.concat(b.ids)});
var ACT={};
function starsNow(){return ALLACT.filter(function(k){return DONE[k]}).length}
function updateStars(){$('#starCount').textContent='⭐ '+starsNow()}
function markDone(id){
  if(!id||DONE[id])return;DONE[id]=1;
  try{localStorage.setItem('mfea-done',JSON.stringify(Object.keys(DONE)))}catch(e){}
  updateStars();
}
 
/* ================= art ================= */
var COLORS={red:'#ff5a5f',orange:'#ff9f45',yellow:'#ffd93d',green:'#5cc96b',blue:'#4d9de0',purple:'#a06cd5',pink:'#ff8fb8',brown:'#a47551'};
var SHAPES={
  circle:'<circle cx="50" cy="50" r="38"/>',
  square:'<rect x="14" y="14" width="72" height="72" rx="8"/>',
  triangle:'<polygon points="50,12 90,86 10,86"/>',
  rectangle:'<rect x="6" y="26" width="88" height="48" rx="8"/>',
  star:'<polygon points="50,8 61,38 94,38 68,57 78,90 50,71 22,90 32,57 6,38 39,38"/>',
  heart:'<path d="M50 88C14 60 6 34 24 20c14-10 26-2 26 10 0-12 12-20 26-10 18 14 10 40-26 68z"/>'
};
function shp(name,color,s){s=s||64;var c=COLORS[color]||color;return '<svg class="shp" viewBox="0 0 100 100" width="'+s+'" height="'+s+'" role="img" aria-label="'+name+'" fill="'+c+'" stroke="'+c+'" stroke-width="4" stroke-linejoin="round">'+SHAPES[name]+'</svg>'}
function sw(c,s){s=s||56;return '<span class="sw" style="background:'+(COLORS[c]||c)+';width:'+s+'px;height:'+s+'px" role="img" aria-label="'+c+'"></span>'}
var BALL='<svg viewBox="0 0 100 100" width="80" height="80" role="img" aria-label="blue ball"><circle cx="50" cy="50" r="42" fill="#4d9de0"/><path d="M12 42Q50 66 88 42" stroke="#fff" stroke-width="7" fill="none" opacity=".8" stroke-linecap="round"/><path d="M20 70Q50 88 80 70" stroke="#fff" stroke-width="5" fill="none" opacity=".5" stroke-linecap="round"/><circle cx="34" cy="30" r="8" fill="#fff" opacity=".6"/></svg>';
var XYLO='<svg viewBox="0 0 120 90" width="124" height="92" role="img" aria-label="xylophone"><rect x="8" y="26" width="104" height="6" rx="3" fill="#c99a6b"/><rect x="14" y="62" width="92" height="6" rx="3" fill="#c99a6b"/><rect x="12" y="8" width="16" height="70" rx="6" fill="#ff5a5f"/><rect x="32" y="16" width="16" height="62" rx="6" fill="#ff9f45"/><rect x="52" y="24" width="16" height="54" rx="6" fill="#ffd93d"/><rect x="72" y="32" width="16" height="46" rx="6" fill="#5cc96b"/><rect x="92" y="40" width="16" height="38" rx="6" fill="#4d9de0"/><circle cx="20" cy="18" r="2.6" fill="#fff" opacity=".8"/><circle cx="40" cy="26" r="2.6" fill="#fff" opacity=".8"/><circle cx="60" cy="34" r="2.6" fill="#fff" opacity=".8"/><circle cx="80" cy="42" r="2.6" fill="#fff" opacity=".8"/><circle cx="100" cy="50" r="2.6" fill="#fff" opacity=".8"/></svg>';
function milo(s,m){s=s||64;
  var mouth=m==='cheer'?'<path d="M47 82Q60 106 73 82Z" fill="#ff8fa3" stroke="#5a3f3a" stroke-width="3" stroke-linejoin="round"/>':'<path d="M50 85Q60 94 70 85" fill="none" stroke="#5a3f3a" stroke-width="3.5" stroke-linecap="round"/>';
  return '<svg class="mascot" viewBox="0 0 120 120" width="'+s+'" height="'+s+'" role="img" aria-label="Milo the bear"><circle cx="26" cy="30" r="17" fill="#c99a6b"/><circle cx="94" cy="30" r="17" fill="#c99a6b"/><circle cx="26" cy="30" r="8" fill="#f6c9c9"/><circle cx="94" cy="30" r="8" fill="#f6c9c9"/><ellipse cx="60" cy="68" rx="44" ry="42" fill="#dcae7e"/><ellipse cx="60" cy="82" rx="21" ry="16" fill="#f8e3c8"/><ellipse cx="60" cy="73" rx="7" ry="5" fill="#5a3f3a"/><circle cx="41" cy="58" r="5.5" fill="#3b2f4a"/><circle cx="79" cy="58" r="5.5" fill="#3b2f4a"/><circle cx="43" cy="56" r="1.8" fill="#fff"/><circle cx="81" cy="56" r="1.8" fill="#fff"/><circle cx="29" cy="76" r="7" fill="#ffb3c1" opacity=".75"/><circle cx="91" cy="76" r="7" fill="#ffb3c1" opacity=".75"/>'+mouth+'</svg>';
}
function bibi(s){s=s||64;
  return '<svg class="mascot" viewBox="0 0 120 120" width="'+s+'" height="'+s+'" role="img" aria-label="Bibi the bunny"><g stroke="#cdb8ea" stroke-width="2.5"><ellipse cx="40" cy="32" rx="12" ry="28" fill="#f3eaff"/><ellipse cx="80" cy="32" rx="12" ry="28" fill="#f3eaff"/></g><ellipse cx="40" cy="34" rx="6" ry="20" fill="#ffc8dd"/><ellipse cx="80" cy="34" rx="6" ry="20" fill="#ffc8dd"/><ellipse cx="60" cy="76" rx="40" ry="37" fill="#f6eeff" stroke="#cdb8ea" stroke-width="2.5"/><circle cx="43" cy="68" r="5" fill="#3b2f4a"/><circle cx="77" cy="68" r="5" fill="#3b2f4a"/><circle cx="45" cy="66" r="1.7" fill="#fff"/><circle cx="79" cy="66" r="1.7" fill="#fff"/><ellipse cx="60" cy="80" rx="6" ry="4.5" fill="#ff8fb8"/><path d="M60 84Q60 92 52 92M60 84Q60 92 68 92" fill="none" stroke="#5a3f3a" stroke-width="3" stroke-linecap="round"/><circle cx="32" cy="82" r="7" fill="#ffc8dd" opacity=".8"/><circle cx="88" cy="82" r="7" fill="#ffc8dd" opacity=".8"/></svg>';
}
function face(x,y){return '<circle cx="'+(x-9)+'" cy="'+(y-3)+'" r="2.8" fill="#3b2f4a"/><circle cx="'+(x+9)+'" cy="'+(y-3)+'" r="2.8" fill="#3b2f4a"/><path d="M'+(x-8)+' '+(y+6)+'Q'+x+' '+(y+15)+' '+(x+8)+' '+(y+6)+'" fill="none" stroke="#3b2f4a" stroke-width="2.6" stroke-linecap="round"/>'}
function reg(id,name,shapes){return '<g fill="#6b5b8a" stroke="#6b5b8a" stroke-width="8" stroke-linejoin="round">'+shapes+'</g><g class="reg" data-id="'+id+'" data-name="'+name+'" fill="#ffffff"><title>'+name+'</title>'+shapes+'</g>'}
function SCENE(){
  return '<svg class="scene" viewBox="0 0 400 300" role="img" aria-label="A coloring picture with a house, a tree, a sun, a cloud, a flower and a ball">'
  +'<rect width="400" height="300" fill="#fff"/>'
  +reg('grass','Grass','<path d="M-10 250Q100 228 200 246T410 242V312H-10Z"/>')
  +reg('cloud','Cloud','<circle cx="78" cy="70" r="20"/><circle cx="104" cy="58" r="26"/><circle cx="134" cy="72" r="20"/><rect x="76" y="68" width="76" height="24" rx="12"/>')
  +reg('sun','Sun','<circle cx="338" cy="58" r="30"/>')
  +'<g class="decor">'+face(338,60)+face(106,72)+'</g>'
  +reg('house','House','<rect x="140" y="152" width="120" height="92"/>')
  +reg('roof','Roof','<polygon points="124,154 200,96 276,154"/>')
  +reg('door','Door','<path d="M182 244V204a18 18 0 0 1 36 0V244Z"/>')
  +reg('window','Window','<rect x="228" y="172" width="26" height="26" rx="4"/>')
  +reg('trunk','Tree trunk','<rect x="312" y="184" width="24" height="62"/>')
  +reg('leaves','Leaves','<circle cx="324" cy="152" r="40"/>')
  +'<path d="M48 226V262" stroke="#5cc96b" stroke-width="6" stroke-linecap="round" fill="none"/>'
  +reg('petals','Flower petals','<circle cx="48" cy="197" r="11"/><circle cx="62" cy="207" r="11"/><circle cx="57" cy="224" r="11"/><circle cx="39" cy="224" r="11"/><circle cx="34" cy="207" r="11"/>')
  +reg('middle','Flower middle','<circle cx="48" cy="212" r="8"/>')
  +reg('ball','Ball','<circle cx="104" cy="270" r="22"/>')
  +'</svg>';
}
 
/* ---- tracing pad ---- */
var PEN=['#ff6fa5','#4d9de0','#ff9f45','#5cc96b','#a06cd5'];
function pad(inner,pen){
  return '<div class="pad" data-pen="'+(pen||PEN[0])+'"><svg class="guide" viewBox="0 0 200 100" aria-hidden="true"><line class="base" x1="8" x2="192" y1="84" y2="84"/>'+inner+'</svg><canvas aria-label="Drawing area. Trace the dotted shape."></canvas><button class="clr digital-only" type="button" aria-label="Erase and try again">↺</button></div>';
}
function padText(a,b,size){size=size||76;return '<text x="52" y="84" font-size="'+size+'">'+a+'</text><text x="148" y="84" font-size="'+size+'">'+b+'</text>'}
function padWord(w){var fs=Math.min(70,Math.floor(176/(w.length*.56)));return '<text x="100" y="80" font-size="'+fs+'">'+w+'</text>'}
function padShape(name){return '<g class="dg" transform="translate(6,6) scale(.88)">'+SHAPES[name]+'</g><g class="dg" transform="translate(106,6) scale(.88)">'+SHAPES[name]+'</g>'}
function initPad(p){
  var c=$('canvas',p),r=c.getBoundingClientRect();if(!r.width)return;
  var dpr=Math.min(window.devicePixelRatio||1,2);
  if(c._W!==Math.round(r.width)){
    c.width=Math.round(r.width*dpr);c.height=Math.round(r.height*dpr);c._W=Math.round(r.width);
    var x=c.getContext('2d');x.setTransform(dpr,0,0,dpr,0,0);x.lineCap='round';x.lineJoin='round';x.lineWidth=Math.max(9,r.width/20);c._x=x;
  }
  if(c._bound)return;c._bound=true;
  var down=false,lx=0,ly=0;
  function pos(e){var b=c.getBoundingClientRect();return [e.clientX-b.left,e.clientY-b.top]}
  c.addEventListener('pointerdown',function(e){down=true;try{c.setPointerCapture(e.pointerId)}catch(_){}var q=pos(e);lx=q[0];ly=q[1];var x=c._x;x.strokeStyle=p.dataset.pen;x.beginPath();x.moveTo(lx,ly);x.lineTo(lx+.1,ly+.1);x.stroke();e.preventDefault()});
  c.addEventListener('pointermove',function(e){if(!down)return;var q=pos(e),x=c._x;x.strokeStyle=p.dataset.pen;x.beginPath();x.moveTo(lx,ly);x.lineTo(q[0],q[1]);x.stroke();lx=q[0];ly=q[1]});
  var up=function(){down=false};c.addEventListener('pointerup',up);c.addEventListener('pointercancel',up);
  $('.clr',p).addEventListener('click',function(){c._x.clearRect(0,0,c.width,c.height)});
}
 
/* ================= interactive engines ================= */
var MOUNTS=[];
function mountQuiz(el,cfg){
  var total=cfg.qs.length,order,i,score,tries,locked,q;
  var praise=['Great job!','You did it!','Super!','Awesome!','Well done!','Hooray!','Fantastic!'];
  function start(){order=shuffle(cfg.qs.map(function(_,k){return k}));i=0;score=0;show()}
  function show(){
    if(i>=total){end();return}
    q=cfg.qs[order[i]];tries=0;locked=false;
    el.innerHTML='<div class="qhead"><span>'+(i+1)+' of '+total+'</span><div class="qbar" aria-hidden="true"><i style="width:'+(i/total*100)+'%"></i></div></div>'
    +'<div class="qprompt"><span>'+q.q+'</span>'+(q.say?'<button type="button" class="say digital-only" data-say="'+esc(q.say)+'" aria-label="Hear the question">🔊</button>':'')+'</div>'
    +(q.big?'<div class="qbig">'+q.big+'</div>':'')
    +'<div class="opts">'+shuffle(q.opts).map(function(o){return '<button type="button" class="opt" data-ok="'+(o.ok?1:0)+'">'+o.h+'</button>'}).join('')+'</div>'
    +'<div class="qfb" aria-live="polite"></div>';
  }
  function end(){
    var r=score/total,st=r>=.85?3:(r>=.55?2:1);
    var msg=['Keep learning!','Great job!','You did it! Superstar!'][st-1];
    el.innerHTML='<div class="qend">'+milo(cfg.compact?64:116,'cheer')+'<div class="bigstars" aria-label="'+st+' of 3 stars">'+'⭐'.repeat(st)+'☆'.repeat(3-st)+'</div><h3>'+msg+'</h3><p>You got '+score+' of '+total+' on the first try.</p><button type="button" class="btn" data-act="again">Play again ↺</button></div>';
    if(cfg.id)markDone(cfg.id);
  }
  el.onclick=function(e){
    var a=e.target.closest('[data-act]');
    if(a){if(a.dataset.act==='next'){i++;show()}else{start()}return}
    var b=e.target.closest('.opt');if(!b||locked||b.disabled)return;
    var fb=$('.qfb',el);
    if(b.dataset.ok==='1'){
      locked=true;b.classList.add('right');if(tries===0)score++;
      $$('.opt',el).forEach(function(o){if(o!==b)o.disabled=true});
      fb.innerHTML='<div class="fb ok">'+milo(40,'cheer')+'<span>'+pick(praise)+' '+(q.fb||'')+'</span></div><button type="button" class="btn" data-act="next">'+(i+1<total?'Next ▶':'Finish ★')+'</button>';
    }else{
      tries++;b.classList.add('wrong');b.disabled=true;
      fb.innerHTML='<div class="fb try"><span>Oops! Try again. You can do it!</span></div>';
    }
  };
  el.classList.toggle('compact',!!cfg.compact);
  start();
}
function mountMatch(el,cfg){
  var ri=0,pairs,matched=0;
  function round(){
    pairs=cfg.rounds[ri];matched=0;
    var right=shuffle(pairs);
    if(pairs.length>1){var guard=0;while(guard++<20&&right.every(function(p,k){return p===pairs[k]}))right=shuffle(pairs)}
    el.innerHTML='<div class="qhead"><span>Round '+(ri+1)+' of '+cfg.rounds.length+'</span></div><p class="inst">'+(cfg.hint||'Tap a picture. Then tap its match!')+'</p>'
    +'<div class="mcols"><div class="mcol">'+pairs.map(function(p){return '<button type="button" class="mitem" data-id="'+p.id+'" data-side="l">'+p.l+'</button>'}).join('')+'</div>'
    +'<div class="mcol">'+right.map(function(p){return '<button type="button" class="mitem" data-id="'+p.id+'" data-side="r">'+p.r+'</button>'}).join('')+'</div></div><div class="qfb" aria-live="polite"></div>';
  }
  el.onclick=function(e){
    var a=e.target.closest('[data-act]');
    if(a){if(a.dataset.act==='next'){ri++}else{ri=0}round();return}
    var b=e.target.closest('.mitem');if(!b||b.classList.contains('matched'))return;
    var side=b.dataset.side,other=side==='l'?'r':'l';
    var same=$('.mitem.sel[data-side="'+side+'"]',el);if(same)same.classList.remove('sel');
    var op=$('.mitem.sel[data-side="'+other+'"]',el);
    if(!op){b.classList.add('sel');return}
    var fb=$('.qfb',el);
    if(op.dataset.id===b.dataset.id){
      [op,b].forEach(function(x){x.classList.remove('sel');x.classList.add('matched')});matched++;
      if(matched===pairs.length){
        var last=ri===cfg.rounds.length-1;
        fb.innerHTML='<div class="fb ok">'+milo(40,'cheer')+'<span>'+(last?'You matched them all! Great job!':'Round complete! Hooray!')+'</span></div><button type="button" class="btn" data-act="'+(last?'again':'next')+'">'+(last?'Play again ↺':'Next round ▶')+'</button>';
        if(last)markDone(cfg.id);
      }else{fb.innerHTML='<div class="fb ok"><span>Yes! A match!</span></div>'}
    }else{
      [op,b].forEach(function(x){x.classList.remove('sel');x.classList.add('shake')});
      setTimeout(function(){[op,b].forEach(function(x){x.classList.remove('shake')})},450);
      fb.innerHTML='<div class="fb try"><span>Not quite. Try again!</span></div>';
    }
  };
  round();
}
function mountColoring(el){
  var cur='yellow',painted={},n=0;
  el.innerHTML='<p class="inst">Pick a crayon. Then tap a part of the picture!</p><div class="crayons">'
  +Object.keys(COLORS).map(function(k){return '<button type="button" class="cray'+(k===cur?' on':'')+'" data-c="'+k+'" style="--c:'+COLORS[k]+'" aria-label="'+k+' crayon"><i></i><span>'+k+'</span></button>'}).join('')
  +'<button type="button" class="cray" data-c="white" style="--c:#fff" aria-label="eraser"><i></i><span>eraser</span></button></div>'
  +'<div class="sheet">'+SCENE()+'</div><div class="qfb" aria-live="polite"></div><div style="text-align:center"><button type="button" class="btn ghost" data-reset>Start again ↺</button></div>';
  el.onclick=function(e){
    var c=e.target.closest('.cray');
    if(c){cur=c.dataset.c;$$('.cray',el).forEach(function(x){x.classList.toggle('on',x===c)});speak(cur==='white'?'eraser':cur);return}
    if(e.target.closest('[data-reset]')){$$('.reg',el).forEach(function(r){r.setAttribute('fill','#ffffff')});painted={};$('.qfb',el).innerHTML='';return}
    var r=e.target.closest('.reg');
    if(r){
      r.setAttribute('fill',cur==='white'?'#ffffff':COLORS[cur]);
      if(cur==='white')delete painted[r.dataset.id];else painted[r.dataset.id]=1;
      n=Object.keys(painted).length;
      if(n>=6){markDone('coloring');$('.qfb',el).innerHTML='<div class="fb ok">'+milo(40,'cheer')+'<span>What a beautiful picture!</span></div>'}
    }
  };
}
var HUNT=[['🍎','red'],['🐳','blue'],['🍌','yellow'],['🐸','green'],['🦊','orange'],['🍇','purple'],['🫐','blue'],['🐞','red'],['🥕','orange'],['🦋','blue'],['🐥','yellow'],['🥦','green'],['💜','purple'],['🍓','red'],['🌻','yellow'],['🐢','green'],['🍊','orange'],['💙','blue'],['🟣','purple'],['🍒','red']];
function mountHunt(el){
  var target='blue',found={},need=0;
  function draw(){
    found={};need=HUNT.filter(function(h){return h[1]===target}).length;
    el.innerHTML='<p class="inst">Find something <span class="dotc" style="background:'+COLORS[target]+'"></span> <b>'+target+'</b>! Tap every '+target+' thing.</p>'
    +'<div class="huntpick">'+['red','orange','yellow','green','blue','purple'].map(function(c){return '<button type="button" class="cray'+(c===target?' on':'')+'" data-c="'+c+'" style="--c:'+COLORS[c]+'" aria-label="Find '+c+'"><i></i><span>'+c+'</span></button>'}).join('')+'</div>'
    +'<div class="hgrid">'+HUNT.map(function(h,k){return '<button type="button" class="hitem" data-k="'+k+'" aria-label="picture '+(k+1)+'">'+h[0]+'</button>'}).join('')+'</div>'
    +'<div class="qfb" aria-live="polite"><div class="fb">Found 0 of '+need+'</div></div>';
  }
  el.onclick=function(e){
    var c=e.target.closest('.cray');if(c){target=c.dataset.c;speak(target);draw();return}
    var b=e.target.closest('.hitem');if(!b||b.classList.contains('yes'))return;
    var h=HUNT[+b.dataset.k],fb=$('.qfb',el);
    if(h[1]===target){
      b.classList.add('yes');found[b.dataset.k]=1;var n=Object.keys(found).length;
      if(n>=need){fb.innerHTML='<div class="fb ok">'+milo(40,'cheer')+'<span>You found them all! Great job!</span></div>';markDone('blue')}
      else fb.innerHTML='<div class="fb ok"><span>Yes! Found '+n+' of '+need+'</span></div>';
    }else{
      b.classList.add('no');setTimeout(function(){b.classList.remove('no')},450);
      fb.innerHTML='<div class="fb try"><span>That one is not '+target+'. Look again!</span></div>';
    }
  };
  draw();
}
var resetArmed=false;
function renderRewards(){
  var box=$('#rw');if(!box)return;
  var n=starsNow(),tot=ALLACT.length;
  var msg=n===0?'Play a game to earn your first star!':(n<tot/2?'Great start! Keep going!':(n<tot?'You are doing amazing!':'You did it! Every star is yours!'));
  box.innerHTML='<div class="rwtop">'+milo(120,'cheer')+bibi(100)+'<h3 style="font-size:30px;margin:6px 0">⭐ '+n+' of '+tot+' stars</h3><div class="meter" role="img" aria-label="'+n+' of '+tot+' stars"><i style="width:'+(n/tot*100)+'%"></i></div><p class="inst">'+msg+'</p></div>'
  +'<div class="cheers"><span>Great Job!</span><span>You Did It!</span><span>Keep Learning!</span></div>'
  +'<div class="badges">'+BADGES.map(function(b){
    var got=b.ids.filter(function(k){return DONE[k]}).length,ok=got===b.ids.length;
    var nextId=b.ids.filter(function(k){return !DONE[k]})[0];
    return '<div class="badge '+(ok?'got':'lock')+'"><div class="be">'+(ok?b.e:'🔒')+'</div><b>'+b.n+'</b><small>'+(ok?'Badge earned! 🏅':got+' of '+b.ids.length+' games finished')+'</small>'+(ok?'':'<button type="button" class="btn ghost" data-go="'+ACT[nextId]+'">Play ▶</button>')+'</div>';
  }).join('')+'</div>'
  +'<p style="text-align:center;margin-top:16px"><button type="button" class="btn ghost" id="btnReset">'+(resetArmed?'Tap again to erase all stars':'Start stars over')+'</button></p>';
}
 
/* ================= content data ================= */
var PAGES=[],KEY=[];
var THEME={info:'Welcome',alpha:'Alphabet Adventure',num:'Numbers & Counting',ani:'Animal World',col:'Colors & Shapes',game:'Game Time',rev:'Review & Certificate'};
var BUDDY={info:'milo',alpha:'milo',num:'bibi',ani:'bibi',col:'milo',game:'bibi',rev:'milo'};
var KIND={learn:['learn','📖 Learn + Trace'],play:['play','👆 Interactive (on screen)'],print:['print','🖨️ Printable worksheet'],cert:['print','🖨️ Printable'],key:['print','🔑 For grown-ups · printable']};
function add(d){d.n=PAGES.length+1;PAGES.push(d);if(d.act)ACT[d.act]=d.n;return d.n}
function keyAdd(type,title,html){KEY.push({p:PAGES.length+1,type:type,title:title,html:html})}
function playPage(o){
  var id=uid();
  MOUNTS.push(function(){mountQuiz($('#'+id),{id:o.act,qs:o.qs})});
  add({kind:'play',theme:o.theme,title:o.title,sub:o.sub,say:o.say,act:o.act,body:'<div class="quiz" id="'+id+'"></div>',notes:o.notes});
}
var tOpt=function(c,ok){return {h:'<span class="o-t">'+c+'</span>',ok:!!ok}};
var eOpt=function(e,ok){return {h:'<span class="o-e">'+e+'</span>',ok:!!ok}};
var wOpt=function(w,ok){return {h:'<span class="o-w">'+w+'</span>',ok:!!ok}};
var cOpt=function(c,ok){return {h:sw(c,58),ok:!!ok}};
var sOpt=function(s,ok){return {h:shp(s,'#8a52c4',58),ok:!!ok}};
var nOpt=tOpt;
function statObjs(e,n){var s='';for(var i=0;i<n;i++)s+='<span>'+e+'</span>';return '<div class="statobjs" role="img" aria-label="'+n+' pictures">'+s+'</div>'}
function tapQs(items,pool,label,say,optFn,fb){
  return items.map(function(t){
    var idx=pool.indexOf(t),d1=pool[(idx+1)%pool.length],d2=pool[(idx+2)%pool.length];
    return {q:label(t),say:say(t),opts:[optFn(t,true),optFn(d1,false),optFn(d2,false)],fb:fb?fb(t):''};
  });
}
function mini(id,title,qs){
  var u=uid();MOUNTS.push(function(){mountQuiz($('#'+u),{id:null,qs:qs,compact:true})});
  return '<div class="mini digital-only"><h3>👆 '+title+'</h3><div class="quiz" id="'+u+'"></div></div>';
}
function nameLine(){return '<div class="nameline"><span>Name: <span class="ln"></span></span><span>Date: <span class="ln s"></span></span></div>'}
function circRow(n,q,items){return '<div class="ws-row"><div class="q"><span class="qn">'+n+'</span>'+q+'</div>'+items+'</div>'}
function circ(h,pic,label){return '<button type="button" class="circ'+(pic?' pic':'')+'" aria-pressed="false">'+h+(label?'<small>'+label+'</small>':'')+'</button>'}
 
/* ---- letters ---- */
var LET=[
['A','Apple','🍎','a big shiny red apple with one green leaf and a tiny smile'],
['B','Bear','🐻','a fluffy brown bear waving hello'],
['C','Cat','🐱','a cute orange kitten with a curly tail'],
['D','Dog','🐶','a happy puppy with floppy ears and a wagging tail'],
['E','Elephant','🐘','a gentle grey baby elephant with big round ears'],
['F','Fish','🐟','a smiling blue fish blowing bubbles'],
['G','Giraffe','🦒','a tall, friendly giraffe with soft brown spots'],
['H','Horse','🐴','a smiling brown pony with a flowing mane'],
['I','Ice cream','🍦','a two-scoop pink and mint ice-cream cone'],
['J','Juice','🧃','a juice box with a straw and a smiling orange slice'],
['K','Kite','🪁','a bright diamond kite with a rainbow tail'],
['L','Lion','🦁','a friendly golden lion cub with a fluffy mane'],
['M','Moon','🌙','a smiling yellow crescent moon with tiny stars'],
['N','Nose','👃','a big friendly cartoon nose sniffing a flower (keep it cute, not realistic)'],
['O','Orange','🍊','a round orange with a green leaf'],
['P','Pig','🐷','a pink piglet with a curly tail'],
['Q','Queen','👸','a kind queen with a small golden crown'],
['R','Rainbow','🌈','a big rainbow with two fluffy clouds'],
['S','Sun','☀️','a smiling yellow sun with soft rays'],
['T','Tree','🌳','a round green tree with a brown trunk'],
['U','Umbrella','☔','a polka-dot umbrella in the rain with a happy duck'],
['V','Violin','🎻','a small violin with a bow and tiny music notes'],
['W','Whale','🐳','a smiling blue whale with a water spout'],
['X','Xylophone',null,'a rainbow xylophone with five coloured bars (original drawing in this file)',XYLO],
['Y','Yarn','🧶','a ball of pink yarn with a loose, curly string'],
['Z','Zebra','🦓','a friendly zebra with soft black-and-white stripes']
];
var LW={};LET.forEach(function(l){LW[l[1]]=l[2]});
function letterCard(l,i){
  var L=l[0],w=l[1];
  return '<article class="card"><div class="bigl"><span>'+L+'</span><span class="lo">'+L.toLowerCase()+'</span></div>'
  +'<div class="pic" role="img" aria-label="'+w+'">'+(l[4]||l[2])+'</div>'
  +'<div class="word"><b>'+w.charAt(0)+'</b>'+w.slice(1)+' <button type="button" class="say digital-only" data-say="'+L+'. '+w+'" aria-label="Hear '+w+'">🔊</button></div>'
  +'<p class="cap">'+L+' is for '+w+'!</p>'
  +pad(padText(L,L.toLowerCase()),PEN[i%PEN.length])+'</article>';
}
 
/* ---- numbers ---- */
var NUMW=['one','two','three','four','five','six','seven','eight','nine','ten','eleven','twelve','thirteen','fourteen','fifteen','sixteen','seventeen','eighteen','nineteen','twenty'];
var NUM=[['☀️','Sun'],['🦆','Ducks'],['🎈','Balloons'],['🌸','Flowers'],['⭐','Stars'],['🦋','Butterflies'],['🧁','Cupcakes'],['🐞','Ladybugs'],['🍎','Apples'],['🐟','Fish'],['🍓','Strawberries'],['🍪','Cookies'],['🌼','Daisies'],['🐝','Bees'],['🍌','Bananas'],['🚗','Cars'],['🍇','Grapes'],['✏️','Pencils'],['🍭','Lollipops'],['🍒','Cherries']];
function numCard(i){
  var n=i+1,w=NUMW[i],e=NUM[i][0],noun=NUM[i][1],sz=n<=5?'sl':(n<=10?'sm':'ss'),o='';
  for(var k=0;k<n;k++)o+='<button type="button" class="obj" aria-label="count">'+e+'</button>';
  return '<article class="card"><div class="bign">'+n+'</div><div class="nword">'+cap(w)+' <button type="button" class="say digital-only" data-say="'+w+'" aria-label="Hear '+w+'">🔊</button></div>'
  +'<div class="objs '+sz+'" data-n="'+n+'" role="img" aria-label="'+n+' '+noun.toLowerCase()+'">'+o+'</div>'
  +'<p class="cap">'+cap(w)+' '+noun+'</p>'
  +pad(padText(n,n,n>9?62:78),PEN[i%PEN.length])+'</article>';
}
 
/* ---- animals ---- */
var ANI=[
['cat','🐱','The cat is small.','Meow!','I say meow. I like milk. Who am I?','a small orange kitten with a curly tail'],
['dog','🐶','The dog is happy.','Woof!','I say woof. I wag my tail. Who am I?','a happy brown puppy with floppy ears'],
['rabbit','🐰','The rabbit is fast.',null,'I have long ears. I hop, hop, hop! Who am I?','a fluffy white rabbit with long pink-inside ears'],
['lion','🦁','The lion is big.','Roar!','I say roar. I have a big, fluffy mane. Who am I?','a friendly golden lion with a round mane and a smile'],
['elephant','🐘','The elephant is very big.','Toot!','I have a long trunk. I am very big. Who am I?','a gentle grey elephant with a curled trunk'],
['monkey','🐵','The monkey is funny.','Ooh-ooh!','I love bananas. I climb trees. Who am I?','a playful brown monkey holding a banana'],
['fish','🐟','The fish can swim.','Blub!','I live in water. I can swim. Who am I?','a smiling blue fish with bubbles'],
['bird','🐦','The bird can fly.','Tweet!','I have wings. I say tweet. Who am I?','a small blue bird singing on a branch'],
['turtle','🐢','The turtle is slow.',null,'I have a hard shell. I walk very slowly. Who am I?','a green turtle with a patterned shell and a kind smile']
];
var AE={};ANI.forEach(function(a){AE[a[0]]=a[1]});
function aniCard(a,i){
  var w=a[0];
  return '<article class="card"><div class="apic" role="img" aria-label="'+w+'">'+a[1]+'</div>'
  +'<div class="aname">'+w+' <button type="button" class="say digital-only" data-say="'+w+'" aria-label="Hear '+w+'">🔊</button></div>'
  +'<p class="sent">This is '+art(w)+' '+w+'. <button type="button" class="say digital-only" data-say="This is '+art(w)+' '+w+'." aria-label="Hear sentence">🔊</button></p>'
  +'<p class="sent">'+a[2]+' <button type="button" class="say digital-only" data-say="'+a[2]+'" aria-label="Hear sentence">🔊</button></p>'
  +pad(padWord(w),PEN[i%PEN.length])+'</article>';
}
 
/* ---- colors + shapes ---- */
var COL=[['red','🍎','apple'],['yellow','☀️','sun'],['blue',BALL,'ball'],['green','🐸','frog'],['orange','🥕','carrot'],['purple','🍇','grapes']];
var SHP=[['circle','blue','like the moon 🌕'],['square','orange','like a picture frame 🖼️'],['triangle','green','like a pizza slice 🍕'],['rectangle','purple','like a door 🚪'],['star','yellow','like a twinkling star 🌟'],['heart','red','like a love heart 💗']];
 
/* ================= BUILD PAGES ================= */
 
/* 1 cover */
function rainbow(t){var cs=['#ff5d8f','#ff8c3a','#e8b100','#3fb55a','#3d8bd6','#8e5bc6'],k=0;return t.split('').map(function(ch){return ch===' '?' ':'<span style="color:'+cs[(k++)%cs.length]+'">'+ch+'</span>'}).join('')}
add({kind:'cover',theme:'info',raw:true,title:'Cover',
 body:'<div class="cover">'
 +[['A','#ff8fb8','4%','5%'],['B','#e8b100','84%','4%'],['C','#3fb55a','7%','64%'],['1','#4d9de0','86%','60%'],['2','#a06cd5','3%','36%'],['3','#ff9f45','90%','34%']].map(function(b,i){return '<span class="blk" style="--c:'+b[1]+';left:'+b[2]+';top:'+b[3]+';animation-delay:'+(i*.4)+'s" aria-hidden="true">'+b[0]+'</span>'}).join('')
 +[['🎈','17%','1%'],['🌈','71%','1%'],['⭐','5%','84%'],['🍎','87%','84%'],['🦋','46%','1%']].map(function(b,i){return '<span class="em" style="left:'+b[1]+';top:'+b[2]+';animation-delay:'+(i*.5)+'s" aria-hidden="true">'+b[0]+'</span>'}).join('')
 +'<p class="cv-kicker">A picture workbook for ages 3 to 7</p>'
 +'<h1 class="cv-title" aria-label="My First English Adventure"><span class="w">'+rainbow('My First')+'</span><span class="w">'+rainbow('English')+'</span><span class="w">'+rainbow('Adventure')+'</span></h1>'
 +'<p class="cv-sub">Learn, Play, and Discover!</p>'
 +'<div class="cv-pals">'+milo(138,'cheer')+'<div class="cv-animals" aria-hidden="true">🐱🐶🐘</div>'+bibi(124)+'</div>'
 +'<label class="cv-brand"><span>Author or brand</span><input type="text" placeholder="Type your name or brand here" aria-label="Author or brand name"></label>'
 +'</div>',
 notes:{art:'Pastel gradient cover. Milo the bear (brown, round, smiling) and Bibi the bunny (lilac, long ears) stand centre. Floating letter blocks A B C and number blocks 1 2 3, plus a balloon, rainbow, star, apple and butterfly. Title letters in six friendly colours.',act:'Printable. The brand box is a text field: type a name on screen, or leave it empty and write by hand after printing.',ans:'None.'}});
 
/* 2 welcome */
add({kind:'info',theme:'info',title:'Hello, Explorer!',sub:'Come on an adventure with Milo and Bibi.',say:'Hi! Let us learn!',
 body:function(){return '<div class="w-hero">'+milo(112,'cheer')+'<span class="bubble big">Hi! I am Milo!</span>'+bibi(100)+'<span class="bubble big">And I am Bibi!</span></div>'
 +'<p class="inst">We will learn letters, numbers, animals, colors and shapes. Look, say, trace and play!</p>'
 +'<div class="grid g3 legend">'
 +'<div class="card"><div class="em2">📖</div><b>Learn + Trace</b><p>Look, listen and trace. Works on screen and prints well.</p></div>'
 +'<div class="card"><div class="em2">👆</div><b>Interactive</b><p>Tap the answers on the screen. These pages are made for tablets, phones and computers.</p></div>'
 +'<div class="card"><div class="em2">🖨️</div><b>Printable</b><p>Print it and use a pencil or crayons. Answers are on page '+PAGES.length+'.</p></div></div>'
 +'<div class="card grown"><h3>👩‍🏫 Grown-ups\u2019 corner</h3><ul>'
 +'<li>Short visits work best: one or two pages a day, about 10 minutes.</li>'
 +'<li>Say each word out loud together and let your child say it back.</li>'
 +'<li>The 🔊 buttons read a word using the voice built into your device, if it has one. It is a computer voice, not a recording, and it may sound different on each device.</li>'
 +'<li>Tracing works with a finger, stylus or mouse. The ↺ button erases. Drawings are not saved.</li>'
 +'<li>Stars are given when a game is finished. They are kept on this device only if your browser allows it.</li>'
 +'<li>Printing: use the 🖨️ menu, or your browser\u2019s own Print command. By default it prints the learning pages, worksheets, certificate and answer key (not the on-screen games).</li>'
 +'<li>Pictures in this edition are emoji drawn by your device, plus a few original drawings (Milo, Bibi, shapes, ball, xylophone). Replace the emoji with original or licensed artwork before you sell or share a print edition. The 📝 Notes button shows an illustration brief for every page.</li></ul></div>'},
 notes:{art:'Milo and Bibi greet the child with speech bubbles. Three large icon cards explain the page types.',act:'Information page for grown-ups and children.',ans:'None.'}});
 
/* 3 contents */
var contentsDef={kind:'info',theme:'info',title:'Our Adventure Map',sub:'Tap a place to go there.',say:'Where shall we go?',
 body:function(){
  var secs=[['alpha','🔤'],['num','🔢'],['ani','🐾'],['col','🎨'],['game','🎮'],['rev','🏅']];
  return '<div class="toc">'+secs.map(function(s){
    var ps=PAGES.filter(function(p){return p.theme===s[0]&&p.n>3&&p.kind!=='key'});
    return '<button type="button" class="tile" style="--tint:var(--t-'+s[0]+')" data-go="'+ps[0].n+'"><span class="te">'+s[1]+'</span><span>'+THEME[s[0]]+'<small>Pages '+ps[0].n+' to '+ps[ps.length-1].n+'</small></span></button>';
  }).join('')+'</div><p class="inst" style="margin-top:16px">Grown-ups: the answer key is on page '+PAGES.length+'.</p>';
 },
 notes:{art:'Six large pastel tiles, one per section, each with a big icon.',act:'Digital navigation page (tiles are buttons). Prints as a simple contents list.',ans:'None.'}};
add(contentsDef);
 
/* 4-10 alphabet */
var LG=[[0,4],[4,8],[8,12],[12,16],[16,20],[20,23],[23,26]];
LG.forEach(function(r,gi){
  var g=LET.slice(r[0],r[1]);
  add({kind:'learn',theme:'alpha',title:'Letters '+g[0][0]+' to '+g[g.length-1][0],sub:'Say it. Look. Trace it with your finger!',say:'Say it with me!',
   body:'<div class="grid '+(g.length===3?'g3':'g2')+'">'+g.map(function(l,i){return letterCard(l,i+gi)}).join('')+'</div>',
   notes:{art:g.map(function(l){return '<b>'+l[0]+' – '+l[1]+':</b> '+l[3]}).join('<br>'),act:'Trace each capital and small letter (digital: finger or mouse on the dotted letters; printable: dotted letters print as tracing guides). Tap 🔊 to hear the word.',ans:'No answer key needed for tracing.'}});
});
 
/* 11 find the letter (interactive) */
var FLQ=[['B','Tap the matching letter.',['P','B','D']],['a','Tap the BIG letter that matches.',['E','A','O']],['S','Tap the matching letter.',['Z','S','E']],['m','Tap the BIG letter that matches.',['N','M','W']],['C','Tap the matching letter.',['O','C','G']],['t','Tap the BIG letter that matches.',['F','T','I']]];
var FLANS=FLQ.map(function(q){return q[0].toUpperCase()});
keyAdd('play','Find the Letter','Answers: '+FLANS.join(' · ')+'.');
playPage({theme:'alpha',title:'Find the Letter',sub:'Look at the letter. Tap the one that matches!',say:'Find the letter!',act:'find-letter',
 qs:FLQ.map(function(q){var ans=q[0].toUpperCase();return {q:q[1],say:q[1],big:'<span class="bt">'+q[0]+'</span>',opts:q[2].map(function(c){return tOpt(c,c===ans)}),fb:'That is '+ans+'!'}}),
 notes:{art:'One giant letter on a pastel card; three big letter buttons below. Milo cheers after a correct tap.',act:'Interactive: 6 questions, wrong taps can be retried, stars at the end.',ans:'B · A · S · M · C · T.'}});
 
/* 12 printable circle the letter */
var CL=[['A',['B','A','D','A','M','A','S','T']],['M',['N','M','W','H','M','E','N','K']],['S',['Z','S','C','S','E','S','O','S']],['t',['f','t','l','t','i','j','t','k']]];
var clKey=CL.map(function(r,i){var pos=[];r[1].forEach(function(c,k){if(c===r[0])pos.push(k+1)});return 'Row '+(i+1)+' ('+r[0]+'): '+pos.length+' — letters number '+pos.join(', ')}).join('<br>');
keyAdd('print','Circle the Letter',clKey);
add({kind:'print',theme:'alpha',title:'Circle the Letter',sub:'Circle every letter that matches the first one.',say:'Use a crayon!',
 body:nameLine()+CL.map(function(r,i){return circRow(i+1,'Circle every <b style="color:var(--acc);font-size:1.5em">'+r[0]+'</b>',r[1].map(function(c){return circ(c)}).join(''))}).join('')
 +'<p class="wbank digital-only">On screen you can tap a letter to circle it. There is no scoring here. Use the answer key.</p>',
 notes:{art:'Rows of large, widely spaced letters on white. Target letter shown big at the start of each row.',act:'Printable worksheet. Child circles the matching letters. (On screen, tapping a letter draws a circle; there is no scoring.)',ans:clKey}});
 
/* 13 circle the correct picture (interactive) */
var PLQ=[['B',['Cat','Bear','Lion'],'Bear'],['D',['Fish','Dog','Moon'],'Dog'],['F',['Tree','Apple','Fish'],'Fish'],['M',['Pig','Moon','Orange'],'Moon'],['P',['Elephant','Zebra','Pig'],'Pig'],['S',['Sun','Rainbow','Bear'],'Sun']];
keyAdd('play','Circle the Correct Picture (starts with…)',PLQ.map(function(q){return q[0]+' → '+q[2]}).join(' · ')+'.');
playPage({theme:'alpha',title:'Which Picture?',sub:'Tap the picture that starts with the letter.',say:'Which picture?',act:'pic-letter',
 qs:PLQ.map(function(q){return {q:'Which picture starts with this letter?',say:'Which picture starts with '+q[0]+'?',big:'<span class="bt">'+q[0]+'</span>',opts:q[1].map(function(w){return eOpt(LW[w],w===q[2])}),fb:q[0]+' is for '+q[2]+'!'}}),
 notes:{art:'Big letter in the centre; three large pictures below (no words, so the child listens for the first sound).',act:'Interactive: 6 questions with retry and stars.',ans:PLQ.map(function(q){return q[0]+' → '+q[2]}).join(', ')+'.'}});
 
/* 14 printable circle the correct picture */
var PCQ=[['C',['Moon','Cat','Pig'],1],['H',['Whale','Rainbow','Horse'],2],['L',['Lion','Tree','Bear'],0],['R',['Cat','Rainbow','Fish'],1],['T',['Apple','Sun','Tree'],2],['Z',['Zebra','Kite','Orange'],0]];
var pcKey=PCQ.map(function(q){return q[0]+' → '+q[1][q[2]]}).join(' · ');
keyAdd('print','Circle the Correct Picture',pcKey+'.');
add({kind:'print',theme:'alpha',title:'Circle the Picture',sub:'Circle the picture that starts with the letter.',say:'Say the words!',
 body:nameLine()+PCQ.map(function(q,i){return circRow(i+1,'Starts with <b style="color:var(--acc);font-size:1.4em">'+q[0]+'</b>',q[1].map(function(w){return circ(LW[w]||'',true,w)}).join(''))}).join(''),
 notes:{art:'Each row: three large pictures with small word labels underneath.',act:'Printable worksheet. Child says each word and circles the picture that starts with the letter.',ans:pcKey+'.'}});
 
/* 15-19 numbers */
[[0,4],[4,8],[8,12],[12,16],[16,20]].forEach(function(r,gi){
  var idx=[];for(var k=r[0];k<r[1];k++)idx.push(k);
  add({kind:'learn',theme:'num',title:'Numbers '+(r[0]+1)+' to '+r[1],sub:'Tap each picture and count. Then trace the number!',say:'Let us count!',
   body:'<div class="grid g2">'+idx.map(numCard).join('')+'</div>',
   notes:{art:idx.map(function(k){return '<b>'+(k+1)+' – '+NUMW[k]+' '+NUM[k][1].toLowerCase()+':</b> '+(k+1)+' cute cartoon '+NUM[k][1].toLowerCase()+', arranged in rows of five'}).join('<br>'),act:'Digital: tap each picture to count 1, 2, 3 (it says the number if your device has a voice) and trace the numeral with a finger. Printable: dotted numerals and the pictures print.',ans:'No answer key needed.'}});
});
 
/* 20 how many (interactive) */
var HMQ=[['🦆',2,'ducks'],['🎈',3,'balloons'],['⭐',5,'stars'],['🍎',4,'apples'],['🐟',7,'fish'],['🌸',10,'flowers']];
keyAdd('play','How Many?',HMQ.map(function(q){return q[1]+' '+q[2]}).join(' · ')+'.');
playPage({theme:'num',title:'How Many?',sub:'Count the pictures. Tap the right number!',say:'How many?',act:'howmany',
 qs:HMQ.map(function(q){var n=q[1],ds=[n+1,n>1?n-1:n+2];return {q:'How many '+q[2]+'?',say:'How many '+q[2]+'?',big:statObjs(q[0],n),opts:[nOpt(n,true),nOpt(ds[0]),nOpt(ds[1])],fb:cap(NUMW[n-1])+' '+q[2]+'!'}}),
 notes:{art:'A tidy group of pictures, then three big numerals as answers.',act:'Interactive: 6 counting questions with retry.',ans:HMQ.map(function(q){return q[1]+' '+q[2]}).join(', ')+'.'}});
 
/* 21 printable count and write */
var CW=[['⭐',2,'stars'],['🐟',4,'fish'],['🌸',6,'flowers'],['🦆',5,'ducks'],['🎈',8,'balloons'],['🍓',9,'strawberries']];
keyAdd('print','Count and Write',CW.map(function(q){return q[1]+' '+q[2]}).join(' · ')+'.');
add({kind:'print',theme:'num',title:'Count and Write',sub:'Count the pictures. Write the number.',say:'Count with your finger!',
 body:nameLine()+'<div class="grid g2">'+CW.map(function(q,i){var s='';for(var k=0;k<q[1];k++)s+=q[0];return '<div class="ws-row" style="display:block"><div class="q"><span class="qn">'+(i+1)+'</span>How many '+q[2]+'?</div><div class="numrow" style="margin:6px 0">'+s+'</div><div style="font-size:24px">Write: <span class="blankbox" style="width:2em"></span></div></div>'}).join('')+'</div>',
 notes:{art:'Six boxes, each with a clear group of one kind of picture and a blank box to write in.',act:'Printable worksheet.',ans:CW.map(function(q){return q[1]+' '+q[2]}).join(', ')+'.'}});
 
/* 22 number matching (interactive) */
function grp(e,n){var s='';for(var i=0;i<n;i++)s+=e;return '<span class="mgrp">'+s+'</span>'}
var nmRounds=[[1,2,3,4,5],[6,7,8,9,10]].map(function(r){return r.map(function(n){return {id:'n'+n,l:'<span class="mnum">'+n+'</span>',r:grp(NUM[n-1][0],n)}})});
(function(){var id=uid();MOUNTS.push(function(){mountMatch($('#'+id),{id:'num-match',rounds:nmRounds,hint:'Tap a number. Then tap the pictures with the same amount!'})});
 keyAdd('play','Match the Number','Each number matches the group with that many pictures (1 sun, 2 ducks, 3 balloons … 10 fish).');
 add({kind:'play',theme:'num',title:'Match the Number',sub:'Number on the left. Pictures on the right.',say:'Match them!',act:'num-match',body:'<div id="'+id+'"></div>',
 notes:{art:'Left: big numerals. Right: groups of pictures in a shuffled order.',act:'Interactive: two rounds, 5 pairs each.',ans:'Each numeral matches the group with the same number of pictures.'}})})();
 
/* 23-25 animals */
[[0,3,'Cat, Dog and Rabbit'],[3,6,'Lion, Elephant and Monkey'],[6,9,'Fish, Bird and Turtle']].forEach(function(r){
  var g=ANI.slice(r[0],r[1]),names=g.map(function(a){return a[0]});
  var qs=tapQs(names,names,function(t){return 'Tap the '+t+'.'},function(t){return 'Tap the '+t},function(t,ok){return eOpt(AE[t],ok)},function(t){return 'That is '+art(t)+' '+t+'!'});
  add({kind:'learn',theme:'ani',title:r[2],sub:'Say hello to each animal!',say:'Hello, friends!',
   body:'<div class="grid g3">'+g.map(function(a,i){return aniCard(a,i+r[0])}).join('')+'</div>'+mini('x','Mini game: tap the animal',qs),
   notes:{art:g.map(function(a){return '<b>'+a[0]+':</b> '+a[5]}).join('<br>'),act:'Digital: tap 🔊 to hear the words and sentences; trace each word; play the mini game. Printable: dotted words print for tracing (the mini game does not print).',ans:'Mini game: tap the animal that is named.'}});
});
 
/* 26 animal sounds (interactive) */
var SND=[['Meow!','cat'],['Woof!','dog'],['Roar!','lion'],['Tweet!','bird'],['Toot!','elephant'],['Ooh-ooh!','monkey']];
var sndPool=['cat','dog','lion','bird','elephant','monkey','fish','rabbit'];
keyAdd('play','Animal Sounds',SND.map(function(s){return s[0].replace('!','')+' → '+s[1]}).join(' · ')+'.');
playPage({theme:'ani',title:'Who Says It?',sub:'Read the sound. Which animal says it?',say:'Who says it?',act:'sounds',
 qs:SND.map(function(s){var others=sndPool.filter(function(a){return a!==s[1]});var d=shuffle(others).slice(0,2);return {q:'Who says “'+s[0].replace('!','')+'”?',say:'Who says '+s[0].replace('!','')+'?',big:'<div class="speech">'+s[0]+'</div>',opts:[eOpt(AE[s[1]],true),eOpt(AE[d[0]]),eOpt(AE[d[1]])],fb:'The '+s[1]+' says '+s[0].replace('!','')+'!'}}),
 notes:{art:'A speech bubble with the sound word; three animal pictures as answers. No audio files are used. The 🔊 button reads the question with the device voice.',act:'Interactive: 6 questions.',ans:SND.map(function(s){return s[0].replace('!','')+' → '+s[1]}).join(', ')+'.'}});
 
/* 27 animal matching (interactive) */
var amRounds=[['cat','dog','rabbit'],['lion','elephant','monkey'],['fish','bird','turtle']].map(function(r){return r.map(function(a){return {id:a,l:AE[a],r:'<span class="mw">'+a+'</span>'}})});
(function(){var id=uid();MOUNTS.push(function(){mountMatch($('#'+id),{id:'ani-match',rounds:amRounds,hint:'Tap an animal. Then tap its name!'})});
 keyAdd('play','Match the Animals','cat, dog, rabbit · lion, elephant, monkey · fish, bird, turtle (each picture matches its name).');
 add({kind:'play',theme:'ani',title:'Match the Animals',sub:'Picture on the left. Name on the right.',say:'Match the animals!',act:'ani-match',body:'<div id="'+id+'"></div>',
 notes:{art:'Left: animal pictures. Right: names in large lower-case type.',act:'Interactive: 3 rounds of 3 pairs.',ans:'Each animal picture matches its own name.'}})})();
 
/* 28 who am i (interactive) */
var WHO=[['cat','dog','fish'],['rabbit','lion','bird'],['lion','monkey','turtle'],['elephant','cat','fish'],['monkey','dog','bird'],['turtle','rabbit','elephant']];
var WHOA=['cat','rabbit','lion','elephant','monkey','turtle'];
var AR={};ANI.forEach(function(a){AR[a[0]]=a[4]});
keyAdd('play','Who Am I?',WHOA.join(' · ')+'.');
playPage({theme:'ani',title:'Who Am I?',sub:'Read the clue. Guess the animal!',say:'Who am I?',act:'whoami',
 qs:WHOA.map(function(a,i){return {q:AR[a],say:AR[a],big:'<span style="font-size:70px">❓</span>',opts:WHO[i].map(function(x){return eOpt(AE[x],x===a)}),fb:'I am '+art(a)+' '+a+'!'}}),
 notes:{art:'A big question mark, then three animal choices.',act:'Interactive riddles: 6 questions. Grown-ups can read the clue aloud; 🔊 reads it with the device voice.',ans:WHOA.join(', ')+'.'}});
 
/* 29 printable who am i + match sounds */
var WHOP=[['cat',['🐱','🐟','🦁']],['lion',['🐢','🦁','🐰']],['elephant',['🐘','🐦','🐵']],['turtle',['🐶','🐢','🐘']]];
var whopKey='Riddles: cat, lion, elephant, turtle. Lines: cat–Meow, dog–Woof, lion–Roar, bird–Tweet.';
keyAdd('print','Who Am I? + Match the Sounds',whopKey);
add({kind:'print',theme:'ani',title:'Who Am I?',sub:'Read the clue. Circle the animal. Then draw lines to match the sounds.',say:'Draw lines!',
 body:nameLine()+WHOP.map(function(q,i){return circRow(i+1,AR[q[0]],q[1].map(function(e){return circ(e,true)}).join(''))}).join('')
 +'<div class="ws-row" style="display:block"><div class="q"><span class="qn">5</span>Draw a line from the animal to its sound.</div><div class="mlines"><div><div class="mrow">🐱 <i class="pt"></i></div><div class="mrow">🐶 <i class="pt"></i></div><div class="mrow">🦁 <i class="pt"></i></div><div class="mrow">🐦 <i class="pt"></i></div></div><div><div class="mrow r"><i class="pt"></i> Roar!</div><div class="mrow r"><i class="pt"></i> Tweet!</div><div class="mrow r"><i class="pt"></i> Meow!</div><div class="mrow r"><i class="pt"></i> Woof!</div></div></div></div>',
 notes:{art:'Four riddle rows with three animals each, then a line-matching box with dots to join.',act:'Printable worksheet. (Drawing lines needs pencil and paper; the circles can be tapped on screen without scoring.)',ans:whopKey}});
 
/* 30 colors */
(function(){
  var names=COL.map(function(c){return c[0]});
  var qs=tapQs(['yellow','purple','blue','red'],names,function(t){return 'Tap '+t+'.'},function(t){return 'Tap the color '+t},function(t,ok){return cOpt(t,ok)},function(t){return 'That is '+t+'!'});
  add({kind:'learn',theme:'col',title:'Colors',sub:'Say the color. Look at the picture!',say:'What color?',
   body:'<div class="grid g3">'+COL.map(function(c){return '<article class="card"><div class="cring" style="--c:'+COLORS[c[0]]+'">'+c[1]+'</div><div class="cword"><span class="dotc" style="background:'+COLORS[c[0]]+'"></span>'+c[0]+' <button type="button" class="say digital-only" data-say="'+c[0]+'" aria-label="Hear '+c[0]+'">🔊</button></div><p class="sent">'+cap(art(c[0]))+' '+c[0]+' '+c[2]+'.</p></article>'}).join('')+'</div>'
   +'<p class="inst" style="margin-top:12px">🖍️ Color the circles above with crayons if you print this page!</p>'+mini('c','Mini game: tap the color',qs),
   notes:{art:'Six large circles outlined in each colour, each with one picture: red apple, yellow sun, blue ball (original drawing), green frog, orange carrot, purple grapes.',act:'Digital: tap 🔊 and play the colour mini game. Printable: the coloured circle outlines print.',ans:'Mini game: tap the colour that is named.'}});
})();
 
/* 31 shapes */
(function(){
  var names=SHP.map(function(s){return s[0]});
  var qs=tapQs(['triangle','circle','heart','square'],names,function(t){return 'Tap the '+t+'.'},function(t){return 'Tap the '+t},function(t,ok){return sOpt(t,ok)},function(t){return 'That is '+art(t)+' '+t+'!'});
  add({kind:'learn',theme:'col',title:'Shapes',sub:'Say the shape. Trace it with your finger!',say:'What shape?',
   body:'<div class="grid g3">'+SHP.map(function(s,i){return '<article class="card"><div style="padding:6px">'+shp(s[0],s[1],88)+'</div><div class="cword">'+s[0]+' <button type="button" class="say digital-only" data-say="'+s[0]+'" aria-label="Hear '+s[0]+'">🔊</button></div><p class="sent">'+s[2]+'</p>'+pad(padShape(s[0]),PEN[i%PEN.length])+'</article>'}).join('')+'</div>'+mini('s','Mini game: tap the shape',qs),
   notes:{art:'Six chunky shapes with rounded corners (circle blue, square orange, triangle green, rectangle purple, star yellow, heart red), each beside a small everyday object.',act:'Digital: trace the dotted shapes, tap 🔊, play the shape mini game. Printable: dotted shapes print for tracing.',ans:'Mini game: tap the shape that is named.'}});
})();
 
/* 32 coloring interactive */
(function(){var id=uid();MOUNTS.push(function(){mountColoring($('#'+id))});
 keyAdd('play','Color the Picture','No wrong answers! A star is given after 6 parts are coloured.');
 add({kind:'play',theme:'col',title:'Color the Picture',sub:'Tap a crayon. Tap the picture. Make it yours!',say:'Let us color!',act:'coloring',body:'<div id="'+id+'"></div>',
 notes:{art:'A simple garden scene: sun with a smile, cloud, house with roof, door and window, tree, flower, ball and grass. Thick outlines, big areas.',act:'Interactive tap-to-color (8 crayons and an eraser). Your colouring is not saved.',ans:'Free colouring. No wrong answers.'}})})();
 
/* 33 printable coloring */
(function(){
  var L=[['sun','yellow'],['roof','red'],['leaves','green'],['ball','blue'],['door','orange'],['flower petals','purple']];
  keyAdd('print','Color the Picture (printable)','Sun yellow, roof red, leaves green, ball blue, door orange, flower petals purple. Everything else: any colour!');
  add({kind:'print',theme:'col',title:'Color the Picture',sub:'Use crayons. Follow the color words!',say:'Use your crayons!',
   body:nameLine()+'<div class="sheet">'+SCENE()+'</div><ul class="rules">'+L.map(function(x){return '<li>'+sw(x[1],24)+' Color the '+x[0]+' <b>'+x[1]+'</b>.</li>'}).join('')+'</ul>',
   notes:{art:'Same garden scene as the interactive page, with white regions and bold outlines ready for crayons.',act:'Printable colouring page with 6 colour instructions.',ans:'Sun yellow, roof red, leaves green, ball blue, door orange, flower petals purple.'}});
})();
 
/* 34 find something blue (interactive) */
(function(){var id=uid();MOUNTS.push(function(){mountHunt($('#'+id))});
 keyAdd('play','Find Something Blue','Blue: whale, blueberries, butterfly, blue heart (4). Other colours: red 4, yellow 3, green 3, orange 3, purple 3. (Emoji shades can differ a little between devices.)');
 add({kind:'play',theme:'col',title:'Find Something Blue',sub:'Tap every blue picture. Then try another color!',say:'Find blue!',act:'blue',body:'<div id="'+id+'"></div>',
 notes:{art:'A 5 by 4 grid of colourful pictures, 3 or 4 for each colour.',act:'Interactive colour hunt. Choose a colour crayon to play again.',ans:'Blue: whale, blueberries, butterfly, blue heart.'}})})();
 
/* 35 printable shape hunt */
(function(){
  var rows=[['triangle',['circle','triangle','square','triangle','star','triangle','heart','rectangle']],['circle',['square','circle','heart','circle','triangle','star','circle','rectangle']],['star',['heart','star','circle','square','star','rectangle','triangle','heart']]];
  var cols=['blue','orange','green','purple','yellow','red','blue','orange'];
  var key=rows.map(function(r,i){var pos=[];r[1].forEach(function(s,k){if(s===r[0])pos.push(k+1)});return 'Row '+(i+1)+' ('+r[0]+'s): '+pos.length+' — shapes number '+pos.join(', ')}).join('<br>');
  keyAdd('print','Shape Hunt',key);
  add({kind:'print',theme:'col',title:'Shape Hunt',sub:'Circle the shape named in each row.',say:'Find the shapes!',
   body:nameLine()+rows.map(function(r,i){return circRow(i+1,'Circle the <b style="color:var(--acc)">'+r[0]+'s</b>',r[1].map(function(s,k){return circ(shp(s,cols[(k+i)%cols.length],52))}).join(''))}).join(''),
   notes:{art:'Rows of eight chunky shapes in mixed colours, evenly spaced.',act:'Printable worksheet. (On screen, tapping draws a circle; no scoring.)',ans:key}});
})();
 
/* 36 picture to word (interactive) */
var PW=[[['Apple','🍎'],['Bear','🐻'],['Sun','☀️'],['Fish','🐟']],[['Elephant','🐘'],['Rainbow','🌈'],['Turtle','🐢'],['Lion','🦁']],[['Balloon','🎈'],['Tree','🌳'],['Bird','🐦'],['Monkey','🐵']]];
(function(){var id=uid();
 var rounds=PW.map(function(r){return r.map(function(p){return {id:p[0],l:p[1],r:'<span class="mw">'+p[0]+'</span>'}})});
 MOUNTS.push(function(){mountMatch($('#'+id),{id:'word-match',rounds:rounds,hint:'Tap a picture. Then tap its word!'})});
 keyAdd('play','Picture-to-Word Match',PW.map(function(r){return r.map(function(p){return p[1]+' '+p[0]}).join(', ')}).join(' | '));
 add({kind:'play',theme:'game',title:'Picture to Word',sub:'Match each picture with its word.',say:'Match the words!',act:'word-match',body:'<div id="'+id+'"></div>',
 notes:{art:'Left: large pictures. Right: words in big, rounded letters.',act:'Interactive: 3 rounds of 4 pairs.',ans:PW.map(function(r){return r.map(function(p){return p[0]}).join(', ')}).join(' | ')}})})();
 
/* 37 missing letter (interactive) */
var ML=[['cat','🐱','a',['a','e','o']],['dog','🐶','o',['o','u','a']],['sun','☀️','u',['u','i','e']],['pig','🐷','i',['i','o','a']],['bed','🛏️','e',['e','a','i']],['hat','🎩','a',['a','u','o']]];
function blankWord(w,v){return w.replace(v,'<span style="display:inline-block;width:.8em;border-bottom:6px solid var(--acc);margin:0 4px"></span>')}
keyAdd('play','Missing Letters',ML.map(function(m){return m[0]+' → '+m[2]}).join(' · ')+'.');
playPage({theme:'game',title:'Missing Letter',sub:'Which letter finishes the word?',say:'Find the missing letter!',act:'missing',
 qs:ML.map(function(m){return {q:'Which letter is missing?',say:'Which letter is missing in '+m[0].split('').join(' ')+'?',big:'<div><div style="font-size:84px">'+m[1]+'</div><div style="font-size:64px;font-weight:700;letter-spacing:6px">'+blankWord(m[0],m[2])+'</div></div>',opts:m[3].map(function(c){return tOpt(c,c===m[2])}),fb:m[0]+'!'}}),
 notes:{art:'One picture, the word with a blank, and three letter buttons.',act:'Interactive: 6 three-letter words (the missing letter is a vowel).',ans:ML.map(function(m){return m[0]+' → '+m[2]}).join(', ')+'.'}});
 
/* 38 quick quiz (interactive) */
var QQ=[
 {q:'Which word says “apple”?',say:'Which word says apple?',big:'<span class="xl">🍎</span>',opts:[wOpt('Apple',1),wOpt('Bear'),wOpt('Sun')],fb:'Apple!'},
 {q:'How many stars?',say:'How many stars?',big:statObjs('⭐',4),opts:[nOpt(3),nOpt(4,1),nOpt(5)],fb:'Four stars!'},
 {q:'Who says “Woof”?',say:'Who says woof?',big:'<div class="speech">Woof!</div>',opts:[eOpt('🐶',1),eOpt('🐱'),eOpt('🐟')],fb:'The dog says woof!'},
 {q:'Tap the color yellow.',say:'Tap the color yellow',opts:[cOpt('red'),cOpt('yellow',1),cOpt('blue')],fb:'Yellow!'},
 {q:'Tap the triangle.',say:'Tap the triangle',opts:[sOpt('circle'),sOpt('triangle',1),sOpt('square')],fb:'A triangle!'},
 {q:'Which letter does “sun” start with?',say:'Which letter does sun start with?',big:'<span class="xl">☀️</span>',opts:[tOpt('S',1),tOpt('T'),tOpt('M')],fb:'S is for sun!'}
];
keyAdd('play','Quick Quiz','apple · 4 stars · dog · yellow · triangle · S.');
playPage({theme:'game',title:'Quick Quiz',sub:'Six fun questions. You can do it!',say:'Quiz time!',act:'quick',qs:QQ,
 notes:{art:'Mixed pictures: apple, four stars, speech bubble, colour dots, shapes, sun.',act:'Interactive multiple-choice quiz with retry and a star rating at the end.',ans:'Apple · 4 · dog · yellow · triangle · S.'}});
 
/* 39 printable missing letters */
(function(){
  var key=ML.map(function(m){return m[0]+' → '+m[2]}).join(' · ');
  keyAdd('print','Missing Letters',key+'.');
  add({kind:'print',theme:'game',title:'Missing Letters',sub:'Write the missing vowel in each box.',say:'a e i o u',
   body:nameLine()+'<p class="inst">Letter bank: <b style="color:var(--acc);letter-spacing:8px;font-size:1.3em">a e i o u</b></p><div class="grid g2">'+ML.map(function(m,i){var w=m[0].replace(m[2],'@');return '<div class="ws-row" style="justify-content:center"><div class="q"><span class="qn">'+(i+1)+'</span></div><span style="font-size:64px">'+m[1]+'</span><span style="font-size:52px;font-weight:700;letter-spacing:4px">'+w.replace('@','<span class="blankbox"></span>')+'</span></div>'}).join('')+'</div>',
   notes:{art:'Six pictures, each beside its word with an empty box.',act:'Printable worksheet.',ans:key+'.'}});
})();
 
/* 40 rewards (interactive) */
add({kind:'play',theme:'game',title:'Stars and Badges',sub:'See what you have earned!',say:'Great job!',body:'<div class="rewards" id="rw"></div>',
 notes:{art:'Milo and Bibi cheer above a star meter and six badge cards (locked badges are grey with a lock).',act:'Interactive: stars come from finishing the 13 games. Badges unlock when all their games are finished. Progress is kept on this device only if the browser allows it.',ans:'Badges: Letter Star (2 games), Number Whiz (2), Animal Friend (3), Color Artist (2), Word Wizard (3), Little Explorer (1).'}});
 
/* 41 printable sticker chart */
add({kind:'print',theme:'game',title:'My Star Chart',sub:'Add a sticker or draw a star each time you finish a page.',say:'Keep going!',
 body:nameLine()+'<div class="stk">'+'<div>★</div>'.repeat(12)+'</div><div class="cheers"><span>Great Job!</span><span>You Did It!</span><span>Keep Learning!</span></div>',
 notes:{art:'Twelve dashed circles to fill with stickers or hand-drawn stars, plus three encouraging phrases.',act:'Printable reward chart.',ans:'None.'}});
 
/* 42 review quiz (interactive) */
var RQ=[
 {q:'Which picture starts with C?',say:'Which picture starts with C?',big:'<span class="bt">C</span>',opts:[eOpt('🐻'),eOpt('🐱',1),eOpt('🍎')],fb:'C is for cat!'},
 {q:'Find the letter D.',say:'Find the letter D',big:'<span class="bt">D</span>',opts:[tOpt('B'),tOpt('D',1),tOpt('P')],fb:'That is D!'},
 {q:'How many balloons?',say:'How many balloons?',big:statObjs('🎈',3),opts:[nOpt(2),nOpt(3,1),nOpt(4)],fb:'Three balloons!'},
 {q:'How many cupcakes?',say:'How many cupcakes?',big:statObjs('🧁',7),opts:[nOpt(6),nOpt(7,1),nOpt(8)],fb:'Seven cupcakes!'},
 {q:'Who says “Roar”?',say:'Who says roar?',big:'<div class="speech">Roar!</div>',opts:[eOpt('🐰'),eOpt('🦁',1),eOpt('🐢')],fb:'The lion says roar!'},
 {q:'I have a long trunk. Who am I?',say:'I have a long trunk. Who am I?',big:'<span style="font-size:70px">❓</span>',opts:[eOpt('🐘',1),eOpt('🐶'),eOpt('🐦')],fb:'I am an elephant!'},
 {q:'Which word says “dog”?',say:'Which word says dog?',big:'<span class="xl">🐶</span>',opts:[wOpt('Cat'),wOpt('Dog',1),wOpt('Sun')],fb:'Dog!'},
 {q:'Tap the color blue.',say:'Tap the color blue',opts:[cOpt('green'),cOpt('blue',1),cOpt('orange')],fb:'Blue!'},
 {q:'Tap the heart.',say:'Tap the heart',opts:[sOpt('square'),sOpt('star'),sOpt('heart',1)],fb:'A heart!'},
 {q:'Which letter is missing?',say:'Which letter is missing in c a t?',big:'<div><div style="font-size:84px">🐱</div><div style="font-size:64px;font-weight:700;letter-spacing:6px">c<span style="display:inline-block;width:.8em;border-bottom:6px solid var(--acc);margin:0 4px"></span>t</div></div>',opts:[tOpt('a',1),tOpt('o'),tOpt('u')],fb:'cat!'}
];
keyAdd('play','Review Quiz','C-cat · D · 3 balloons · 7 cupcakes · lion · elephant · Dog · blue · heart · a (cat).');
playPage({theme:'rev',title:'Review Quiz',sub:'Ten questions from the whole book!',say:'Show what you know!',act:'review',qs:RQ,
 notes:{art:'Mixed review: letters, counting, animals, words, colours, shapes, missing letter.',act:'Interactive: 10 questions with retry and star rating. Finishing it earns the Little Explorer badge.',ans:'C-cat · D · 3 · 7 · lion · elephant · dog · blue · heart · a.'}});
 
/* 43 printable review */
(function(){
  var key='1. Bear · 2. 7 · 3. Lion · 4. Blue (third) · 5. Triangle (middle) · 6. dog → o · 7. elephant · 8. three';
  keyAdd('print','Review Quiz (printable)',key);
  add({kind:'print',theme:'rev',title:'Review Quiz',sub:'Do your best. Great job, explorer!',say:'You can do it!',
   body:nameLine()
   +circRow(1,'Circle the picture that starts with <b>B</b>.',circ('🐱',true)+circ('🐻',true)+circ('🍎',true))
   +'<div class="ws-row"><div class="q"><span class="qn">2</span>How many apples? Write the number.</div><span class="numrow">🍎🍎🍎🍎🍎🍎🍎</span><span class="blankbox" style="width:2em"></span></div>'
   +circRow(3,'Who says “Roar”?',circ('🐶',true)+circ('🦁',true)+circ('🐟',true))
   +circRow(4,'Circle the color <b>blue</b>.',circ(sw('red',48))+circ(sw('yellow',48))+circ(sw('blue',48)))
   +circRow(5,'Circle the <b>triangle</b>.',circ(shp('circle','purple',52))+circ(shp('triangle','purple',52))+circ(shp('square','purple',52)))
   +'<div class="ws-row"><div class="q"><span class="qn">6</span>Write the missing letter.</div><span style="font-size:52px;font-weight:700;letter-spacing:4px">🐶 d<span class="blankbox"></span>g</span></div>'
   +circRow(7,'Which word is the picture? 🐘',circ('elephant')+circ('lion')+circ('turtle'))
   +'<div class="ws-row"><div class="q"><span class="qn">8</span>Write the number word for 3. <span class="wbank">(one · two · three)</span></div><span class="ln" style="min-width:220px"></span></div>',
   notes:{art:'Eight clearly separated questions with large pictures.',act:'Printable review. Circle, count and write.',ans:key}});
})();
 
/* 44 certificate */
add({kind:'cert',theme:'rev',title:'Little English Explorer',sub:'You finished the adventure!',say:'Hooray!',
 body:'<div class="cert"><div class="bigs" aria-hidden="true">⭐⭐⭐</div><h3>Little English Explorer</h3><p class="small">Certificate of Achievement</p>'
 +'<div style="display:flex;justify-content:center;gap:10px;align-items:flex-end">'+milo(100,'cheer')+bibi(90)+'</div>'
 +'<p class="small">This certificate is proudly given to</p><input class="cert-name" type="text" placeholder="Type a name here" aria-label="Child\u2019s name">'
 +'<p class="small">for finishing <b>My First English Adventure</b>!</p>'
 +'<div class="says"><span>Great Job!</span><span>You Did It!</span><span>Keep Learning!</span></div>'
 +'<div class="sign"><div><input type="text" aria-label="Date" placeholder="Date"><br>Date</div><div><input type="text" aria-label="Signed by" placeholder="Name"><br>Teacher or parent</div></div></div>',
 notes:{art:'Gold double border, three stars, Milo and Bibi, three encouraging phrases, name, date and signature lines.',act:'Printable certificate. Type the name on screen before printing, or write it by hand. Use 🖨️ Print → This page only.',ans:'None.'}});
 
/* 45 answer key */
add({kind:'key',theme:'info',title:'Answer Key',sub:'For parents and teachers.',say:'Answers inside!',
 body:function(){return '<p class="inst">🖨️ = printable worksheet · 👆 = interactive (the screen checks answers; they are listed here too).</p>'+KEY.map(function(k){return '<div class="kitem"><h3><span class="kp">p. '+k.p+'</span>'+k.title+' <small>'+(k.type==='print'?'🖨️ Printable':'👆 Interactive')+'</small></h3><div>'+k.html+'</div></div>'}).join('')},
 notes:{art:'Compact two-line entries, one per activity page.',act:'Printable answer key.',ans:'This page.'}});
 
/* ================= render ================= */
function notesHTML(d){
  var n=d.notes||{};var kind=KIND[d.kind];
  return '<div class="notes"><b>📝 Page '+d.n+' notes</b><dl>'
  +(kind?'<dt>Type</dt><dd>'+kind[1]+'</dd>':'')
  +(n.art?'<dt>Illustration brief</dt><dd>'+n.art+'</dd>':'')
  +(n.act?'<dt>Activity</dt><dd>'+n.act+'</dd>':'')
  +(n.ans?'<dt>Answer</dt><dd>'+n.ans+'</dd>':'')+'</dl></div>';
}
function pageHTML(d){
  var body=typeof d.body==='function'?d.body():d.body;
  if(d.raw)return '<section class="page raw t-'+d.theme+'" data-kind="'+d.kind+'" aria-label="'+d.title+'">'+body+notesHTML(d)+'</section>';
  var k=KIND[d.kind]||KIND.learn,buddy=BUDDY[d.theme]==='bibi'?bibi(62):milo(62);
  return '<section class="page t-'+d.theme+'" data-kind="'+d.kind+'" aria-label="Page '+d.n+': '+d.title+'">'
  +'<header class="phead"><div class="txt"><div class="chips"><span class="chip">'+THEME[d.theme]+'</span>'+(KIND[d.kind]?'<span class="chip k-'+k[0]+'">'+k[1]+'</span>':'')+'</div>'
  +'<h2 class="ptitle">'+d.title+'</h2>'+(d.sub?'<p class="psub">'+d.sub+'</p>':'')+'</div>'
  +'<div class="buddy">'+buddy+(d.say?'<span class="bubble">'+d.say+'</span>':'')+'</div></header>'
  +'<div class="pbody">'+body+'</div>'+notesHTML(d)
  +'<footer class="pf"><span>My First English Adventure</span><span>Page '+d.n+'</span></footer></section>';
}
$('#stage').innerHTML=PAGES.map(pageHTML).join('');
MOUNTS.forEach(function(f){f()});
 
/* drawer */
(function(){
  var icons={cover:'⭐',info:'⭐',learn:'📖',play:'👆',print:'🖨️',cert:'🎓',key:'🔑'},last='',html='';
  PAGES.forEach(function(p){
    var s=(p.kind==='key')?'For grown-ups':(THEME[p.theme]);
    if(s!==last){html+='<div class="dsec">'+s+'</div>';last=s}
    html+='<button type="button" class="ditem" data-go="'+p.n+'"><span class="dn">'+p.n+'</span><span>'+icons[p.kind]+' '+p.title+'</span></button>';
  });
  $('#dlist').innerHTML=html;
})();
 
/* ================= navigation ================= */
var cur=1;
function go(n){
  n=Math.max(1,Math.min(PAGES.length,n));cur=n;
  var pages=$$('.page');
  pages.forEach(function(p,i){p.classList.toggle('cur',i===n-1)});
  var p=pages[n-1];$('#stage').scrollTop=0;
  $$('.pad',p).forEach(initPad);
  if($('#rw',p)){resetArmed=false;renderRewards()}
  $('#pgno').textContent=n+' / '+PAGES.length;
  $('#btnPrev').disabled=n===1;$('#btnNext').disabled=n===PAGES.length;
  $$('.ditem').forEach(function(b){b.classList.toggle('on',+b.dataset.go===n)});
  $('#drawer').classList.remove('open');
  if(canSpeak){try{speechSynthesis.cancel()}catch(e){}}
}
function printNow(mode){
  var b=document.body;b.classList.remove('print-all','print-one');
  $$('.print-this').forEach(function(x){x.classList.remove('print-this')});
  if(mode==='all')b.classList.add('print-all');
  if(mode==='page'){b.classList.add('print-one');$$('.page')[cur-1].classList.add('print-this')}
  $('#pm').removeAttribute('open');
  try{window.print()}catch(e){}
}
window.addEventListener('afterprint',function(){document.body.classList.remove('print-all','print-one');$$('.print-this').forEach(function(x){x.classList.remove('print-this')})});
 
document.addEventListener('click',function(e){
  var t=e.target;
  var g=t.closest('[data-go]');if(g){go(+g.dataset.go);return}
  var s=t.closest('[data-say]');if(s){speak(s.dataset.say);return}
  var pr=t.closest('[data-print]');if(pr){printNow(pr.dataset.print);return}
  if(t.closest('[data-close]')){$('#drawer').classList.remove('open');return}
  var o=t.closest('.obj');
  if(o){
    var box=o.parentElement,n=+box.dataset.n;
    if((box._c||0)>=n){box._c=0;$$('.obj',box).forEach(function(x){x.classList.remove('counted');x.removeAttribute('data-k')})}
    if(!o.classList.contains('counted')){box._c=(box._c||0)+1;o.classList.add('counted');o.setAttribute('data-k',box._c);speak(NUMW[box._c-1])}
    return;
  }
  var c=t.closest('.circ');if(c){var on=c.classList.toggle('on');c.setAttribute('aria-pressed',on);return}
  if(t.id==='btnReset'){
    if(!resetArmed){resetArmed=true;renderRewards()}
    else{DONE={};try{localStorage.removeItem('mfea-done')}catch(_){}resetArmed=false;updateStars();renderRewards()}
    return;
  }
  var pm=$('#pm');if(pm.open&&!t.closest('#pm'))pm.removeAttribute('open');
});
$('#btnPrev').addEventListener('click',function(){go(cur-1)});
$('#btnNext').addEventListener('click',function(){go(cur+1)});
$('#btnMenu').addEventListener('click',function(){$('#drawer').classList.add('open')});
$('#btnNotes').addEventListener('click',function(){var on=document.body.classList.toggle('show-notes');this.setAttribute('aria-pressed',on)});
document.addEventListener('keydown',function(e){
  var tag=(e.target.tagName||'').toLowerCase();if(tag==='input'||tag==='textarea')return;
  if(e.key==='ArrowRight')go(cur+1);else if(e.key==='ArrowLeft')go(cur-1);else if(e.key==='Escape')$('#drawer').classList.remove('open');
});
var rz;window.addEventListener('resize',function(){clearTimeout(rz);rz=setTimeout(function(){var p=$$('.page')[cur-1];if(p)$$('.pad',p).forEach(initPad)},150)});
updateStars();go(1);
})();
</script>
</body>
</html>
