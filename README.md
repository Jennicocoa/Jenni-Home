<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Jenni's Dashboard</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet" />
<style>
:root{--bg:#faf9f7;--bg2:#f2f0ec;--bg3:#e8e4dd;--text:#1a1916;--text2:#6b6860;--text3:#a09d97;--border:rgba(26,25,22,0.09);--border2:rgba(26,25,22,0.16);--pink:#c9506a;--pink-l:#fdf0f2;--pink-m:#ED93B1;--teal:#1d9e75;--teal-l:#edf7f2;--amber:#b06a1a;--amber-l:#fdf4e8;--amber-m:#FAC775;--purple:#6b52a8;--purple-l:#f3f0fb;--coral:#c05a38;--coral-l:#fdf1ed;--coral-m:#F0997B;--blue:#3a6fa8;--blue-l:#eef3fa;--green:#2a7a52;--green-l:#edf7f2;--radius:14px;--radius-sm:8px;}
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);padding-bottom:4rem;}
.page{max-width:680px;margin:0 auto;padding:1.5rem 1rem;}
.header{margin-bottom:1.75rem;display:flex;align-items:flex-start;justify-content:space-between;}
.greeting{font-family:'DM Serif Display',serif;font-size:1.75rem;line-height:1.15;}
.greeting em{font-style:italic;color:var(--pink);}
.dateline{font-size:.72rem;color:var(--text3);margin-top:.25rem;letter-spacing:.05em;text-transform:uppercase;}
.theme-btn{background:none;border:1px solid var(--border2);border-radius:50%;width:34px;height:34px;cursor:pointer;font-size:14px;color:var(--text2);display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.section{margin-bottom:1.75rem;}
.sec-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:.6rem;}
.sec-label{font-size:.65rem;font-weight:500;text-transform:uppercase;letter-spacing:.1em;color:var(--text3);}
.sec-action{font-size:.72rem;color:var(--text3);cursor:pointer;background:none;border:none;font-family:inherit;padding:0;}
.card{background:white;border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;}

/* DIVIDER */
.section-divider{display:flex;align-items:center;gap:12px;margin:2rem 0 1.75rem;}
.divider-label{font-family:'DM Serif Display',serif;font-size:1.1rem;color:var(--text2);white-space:nowrap;font-style:italic;}
.divider-line{flex:1;height:1px;background:var(--border2);}

/* FOCUS */
.focus-card{background:white;border:1px solid var(--border);border-radius:var(--radius);padding:.85rem 1rem;margin-bottom:6px;display:flex;align-items:flex-start;gap:10px;}
.fc-check{width:20px;height:20px;border-radius:50%;border:1.5px solid var(--border2);flex-shrink:0;margin-top:1px;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:all .15s;}
.fc-check.done{background:var(--teal);border-color:var(--teal);}
.fc-check.done::after{content:'✓';font-size:10px;color:white;}
.fc-body{flex:1;}
.fc-title{font-size:.9rem;color:var(--text);line-height:1.4;}
.fc-title.done{text-decoration:line-through;color:var(--text3);}
.fc-due{font-size:.72rem;color:var(--text3);margin-top:2px;}
.fc-due.urgent{color:var(--coral);font-weight:500;}
.cat-pill{font-size:.65rem;padding:2px 8px;border-radius:20px;white-space:nowrap;flex-shrink:0;}
.focus-empty{font-size:.82rem;color:var(--text3);font-style:italic;padding:.4rem 0;}

/* EVENTS */
.events-row{display:flex;gap:8px;overflow-x:auto;padding-bottom:4px;scrollbar-width:none;}
.events-row::-webkit-scrollbar{display:none;}
.ev-card{background:white;border:1px solid var(--border);border-radius:var(--radius);padding:.9rem 1rem;min-width:148px;flex-shrink:0;position:relative;overflow:hidden;}
.ev-accent{position:absolute;top:0;left:0;right:0;height:3px;}
.ev-emoji{font-size:1.5rem;display:block;margin-bottom:.35rem;}
.ev-num{font-family:'DM Serif Display',serif;font-size:2rem;line-height:1;color:var(--text);}
.ev-unit{font-size:.65rem;color:var(--text3);text-transform:uppercase;letter-spacing:.04em;margin-bottom:.3rem;}
.ev-name{font-size:.78rem;color:var(--text);font-weight:500;line-height:1.3;}
.ev-date-str{font-size:.65rem;color:var(--text3);margin-top:.2rem;}
.ev-add{display:flex;align-items:center;justify-content:center;min-height:110px;border:1px dashed var(--border2);border-radius:var(--radius);cursor:pointer;background:none;font-size:.78rem;color:var(--text3);font-family:inherit;flex-shrink:0;width:110px;transition:color .15s;}
.ev-add:hover{color:var(--text);}

/* TASKS */
.tier-head{font-size:.65rem;font-weight:500;text-transform:uppercase;letter-spacing:.07em;padding:6px 12px;background:var(--bg2);border-bottom:1px solid var(--border);color:var(--text3);}
.tier-head.urgent{background:#FAECE7;color:#993C1D;}
.task-row{display:flex;align-items:flex-start;gap:8px;padding:8px 12px;border-bottom:1px solid var(--border);transition:background .1s;}
.task-row:last-child{border-bottom:none;}
.task-row:hover{background:var(--bg);}
.t-check{width:17px;height:17px;border-radius:50%;border:1.5px solid var(--border2);flex-shrink:0;margin-top:2px;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:all .15s;}
.t-check.sq{border-radius:4px;}
.t-check.done{background:var(--teal);border-color:var(--teal);}
.t-check.done::after{content:'✓';font-size:9px;color:white;}
.t-body{flex:1;min-width:0;}
.t-title{font-size:.85rem;color:var(--text);line-height:1.4;}
.t-title.done{text-decoration:line-through;color:var(--text3);}
.t-meta{display:flex;gap:5px;margin-top:3px;flex-wrap:wrap;align-items:center;}
.due-urgent{font-size:.68rem;color:var(--coral);font-weight:500;}
.due-soon{font-size:.68rem;color:var(--amber);}
.due-normal{font-size:.68rem;color:var(--text3);}
.star-btn{background:none;border:none;cursor:pointer;font-size:14px;color:var(--text3);padding:2px;flex-shrink:0;margin-top:1px;line-height:1;transition:color .12s;}
.star-btn.on{color:var(--amber);}
.pin-btn{background:none;border:none;cursor:pointer;font-size:13px;padding:2px;flex-shrink:0;margin-top:1px;line-height:1;color:var(--text3);transition:color .12s;}
.pin-btn.pinned{color:var(--pink);}
.del-btn{background:none;border:none;cursor:pointer;font-size:11px;color:var(--text3);padding:2px;flex-shrink:0;opacity:0;transition:opacity .12s;line-height:1;}
.task-row:hover .del-btn{opacity:1;}

/* ADD */
.add-area{margin-top:.55rem;}
.add-row{display:flex;gap:5px;flex-wrap:wrap;}
.add-row input,.add-row select{font-size:.8rem;padding:7px 9px;border:1px solid var(--border2);border-radius:var(--radius-sm);background:white;color:var(--text);font-family:'DM Sans',sans-serif;outline:none;}
.add-row input.main{flex:1;min-width:120px;}
.add-row input.date-in{width:130px;}
.add-row select{width:128px;}
.add-btn{padding:7px 12px;border:1px solid var(--border2);border-radius:var(--radius-sm);background:var(--text);color:white;cursor:pointer;font-size:.8rem;font-family:'DM Sans',sans-serif;}

/* ASPIRATIONAL */
.asp-header{display:flex;align-items:center;gap:8px;padding:8px 12px;border-bottom:1px solid var(--border);cursor:pointer;transition:background .1s;}
.asp-header:hover{background:var(--bg);}
.asp-chevron{font-size:10px;color:var(--text3);flex-shrink:0;transition:transform .2s;}
.asp-chevron.open{transform:rotate(90deg);}
.asp-text{font-size:.85rem;color:var(--text2);flex:1;font-style:italic;}
.asp-notes-area{padding:9px 12px;background:var(--bg2);border-bottom:1px solid var(--border);}
.asp-notes-area textarea{width:100%;background:transparent;border:none;outline:none;font-size:.8rem;font-family:'DM Sans',sans-serif;color:var(--text);resize:none;min-height:56px;line-height:1.6;}
.asp-notes-area textarea::placeholder{color:var(--text3);font-style:italic;}
.asp-del{background:none;border:none;cursor:pointer;color:var(--text3);font-size:11px;opacity:0;padding:2px;}
.asp-header:hover .asp-del{opacity:1;}

/* NOTES */
.notes-ta{width:100%;min-height:90px;font-size:.82rem;font-family:'DM Sans',sans-serif;color:var(--text);border:none;outline:none;resize:none;background:transparent;line-height:1.7;padding:12px;}
.notes-ta::placeholder{color:var(--text3);font-style:italic;}
.notes-footer{font-size:.68rem;color:var(--text3);padding:5px 12px;border-top:1px solid var(--border);font-style:italic;}

/* MOOD */
.mood-pills-wrap{display:flex;gap:5px;flex-wrap:wrap;padding:9px 12px;border-bottom:1px solid var(--border);}
.mood-pill{font-size:.75rem;padding:5px 11px;border-radius:20px;border:1px solid var(--border2);cursor:pointer;background:transparent;color:var(--text2);font-family:'DM Sans',sans-serif;transition:all .12s;}
.mood-pill.sel{border-width:1.5px;}
.tag-section{padding:9px 12px;border-bottom:1px solid var(--border);}
.tag-sec-label{font-size:.67rem;color:var(--text3);margin-bottom:6px;}
.tags-row{display:flex;gap:5px;flex-wrap:wrap;}
.tag-btn{font-size:.68rem;padding:4px 9px;border-radius:20px;border:1px solid var(--border);cursor:pointer;background:transparent;font-family:'DM Sans',sans-serif;color:var(--text2);transition:all .12s;white-space:nowrap;}
.tag-btn.sel{border-width:1.5px;}
.custom-tag-row{display:flex;gap:5px;margin-top:7px;}
.custom-tag-row input{font-size:.75rem;padding:4px 9px;border:1px solid var(--border2);border-radius:20px;background:white;color:var(--text);font-family:'DM Sans',sans-serif;outline:none;flex:1;min-width:80px;}
.custom-tag-row button{font-size:.72rem;padding:4px 10px;border:1px solid var(--border2);border-radius:20px;background:transparent;color:var(--text2);cursor:pointer;font-family:'DM Sans',sans-serif;}
.journal-write{padding:9px 12px;border-bottom:1px solid var(--border);}
.journal-write textarea{width:100%;background:transparent;border:none;outline:none;font-size:.82rem;font-family:'DM Sans',sans-serif;color:var(--text);resize:none;min-height:52px;line-height:1.6;}
.journal-write textarea::placeholder{color:var(--text3);font-style:italic;}
.save-bar{display:flex;justify-content:flex-end;padding:7px 12px;background:var(--bg2);border-bottom:1px solid var(--border);}

/* ANALYTICS */
.analytics-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:7px;padding:10px 12px;border-bottom:1px solid var(--border);}
.a-stat{background:var(--bg2);border-radius:var(--radius-sm);padding:9px 10px;}
.a-val{font-size:1.2rem;font-weight:500;color:var(--text);}
.a-lbl{font-size:.67rem;color:var(--text3);margin-top:2px;line-height:1.3;}
.chart-wrap{padding:10px 12px;border-bottom:1px solid var(--border);}
.chart-legend{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:7px;}
.leg{display:flex;align-items:center;gap:3px;font-size:.68rem;color:var(--text2);}
.leg-sq{width:8px;height:8px;border-radius:2px;flex-shrink:0;}
.insight-row{display:flex;gap:9px;padding:8px 12px;border-bottom:1px solid var(--border);align-items:flex-start;}
.insight-row:last-child{border-bottom:none;}
.i-icon{font-size:13px;flex-shrink:0;margin-top:1px;}
.i-text{font-size:.78rem;color:var(--text2);line-height:1.5;}
.i-text strong{color:var(--text);font-weight:500;}

/* CYCLE */
.cycle-summary{padding:14px 12px;}
.cycle-day-line{font-size:.72rem;color:var(--text3);text-transform:uppercase;letter-spacing:.05em;margin-bottom:10px;}
.cycle-phase-bar{display:flex;gap:2px;margin-bottom:10px;}
.phase-seg{height:8px;border-radius:4px;}
.cycle-phase-row{display:flex;align-items:flex-start;gap:10px;margin-bottom:0;}
.phase-badge{font-size:.7rem;font-weight:500;padding:3px 10px;border-radius:20px;white-space:nowrap;flex-shrink:0;}
.phase-desc{font-size:.76rem;color:var(--text2);line-height:1.5;}
.cycle-stats{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:7px;padding:10px 12px;border-top:1px solid var(--border);}
.c-stat{background:var(--bg2);border-radius:var(--radius-sm);padding:8px 10px;}
.c-val{font-size:1rem;font-weight:500;color:var(--text);}
.c-lbl{font-size:.67rem;color:var(--text3);margin-top:2px;}
.phase-insights{border-top:1px solid var(--border);}
.phase-insight-row{display:flex;gap:9px;padding:8px 12px;border-bottom:1px solid var(--border);align-items:flex-start;}
.phase-insight-row:last-child{border-bottom:none;}
.cycle-input-row{display:flex;gap:6px;flex-wrap:wrap;padding:9px 12px;border-top:1px solid var(--border);align-items:center;}
.cycle-input-row label{font-size:.75rem;color:var(--text2);}
.cycle-input-row input{font-size:.8rem;padding:6px 8px;border:1px solid var(--border2);border-radius:var(--radius-sm);background:white;color:var(--text);font-family:'DM Sans',sans-serif;outline:none;width:128px;}

.ev-form{margin-top:.55rem;display:none;}
body.dark{--bg:#141412;--bg2:#1e1d1a;--bg3:#272521;--text:#f0ede8;--text2:#9e9b94;--text3:#6b6860;--border:rgba(240,237,232,.08);--border2:rgba(240,237,232,.14);}
body.dark .card,body.dark .ev-card,body.dark .focus-card,body.dark .add-row input,body.dark .add-row select,body.dark .cycle-input-row input,body.dark .custom-tag-row input{background:#1e1d1a;}
body.dark .task-row:hover,body.dark .asp-header:hover{background:#272521;}
</style>
</head>
<body>
<div class="page">

  <div class="header">
    <div>
      <div class="greeting" id="greeting">Good morning, <em>Jenni</em></div>
      <div class="dateline" id="dateline"></div>
    </div>
    <button class="theme-btn" id="theme-btn">☾</button>
  </div>

  <!-- TODAY'S FOCUS -->
  <div class="section">
    <div class="sec-head">
      <div class="sec-label">Today's focus</div>
      <div style="font-size:.68rem;color:var(--text3);">Pin up to 3 tasks below ↓</div>
    </div>
    <div id="focus-list"></div>
    <div class="focus-empty" id="focus-empty" style="display:none;">Pin up to 3 tasks from your list below to set your focus for today.</div>
  </div>

  <!-- COMING UP -->
  <div class="section">
    <div class="sec-head">
      <div class="sec-label">Coming up</div>
      <button class="sec-action" id="ev-toggle-btn">+ add</button>
    </div>
    <div class="events-row" id="events-row"></div>
    <div class="ev-form" id="ev-form">
      <div class="add-row">
        <input class="main" type="text" id="ev-name" placeholder="Event name..." />
        <input class="date-in" type="date" id="ev-date" />
        <input style="width:65px;" type="text" id="ev-emoji" placeholder="emoji" />
        <button class="add-btn" id="ev-add-btn">Add</button>
      </div>
    </div>
  </div>

  <!-- MUST DO -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">Must do</div>
    <div class="card" id="must-list"></div>
    <div class="add-area"><div class="add-row">
      <input class="main" type="text" id="must-input" placeholder="Add a must-do task..." />
      <input class="date-in" type="date" id="must-date" />
      <select id="must-cat"></select>
      <button class="add-btn" id="must-add-btn">Add</button>
    </div></div>
  </div>

  <!-- WANT TO DO -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">Want to do</div>
    <div class="card" id="want-list"></div>
    <div class="add-area"><div class="add-row">
      <input class="main" type="text" id="want-input" placeholder="Add a want-to-do task..." />
      <select id="want-cat"></select>
      <button class="add-btn" id="want-add-btn">Add</button>
    </div></div>
  </div>

  <!-- ASPIRATIONAL -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">Someday / aspirational</div>
    <div class="card" id="asp-card"></div>
    <div class="add-area"><div class="add-row">
      <input class="main" type="text" id="asp-input" placeholder="Add an idea or longer-term goal..." />
      <button class="add-btn" id="asp-add-btn">Add</button>
    </div></div>
  </div>

  <!-- NOTES -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">Notes & brain dump</div>
    <div class="card">
      <textarea class="notes-ta" id="notes-ta" placeholder="Brain dumps, reminders, random thoughts — anything goes here..."></textarea>
      <div class="notes-footer" id="notes-footer"></div>
    </div>
  </div>

  <!-- WELLNESS DIVIDER -->
  <div class="section-divider">
    <div class="divider-line"></div>
    <div class="divider-label">Wellness</div>
    <div class="divider-line"></div>
  </div>

  <!-- MOOD CHECK-IN -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">How are you feeling today?</div>
    <div class="card">
      <div class="mood-pills-wrap" id="mood-pills"></div>
      <div class="tag-section">
        <div class="tag-sec-label">Felt good because of...</div>
        <div class="tags-row" id="pos-tags"></div>
        <div class="custom-tag-row">
          <input type="text" id="pos-custom-input" placeholder="Add your own..." />
          <button id="pos-custom-btn">+ Add</button>
        </div>
      </div>
      <div class="tag-section">
        <div class="tag-sec-label">Felt off because of...</div>
        <div class="tags-row" id="neg-tags"></div>
        <div class="custom-tag-row">
          <input type="text" id="neg-custom-input" placeholder="Add your own..." />
          <button id="neg-custom-btn">+ Add</button>
        </div>
      </div>
      <div class="journal-write">
        <textarea id="today-note" placeholder="What else is on your mind today..."></textarea>
      </div>
      <div class="save-bar"><button class="add-btn" id="log-mood-btn">Save today's check-in</button></div>
    </div>
  </div>

  <!-- MOOD ANALYTICS -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">Mood this week</div>
    <div class="card">
      <div class="analytics-grid" id="analytics-grid"></div>
      <div class="chart-wrap">
        <div class="chart-legend">
          <div class="leg"><div class="leg-sq" style="background:#ED93B1;"></div>Great</div>
          <div class="leg"><div class="leg-sq" style="background:#9FE1CB;"></div>Good</div>
          <div class="leg"><div class="leg-sq" style="background:#FAC775;"></div>Okay</div>
          <div class="leg"><div class="leg-sq" style="background:#AFA9EC;"></div>Low</div>
          <div class="leg"><div class="leg-sq" style="background:#F0997B;"></div>Stressed</div>
          <div class="leg"><div class="leg-sq" style="background:#E8E4DD;"></div>Not logged</div>
        </div>
        <div style="position:relative;height:72px;"><canvas id="moodChart" role="img" aria-label="Weekly mood bar chart">Weekly mood</canvas></div>
        <div style="display:flex;justify-content:space-between;margin-top:4px;" id="day-labels"></div>
      </div>
      <div id="insights-section"></div>
    </div>
  </div>

  <!-- CYCLE TRACKER -->
  <div class="section">
    <div class="sec-label" style="margin-bottom:.6rem;">Cycle</div>
    <div class="card">
      <div class="cycle-summary" id="cycle-summary"></div>
      <div class="cycle-stats" id="cycle-stats"></div>
      <div class="phase-insights" id="phase-insights"></div>
      <div class="cycle-input-row">
        <label>Last period start:</label>
        <input type="date" id="period-start-input" />
        <label style="margin-left:4px;">Cycle length:</label>
        <input type="number" id="cycle-len-input" placeholder="28" style="width:58px;" min="21" max="45" />
        <button class="add-btn" id="save-cycle-btn">Save</button>
      </div>
    </div>
  </div>

</div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
const CATS=[{id:'bachelorette',label:'Bachelorette',color:'#c9506a',bg:'#fdf0f2'},{id:'career',label:'Career',color:'#3a6fa8',bg:'#eef3fa'},{id:'health',label:'Health & wellness',color:'#2a7a52',bg:'#edf7f2'},{id:'finance',label:'Finance',color:'#1d7a8a',bg:'#edf6f8'},{id:'home',label:'Home',color:'#888780',bg:'#F1EFE8'},{id:'social',label:'Social',color:'#c9506a',bg:'#fdf0f2'},{id:'family',label:'Family',color:'#b06a1a',bg:'#fdf4e8'},{id:'personal',label:'Personal',color:'#6b52a8',bg:'#f3f0fb'},{id:'travel',label:'Travel',color:'#c05a38',bg:'#fdf1ed'}];
const CAT_MAP={};CATS.forEach(c=>CAT_MAP[c.id]=c);

const MOODS=[
  {id:'great',label:'😊 Great',color:'#ED93B1',bg:'#FBEAF0',tc:'#72243E',score:5},
  {id:'good',label:'🙂 Good',color:'#9FE1CB',bg:'#E1F5EE',tc:'#085041',score:4},
  {id:'okay',label:'😐 Okay',color:'#FAC775',bg:'#FAEEDA',tc:'#633806',score:3},
  {id:'low',label:'😔 Low',color:'#AFA9EC',bg:'#EEEDFE',tc:'#3C3489',score:2},
  {id:'stressed',label:'😤 Stressed',color:'#F0997B',bg:'#FAECE7',tc:'#712B13',score:2},
  {id:'anxious',label:'😰 Anxious',color:'#AFA9EC',bg:'#EEEDFE',tc:'#3C3489',score:2},
  {id:'overwhelmed',label:'🌊 Overwhelmed',color:'#F0997B',bg:'#FAECE7',tc:'#712B13',score:1},
];
const MOOD_MAP={};MOODS.forEach(m=>MOOD_MAP[m.id]=m);

const POS_TAGS_DEF=[
  {id:'workout',label:'workout',color:'#2a7a52',bg:'#edf7f2'},
  {id:'quality sleep',label:'quality sleep',color:'#3a6fa8',bg:'#eef3fa'},
  {id:'outdoors',label:'outdoors',color:'#1d7a8a',bg:'#edf6f8'},
  {id:'social',label:'social',color:'#c9506a',bg:'#fdf0f2'},
  {id:'self-care',label:'self-care',color:'#6b52a8',bg:'#f3f0fb'},
  {id:'healthy eating',label:'healthy eating',color:'#639922',bg:'#EAF3DE'},
  {id:'relationship',label:'relationship',color:'#c9506a',bg:'#fdf0f2'},
  {id:'work win',label:'work win',color:'#b06a1a',bg:'#fdf4e8'},
  {id:'yoga',label:'yoga',color:'#1d9e75',bg:'#edf7f2'},
  {id:'f45',label:'f45',color:'#c05a38',bg:'#fdf1ed'},
  {id:'sauna',label:'sauna',color:'#BA7517',bg:'#FAEEDA'},
  {id:'reading',label:'reading',color:'#534AB7',bg:'#EEEDFE'},
];
const NEG_TAGS_DEF=[
  {id:'work stress',label:'work stress',color:'#c05a38',bg:'#fdf1ed'},
  {id:'poor sleep',label:'poor sleep',color:'#3a6fa8',bg:'#eef3fa'},
  {id:'no exercise',label:'no exercise',color:'#888780',bg:'#F1EFE8'},
  {id:'overwhelm',label:'overwhelm',color:'#993C1D',bg:'#FAECE7'},
  {id:'conflict',label:'conflict',color:'#c9506a',bg:'#fdf0f2'},
  {id:'alcohol',label:'alcohol',color:'#b06a1a',bg:'#fdf4e8'},
  {id:'bad eating',label:'bad eating',color:'#639922',bg:'#EAF3DE'},
  {id:'lack of personal time',label:'lack of personal time',color:'#6b52a8',bg:'#f3f0fb'},
];

const PHASES=[
  {name:'Menstrual',days:5,color:'#ED93B1',badge_bg:'#FBEAF0',badge_color:'#72243E',desc:'Rest and reset. Energy is lower — this is your body asking for gentleness, not performance.',insights:[{icon:'🧠',title:'Energy',text:"Low energy is normal. Protect your morning run but don't push intensity."},{icon:'💪',title:'Exercise',text:'Gentle movement — walks, yoga, light stretching. Skip high-intensity F45 if your body resists.'},{icon:'🍽️',title:'Nutrition',text:'Iron-rich foods help replenish. Dark chocolate is genuinely medicinal here.'},{icon:'❤️',title:'Emotional',text:'You may want more solitude. Communicate that need to Leland rather than withdrawing silently.'}]},
  {name:'Follicular',days:9,color:'#9FE1CB',badge_bg:'#E1F5EE',badge_color:'#085041',desc:"Rising energy and clarity — your most cognitively sharp phase. Ideal for big pushes at work.",insights:[{icon:'🧠',title:'Energy',text:'Naturally rising. Great week for hard conversations, strategy work, or anything requiring focus.'},{icon:'💪',title:'Exercise',text:'Your body responds well to intensity now. F45 and strength training will feel great.'},{icon:'🍽️',title:'Nutrition',text:"Lighter, fresher foods feel right. Good week to start a new healthy habit."},{icon:'❤️',title:'Emotional',text:"Social and communicative. Good week to plan that date night with Leland."}]},
  {name:'Ovulation',days:2,color:'#FAC775',badge_bg:'#FAEEDA',badge_color:'#633806',desc:"Peak energy and confidence — you're at your most magnetic and outgoing.",insights:[{icon:'🧠',title:'Energy',text:'Peak. Schedule your most important pitches or social events around this window.'},{icon:'💪',title:'Exercise',text:'Go hard. Pain tolerance and performance are at their highest.'},{icon:'🍽️',title:'Nutrition',text:'Lighter meals feel best. Zinc-rich foods (pumpkin seeds, chickpeas) support hormone balance.'},{icon:'❤️',title:'Emotional',text:"You'll feel most connected and open. Great time for deeper conversations with Leland."}]},
  {name:'Luteal',days:12,color:'#EF9F27',badge_bg:'#FAEEDA',badge_color:'#633806',desc:'Slowing down and turning inward. Your body is preparing — not failing.',insights:[{icon:'🧠',title:'Energy',text:'Dips toward the end. Front-load harder work earlier in the day.'},{icon:'💪',title:'Exercise',text:'Yoga and walks feel better than intense sessions as the phase progresses.'},{icon:'🍽️',title:'Nutrition',text:'Magnesium (dark chocolate, leafy greens, nuts) helps with PMS. Cravings are hormonal, not weakness.'},{icon:'❤️',title:'Emotional',text:'More sensitive to friction. A good week to name your needs to Leland rather than pushing through.'}]},
];

const EVENT_COLORS=['#ED93B1','#AFA9EC','#9FE1CB','#FAC775','#F0997B','#85B7EB'];
const DEFAULT_EVENTS=[{id:'e1',label:"Des's bachelorette",date:'2025-05-24',emoji:'🌊',colorIdx:0},{id:'e2',label:"Maddie's bachelorette",date:'2025-06-12',emoji:'🎲',colorIdx:1},{id:'e3',label:"Des's wedding",date:'2025-06-28',emoji:'👰🏻‍♀️',colorIdx:2}];
const DEFAULT_MUST=[{id:'m1',text:'Submit protein menu to Sookie (Love Hibachi)',cat:'bachelorette',due:'2025-05-23',done:false,pinned:true},{id:'m2',text:'Confirm dietary restrictions for 2 guests',cat:'bachelorette',due:'2025-05-23',done:false,pinned:true},{id:'m3',text:'Book accommodation in France',cat:'travel',due:'2025-06-01',done:false,pinned:false},{id:'m4',text:'Send birthday card',cat:'social',due:'2025-05-20',done:false,pinned:false}];
const DEFAULT_WANT=[{id:'w1',text:'Buy gym bag + pack it ready to go',cat:'health',starred:true,done:false,pinned:true},{id:'w2',text:'Research house cleaner options',cat:'home',starred:false,done:false,pinned:false},{id:'w3',text:'Plan a date night with Leland',cat:'personal',starred:true,done:false,pinned:false},{id:'w4',text:'Review personal finances / savings check-in',cat:'finance',starred:false,done:false,pinned:false},{id:'w5',text:'Post TikToks this week',cat:'personal',starred:false,done:false,pinned:false}];
const DEFAULT_ASP=[{id:'a1',text:'Build out a meal prep planning agent',notes:''},{id:'a2',text:'Post TikToks consistently — batch on Sundays',notes:'Batch record on Sundays. Use CapCut for editing. Target 3x/week.'},{id:'a3',text:'Look into sauna membership options',notes:''},{id:'a4',text:'Get a consistent meal prep routine going',notes:''}];

let events=[],mustTasks=[],wantTasks=[],aspirations=[],moodLogs=[];
let selectedMood='',selectedPosTags=[],selectedNegTags=[];
let customPosTags=[],customNegTags=[];
let periodStart='',cycleLen=28,notesTimer=null,moodChart=null;

const ls=k=>{try{return JSON.parse(localStorage.getItem(k));}catch{return null;}};
const lsSet=(k,v)=>{try{localStorage.setItem(k,JSON.stringify(v));}catch{}};
const uid=()=>'_'+Math.random().toString(36).slice(2,9);

function loadAll(){
  events=ls('jd5_events')||[...DEFAULT_EVENTS];
  mustTasks=ls('jd5_must')||[...DEFAULT_MUST];
  wantTasks=ls('jd5_want')||[...DEFAULT_WANT];
  aspirations=ls('jd5_asp')||[...DEFAULT_ASP];
  moodLogs=ls('jd5_moods')||[];
  periodStart=ls('jd5_period_start')||'2025-04-11';
  cycleLen=ls('jd5_cycle_len')||28;
  customPosTags=ls('jd5_pos_custom')||[];
  customNegTags=ls('jd5_neg_custom')||[];
  const notes=ls('jd5_notes');
  if(notes)document.getElementById('notes-ta').value=notes;
  document.getElementById('period-start-input').value=periodStart;
  document.getElementById('cycle-len-input').value=cycleLen;
}

function daysUntil(ds){if(!ds)return null;return Math.ceil((new Date(ds+'T00:00:00')-new Date(new Date().toDateString()))/86400000);}
function formatDue(ds){const d=daysUntil(ds);if(d===null)return '';if(d<0)return 'Overdue';if(d===0)return 'Due today';if(d===1)return 'Due tomorrow';if(d<=7)return`Due in ${d} days`;return'Due '+new Date(ds+'T00:00:00').toLocaleDateString('en-US',{month:'short',day:'numeric'});}
function dueClass(ds){const d=daysUntil(ds);if(d===null)return '';if(d<=2)return 'due-urgent';if(d<=7)return 'due-soon';return 'due-normal';}

function renderHeader(){
  const h=new Date().getHours();const g=h<12?'Good morning':h<17?'Good afternoon':'Good evening';
  document.getElementById('greeting').innerHTML=`${g}, <em>Jenni</em>`;
  document.getElementById('dateline').textContent=new Date().toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric'});
}

function getPinnedCount(){return[...mustTasks,...wantTasks].filter(t=>t.pinned&&!t.done).length;}

function renderFocus(){
  const all=[...mustTasks.map(t=>({...t,tier:'must'})),...wantTasks.map(t=>({...t,tier:'want'}))];
  const pinned=all.filter(t=>t.pinned&&!t.done);
  const el=document.getElementById('focus-list');
  const empty=document.getElementById('focus-empty');
  el.innerHTML='';
  if(!pinned.length){empty.style.display='';return;}
  empty.style.display='none';
  pinned.forEach(t=>{
    const cat=CAT_MAP[t.cat];
    const div=document.createElement('div');div.className='focus-card';
    div.innerHTML=`<div class="fc-check ${t.done?'done':''}"></div><div class="fc-body"><div class="fc-title ${t.done?'done':''}">${t.text}</div>${t.due?`<div class="fc-due ${daysUntil(t.due)!==null&&daysUntil(t.due)<=3?'urgent':''}">${formatDue(t.due)}</div>`:''}</div>${cat?`<span class="cat-pill" style="background:${cat.bg};color:${cat.color};">${cat.label}</span>`:''}`;
    div.querySelector('.fc-check').onclick=()=>{
      const src=t.tier==='must'?mustTasks:wantTasks;
      const found=src.find(x=>x.id===t.id);
      if(found){found.done=!found.done;if(found.done)found.pinned=false;}
      lsSet(t.tier==='must'?'jd5_must':'jd5_want',src);
      renderAll();
    };
    el.appendChild(div);
  });
}

function renderEvents(){
  const row=document.getElementById('events-row');row.innerHTML='';
  [...events].sort((a,b)=>new Date(a.date)-new Date(b.date)).forEach(ev=>{
    const d=daysUntil(ev.date);
    const color=EVENT_COLORS[ev.colorIdx%EVENT_COLORS.length];
    const card=document.createElement('div');card.className='ev-card';
    // always show emoji + days count, no 🎉 replacement
    card.innerHTML=`<div class="ev-accent" style="background:${color};"></div><span class="ev-emoji">${ev.emoji||'📅'}</span><div class="ev-num">${Math.max(0,d)}</div><div class="ev-unit">${d<=1?'day away':'days away'}</div><div class="ev-name">${ev.label}</div><div class="ev-date-str">${new Date(ev.date+'T00:00:00').toLocaleDateString('en-US',{month:'short',day:'numeric'})}</div>`;
    row.appendChild(card);
  });
  const ab=document.createElement('button');ab.className='ev-add';ab.textContent='+ add event';
  ab.onclick=()=>{document.getElementById('ev-form').style.display='';document.getElementById('ev-name').focus();};
  row.appendChild(ab);
}

function renderMustTasks(){
  const el=document.getElementById('must-list');el.innerHTML='';
  const sorted=[...mustTasks].sort((a,b)=>{if(a.done!==b.done)return a.done?1:-1;if(!a.done&&!b.done&&a.pinned!==b.pinned)return a.pinned?-1:1;const da=daysUntil(a.due),db=daysUntil(b.due);if(da!==null&&db!==null)return da-db;if(da!==null)return -1;if(db!==null)return 1;return 0;});
  if(!sorted.length){el.innerHTML='<div style="padding:1rem;font-size:.82rem;color:var(--text3);text-align:center;font-style:italic;">No must-do tasks — nice!</div>';return;}
  const urgent=sorted.filter(t=>!t.done&&daysUntil(t.due)!==null&&daysUntil(t.due)<=3);
  const rest=sorted.filter(t=>!(!t.done&&daysUntil(t.due)!==null&&daysUntil(t.due)<=3));
  if(urgent.length){const l=document.createElement('div');l.className='tier-head urgent';l.textContent='⚡ Urgent — due very soon';el.appendChild(l);urgent.forEach(t=>el.appendChild(makeMustRow(t)));}
  if(rest.length){const l=document.createElement('div');l.className='tier-head';l.textContent='Upcoming';el.appendChild(l);rest.forEach(t=>el.appendChild(makeMustRow(t)));}
}
function makeMustRow(t){
  const cat=CAT_MAP[t.cat];const pc=getPinnedCount();const canPin=t.pinned||(pc<3&&!t.done);
  const row=document.createElement('div');row.className='task-row';
  row.innerHTML=`<div class="t-check ${t.done?'done':''}"></div><div class="t-body"><div class="t-title ${t.done?'done':''}">${t.text}</div><div class="t-meta">${t.due?`<span class="${dueClass(t.due)}">${formatDue(t.due)}</span>`:''} ${cat?`<span class="cat-pill" style="background:${cat.bg};color:${cat.color};">${cat.label}</span>`:''}</div></div><button class="pin-btn ${t.pinned?'pinned':''}" title="${t.pinned?'Unpin from focus':'Pin to focus'}" ${!canPin?'disabled':''}>📍</button><button class="del-btn">✕</button>`;
  row.querySelector('.t-check').onclick=()=>{t.done=!t.done;if(t.done)t.pinned=false;lsSet('jd5_must',mustTasks);renderAll();};
  row.querySelector('.pin-btn').onclick=()=>{if(!t.pinned&&getPinnedCount()>=3)return;t.pinned=!t.pinned;lsSet('jd5_must',mustTasks);renderAll();};
  row.querySelector('.del-btn').onclick=()=>{mustTasks=mustTasks.filter(x=>x.id!==t.id);lsSet('jd5_must',mustTasks);renderAll();};
  return row;
}
function renderWantTasks(){
  const el=document.getElementById('want-list');el.innerHTML='';
  const sorted=[...wantTasks].sort((a,b)=>{if(a.done!==b.done)return a.done?1:-1;if(!a.done&&!b.done&&a.pinned!==b.pinned)return a.pinned?-1:1;if(a.starred!==b.starred)return a.starred?-1:1;return 0;});
  if(!sorted.length){el.innerHTML='<div style="padding:1rem;font-size:.82rem;color:var(--text3);text-align:center;font-style:italic;">Add things you want to get to</div>';return;}
  sorted.forEach(t=>{
    const cat=CAT_MAP[t.cat];const pc=getPinnedCount();const canPin=t.pinned||(pc<3&&!t.done);
    const row=document.createElement('div');row.className='task-row';
    row.innerHTML=`<div class="t-check sq ${t.done?'done':''}"></div><div class="t-body"><div class="t-title ${t.done?'done':''}">${t.text}</div><div class="t-meta">${cat?`<span class="cat-pill" style="background:${cat.bg};color:${cat.color};">${cat.label}</span>`:''}</div></div><button class="star-btn ${t.starred?'on':''}">★</button><button class="pin-btn ${t.pinned?'pinned':''}" ${!canPin?'disabled':''}>📍</button><button class="del-btn">✕</button>`;
    row.querySelector('.t-check').onclick=()=>{t.done=!t.done;if(t.done)t.pinned=false;lsSet('jd5_want',wantTasks);renderAll();};
    row.querySelector('.star-btn').onclick=()=>{t.starred=!t.starred;lsSet('jd5_want',wantTasks);renderWantTasks();};
    row.querySelector('.pin-btn').onclick=()=>{if(!t.pinned&&getPinnedCount()>=3)return;t.pinned=!t.pinned;lsSet('jd5_want',wantTasks);renderAll();};
    row.querySelector('.del-btn').onclick=()=>{wantTasks=wantTasks.filter(x=>x.id!==t.id);lsSet('jd5_want',wantTasks);renderAll();};
    el.appendChild(row);
  });
}
function renderAsp(){
  const el=document.getElementById('asp-card');el.innerHTML='';
  if(!aspirations.length){el.innerHTML='<div style="padding:1rem;font-size:.82rem;color:var(--text3);text-align:center;font-style:italic;">Add ideas and goals you want to work toward someday</div>';return;}
  aspirations.forEach(a=>{
    const item=document.createElement('div');
    const hdr=document.createElement('div');hdr.className='asp-header';
    hdr.innerHTML=`<span class="asp-chevron ${a.notes?'open':''}">▶</span><span class="asp-text">${a.text}</span><button class="asp-del">✕</button>`;
    const nd=document.createElement('div');nd.className='asp-notes-area';nd.style.display=a.notes?'':'none';
    const ta=document.createElement('textarea');ta.placeholder='Notes, ideas, progress...';ta.value=a.notes||'';
    ta.oninput=()=>{a.notes=ta.value;lsSet('jd5_asp',aspirations);};
    nd.appendChild(ta);
    hdr.onclick=e=>{if(e.target.classList.contains('asp-del'))return;const open=nd.style.display!=='none';nd.style.display=open?'none':'';hdr.querySelector('.asp-chevron').classList.toggle('open',!open);};
    hdr.querySelector('.asp-del').onclick=e=>{e.stopPropagation();aspirations=aspirations.filter(x=>x.id!==a.id);lsSet('jd5_asp',aspirations);renderAsp();};
    item.appendChild(hdr);item.appendChild(nd);el.appendChild(item);
  });
}

function renderMoodPills(){
  const el=document.getElementById('mood-pills');el.innerHTML='';
  MOODS.forEach(m=>{
    const btn=document.createElement('button');btn.className='mood-pill'+(selectedMood===m.id?' sel':'');btn.textContent=m.label;
    if(selectedMood===m.id){btn.style.background=m.bg;btn.style.color=m.tc;btn.style.borderColor=m.color;}
    btn.onclick=()=>{selectedMood=selectedMood===m.id?'':m.id;renderMoodPills();};
    el.appendChild(btn);
  });
}

function renderTagGroup(elId,defs,custom,selected,onToggle){
  const el=document.getElementById(elId);el.innerHTML='';
  const all=[...defs,...custom.map(t=>({id:t,label:t,color:'#6b52a8',bg:'#f3f0fb'}))];
  all.forEach(t=>{
    const btn=document.createElement('button');const sel=selected.includes(t.id);
    btn.className='tag-btn'+(sel?' sel':'');btn.textContent=t.label;
    if(sel){btn.style.background=t.bg;btn.style.color=t.color;btn.style.borderColor=t.color;}
    else{btn.style.background='';btn.style.color='';btn.style.borderColor='';}
    btn.onclick=()=>onToggle(t.id);
    el.appendChild(btn);
  });
}
function renderPosTags(){renderTagGroup('pos-tags',POS_TAGS_DEF,customPosTags,selectedPosTags,t=>{const i=selectedPosTags.indexOf(t);i>=0?selectedPosTags.splice(i,1):selectedPosTags.push(t);renderPosTags();});}
function renderNegTags(){renderTagGroup('neg-tags',NEG_TAGS_DEF,customNegTags,selectedNegTags,t=>{const i=selectedNegTags.indexOf(t);i>=0?selectedNegTags.splice(i,1):selectedNegTags.push(t);renderNegTags();});}

document.getElementById('pos-custom-btn').onclick=()=>{const inp=document.getElementById('pos-custom-input');const val=inp.value.trim();if(!val)return;customPosTags.push(val);lsSet('jd5_pos_custom',customPosTags);inp.value='';renderPosTags();};
document.getElementById('pos-custom-input').addEventListener('keydown',e=>{if(e.key==='Enter')document.getElementById('pos-custom-btn').click();});
document.getElementById('neg-custom-btn').onclick=()=>{const inp=document.getElementById('neg-custom-input');const val=inp.value.trim();if(!val)return;customNegTags.push(val);lsSet('jd5_neg_custom',customNegTags);inp.value='';renderNegTags();};
document.getElementById('neg-custom-input').addEventListener('keydown',e=>{if(e.key==='Enter')document.getElementById('neg-custom-btn').click();});

function logMood(){
  if(!selectedMood){alert('Pick a mood first!');return;}
  const todayKey=new Date().toISOString().slice(0,10);
  const existing=moodLogs.findIndex(l=>l.date===todayKey);
  const entry={date:todayKey,mood:selectedMood,posTags:[...selectedPosTags],negTags:[...selectedNegTags],note:document.getElementById('today-note').value.trim()};
  if(existing>=0)moodLogs[existing]=entry;else moodLogs.push(entry);
  lsSet('jd5_moods',moodLogs);
  selectedMood='';selectedPosTags=[];selectedNegTags=[];
  document.getElementById('today-note').value='';
  renderMoodPills();renderPosTags();renderNegTags();renderMoodAnalytics();
}

function getLast7(){
  const days=[];
  for(let i=6;i>=0;i--){const d=new Date();d.setDate(d.getDate()-i);const key=d.toISOString().slice(0,10);const log=moodLogs.find(l=>l.date===key);days.push({key,day:d.toLocaleDateString('en-US',{weekday:'short'}),log});}
  return days;
}
function renderMoodAnalytics(){
  const days=getLast7();const logged=days.filter(d=>d.log);
  const goodDays=logged.filter(d=>['great','good'].includes(d.log.mood)).length;
  const stressedDays=logged.filter(d=>['stressed','anxious','overwhelmed'].includes(d.log.mood)).length;
  const pct=logged.length?Math.round((goodDays/logged.length)*100):0;
  const stPct=logged.length?Math.round((stressedDays/logged.length)*100):0;
  const posCount={};logged.forEach(d=>d.log.posTags.forEach(t=>posCount[t]=(posCount[t]||0)+1));
  const topPos=Object.entries(posCount).sort((a,b)=>b[1]-a[1])[0];
  const negCount={};logged.forEach(d=>d.log.negTags.forEach(t=>negCount[t]=(negCount[t]||0)+1));
  const topNeg=Object.entries(negCount).sort((a,b)=>b[1]-a[1])[0];
  document.getElementById('analytics-grid').innerHTML=`<div class="a-stat"><div class="a-val" style="color:#ED93B1;">${logged.length?pct+'%':'—'}</div><div class="a-lbl">Great or good days</div></div><div class="a-stat"><div class="a-val" style="color:#F0997B;">${logged.length?stPct+'%':'—'}</div><div class="a-lbl">Stressed or anxious days</div></div><div class="a-stat"><div class="a-val" style="font-size:.9rem;">${topPos?topPos[0]:'—'}</div><div class="a-lbl">Top mood booster</div></div><div class="a-stat"><div class="a-val" style="font-size:.9rem;">${topNeg?topNeg[0]:'—'}</div><div class="a-lbl">Top mood drain</div></div>`;
  const labelsEl=document.getElementById('day-labels');labelsEl.innerHTML='';
  days.forEach(d=>{const s=document.createElement('span');s.style.cssText='flex:1;text-align:center;font-size:.65rem;color:var(--text3);';s.textContent=d.day;labelsEl.appendChild(s);});
  const MC={great:'#ED93B1',good:'#9FE1CB',okay:'#FAC775',low:'#AFA9EC',stressed:'#F0997B',anxious:'#AFA9EC',overwhelmed:'#F0997B'};
  const MS={great:5,good:4,okay:3,low:2,stressed:2,anxious:2,overwhelmed:1};
  if(moodChart){moodChart.destroy();moodChart=null;}
  moodChart=new Chart(document.getElementById('moodChart'),{type:'bar',data:{labels:days.map(d=>d.day),datasets:[{data:days.map(d=>d.log?MS[d.log.mood]||0:0),backgroundColor:days.map(d=>d.log?(MC[d.log.mood]||'#E8E4DD'):'#E8E4DD'),borderRadius:4,borderSkipped:false}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:ctx=>days[ctx.dataIndex].log?days[ctx.dataIndex].log.mood:'not logged'}}},scales:{x:{display:false},y:{display:false,min:0,max:6}}}});
  const ins=document.getElementById('insights-section');ins.innerHTML='';
  if(!logged.length){ins.innerHTML='<div style="padding:.75rem 12px;font-size:.78rem;color:var(--text3);font-style:italic;">Start logging your mood daily to see patterns here.</div>';return;}
  const rows=[];
  if(topPos&&posCount[topPos[0]]>=2)rows.push({icon:'💡',text:`You felt best on days you <strong>${topPos[0]}</strong>. That showed up ${topPos[1]}x this week — protect it.`});
  if(topNeg&&negCount[topNeg[0]]>=2)rows.push({icon:'⚠️',text:`<strong>${topNeg[0]}</strong> drained you ${topNeg[1]} days this week. Worth noticing.`});
  if(pct>=60)rows.push({icon:'✨',text:`<strong>${pct}% of your logged days were good or great.</strong> Whatever you're doing is working.`});
  if(stPct>=40)rows.push({icon:'🌿',text:`High stress week. Consider a wind-down ritual after your 4pm work block.`});
  if(!rows.length)rows.push({icon:'📊',text:`Keep logging daily — patterns take a few days to emerge.`});
  rows.forEach(r=>{const div=document.createElement('div');div.className='insight-row';div.innerHTML=`<div class="i-icon">${r.icon}</div><div class="i-text">${r.text}</div>`;ins.appendChild(div);});
}

function renderCycle(){
  const sum=document.getElementById('cycle-summary');
  if(!periodStart){sum.innerHTML='<div style="font-size:.82rem;color:var(--text3);font-style:italic;">Enter your last period start date below to activate cycle tracking.</div>';document.getElementById('cycle-stats').innerHTML='';document.getElementById('phase-insights').innerHTML='';return;}
  const start=new Date(periodStart+'T00:00:00');
  const today=new Date(new Date().toDateString());
  const dayOfCycle=Math.floor((today-start)/86400000)+1;
  const clampedDay=((dayOfCycle-1)%cycleLen)+1;
  let phaseIdx=0,cumDays=0;
  for(let i=0;i<PHASES.length;i++){if(clampedDay<=cumDays+PHASES[i].days){phaseIdx=i;break;}cumDays+=PHASES[i].days;}
  const phase=PHASES[phaseIdx];
  const nextPeriod=new Date(start);
  while((nextPeriod-today)/86400000<0)nextPeriod.setDate(nextPeriod.getDate()+cycleLen);
  const daysToNext=Math.ceil((nextPeriod-today)/86400000);
  const nextPeriodStr=nextPeriod.toLocaleDateString('en-US',{month:'short',day:'numeric'});
  const ovulation=new Date(nextPeriod);ovulation.setDate(ovulation.getDate()-14);
  const ovulationStr=ovulation.toLocaleDateString('en-US',{month:'short',day:'numeric'});

  // Phase progress bar
  sum.innerHTML=`
    <div class="cycle-day-line">Day ${clampedDay} of ${cycleLen} &nbsp;·&nbsp; ${phase.name} phase</div>
    <div class="cycle-phase-bar" id="cycle-phase-bar"></div>
    <div class="cycle-phase-row">
      <span class="phase-badge" style="background:${phase.badge_bg};color:${phase.badge_color};">${phase.name}</span>
      <div class="phase-desc">${phase.desc}</div>
    </div>
  `;
  const bar=document.getElementById('cycle-phase-bar');
  let dc=0;
  PHASES.forEach(p=>{
    for(let i=0;i<p.days;i++){
      dc++;
      const seg=document.createElement('div');seg.className='phase-seg';seg.style.flex='1';
      seg.style.background=dc<=clampedDay?p.color:'var(--bg3)';
      seg.style.opacity=dc===clampedDay?'1':dc<clampedDay?'0.6':'0.18';
      bar.appendChild(seg);
    }
  });

  document.getElementById('cycle-stats').innerHTML=`
    <div class="c-stat"><div class="c-val">Day ${clampedDay}</div><div class="c-lbl">Today in your cycle</div></div>
    <div class="c-stat"><div class="c-val">${daysToNext > 0 ? daysToNext+' days' : 'Today'}</div><div class="c-lbl">Until next period (est.)</div></div>
    <div class="c-stat"><div class="c-val">${nextPeriodStr}</div><div class="c-lbl">Next period (est.)</div></div>
    <div class="c-stat"><div class="c-val">${ovulationStr}</div><div class="c-lbl">Next ovulation (est.)</div></div>
  `;

  const pi=document.getElementById('phase-insights');
  pi.innerHTML='<div style="font-size:.65rem;font-weight:500;text-transform:uppercase;letter-spacing:.07em;padding:6px 12px;color:var(--text3);border-bottom:1px solid var(--border);background:var(--bg2);">What to expect this week</div>';
  phase.insights.forEach(ins=>{const div=document.createElement('div');div.className='phase-insight-row';div.innerHTML=`<div class="i-icon">${ins.icon}</div><div class="i-text"><strong>${ins.title}:</strong> ${ins.text}</div>`;pi.appendChild(div);});
}

document.getElementById('notes-ta').addEventListener('input',()=>{
  clearTimeout(notesTimer);document.getElementById('notes-footer').textContent='Saving...';
  notesTimer=setTimeout(()=>{lsSet('jd5_notes',document.getElementById('notes-ta').value);document.getElementById('notes-footer').textContent='Saved '+new Date().toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'});},800);
});

function populateCatSelect(id){const sel=document.getElementById(id);CATS.forEach(c=>{const o=document.createElement('option');o.value=c.id;o.textContent=c.label;sel.appendChild(o);});}
function renderAll(){renderFocus();renderMustTasks();renderWantTasks();}

document.getElementById('ev-toggle-btn').onclick=()=>{const f=document.getElementById('ev-form');f.style.display=f.style.display==='none'?'':'none';};
document.getElementById('ev-add-btn').onclick=()=>{const name=document.getElementById('ev-name').value.trim();const date=document.getElementById('ev-date').value;const emoji=document.getElementById('ev-emoji').value.trim()||'📅';if(!name||!date)return;events.push({id:uid(),label:name,date,emoji,colorIdx:events.length%EVENT_COLORS.length});lsSet('jd5_events',events);document.getElementById('ev-name').value='';document.getElementById('ev-date').value='';document.getElementById('ev-emoji').value='';document.getElementById('ev-form').style.display='none';renderEvents();};
document.getElementById('must-add-btn').onclick=()=>{const text=document.getElementById('must-input').value.trim();if(!text)return;mustTasks.push({id:uid(),text,cat:document.getElementById('must-cat').value,due:document.getElementById('must-date').value,done:false,pinned:false});lsSet('jd5_must',mustTasks);document.getElementById('must-input').value='';document.getElementById('must-date').value='';renderAll();renderMustTasks();};
document.getElementById('must-input').addEventListener('keydown',e=>{if(e.key==='Enter')document.getElementById('must-add-btn').click();});
document.getElementById('want-add-btn').onclick=()=>{const text=document.getElementById('want-input').value.trim();if(!text)return;wantTasks.push({id:uid(),text,cat:document.getElementById('want-cat').value,starred:false,done:false,pinned:false});lsSet('jd5_want',wantTasks);document.getElementById('want-input').value='';renderAll();renderWantTasks();};
document.getElementById('want-input').addEventListener('keydown',e=>{if(e.key==='Enter')document.getElementById('want-add-btn').click();});
document.getElementById('asp-add-btn').onclick=()=>{const text=document.getElementById('asp-input').value.trim();if(!text)return;aspirations.push({id:uid(),text,notes:''});lsSet('jd5_asp',aspirations);document.getElementById('asp-input').value='';renderAsp();};
document.getElementById('asp-input').addEventListener('keydown',e=>{if(e.key==='Enter')document.getElementById('asp-add-btn').click();});
document.getElementById('log-mood-btn').onclick=logMood;
document.getElementById('save-cycle-btn').onclick=()=>{const ps=document.getElementById('period-start-input').value;const cl=parseInt(document.getElementById('cycle-len-input').value)||28;if(!ps){alert('Please enter your last period start date.');return;}periodStart=ps;cycleLen=cl;lsSet('jd5_period_start',periodStart);lsSet('jd5_cycle_len',cycleLen);renderCycle();};
document.getElementById('theme-btn').onclick=()=>{document.body.classList.toggle('dark');lsSet('jd5_dark',document.body.classList.contains('dark'));};
if(ls('jd5_dark'))document.body.classList.add('dark');

loadAll();
populateCatSelect('must-cat');populateCatSelect('want-cat');
renderHeader();renderFocus();renderEvents();renderMustTasks();renderWantTasks();renderAsp();
renderMoodPills();renderPosTags();renderNegTags();renderMoodAnalytics();renderCycle();
</script>
</body>
</html>
