<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover, user-scalable=no">
<title>Дом на двоих</title>
<script src="https://telegram.org/js/telegram-web-app.js"></script>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,600&family=Figtree:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#191420;--bg2:#221b29;--card:#2b2333;--card2:#352b3f;--field:rgba(0,0,0,.28);
  --line:rgba(255,238,220,.09);--txt:#f5ede4;--soft:#cdbfcb;--hint:#9d90a3;
  --accent:#e8b873;--accent2:#f4d4a0;--on:#2a1c10;--ok:#93bf9f;--danger:#ef8f8f;
  --glow:rgba(232,184,115,.17);--shadow:0 14px 34px rgba(0,0,0,.4);
  --serif:"Fraunces",Georgia,"Times New Roman",serif;
  --sans:"Figtree",system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;
  --r:24px;
}
:root[data-theme="light"]{
  --bg:#f5efe6;--bg2:#ece3d6;--card:#fffdf9;--card2:#f8f0e4;--field:#f2eadf;
  --line:rgba(70,45,35,.1);--txt:#2b2229;--soft:#5f515b;--hint:#8f8189;
  --accent:#b06a22;--accent2:#c98640;--on:#ffffff;--ok:#3e8a5b;--danger:#c9484b;
  --glow:rgba(176,106,34,.15);--shadow:0 14px 30px rgba(90,60,40,.15);
}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{margin:0}
body{font-family:var(--sans);background:radial-gradient(900px 460px at 85% -120px,var(--glow),transparent 70%),radial-gradient(700px 380px at -10% 30%,rgba(227,154,154,.07),transparent 70%),var(--bg);background-attachment:fixed;color:var(--txt);font-size:16px;line-height:1.45;min-height:100vh;padding-bottom:calc(112px + env(safe-area-inset-bottom));-webkit-font-smoothing:antialiased}
button{font:inherit;color:inherit;border:0;background:none;cursor:pointer;padding:0}
input,select{font:inherit;color:var(--txt);background:var(--field);border:1px solid var(--line);border-radius:16px;padding:13px 15px;width:100%;min-width:0;outline:none;transition:border-color .15s,box-shadow .15s}
input::placeholder{color:var(--hint)}
input:focus,select:focus{border-color:var(--accent);box-shadow:0 0 0 3px var(--glow)}
input[type=checkbox]{accent-color:var(--accent)}
select{appearance:none;-webkit-appearance:none;background-image:linear-gradient(45deg,transparent 50%,var(--hint) 50%),linear-gradient(135deg,var(--hint) 50%,transparent 50%);background-position:calc(100% - 20px) 52%,calc(100% - 14px) 52%;background-size:6px 6px;background-repeat:no-repeat;padding-right:34px}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px}

header{display:flex;align-items:flex-end;justify-content:space-between;gap:12px;max-width:640px;margin:0 auto;padding:calc(22px + env(safe-area-inset-top)) 20px 14px}
.hello p{margin:0 0 2px;color:var(--soft);font-size:15px}
header h1{font-family:var(--serif);font-weight:600;font-size:36px;line-height:1.05;letter-spacing:-.02em;margin:0}
.head-r{display:flex;align-items:center;gap:12px}
.pair{display:flex}
.pair span{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:var(--serif);font-weight:600;font-size:16px;border:2px solid var(--bg)}
.pair span:first-child{background:var(--accent);color:var(--on)}
.pair span:last-child{background:#e39a9a;color:#3a1c1c;margin-left:-10px}
.gear{width:42px;height:42px;border-radius:50%;background:var(--card);border:1px solid var(--line);display:flex;align-items:center;justify-content:center;color:var(--soft)}
.gear svg{width:20px;height:20px}
svg.i{fill:none;stroke:currentColor;stroke-width:1.8;stroke-linecap:round;stroke-linejoin:round}

main{padding:0 16px 12px;max-width:640px;margin:0 auto}
main.enter{animation:enter .38s cubic-bezier(.2,.7,.2,1)}
@keyframes enter{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:none}}

.card{background:var(--card);border:1px solid var(--line);border-radius:var(--r);padding:20px;margin-bottom:14px;box-shadow:var(--shadow)}
.card h2{font-family:var(--serif);font-size:19px;font-weight:600;letter-spacing:-.01em;color:var(--txt);margin:0 0 14px}
.card.hero{background:linear-gradient(150deg,var(--card2),var(--card) 70%);position:relative;overflow:hidden}
.card.hero::after{content:"";position:absolute;right:-60px;top:-60px;width:200px;height:200px;border-radius:50%;background:radial-gradient(circle,var(--glow),transparent 70%);pointer-events:none}
.row{display:flex;gap:10px;align-items:center}
.row>*{flex:1}
.row>.fix{flex:0 0 auto}
.grow{flex:1}
.stack{display:flex;flex-direction:column;gap:10px}

.btn{background:linear-gradient(180deg,var(--accent2),var(--accent));color:var(--on);border-radius:16px;padding:13px 18px;font-weight:700;text-align:center;box-shadow:0 6px 16px var(--glow);transition:transform .12s,filter .12s}
.btn:active{transform:scale(.98);filter:brightness(.96)}
.btn.soft{background:var(--field);color:var(--txt);box-shadow:none;border:1px solid var(--line);font-weight:600}
.btn.small{padding:8px 14px;font-size:14px;border-radius:12px}
.btn.block{display:block;width:100%}
.btn.danger{background:var(--danger);color:#fff;box-shadow:none}
.btn svg{width:20px;height:20px;vertical-align:-4px}

.chip{display:inline-flex;align-items:center;gap:6px;padding:9px 15px;border-radius:999px;background:var(--field);border:1px solid var(--line);font-size:14px;font-weight:600;color:var(--soft);transition:background .15s,color .15s}
.chip.on{background:var(--accent);border-color:var(--accent);color:var(--on)}
.chips{display:flex;flex-wrap:wrap;gap:8px}

.item{display:flex;align-items:center;gap:14px;padding:13px 0;border-bottom:1px solid var(--line)}
.item:last-child{border-bottom:0}
.item .t{flex:1;min-width:0;word-wrap:break-word;font-weight:500}
.item .s{font-size:13px;color:var(--hint);font-weight:400;margin-top:1px}
.item.done .t{text-decoration:line-through;color:var(--hint)}
.chk{width:28px;height:28px;border-radius:50%;border:2px solid var(--hint);flex:0 0 28px;display:flex;align-items:center;justify-content:center;font-size:14px;color:transparent;transition:background .15s,border-color .15s}
.item.done .chk{background:var(--ok);border-color:var(--ok);color:#fff}
.thumb{width:46px;height:46px;border-radius:14px;object-fit:cover;flex:0 0 46px;border:1px solid var(--line)}
.x{color:var(--hint);font-size:22px;padding:4px 8px;line-height:1}
.cat{font-family:var(--serif);font-size:15px;font-weight:600;color:var(--accent);margin:14px 0 0}
.cat:first-child{margin-top:0}
.big{font-family:var(--serif);font-size:48px;font-weight:600;letter-spacing:-.03em;line-height:1.05;position:relative;z-index:1}
.pos{color:var(--ok)}.neg{color:var(--danger)}
.muted{color:var(--hint);font-size:14px}
.empty{color:var(--hint);text-align:center;padding:18px 0;font-size:15px}

.tabs{position:fixed;left:14px;right:14px;bottom:calc(12px + env(safe-area-inset-bottom));z-index:10;display:flex;gap:2px;max-width:612px;margin:0 auto;padding:7px;border-radius:28px;background:color-mix(in srgb,var(--card) 88%,transparent);backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);border:1px solid var(--line);box-shadow:var(--shadow)}
.tabs button{flex:1;display:flex;flex-direction:column;align-items:center;gap:3px;padding:9px 0 7px;font-size:11px;color:var(--hint);border-radius:21px;font-weight:600;transition:background .2s,color .2s}
.tabs button i{display:block;height:24px}
.tabs button svg{width:24px;height:24px}
.tabs button.on{color:var(--accent);background:var(--glow)}

.sheet-bg{position:fixed;inset:0;background:rgba(10,6,14,.55);backdrop-filter:blur(4px);-webkit-backdrop-filter:blur(4px);z-index:20;display:flex;align-items:flex-end;justify-content:center}
.sheet{background:var(--card);border:1px solid var(--line);width:100%;max-width:640px;border-radius:30px 30px 0 0;padding:24px 20px calc(24px + env(safe-area-inset-bottom));max-height:88vh;overflow:auto;animation:enter .3s cubic-bezier(.2,.7,.2,1)}
.sheet h3{font-family:var(--serif);margin:0 0 14px;font-size:26px;font-weight:600;letter-spacing:-.01em}
.toast{position:fixed;left:50%;bottom:calc(104px + env(safe-area-inset-bottom));transform:translateX(-50%);background:var(--txt);color:var(--bg);padding:11px 18px;border-radius:16px;font-size:14px;font-weight:600;z-index:40;max-width:90%;text-align:center;box-shadow:var(--shadow)}

.wheelbox{position:relative;width:min(320px,84vw);margin:10px auto 18px;filter:drop-shadow(0 14px 22px rgba(0,0,0,.28))}
.wheelbox svg{width:100%;height:auto;display:block}
.pointer{position:absolute;top:-10px;left:50%;transform:translateX(-50%);width:0;height:0;border-left:13px solid transparent;border-right:13px solid transparent;border-top:26px solid var(--accent2);z-index:2;filter:drop-shadow(0 2px 3px rgba(0,0,0,.4))}
.hub{position:absolute;left:50%;top:50%;width:58px;height:58px;margin:-29px 0 0 -29px;border-radius:50%;background:var(--card);border:3px solid var(--accent);box-shadow:0 4px 14px rgba(0,0,0,.35);display:flex;align-items:center;justify-content:center;font-size:22px;color:var(--accent)}
#wheel{transform-origin:50% 50%}
.result{text-align:center;background:linear-gradient(150deg,var(--card2),var(--card));border-color:var(--accent)}
.result .name{font-family:var(--serif);font-size:30px;font-weight:600;letter-spacing:-.02em;margin:4px 0 10px}
.timer{font-family:var(--serif);font-size:68px;font-weight:600;text-align:center;font-variant-numeric:tabular-nums;margin:8px 0 16px}
.photo-on{background:var(--ok)!important;color:#fff!important}
@media(prefers-reduced-motion:reduce){#wheel{transition:none!important}main.enter,.sheet{animation:none}}
</style>
</head>
<body>
<header><div class="hello"><p id="greet"></p><h1 id="title">Покупки</h1></div><div class="head-r"><div class="pair" id="pair" aria-hidden="true"></div><button class="gear" data-act="settings" aria-label="Настройки"><svg class="i" viewBox="0 0 24 24"><path d="M4 8h10M18 8h2M4 16h2M10 16h10"/><circle cx="16" cy="8" r="2"/><circle cx="8" cy="16" r="2"/></svg></button></div></header>
<main id="view"></main>
<nav class="tabs" id="tabs"></nav>
<div id="layer"></div>

<script>
(function(){
"use strict";
var tg=window.Telegram&&window.Telegram.WebApp;
if(tg){try{tg.ready();tg.expand();}catch(e){}}
function haptic(t){try{tg&&tg.HapticFeedback&&tg.HapticFeedback.impactOccurred(t||"light");}catch(e){}}

/* ---------- данные ---------- */
var KEY="pair-app-v1";
var CATS=["Овощи и фрукты","Молочка","Мясо и рыба","Хлеб и крупы","Бытовая химия","Другое"];
var KEYWORDS={
  "Овощи и фрукты":["огур","помидор","томат","яблок","банан","лук","морков","картош","салат","зелень","авокадо","лимон","перец","капуст","груш"],
  "Молочка":["молок","сыр","йогурт","кефир","творог","масло слив","сметан","яйц","сливк"],
  "Мясо и рыба":["мяс","кур","говяд","свин","рыб","лосос","фарш","колбас","тунец","стейк"],
  "Хлеб и крупы":["хлеб","рис","греч","макарон","паста","мука","овсян","батон","круп"],
  "Бытовая химия":["порошок","мыло","шампун","губк","гель","салфет","бумаг","мешк","пакет","средство"]
};
var EXP_CATS=["Еда","Квартплата","Развлечения","Другое"];
var SEED_MEALS=[
  {name:"Паста карбонара",min:25,tags:["dinner"],ing:["паста","бекон","яйца","сыр"]},
  {name:"Омлет с зеленью",min:10,tags:["veg"],ing:["яйца","зелень","молоко"]},
  {name:"Салат с тунцом",min:15,tags:[],ing:["тунец","салат","помидоры"]},
  {name:"Гречка с курицей",min:30,tags:["dinner"],ing:["гречка","курица","лук"]},
  {name:"Овощное рагу",min:40,tags:["veg","dinner"],ing:["кабачок","помидоры","перец","лук"]},
  {name:"Тосты с авокадо",min:10,tags:["veg"],ing:["хлеб","авокадо","лимон"]},
  {name:"Рис с овощами",min:25,tags:["veg"],ing:["рис","морковь","перец"]},
  {name:"Стейк с картофелем",min:40,tags:["dinner"],ing:["стейк","картошка"]}
];
function uid(){return Date.now().toString(36)+Math.random().toString(36).slice(2,7);}
function seed(){
  var me=(tg&&tg.initDataUnsafe&&tg.initDataUnsafe.user&&tg.initDataUnsafe.user.first_name)||"Я";
  return {me:me,partner:"Партнёр",shop:[],freq:{},expenses:[],recurring:[],tasks:[],
    meals:SEED_MEALS.map(function(m){return {id:uid(),name:m.name,min:m.min,tags:m.tags.slice(),ing:m.ing.slice(),fav:false};}),
    meters:[],contacts:[],wish:[]};
}
function load(){try{var s=JSON.parse(localStorage.getItem(KEY));if(s&&s.shop)return s;}catch(e){}return seed();}
var S=load();
function persist(){try{localStorage.setItem(KEY,JSON.stringify(S));}catch(e){toast("Не удалось сохранить: мало места");}}
function save(){persist();if(typeof onSaved==="function")onSaved();}

/* ---------- утилиты ---------- */
function esc(s){return String(s==null?"":s).replace(/[&<>"']/g,function(c){return {"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c];});}
function $(id){return document.getElementById(id);}
function val(id){var e=$(id);return e?e.value.trim():"";}
function money(n){return (Math.round(n*100)/100).toLocaleString("ru-RU",{minimumFractionDigits:0,maximumFractionDigits:2})+" €";}
function today(){var d=new Date();return d.getFullYear()+"-"+("0"+(d.getMonth()+1)).slice(-2)+"-"+("0"+d.getDate()).slice(-2);}
function fmtDate(s){if(!s)return "";var p=s.split("-");return p[2]+"."+p[1];}
function who(w){return w==="me"?S.me:w==="partner"?S.partner:"Любой";}
function toast(t){var e=document.createElement("div");e.className="toast";e.textContent=t;document.body.appendChild(e);setTimeout(function(){e.remove();},2400);}
function guessCat(t){t=t.toLowerCase();for(var c in KEYWORDS){if(KEYWORDS[c].some(function(k){return t.indexOf(k)>-1;}))return c;}return "Другое";}
function share(text){
  var url="https://t.me/share/url?url="+encodeURIComponent(location.href.split("#")[0])+"&text="+encodeURIComponent(text);
  if(tg&&tg.openTelegramLink)tg.openTelegramLink(url);else window.open(url,"_blank");
}
function opts(arr,sel){return arr.map(function(a){var v=a.v!==undefined?a.v:a,l=a.l!==undefined?a.l:a;return '<option value="'+esc(v)+'"'+(v===sel?" selected":"")+'>'+esc(l)+'</option>';}).join("");}
function whoOpts(any,sel){var a=[{v:"me",l:S.me},{v:"partner",l:S.partner}];if(any)a.push({v:"any",l:"Любой"});return opts(a,sel);}

/* ---------- навигация ---------- */
var TABS=[["shop","🛒","Покупки"],["money","💶","Деньги"],["tasks","✅","Задачи"],["food","🎰","Еда"],["home","🏠","Дом"]];
var tab="shop";
var pendingPhoto=null;
var F={quick:false,veg:false,dinner:false,fav:false};
var rot=0,spinning=false,result=null,wheelPool=[];

var ICON={
  shop:'<svg class="i" viewBox="0 0 24 24"><path d="M6 8h12l-1 11H7L6 8z"/><path d="M9 8V6a3 3 0 0 1 6 0v2"/></svg>',
  money:'<svg class="i" viewBox="0 0 24 24"><rect x="3" y="6" width="18" height="13" rx="3.5"/><path d="M3 10.5h18"/><circle cx="16.5" cy="14.8" r="1"/></svg>',
  tasks:'<svg class="i" viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><path d="M8 12.5l2.7 2.7L16 9.5"/></svg>',
  food:'<svg class="i" viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><path d="M12 3v9l6.4 6.4M12 12l-6.4 6.4M12 12l-9 0"/></svg>',
  home:'<svg class="i" viewBox="0 0 24 24"><path d="M4 11l8-7 8 7"/><path d="M6 10v9h12v-9"/><path d="M10 19v-5h4v5"/></svg>'
};
function applyTheme(){
  var dark=(tg&&tg.colorScheme)?tg.colorScheme==="dark":(window.matchMedia&&window.matchMedia("(prefers-color-scheme: dark)").matches);
  document.documentElement.setAttribute("data-theme",dark?"dark":"light");
  var c=dark?"#191420":"#f5efe6";
  try{if(tg&&tg.setHeaderColor)tg.setHeaderColor(c);if(tg&&tg.setBackgroundColor)tg.setBackgroundColor(c);}catch(e){}
}
if(tg&&tg.onEvent){try{tg.onEvent("themeChanged",applyTheme);}catch(e){}}
applyTheme();
function greet(){var h=new Date().getHours();return h<5?"Доброй ночи":h<12?"Доброе утро":h<18?"Добрый день":"Добрый вечер";}
function initial(n){return (n||"?").trim().charAt(0).toUpperCase();}
function head(){
  $("greet").textContent=greet()+((S.me&&S.me!=="Я")?", "+S.me:"");
  $("pair").innerHTML="<span>"+esc(initial(S.me))+"</span><span>"+esc(initial(S.partner))+"</span>";
}
function render(){
  $("title").textContent=TABS.filter(function(t){return t[0]===tab;})[0][2];head();
  $("tabs").innerHTML=TABS.map(function(t){return '<button data-act="tab" data-v="'+t[0]+'" class="'+(t[0]===tab?"on":"")+'"><i>'+ICON[t[0]]+'</i>'+t[2]+'</button>';}).join("");
  var v={shop:vShop,money:vMoney,tasks:vTasks,food:vFood,home:vHome}[tab]();
  $("view").innerHTML=v;
}

/* ---------- 1. покупки ---------- */
function vShop(){
  var open=S.shop.filter(function(i){return !i.done;}),done=S.shop.filter(function(i){return i.done;});
  var inOpen={};open.forEach(function(i){inOpen[i.text.toLowerCase()]=1;});
  var freq=Object.keys(S.freq).map(function(k){return {t:S.freq[k].label||k,k:k,c:S.freq[k].count};}).filter(function(f){return !inOpen[f.t.toLowerCase()];}).sort(function(a,b){return b.c-a.c;}).slice(0,8);
  var h='<div class="card"><div class="stack">'+
    '<div class="row"><input id="shop-t" placeholder="Что купить?" autocomplete="off"><button class="btn soft fix '+(pendingPhoto?"photo-on":"")+'" data-act="pick-photo" aria-label="Фото"><svg class="i" viewBox="0 0 24 24"><path d="M4 8h3l1.5-2h7L17 8h3v11H4z"/><circle cx="12" cy="13" r="3.2"/></svg></button></div>'+
    '<div class="row"><select id="shop-c"><option value="">Категория: авто</option>'+opts(CATS)+'</select><button class="btn fix" data-act="shop-add">Добавить</button></div></div>'+
    '<input type="file" id="photo-in" accept="image/*" hidden></div>';
  if(freq.length)h+='<div class="card"><h2>Берёте часто, добавить в один тап</h2><div class="chips">'+freq.map(function(f){return '<button class="chip" data-act="shop-quick" data-v="'+esc(f.t)+'">+ '+esc(f.t)+'</button>';}).join("")+'</div></div>';
  if(!open.length)h+='<div class="card empty">Список пуст. Добавьте первое, а второй увидит его у себя.</div>';
  else{
    h+='<div class="card">';
    CATS.forEach(function(c){
      var it=open.filter(function(i){return i.cat===c;});if(!it.length)return;
      h+='<div class="cat">'+esc(c)+'</div>'+it.map(shopRow).join("");
    });
    h+='</div>';
  }
  if(done.length)h+='<div class="card"><h2>Куплено</h2>'+done.map(shopRow).join("")+'<button class="btn soft block" style="margin-top:10px" data-act="shop-clear">Убрать купленное</button></div>';
  return h;
}
function shopRow(i){
  return '<div class="item '+(i.done?"done":"")+'"><button class="chk" data-act="shop-toggle" data-id="'+i.id+'" aria-label="Отметить">✓</button>'+
    (i.photo?'<img class="thumb" src="'+i.photo+'" alt="">':"")+'<div class="t">'+esc(i.text)+'</div>'+
    '<button class="x" data-act="shop-del" data-id="'+i.id+'" aria-label="Удалить">×</button></div>';
}
function addShop(text,cat,photo){
  text=text.trim();if(!text)return;
  cat=cat||guessCat(text);
  S.shop.unshift({id:uid(),text:text,cat:cat,done:false,photo:photo||null});
  var k=text.toLowerCase();
  S.freq[k]=S.freq[k]||{count:0,cat:cat};S.freq[k].count++;S.freq[k].cat=cat;
  // красивое отображение для частых: сохраняем оригинальный регистр первого ввода
  S.freq[k].label=S.freq[k].label||text;
}

/* ---------- 2. деньги ---------- */
function balance(){var tot=0,mine=0;S.expenses.forEach(function(e){if(e.settled)return;tot+=e.amount;if(e.who==="me")mine+=e.amount;});return mine-tot/2;}
function daysUntil(day){
  var n=new Date();n.setHours(0,0,0,0);
  var d=new Date(n.getFullYear(),n.getMonth(),day);
  if(d<n)d=new Date(n.getFullYear(),n.getMonth()+1,day);
  return Math.round((d-n)/86400000);
}
function vMoney(){
  var b=balance(),unsettled=S.expenses.filter(function(e){return !e.settled;});
  var line=Math.abs(b)<0.005?"Всё поровну":(b>0?S.partner+" должен(на) тебе":"Ты должен(на) "+S.partner);
  var h='<div class="card hero"><h2>Баланс</h2><div class="big '+(b>0.005?"pos":b<-0.005?"neg":"")+'">'+(Math.abs(b)<0.005?"0 €":money(Math.abs(b)))+'</div><div class="muted">'+esc(line)+'. Расходы делятся пополам.</div>'+
    (unsettled.length?'<button class="btn block" style="margin-top:12px" data-act="settle">Урегулировать баланс</button>':"")+'</div>';
  h+='<div class="card"><h2>Новая трата</h2><div class="stack">'+
    '<div class="row"><input id="ex-a" type="number" inputmode="decimal" step="0.01" placeholder="Сумма, €"><select id="ex-c">'+opts(EXP_CATS)+'</select></div>'+
    '<div class="row"><select id="ex-w">'+whoOpts(false,"me")+'</select><input id="ex-n" placeholder="Заметка"></div>'+
    '<button class="btn block" data-act="ex-add">Записать</button></div></div>';
  h+='<div class="card"><h2>Последние траты</h2>'+(S.expenses.length?S.expenses.slice(0,15).map(function(e){
    return '<div class="item '+(e.settled?"done":"")+'"><div class="t">'+esc(e.cat)+(e.note?": "+esc(e.note):"")+'<div class="s">'+esc(who(e.who))+' заплатил(а), '+fmtDate(e.date)+(e.settled?", урегулировано":"")+'</div></div><b>'+money(e.amount)+'</b><button class="x" data-act="ex-del" data-id="'+e.id+'" aria-label="Удалить">×</button></div>';
  }).join(""):'<div class="empty">Пока пусто</div>')+'</div>';
  h+='<div class="card"><h2>Регулярные платежи</h2>'+(S.recurring.length?S.recurring.map(function(r){
    var d=daysUntil(r.day),soon=d<=3;
    return '<div class="item"><div class="t">'+esc(r.title)+'<div class="s '+(soon?"neg":"")+'">'+(d===0?"сегодня":d===1?"завтра":"через "+d+" дн.")+', '+r.day+'-го числа</div></div><b>'+money(r.amount)+'</b><button class="x" data-act="rec-del" data-id="'+r.id+'" aria-label="Удалить">×</button></div>';
  }).join(""):'<div class="empty">Добавьте аренду, интернет, подписки</div>')+
    '<div class="stack" style="margin-top:10px"><input id="rc-t" placeholder="Название, например: Аренда"><div class="row"><input id="rc-a" type="number" inputmode="decimal" placeholder="Сумма, €"><input id="rc-d" type="number" inputmode="numeric" min="1" max="31" placeholder="Число месяца"></div><button class="btn soft block" data-act="rec-add">Добавить платёж</button></div></div>';
  return h;
}

/* ---------- 3. задачи ---------- */
function vTasks(){
  var open=S.tasks.filter(function(t){return !t.done;}).sort(function(a,b){return (a.due||"9999").localeCompare(b.due||"9999");});
  var done=S.tasks.filter(function(t){return t.done;});
  var h='<div class="card"><h2>Новая задача</h2><div class="stack"><input id="tk-t" placeholder="Например: помыть окна"><div class="row"><input id="tk-d" type="date"><select id="tk-w">'+whoOpts(true,"any")+'</select></div>'+
    '<label class="row" style="gap:10px"><input id="tk-r" type="checkbox" style="width:22px;flex:0 0 22px;padding:0"><span class="grow muted">Повторять каждую неделю со сменой исполнителя</span></label>'+
    '<button class="btn block" data-act="tk-add">Добавить</button></div></div>';
  h+='<div class="card">'+(open.length?open.map(function(t){
    var late=t.due&&t.due<today();
    return '<div class="item"><button class="chk" data-act="tk-toggle" data-id="'+t.id+'" aria-label="Готово">✓</button><div class="t">'+esc(t.title)+'<div class="s '+(late?"neg":"")+'">'+esc(who(t.who))+(t.due?", до "+fmtDate(t.due):"")+(late?", просрочено":"")+(t.repeat?", повтор":"")+'</div></div>'+
      (t.who==="any"?'<button class="btn small" data-act="tk-take" data-id="'+t.id+'">Беру</button>':'<button class="btn soft small" data-act="tk-pass" data-id="'+t.id+'">Передать</button>')+
      '<button class="x" data-act="tk-del" data-id="'+t.id+'" aria-label="Удалить">×</button></div>';
  }).join(""):'<div class="empty">Открытых задач нет</div>')+'</div>';
  if(done.length)h+='<div class="card"><h2>Сделано, '+done.length+'</h2>'+done.slice(0,10).map(function(t){return '<div class="item done"><button class="chk" data-act="tk-toggle" data-id="'+t.id+'" aria-label="Вернуть">✓</button><div class="t">'+esc(t.title)+'<div class="s">'+esc(who(t.who))+'</div></div><button class="x" data-act="tk-del" data-id="'+t.id+'" aria-label="Удалить">×</button></div>';}).join("")+'<button class="btn soft block" style="margin-top:10px" data-act="tk-clear">Очистить сделанное</button></div>';
  return h;
}

/* ---------- 4. рулетка ---------- */
var PAL=["#e8b873","#e39a9a","#93bf9f","#b4a4de","#e7a97a","#8fc0d6","#d6b0cf","#b9cf86"];
function pool(){
  return S.meals.filter(function(m){
    if(F.quick&&!(m.min<=20))return false;
    if(F.veg&&m.tags.indexOf("veg")<0)return false;
    if(F.dinner&&m.tags.indexOf("dinner")<0)return false;
    if(F.fav&&!m.fav)return false;
    return true;
  });
}
function wheelSvg(items){
  var n=items.length,R=150,c=160,h='<svg viewBox="0 0 320 320" id="wheel" style="transform:rotate('+rot+'deg)">';
  if(n===1){h+='<circle cx="160" cy="160" r="150" fill="'+PAL[0]+'"/><text x="160" y="166" text-anchor="middle" fill="#2a1f26" font-size="18" font-weight="700">'+esc(items[0].name.slice(0,18))+'</text>';}
  else for(var i=0;i<n;i++){
    var a0=i*360/n,a1=(i+1)*360/n;
    var p0=pt(a0,R),p1=pt(a1,R),large=(a1-a0)>180?1:0;
    h+='<path d="M'+c+','+c+' L'+p0[0]+','+p0[1]+' A'+R+','+R+' 0 '+large+' 1 '+p1[0]+','+p1[1]+' Z" fill="'+PAL[i%PAL.length]+'" stroke="rgba(255,250,240,.75)" stroke-width="2"/>';
    var mid=(a0+a1)/2,tp=pt(mid,R*0.6);
    h+='<text x="'+tp[0]+'" y="'+tp[1]+'" fill="#2a1f26" font-size="'+(n>8?11:13)+'" font-weight="700" text-anchor="middle" dominant-baseline="middle" transform="rotate('+(mid-90+(mid>180?180:0))+' '+tp[0]+' '+tp[1]+')">'+esc(items[i].name.length>13?items[i].name.slice(0,12)+"…":items[i].name)+'</text>';
  }
  return h+'</svg>';
}
function pt(a,r){var rad=a*Math.PI/180;return [(160+r*Math.sin(rad)).toFixed(2),(160-r*Math.cos(rad)).toFixed(2)];}
function vFood(){
  var p=pool();
  if(p.length>12){p=p.slice().sort(function(){return Math.random()-.5;}).slice(0,12);}
  wheelPool=p;
  var h='<div class="card"><h2>Фильтры</h2><div class="chips">'+
    [["quick","До 20 минут"],["veg","Без мяса"],["dinner","Ужин"],["fav","Избранное"]].map(function(f){return '<button class="chip '+(F[f[0]]?"on":"")+'" data-act="filter" data-v="'+f[0]+'">'+f[1]+'</button>';}).join("")+'</div></div>';
  h+='<div class="card">';
  if(!p.length)h+='<div class="empty">Под фильтры ничего не подходит. Снимите фильтр или добавьте блюдо ниже.</div>';
  else{
    h+='<div class="wheelbox"><div class="pointer"></div>'+wheelSvg(p)+'<button class="hub" data-act="spin" aria-label="Крутить">✦</button></div>'+
      '<button class="btn block" data-act="spin">Крутить</button>';
  }
  h+='</div>';
  if(result){
    var m=S.meals.filter(function(x){return x.id===result;})[0];
    if(m)h+='<div class="card result"><div class="muted">Сегодня едим</div><div class="name">'+esc(m.name)+'</div><div class="muted" style="margin-bottom:12px">'+m.min+' мин'+(m.ing.length?", "+esc(m.ing.join(", ")):"")+'</div>'+
      '<div class="stack"><button class="btn block" data-act="cook" data-id="'+m.id+'">Готовим!</button><div class="row"><button class="btn soft" data-act="share-meal" data-id="'+m.id+'">Написать в чат</button><button class="btn soft" data-act="fav" data-id="'+m.id+'">'+(m.fav?"★ В избранном":"☆ В избранное")+'</button></div></div></div>';
  }
  h+='<div class="card"><h2>Ваши блюда, '+S.meals.length+'</h2>'+S.meals.map(function(m){
    return '<div class="item"><button class="x" style="font-size:22px" data-act="fav" data-id="'+m.id+'" aria-label="Избранное">'+(m.fav?"★":"☆")+'</button><div class="t">'+esc(m.name)+'<div class="s">'+m.min+' мин'+(m.tags.indexOf("veg")>-1?", без мяса":"")+(m.tags.indexOf("dinner")>-1?", ужин":"")+'</div></div><button class="x" data-act="meal-del" data-id="'+m.id+'" aria-label="Удалить">×</button></div>';
  }).join("")+
  '<div class="stack" style="margin-top:12px"><input id="ml-n" placeholder="Название блюда"><div class="row"><input id="ml-m" type="number" inputmode="numeric" placeholder="Минут"><input id="ml-i" placeholder="Продукты через запятую"></div>'+
  '<div class="chips"><label class="chip"><input type="checkbox" id="ml-v" style="width:18px;padding:0"> Без мяса</label><label class="chip"><input type="checkbox" id="ml-d" style="width:18px;padding:0"> Ужин</label></div>'+
  '<button class="btn soft block" data-act="meal-add">Добавить в рулетку</button></div></div>';
  return h;
}
function spin(){
  if(spinning||!wheelPool.length)return;
  spinning=true;haptic("medium");result=null;
  var n=wheelPool.length,seg=360/n,extra=360*5+Math.random()*360;
  var newRot=rot+extra,el=$("wheel");
  if(el){el.style.transition="transform 4.2s cubic-bezier(.12,.7,.1,1)";el.style.transform="rotate("+newRot+"deg)";}
  setTimeout(function(){
    rot=newRot%360;
    var idx=Math.floor(((360-rot)%360)/seg)%n;
    result=wheelPool[idx].id;spinning=false;
    haptic("heavy");render();
    var r=document.querySelector(".result");if(r&&r.scrollIntoView)r.scrollIntoView({behavior:"smooth",block:"center"});
  },el?4300:0);
}
var timerId=null;
function cook(id){
  var m=S.meals.filter(function(x){return x.id===id;})[0];if(!m)return;
  var have={};S.shop.forEach(function(i){if(!i.done)have[i.text.toLowerCase()]=1;});
  var added=0;
  m.ing.forEach(function(g){if(!have[g.toLowerCase()]){addShop(g,null,null);added++;}});
  save();
  var secs=Math.max(1,m.min)*60;
  openSheet('<h3>'+esc(m.name)+'</h3><div class="muted">'+(added?"В список покупок добавлено: "+added+". ":"Все продукты уже в списке. ")+'Таймер на '+m.min+' мин.</div><div class="timer" id="tm">'+fmtT(secs)+'</div>'+
    '<div class="stack"><button class="btn block" id="tm-go">Запустить таймер</button><button class="btn soft block" data-act="close">Закрыть</button></div>');
  var go=$("tm-go");
  go.onclick=function(){
    if(timerId){clearInterval(timerId);timerId=null;go.textContent="Запустить таймер";return;}
    go.textContent="Остановить";
    var end=Date.now()+secs*1000;
    timerId=setInterval(function(){
      var left=Math.round((end-Date.now())/1000);
      if(left<=0){clearInterval(timerId);timerId=null;$("tm")&&($("tm").textContent="00:00");haptic("heavy");
        if(tg&&tg.showAlert)tg.showAlert("Готово! "+m.name);else alert("Готово! "+m.name);return;}
      var t=$("tm");if(t)t.textContent=fmtT(left);
    },500);
  };
}
function fmtT(s){return ("0"+Math.floor(s/60)).slice(-2)+":"+("0"+(s%60)).slice(-2);}

/* ---------- 5. дом ---------- */
function vHome(){
  var h='<div class="card"><h2>Показания счётчиков</h2>'+(S.meters.length?'<div class="item" style="font-size:13px;color:var(--hint)"><div class="t">Дата</div><div style="width:70px;text-align:right">Вода</div><div style="width:70px;text-align:right">Свет</div><div style="width:28px"></div></div>'+S.meters.map(function(m){
    return '<div class="item"><div class="t">'+fmtDate(m.date)+'</div><div style="width:70px;text-align:right">'+esc(m.water)+'</div><div style="width:70px;text-align:right">'+esc(m.power)+'</div><button class="x" data-act="mt-del" data-id="'+m.id+'" aria-label="Удалить">×</button></div>';
  }).join(""):'<div class="empty">Записывайте цифры раз в месяц</div>')+
    '<div class="row" style="margin-top:10px"><input id="mt-w" type="number" inputmode="decimal" placeholder="Вода"><input id="mt-p" type="number" inputmode="decimal" placeholder="Электричество"><button class="btn fix" data-act="mt-add">+</button></div></div>';
  h+='<div class="card"><h2>Контакты и данные</h2>'+(S.contacts.length?S.contacts.map(function(c){
    return '<div class="item"><div class="t"><div class="s">'+esc(c.label)+'</div>'+esc(c.value)+'</div><button class="btn soft small" data-act="copy" data-id="'+c.id+'">Копировать</button><button class="x" data-act="ct-del" data-id="'+c.id+'" aria-label="Удалить">×</button></div>';
  }).join(""):'<div class="empty">Мастер по ремонту, домофон, Wi-Fi для гостей</div>')+
    '<div class="stack" style="margin-top:10px"><div class="row"><input id="ct-l" placeholder="Что это"><input id="ct-v" placeholder="Номер или данные"></div><button class="btn soft block" data-act="ct-add">Добавить</button></div>'+
    '<p class="muted" style="margin:10px 0 0">Данные хранятся на устройстве без шифрования. Банковские пароли лучше держать в менеджере паролей.</p></div>';
  h+='<div class="card"><h2>Вишлист на двоих</h2>'+(S.wish.length?S.wish.map(function(w){
    return '<div class="item '+(w.done?"done":"")+'"><button class="chk" data-act="ws-toggle" data-id="'+w.id+'" aria-label="Готово">✓</button><div class="t">'+esc(w.text)+'<div class="s">'+esc(w.kind)+'</div></div><button class="x" data-act="ws-del" data-id="'+w.id+'" aria-label="Удалить">×</button></div>';
  }).join(""):'<div class="empty">Куда сходить, что купить в дом</div>')+
    '<div class="row" style="margin-top:10px"><input id="ws-t" placeholder="Например: новый плед"><select class="fix" id="ws-k" style="width:120px">'+opts(["Купить","Сходить"])+'</select><button class="btn fix" data-act="ws-add">+</button></div></div>';
  return h;
}

/* ---------- модальные окна ---------- */
function openSheet(html){
  closeSheet();
  var d=document.createElement("div");d.className="sheet-bg";d.id="sheet";
  d.innerHTML='<div class="sheet">'+html+'</div>';
  d.addEventListener("click",function(e){if(e.target===d)closeSheet();});
  document.body.appendChild(d);
}
function closeSheet(){var s=$("sheet");if(s)s.remove();if(timerId){clearInterval(timerId);timerId=null;}}
/* ---------- фото ---------- */
function handlePhoto(file){
  if(!file)return;
  var rd=new FileReader();
  rd.onload=function(){
    var img=new Image();
    img.onload=function(){
      var max=160,k=Math.min(1,max/Math.max(img.width,img.height));
      var c=document.createElement("canvas");c.width=Math.round(img.width*k);c.height=Math.round(img.height*k);
      c.getContext("2d").drawImage(img,0,0,c.width,c.height);
      pendingPhoto=c.toDataURL("image/jpeg",.7);render();
      var t=$("shop-t");if(t)t.focus();
      toast("Фото прикреплено к следующему товару");
    };
    img.src=rd.result;
  };
  rd.readAsDataURL(file);
}

/* ---------- действия ---------- */
function byId(arr,id){for(var i=0;i<arr.length;i++)if(arr[i].id===id)return arr[i];return null;}
function rm(arr,id){for(var i=0;i<arr.length;i++)if(arr[i].id===id){arr.splice(i,1);return;}}
var A={
  tab:function(el){tab=el.dataset.v;render();window.scrollTo(0,0);var m=document.getElementById("view");m.classList.remove("enter");void m.offsetWidth;m.classList.add("enter");},
  settings:settings,
  close:closeSheet,
  "st-save":function(){S.me=val("st-me")||"Я";S.partner=val("st-pa")||"Партнёр";save();closeSheet();render();},
  "st-reset":function(){
    var doit=function(){S=seed();save();closeSheet();render();};
    if(tg&&tg.showConfirm)tg.showConfirm("Стереть все данные без возможности восстановления?",function(ok){if(ok)doit();});
    else if(confirm("Стереть все данные?"))doit();
  },
  /* покупки */
  "pick-photo":function(){$("photo-in").click();},
  "shop-add":function(){var t=val("shop-t");if(!t)return;addShop(t,val("shop-c"),pendingPhoto);pendingPhoto=null;save();haptic();render();var i=$("shop-t");if(i)i.focus();},
  "shop-quick":function(el){addShop(el.dataset.v,S.freq[el.dataset.v.toLowerCase()]&&S.freq[el.dataset.v.toLowerCase()].cat,null);save();haptic();render();},
  "shop-toggle":function(el){var i=byId(S.shop,el.dataset.id);if(i){i.done=!i.done;save();haptic();render();}},
  "shop-del":function(el){rm(S.shop,el.dataset.id);save();render();},
  "shop-clear":function(){S.shop=S.shop.filter(function(i){return !i.done;});save();render();},
  /* деньги */
  "ex-add":function(){
    var a=parseFloat(val("ex-a").replace(",","."));
    if(!(a>0)){toast("Введите сумму");return;}
    S.expenses.unshift({id:uid(),who:val("ex-w"),amount:a,cat:val("ex-c"),note:val("ex-n"),date:today(),settled:false});
    save();haptic();render();
  },
  "ex-del":function(el){rm(S.expenses,el.dataset.id);save();render();},
  settle:function(){
    var b=balance();
    var msg=Math.abs(b)<0.005?"Баланс уже нулевой.":(b>0?S.partner+" отдаёт тебе "+money(b):"Ты отдаёшь "+S.partner+" "+money(-b));
    var doit=function(){S.expenses.forEach(function(e){e.settled=true;});save();render();toast("Баланс урегулирован");};
    if(tg&&tg.showConfirm)tg.showConfirm(msg+". Отметить как урегулированное?",function(ok){if(ok)doit();});
    else if(confirm(msg+". Отметить как урегулированное?"))doit();
  },
  "rec-add":function(){
    var a=parseFloat(val("rc-a").replace(",",".")),d=parseInt(val("rc-d"),10),t=val("rc-t");
    if(!t||!(a>0)||!(d>=1&&d<=31)){toast("Заполните название, сумму и число месяца");return;}
    S.recurring.push({id:uid(),title:t,amount:a,day:d});save();render();
  },
  "rec-del":function(el){rm(S.recurring,el.dataset.id);save();render();},
  /* задачи */
  "tk-add":function(){
    var t=val("tk-t");if(!t)return;
    S.tasks.push({id:uid(),title:t,due:val("tk-d")||"",who:val("tk-w"),repeat:$("tk-r").checked,done:false});
    save();haptic();render();
  },
  "tk-toggle":function(el){
    var t=byId(S.tasks,el.dataset.id);if(!t)return;
    t.done=!t.done;
    if(t.done&&t.repeat){
      var d=t.due?new Date(t.due+"T00:00:00"):new Date();d.setDate(d.getDate()+7);
      var nd=d.getFullYear()+"-"+("0"+(d.getMonth()+1)).slice(-2)+"-"+("0"+d.getDate()).slice(-2);
      S.tasks.push({id:uid(),title:t.title,due:nd,who:t.who==="me"?"partner":t.who==="partner"?"me":"any",repeat:true,done:false});
      toast("Следующая очередь: "+(t.who==="me"?S.partner:t.who==="partner"?S.me:"любой"));
    }
    save();haptic();render();
  },
  "tk-take":function(el){var t=byId(S.tasks,el.dataset.id);if(t){t.who="me";save();render();}},
  "tk-pass":function(el){var t=byId(S.tasks,el.dataset.id);if(t){t.who=t.who==="me"?"partner":"me";save();render();}},
  "tk-del":function(el){rm(S.tasks,el.dataset.id);save();render();},
  "tk-clear":function(){S.tasks=S.tasks.filter(function(t){return !t.done;});save();render();},
  /* еда */
  filter:function(el){F[el.dataset.v]=!F[el.dataset.v];result=null;render();},
  spin:spin,
  cook:function(el){cook(el.dataset.id);render();},
  fav:function(el){var m=byId(S.meals,el.dataset.id);if(m){m.fav=!m.fav;save();haptic();render();}},
  "share-meal":function(el){var m=byId(S.meals,el.dataset.id);if(m)share("Рулетка выбрала: "+m.name+". Готовим!");},
  "meal-add":function(){
    var n=val("ml-n");if(!n)return;
    var tags=[];if($("ml-v").checked)tags.push("veg");if($("ml-d").checked)tags.push("dinner");
    var ing=val("ml-i").split(",").map(function(s){return s.trim();}).filter(Boolean);
    S.meals.push({id:uid(),name:n,min:parseInt(val("ml-m"),10)||30,tags:tags,ing:ing,fav:false});
    save();render();
  },
  "meal-del":function(el){rm(S.meals,el.dataset.id);if(result===el.dataset.id)result=null;save();render();},
  /* дом */
  "mt-add":function(){var w=val("mt-w"),p=val("mt-p");if(!w&&!p)return;S.meters.unshift({id:uid(),date:today(),water:w||"-",power:p||"-"});save();render();},
  "mt-del":function(el){rm(S.meters,el.dataset.id);save();render();},
  "ct-add":function(){var l=val("ct-l"),v=val("ct-v");if(!l||!v)return;S.contacts.push({id:uid(),label:l,value:v});save();render();},
  "ct-del":function(el){rm(S.contacts,el.dataset.id);save();render();},
  copy:function(el){
    var c=byId(S.contacts,el.dataset.id);if(!c)return;
    if(navigator.clipboard&&navigator.clipboard.writeText)navigator.clipboard.writeText(c.value).then(function(){toast("Скопировано");},function(){toast("Не удалось скопировать");});
    else toast(c.value);
  },
  "ws-add":function(){var t=val("ws-t");if(!t)return;S.wish.push({id:uid(),text:t,kind:val("ws-k"),done:false});save();render();},
  "ws-toggle":function(el){var w=byId(S.wish,el.dataset.id);if(w){w.done=!w.done;save();render();}},
  "ws-del":function(el){rm(S.wish,el.dataset.id);save();render();}
};
document.addEventListener("click",function(e){
  var el=e.target.closest("[data-act]");if(!el)return;
  var f=A[el.dataset.act];if(f)f(el);
});
document.addEventListener("keydown",function(e){
  if(e.key==="Enter"&&e.target.id==="shop-t"){A["shop-add"]();}
});
document.addEventListener("change",function(e){if(e.target.id==="photo-in")handlePhoto(e.target.files[0]);});

/* ---------- синхронизация пары (Supabase) ---------- */
var CK="pair-sync-v1";
var COLS=["shop","expenses","recurring","tasks","meals","meters","contacts","wish"];
var cfg=(function(){try{var c=JSON.parse(localStorage.getItem(CK));if(c&&c.code){c.snap=c.snap||{};c.tomb=c.tomb||{};c.nm=c.nm||{};c.pref=c.pref||{tg:null,push:false};return c;}}catch(e){}return null;})();
var syncBusy=false,syncTimer=null,dirty=false,lastSync=0,lastErr="",pendingR=false;
function cfgSave(){try{if(cfg)localStorage.setItem(CK,JSON.stringify(cfg));else localStorage.removeItem(CK);}catch(e){}}
function other(s){return s==="a"?"b":"a";}
function strip(o){var c={};for(var k in o)if(k!=="u")c[k]=o[k];return c;}
function canon(v){
  if(Array.isArray(v))return "["+v.map(canon).join(",")+"]";
  if(v&&typeof v==="object")return "{"+Object.keys(v).filter(function(k){return v[k]!==undefined;}).sort().map(function(k){return JSON.stringify(k)+":"+canon(v[k]);}).join(",")+"}";
  return JSON.stringify(v===undefined?null:v);
}
function sig(){return canon({c:COLS.map(function(c){return S[c]||[];}),f:S.freq||{},me:S.me,pa:S.partner});}
function norm(d){d=d||{};d.nm=d.nm||{};d.cols=d.cols||{};COLS.forEach(function(c){d.cols[c]=d.cols[c]||[];});d.freq=d.freq||{};d.tomb=d.tomb||{};return d;}

/* «я/партнёр» на телефоне <-> слоты a/b в общей базе */
function mapWho(c,it,toS){
  if(c!=="expenses"&&c!=="tasks")return it;
  var o={};for(var k in it)o[k]=it[k];
  var me=cfg.slot,ot=other(cfg.slot);
  if(toS)o.who=it.who==="me"?me:it.who==="partner"?ot:it.who;
  else o.who=it.who===me?"me":it.who===ot?"partner":it.who;
  return o;
}
/* отметить изменённые записи временем, удалённые запомнить как «надгробия» */
function stamp(){
  var now=Date.now(),seen={},ch=false;
  COLS.forEach(function(c){(S[c]||[]).forEach(function(it){
    seen[it.id]=1;
    var j=canon(strip(it));
    if(cfg.snap[it.id]!==j){it.u=now;cfg.snap[it.id]=j;ch=true;}
    else if(!it.u){it.u=now;ch=true;}
  });});
  Object.keys(cfg.snap).forEach(function(id){if(!seen[id]){cfg.tomb[id]=now;delete cfg.snap[id];ch=true;}});
  ["a","b"].forEach(function(s){
    var cur=cfg.nm[s]||null,want=s===cfg.slot?S.me:S.partner,o,k;
    if(s===cfg.slot){
      var pf=cfg.pref||{};
      if(!cur||cur.n!==want||(cur.tg||null)!==(pf.tg||null)||!!cur.push!==!!pf.push){
        o={};if(cur)for(k in cur)o[k]=cur[k];
        o.n=want;o.tg=pf.tg||null;o.push=!!pf.push;o.u=now;cfg.nm[s]=o;ch=true;
      }
    }else if(!cur||cur.n!==want){
      o={};if(cur)for(k in cur)o[k]=cur[k];
      o.n=want;o.u=now;cfg.nm[s]=o;ch=true;
    }
  });
  return ch;
}
function buildDoc(){
  var d={nm:cfg.nm,cols:{},freq:S.freq||{},tomb:cfg.tomb};
  COLS.forEach(function(c){d.cols[c]=(S[c]||[]).map(function(it){return mapWho(c,it,true);});});
  return JSON.parse(JSON.stringify(d));
}
function mergeDoc(rd){
  var local=buildDoc();
  if(!rd)return local;
  rd=norm(rd);
  var out={nm:{},cols:{},freq:{},tomb:{}};
  ["a","b"].forEach(function(s){var x=local.nm[s],y=rd.nm[s];out.nm[s]=!y?x:!x?y:(y.u>x.u?y:x);});
  var tomb={},cut=Date.now()-60*86400000;
  [rd.tomb,local.tomb].forEach(function(src){Object.keys(src).forEach(function(k){tomb[k]=Math.max(tomb[k]||0,src[k]);});});
  Object.keys(tomb).forEach(function(k){if(tomb[k]<cut)delete tomb[k];});
  out.tomb=tomb;
  COLS.forEach(function(c){
    var m={};
    rd.cols[c].concat(local.cols[c]).forEach(function(it){var p=m[it.id];if(!p||(it.u||0)>(p.u||0))m[it.id]=it;});
    out.cols[c]=Object.keys(m).filter(function(id){return !(tomb[id]&&tomb[id]>=(m[id].u||0));}).sort().map(function(id){return m[id];});
  });
  [rd.freq,local.freq].forEach(function(src){Object.keys(src).forEach(function(k){var p=out.freq[k],q=src[k];if(!p||(q.count||0)>(p.count||0))out.freq[k]=q;});});
  return out;
}
function applyDoc(d){
  d=norm(d);
  var present={};
  COLS.forEach(function(c){
    var arr=d.cols[c].map(function(it){return mapWho(c,it,false);});
    var desc=(c==="shop"||c==="expenses"||c==="meters");
    arr.sort(function(x,y){return desc?(x.id<y.id?1:-1):(x.id<y.id?-1:1);});
    S[c]=arr;
    arr.forEach(function(it){present[it.id]=1;cfg.snap[it.id]=canon(strip(it));});
  });
  Object.keys(cfg.snap).forEach(function(id){if(!present[id])delete cfg.snap[id];});
  S.freq=d.freq;
  cfg.tomb=d.tomb;cfg.nm=d.nm;
  var mine=d.nm[cfg.slot];if(mine)cfg.pref={tg:mine.tg||null,push:!!mine.push};
  if(d.nm[cfg.slot]&&d.nm[cfg.slot].n)S.me=d.nm[cfg.slot].n;
  if(d.nm[other(cfg.slot)]&&d.nm[other(cfg.slot)].n)S.partner=d.nm[other(cfg.slot)].n;
}
function rpc(fn,body){
  var h={"Content-Type":"application/json","apikey":cfg.key};
  if(/^eyJ/.test(cfg.key))h.Authorization="Bearer "+cfg.key;
  return fetch(cfg.url.replace(/\/+$/,"")+"/rest/v1/rpc/"+fn,{method:"POST",headers:h,body:JSON.stringify(body)}).then(function(r){
    if(!r.ok)return r.text().then(function(t){throw new Error("HTTP "+r.status+" "+t.slice(0,140));});
    return r.json();
  });
}
function syncNow(force){
  if(!cfg||syncBusy)return Promise.resolve();
  syncBusy=true;
  var before=sig();
  if(stamp())dirty=true;
  return (function attempt(n){
    return rpc("hh_get",{p_code:cfg.code}).then(function(rows){
      var rem=rows&&rows[0]?rows[0]:null;
      if(rem&&rem.rev===cfg.rev&&!dirty&&!force)return;
      var merged=mergeDoc(rem?rem.data:null);
      var same=!!rem&&canon(merged)===canon(norm(rem.data));
      applyDoc(merged);
      if(same){cfg.rev=rem.rev;dirty=false;return;}
      return rpc("hh_put",{p_code:cfg.code,p_data:merged,p_rev:rem?rem.rev:0}).then(function(nr){
        if(nr>0){cfg.rev=nr;dirty=false;return;}
        if(n<3)return attempt(n+1);
        throw new Error("конфликт записи, повторим позже");
      });
    });
  })(0).then(function(){lastSync=Date.now();lastErr="";},function(e){lastErr=String(e&&e.message||e);}).then(function(){
    syncBusy=false;cfgSave();persist();
    if(sig()!==before)softRender();
    updateStatus();
  });
}
function onSaved(){if(!cfg)return;dirty=true;clearTimeout(syncTimer);syncTimer=setTimeout(function(){syncNow();},700);}
function softRender(){
  if(spinning){pendingR=true;return;}
  pendingR=false;
  var vals={},foc=null,ae=document.activeElement;
  var v=$("view");
  if(v){Array.prototype.forEach.call(v.querySelectorAll("input[id],select[id]"),function(e){vals[e.id]=e.type==="checkbox"?e.checked:e.value;});}
  if(ae&&ae.id&&v&&v.contains(ae))foc={id:ae.id,s:ae.selectionStart,e:ae.selectionEnd};
  var y=window.scrollY;
  render();
  Object.keys(vals).forEach(function(id){var e=$(id);if(!e||e.type==="file")return;if(e.type==="checkbox")e.checked=vals[id];else e.value=vals[id];});
  if(foc){var f=$(foc.id);if(f){try{f.focus({preventScroll:true});if(foc.s!=null&&f.setSelectionRange)f.setSelectionRange(foc.s,foc.e);}catch(x){}}}
  window.scrollTo(0,y);
}
setInterval(function(){if(cfg&&document.visibilityState==="visible")syncNow();},6000);
document.addEventListener("visibilitychange",function(){if(cfg&&document.visibilityState==="visible")syncNow();});
function updateStatus(){
  var e=$("sy-stat");if(!e||!cfg)return;
  e.textContent=lastErr?"Ошибка связи: "+lastErr:(lastSync?"Подключено. Обновлено в "+new Date(lastSync).toLocaleTimeString("ru-RU",{hour:"2-digit",minute:"2-digit"}):"Подключение…");
}

/* ---------- приглашение ---------- */
function b64u(s){return btoa(s).replace(/\+/g,"-").replace(/\//g,"_").replace(/=+$/,"");}
function unb64u(s){s=s.replace(/-/g,"+").replace(/_/g,"/");while(s.length%4)s+="=";return atob(s);}
function inviteCode(){return "GF1-"+b64u(JSON.stringify({u:cfg.url,k:cfg.key,c:cfg.code}));}
function randCode(){var a=new Uint8Array(16);crypto.getRandomValues(a);return Array.prototype.map.call(a,function(x){return ("0"+x.toString(16)).slice(-2);}).join("");}
function findInvite(t){var m=String(t||"").match(/GF1-[A-Za-z0-9_-]+/);return m?m[0]:"";}
function friendly(msg){return /hh_get|hh_put|404|PGRST/.test(msg)?"Не выполнен SQL-скрипт в Supabase (см. инструкцию). "+msg:msg;}

function joinWith(inv,name){
  var p;try{p=JSON.parse(unb64u(inv.slice(4)));if(!p.u||!p.k||!p.c)throw 0;}catch(e){toast("Код повреждён, скопируйте его целиком");return;}
  var prev=cfg;
  cfg={url:p.u,key:p.k,code:p.c,slot:"b",rev:0,snap:{},tomb:{},nm:{},pref:{tg:null,push:false}};
  toast("Подключаюсь…");
  rpc("hh_get",{p_code:cfg.code}).then(function(rows){
    var rem=rows&&rows[0];
    if(!rem)throw new Error("пара с таким кодом не найдена");
    var d=norm(rem.data);
    d.nm.b={n:name||(d.nm.b&&d.nm.b.n)||"Я",u:Date.now()};
    COLS.forEach(function(c){S[c]=[];});S.freq={};
    applyDoc(d);
    cfg.rev=rem.rev;dirty=true;
    return syncNow(true);
  }).then(function(){
    if(lastErr)throw new Error(lastErr);
    closeSheet();render();toast("Готово, вы в паре");
  }).catch(function(e){cfg=prev;cfgSave();toast("Не вышло: "+friendly(String(e.message||e)));});
}

/* ---------- окно настроек ---------- */
function settings(){
  var h='<h3>Настройки</h3><div class="stack"><div class="muted">Как вас называть в приложении</div><input id="st-me" value="'+esc(S.me)+'" placeholder="Твоё имя"><input id="st-pa" value="'+esc(S.partner)+'" placeholder="Имя партнёра"><button class="btn block" data-act="st-save">Сохранить имена</button>';
  h+='<h3 style="margin-top:20px">Общая пара</h3>';
  if(cfg){
    h+='<div class="muted" id="sy-stat"></div><div class="muted">Код приглашения: отправьте его партнёру</div><input id="sy-code" readonly value="'+esc(inviteCode())+'">'+
      '<div class="row"><button class="btn soft" data-act="sy-copy">Скопировать</button><button class="btn soft" data-act="sy-share">Отправить в Telegram</button></div>'+
      '<button class="btn soft block" data-act="sy-now">Синхронизировать сейчас</button><button class="btn soft block" data-act="sy-off">Отключить на этом телефоне</button>'+
      '<p class="muted" style="margin:0">Данные лежат в вашем проекте Supabase. Не храните в «Контактах» пароли от банков.</p>'+
      '<h3 style="margin-top:20px">Напоминания</h3><div class="muted">Каждый вечер в 19:00 бот напишет вам в Telegram: на что завтра ваша очередь, что просрочено и какие платежи скоро. Если напоминать нечего, сообщения не будет. Каждый включает их на своём телефоне.</div>'+
      (cfg.pref&&cfg.pref.push?'<div class="muted" style="color:var(--ok)">Напоминания включены</div><div class="row"><button class="btn soft" data-act="pu-test">Прислать тест</button><button class="btn soft" data-act="pu-off">Выключить</button></div>':'<button class="btn block" data-act="pu-on">Включить напоминания</button>');
  }else{
    h+='<p class="muted" style="margin:0">Чтобы списки и баланс обновлялись у обоих сразу, подключите общую базу. Первый из вас создаёт пару, второй присоединяется по коду.</p>'+
      '<input id="sy-url" placeholder="Project URL, https://xxxx.supabase.co" autocapitalize="off" autocorrect="off"><input id="sy-key" placeholder="Publishable или anon ключ" autocapitalize="off" autocorrect="off"><button class="btn block" data-act="sy-create">Создать пару</button>'+
      '<div class="muted" style="margin-top:6px">Или присоединитесь по коду от партнёра</div><input id="sy-inv" placeholder="Код приглашения GF1-…" autocapitalize="off" autocorrect="off"><button class="btn soft block" data-act="sy-join">Присоединиться</button>'+
      '<p class="muted" style="margin:0">При присоединении данные на этом телефоне заменятся данными пары.</p>';
  }
  h+='<button class="btn danger block" data-act="st-reset" style="margin-top:12px">Стереть данные на этом телефоне</button><button class="btn soft block" data-act="close">Закрыть</button></div>';
  openSheet(h);updateStatus();
}
A.settings=settings;
A["sy-create"]=function(){
  var url=val("sy-url"),key=val("sy-key");
  if(!/^https:\/\/.+/.test(url)||!key){toast("Вставьте Project URL и ключ из Supabase");return;}
  S.me=val("st-me")||S.me;S.partner=val("st-pa")||S.partner;
  cfg={url:url,key:key,code:randCode(),slot:"a",rev:0,snap:{},tomb:{},nm:{},pref:{tg:null,push:false}};
  dirty=true;toast("Создаю пару…");
  syncNow(true).then(function(){
    if(lastErr){var e=lastErr;cfg=null;cfgSave();lastErr="";toast("Не вышло: "+friendly(e));return;}
    persist();settings();render();toast("Пара создана. Отправьте код партнёру");
  });
};
A["sy-join"]=function(){
  var inv=findInvite(val("sy-inv"));
  if(!inv){toast("Код приглашения не распознан");return;}
  joinWith(inv,val("st-me")||(S.me!=="Я"?S.me:""));
};
A["sy-copy"]=function(){
  var t=inviteCode();
  if(navigator.clipboard&&navigator.clipboard.writeText)navigator.clipboard.writeText(t).then(function(){toast("Код скопирован");},function(){toast("Выделите код и скопируйте вручную");});
  else{var e=$("sy-code");if(e){e.select();}toast("Выделите код и скопируйте");}
};
A["sy-share"]=function(){share("Присоединяйся к нашей паре в приложении «Дом на двоих». Код приглашения:\n"+inviteCode());};
A["sy-now"]=function(){syncNow(true).then(function(){toast(lastErr?"Ошибка: "+friendly(lastErr):"Синхронизировано");});};
A["sy-off"]=function(){
  var doit=function(){cfg=null;cfgSave();lastSync=0;closeSheet();settings();};
  var msg="Отключить синхронизацию на этом телефоне? Данные здесь останутся, у партнёра тоже.";
  if(tg&&tg.showConfirm)tg.showConfirm(msg,function(ok){if(ok)doit();});else if(confirm(msg))doit();
};
A["st-reset"]=function(){
  var doit=function(){cfg=null;cfgSave();S=seed();save();closeSheet();render();};
  var msg="Стереть данные на этом телефоне? Если подключена пара, синхронизация отключится, а у партнёра всё сохранится.";
  if(tg&&tg.showConfirm)tg.showConfirm(msg,function(ok){if(ok)doit();});else if(confirm(msg))doit();
};


/* ---------- напоминания в Telegram ---------- */
function callNotify(body){
  var url=cfg.url.replace(/\/+$/,"")+"/functions/v1/notify";
  return fetch(url,{method:"POST",headers:{"Content-Type":"application/json","apikey":cfg.key},body:JSON.stringify(body)}).then(function(r){
    return r.json().catch(function(){return {};}).then(function(j){if(!r.ok&&!j.error)j.error=j.message||j.msg||("HTTP "+r.status);return j;});
  });
}
function pfriendly(e){
  e=String(e||"");
  if(e==="no_tg")return "ваш Telegram-ID ещё не дошёл до базы, повторите через пару секунд";
  if(/not found|NOT_FOUND|HTTP 404/i.test(e))return "функция notify не развёрнута в Supabase (см. инструкцию)";
  if(/JWT|401|403/i.test(e))return "у функции notify включена проверка JWT, выключите её";
  if(/chat not found|Forbidden|blocked/i.test(e))return "бот не может вам писать: откройте бота и нажмите Start";
  return e||"неизвестная ошибка";
}
A["pu-on"]=function(){
  var u=tg&&tg.initDataUnsafe&&tg.initDataUnsafe.user;
  if(!u||!u.id){toast("Откройте приложение внутри Telegram, там я узнаю ваш аккаунт");return;}
  var go=function(){cfg.pref={tg:u.id,push:true};save();settings();toast("Напоминания включены");};
  if(tg.requestWriteAccess)tg.requestWriteAccess(function(ok){if(ok)go();else toast("Разрешите боту писать вам, иначе напоминания не придут");});
  else go();
};
A["pu-off"]=function(){cfg.pref={tg:cfg.pref&&cfg.pref.tg||null,push:false};save();settings();toast("Напоминания выключены");};
A["pu-test"]=function(){
  toast("Отправляю…");
  syncNow(true).then(function(){return callNotify({action:"test",code:cfg.code,slot:cfg.slot});}).then(function(j){
    toast(j.ok?"Проверьте чат с ботом":"Не вышло: "+pfriendly(j.error));
  },function(){toast("Не вышло: нет связи с функцией notify");});
};

/* приглашение из ссылки: t.me/бот/app?startapp=GF1-... или #GF1-... */
(function(){
  if(cfg)return;
  var sp=(tg&&tg.initDataUnsafe&&tg.initDataUnsafe.start_param)||"";
  var inv=findInvite(sp)||findInvite(location.hash);
  if(!inv)return;
  setTimeout(function(){
    openSheet('<h3>Вас приглашают в пару</h3><div class="stack"><div class="muted">Данные на этом телефоне заменятся общими данными пары.</div><input id="jn-name" value="'+esc(S.me!=="Я"?S.me:"")+'" placeholder="Ваше имя"><button class="btn block" id="jn-go">Присоединиться</button><button class="btn soft block" data-act="close">Позже</button></div>');
    var b=$("jn-go");if(b)b.onclick=function(){joinWith(inv,val("jn-name"));};
  },300);
})();
if(cfg)setTimeout(function(){syncNow(true);},400);

render();
})();
</script>
</body>
</html>
