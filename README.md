
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shuklagandaki Business Executive Dashboard</title>
<script>
function _loadLib(urls, checkFn, onDone){
  var i = 0;
  function tryNext(){
    if(checkFn()){ onDone(); return; }
    if(i >= urls.length){ onDone(); return; }
    var s = document.createElement('script');
    s.src = urls[i++];
    s.onload = function(){ onDone(); };
    s.onerror = tryNext;
    document.head.appendChild(s);
  }
  tryNext();
}
window._libsReady = { chart:false, xlsx:false };
_loadLib([
  'https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.0/chart.umd.min.js',
  'https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js',
  'https://unpkg.com/chart.js@4.4.0/dist/chart.umd.min.js'
], function(){ return typeof Chart !== 'undefined'; }, function(){ window._libsReady.chart = (typeof Chart !== 'undefined'); if(window._onLibsReady) window._onLibsReady(); });
_loadLib([
  'https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js',
  'https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js',
  'https://unpkg.com/xlsx@0.18.5/dist/xlsx.full.min.js'
], function(){ return typeof XLSX !== 'undefined'; }, function(){ window._libsReady.xlsx = (typeof XLSX !== 'undefined'); if(window._onLibsReady) window._onLibsReady(); });
</script>
<script type="module">
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyALb8QcMC_3BSDy27wsQaYkPgma2XStCes",
  authDomain: "data-f8737.firebaseapp.com",
  projectId: "data-f8737",
  storageBucket: "data-f8737.firebasestorage.app",
  messagingSenderId: "214517440168",
  appId: "1:214517440168:web:fecc77066bdd987a20ec9d",
  measurementId: "G-2RW9GZMTLX"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
</script>
<style>
:root{
  --bg:#f3f5fb; --bg2:#ffffff; --panel:#ffffff; --panel2:#f7f8fd; --border:#e8eaf6;
  --txt:#1b2140; --txt2:#6b7290; --txt3:#9aa0c0;
  --accent:#6d5bf6; --accent2:#4e8dff; --green:#22c48d; --red:#ff5c7c; --amber:#ffab3d;
  --grad1:linear-gradient(135deg,#6d5bf6,#4e8dff);
  --grad2:linear-gradient(135deg,#efe9ff,#e8f0ff);
  --grad-side:linear-gradient(165deg,#241a5e 0%,#4630b8 45%,#6d5bf6 100%);
  --radius:16px;
}
*{box-sizing:border-box;}
html,body{margin:0;padding:0;background:var(--bg);color:var(--txt);font-family:'Segoe UI',system-ui,-apple-system,sans-serif;}
body{min-height:100vh;}
::-webkit-scrollbar{width:8px;height:8px;}
::-webkit-scrollbar-thumb{background:#d7dcf2;border-radius:4px;}
.app{display:flex;min-height:100vh;}
.sidebar{width:250px;flex-shrink:0;background:var(--grad-side);border-right:none;padding:20px 14px;position:sticky;top:0;height:100vh;overflow-y:auto;color:#fff;}
.brand{display:flex;align-items:center;gap:10px;padding:6px 8px 20px 8px;border-bottom:1px solid #ffffff2b;margin-bottom:16px;}
.brand-badge{width:38px;height:38px;border-radius:11px;background:#ffffff;display:flex;align-items:center;justify-content:center;font-weight:800;color:#5c4bdb;box-shadow:0 4px 14px #00000030;}
.brand-text b{display:block;font-size:14px;letter-spacing:.3px;color:#fff;}
.brand-text span{display:block;font-size:11px;color:#d9d4ff;}
.nav-group-label{font-size:10.5px;color:#c8c2f7;text-transform:uppercase;letter-spacing:1px;margin:16px 8px 8px;}
.nav-btn{display:flex;align-items:center;gap:10px;width:100%;text-align:left;background:transparent;border:none;color:#e3dffb;padding:10px 12px;border-radius:11px;font-size:13.5px;cursor:pointer;}
.nav-btn:hover{background:#ffffff1c;color:#fff;}
.nav-btn.active{background:#ffffff;color:#5c4bdb;font-weight:700;box-shadow:0 6px 16px #00000025;}
.nav-ico{width:20px;text-align:center;font-size:14px;}
.main{flex:1;min-width:0;padding:22px 28px 60px;}
.topbar{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:12px;margin-bottom:20px;}
.topbar h1{font-size:21px;margin:0;font-weight:800;color:var(--txt);} 
.topbar .sub{color:var(--txt3);font-size:12.5px;margin-top:2px;}
.controls{display:flex;gap:8px;flex-wrap:wrap;align-items:center;}
.pill-tabs{display:flex;gap:6px;background:var(--panel);padding:4px;border-radius:11px;border:1px solid var(--border);flex-wrap:wrap;box-shadow:0 2px 10px #6d5bf60d;}
.pill-tabs button{background:transparent;border:none;color:var(--txt2);padding:7px 13px;border-radius:8px;font-size:12.5px;cursor:pointer;font-weight:600;}
.pill-tabs button.active{background:var(--grad1);color:#fff;}
select, input[type=text], input[type=file]{background:#fff;border:1px solid var(--border);color:var(--txt);padding:7px 10px;border-radius:9px;font-size:12.5px;}
select:focus,input:focus{outline:1px solid var(--accent);}
.btn{background:var(--grad1);color:#fff;border:none;padding:9px 15px;border-radius:10px;font-size:12.5px;font-weight:700;cursor:pointer;box-shadow:0 6px 14px #6d5bf636;}
.btn.ghost{background:#fff;border:1px solid var(--border);color:var(--txt2);box-shadow:none;}
.btn.small{padding:6px 11px;font-size:11.5px;}
.btn:hover{filter:brightness(1.06);} 
.grid{display:grid;gap:14px;}
.kpi-grid{grid-template-columns:repeat(auto-fit,minmax(178px,1fr));}
.kpi{background:var(--grad1);color:#fff;border:none;border-radius:var(--radius);padding:17px;position:relative;overflow:hidden;box-shadow:0 10px 24px #4e5eea26;}
.kpi:nth-child(3n+2){background:linear-gradient(135deg,#4e8dff,#6d5bf6);}
.kpi:nth-child(3n+3){background:linear-gradient(135deg,#8a63f2,#c15be0);}
.kpi .lbl{color:#ffffffcc;font-size:11.5px;text-transform:uppercase;letter-spacing:.6px;margin-bottom:8px;}
.kpi .val{font-size:24px;font-weight:800;color:#fff;}
.kpi .delta{font-size:11.5px;margin-top:6px;font-weight:600;color:#ffffffdd;}
.kpi .delta.up{color:#d8ffe9;} .kpi .delta.down{color:#ffe0e6;}
.kpi .bar{height:5px;border-radius:3px;background:#ffffff33;margin-top:10px;overflow:hidden;}
.kpi .bar i{display:block;height:100%;background:#fff;}
.panel{background:var(--panel);border:1px solid var(--border);border-radius:var(--radius);padding:18px;margin-bottom:16px;box-shadow:0 4px 18px #6d5bf60d;}
.panel h3{margin:0 0 4px;font-size:14.5px;color:var(--txt);} 
.panel .hint{color:var(--txt3);font-size:11.5px;margin-bottom:14px;}
.two-col{display:grid;grid-template-columns:1.3fr 1fr;gap:16px;}
.three-col{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
@media(max-width:1000px){.two-col,.three-col{grid-template-columns:1fr;}}
table{width:100%;border-collapse:collapse;font-size:12.3px;}
th{text-align:left;color:var(--txt3);font-weight:700;text-transform:uppercase;font-size:10.5px;letter-spacing:.4px;padding:9px 10px;border-bottom:1px solid var(--border);position:sticky;top:0;background:linear-gradient(180deg,#fff,#fff);}
td{padding:9px 10px;border-bottom:1px solid #f0f1fa;color:var(--txt);} 
tr:hover td{background:#f7f7ff;}
.tbl-wrap{max-height:420px;overflow:auto;border-radius:12px;border:1px solid var(--border);} 
.tag{display:inline-block;padding:2px 9px;border-radius:20px;font-size:10.5px;font-weight:700;}
.tag.new{background:#e4f9f1;color:#159a6c;}
.tag.ret{background:#eaf1ff;color:#3568d8;}
.tag.win{background:#fff2e0;color:#c67a12;}
.tag.ns{background:#ffe8ec;color:#d43a58;}
.badge-olt{background:#eeeaff;color:#5c4bdb;padding:3px 9px;border-radius:7px;font-size:10.5px;font-weight:700;}
.progress-row{display:flex;align-items:center;gap:10px;margin-bottom:10px;} 
.progress-row .name{width:80px;font-size:12px;color:var(--txt2);flex-shrink:0;}
.progress-row .track{flex:1;height:8px;background:#eef0fb;border-radius:5px;overflow:hidden;}
.progress-row .track i{display:block;height:100%;border-radius:5px;}
.progress-row .pct{width:52px;text-align:right;font-size:12px;font-weight:700;flex-shrink:0;color:var(--txt);} 
.import-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px;}
.import-card{background:var(--panel2);border:1px dashed #cfc9f9;border-radius:14px;padding:16px;} 
.import-card h4{margin:0 0 4px;font-size:13px;color:var(--txt);}
.import-card p{color:var(--txt3);font-size:11.3px;margin:0 0 10px;}
.import-card .status{font-size:11px;color:#159a6c;margin-top:8px;}
.import-card input[type=file]{width:100%;margin-bottom:8px;}
.chip-row{display:flex;gap:6px;margin-bottom:8px;flex-wrap:wrap;}
.chip-row select{flex:1;min-width:100px;}
canvas{max-width:100%;}
.chart-box{position:relative;width:100%;height:230px;}
.chart-box canvas{position:absolute;top:0;left:0;width:100%!important;height:100%!important;}
.note{background:#f1eeff;border-left:3px solid var(--accent);padding:10px 14px;border-radius:10px;font-size:12px;color:#4b3f99;margin-bottom:14px;}
.editable-tbl input{width:70px;background:#fff;border:1px solid var(--border);color:var(--txt);padding:4px 6px;border-radius:6px;font-size:11.5px;} 
.section{display:none;}
.section.active{display:block;}
.footer-note{color:var(--txt3);font-size:11px;text-align:center;margin-top:30px;}
.flex-between{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;}
.small-muted{color:var(--txt3);font-size:11px;}
.sync-pill{display:inline-block;padding:4px 10px;border-radius:20px;font-size:11px;font-weight:700;}
.sync-pill.sync-ok{background:#e4f9f1;color:#159a6c;}
.sync-pill.sync-off{background:#ffe8ec;color:#d43a58;}
.sync-pill.sync-busy{background:#fff2e0;color:#c67a12;}
.pct-switch{width:34px;height:19px;border-radius:20px;background:#dfe1f2;position:relative;transition:.15s;flex-shrink:0;}
.pct-switch i{position:absolute;top:2px;left:2px;width:15px;height:15px;border-radius:50%;background:#fff;box-shadow:0 1px 3px #0002;transition:.15s;}
.pct-switch.on{background:var(--grad1);} 
.pct-switch.on i{left:17px;} 
.toast{position:fixed;top:20px;right:20px;z-index:9999;background:#fff;border:1px solid var(--border);border-radius:14px;box-shadow:0 14px 40px #0002;padding:16px 18px;width:320px;transform:translateX(110%);opacity:0;pointer-events:none;transition:all .28s cubic-bezier(.2,.9,.2,1);} 
.toast.show{transform:translateX(0);opacity:1;pointer-events:auto;}
.toast .toast-title{font-weight:800;font-size:13.5px;color:var(--txt);margin-bottom:4px;}
.toast .toast-detail{font-size:12px;color:var(--txt2);line-height:1.5;} 
.insight-card{background:#ffffff1c;border:1px solid #ffffff30;border-radius:14px;padding:14px;margin-top:14px;color:#fff;} 
.insight-card b{display:block;font-size:12.5px;margin-bottom:4px;} 
.insight-card span{font-size:11.3px;color:#e3dffb;} 
.quick-actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:4px;} 
.quick-actions button{flex:1;min-width:140px;background:var(--grad1);color:#fff;border:none;padding:12px 14px;border-radius:12px;font-size:12.5px;font-weight:700;cursor:pointer;box-shadow:0 8px 18px #6d5bf636;} 
.quick-actions button:nth-child(2){background:linear-gradient(135deg,#4e8dff,#6d5bf6);} 
.quick-actions button:nth-child(3){background:linear-gradient(135deg,#7a63e8,#a75be0);} 
.quick-actions button:nth-child(4){background:linear-gradient(135deg,#9a5be0,#c15be0);} 
.quick-actions button:nth-child(5){background:linear-gradient(135deg,#e0605b,#ea7a5b);} 
</style>
</head>
<body>

<div class="app">
  <div class="toast" id="importToast">
    <div class="toast-title">Imported</div>
    <div class="toast-detail">&nbsp;</div>
    <div class="chip-row" style="margin-top:8px;">
      <button class="btn small toast-push-btn" style="display:none;">Retry Cloud Push</button>
      <button class="btn ghost small toast-close-btn">Close</button>
    </div>
  </div>
  <div class="sidebar">
    <div class="brand">
      <div class="brand-badge">SG</div>
      <div class="brand-text"><b>Shuklagandaki</b><span>Business Executive Dashboard</span></div>
    </div>
    <div class="nav-group-label">Overview</div>
    <button class="nav-btn active" data-tab="overview"><span class="nav-ico">&#9733;</span> Executive Overview</button>
    <div class="nav-group-label">Analysis</div>
    <button class="nav-btn" data-tab="behaviour"><span class="nav-ico">&#128100;</span> Customer Behaviour</button>
    <button class="nav-btn" data-tab="growth"><span class="nav-ico">&#128200;</span> Sales &amp; Growth</button>
    <button class="nav-btn" data-tab="revenue"><span class="nav-ico">&#128176;</span> Revenue &amp; Performance</button>
    <div class="nav-group-label">Admin</div>
    <button class="nav-btn" data-tab="import"><span class="nav-ico">&#8593;</span> Data Import</button>
    <button class="nav-btn" data-tab="targets"><span class="nav-ico">&#127919;</span> Manage Targets</button>
    <div class="nav-group-label">Fiscal Year</div>
    <div class="chip-row" style="padding:0 8px;">
      <select id="fySelect"><option value="2083/84">FY 2083/84</option><option value="2082/83">FY 2082/83</option></select>
    </div>
    <div class="nav-group-label">Cloud Sync</div>
    <div style="padding:0 8px;"><span class="sync-pill sync-off" id="syncStatus">&#9729; Connecting...</span></div>
    <div class="insight-card" id="sidebar-insight"><b>Today's Insights</b><span>Loading...</span></div>
    <div class="footer-note" style="text-align:left;padding:10px 8px;color:#c8c2f7;">Data syncs to Firebase automatically on import. Also cached locally in this browser as offline backup.</div>
  </div>

  <div class="main">
    <div class="topbar">
      <div>
        <h1 id="pageTitle">Executive Overview</h1>
        <div class="sub" id="pageSub">Shuklagandaki Branch &middot; M1&ndash;M12 performance, connected end to end</div>
      </div>
      <div class="controls">
        <div class="pill-tabs" id="oltTabs">
          <button data-olt="ALL" class="active">All OLT</button>
          <button data-olt="SKGD01">SKGD01</button>
          <button data-olt="VMAD01">VMAD01</button>
          <button data-olt="RISH01">RISH01</button>
        </div>
        <select id="monthSelect"></select>
        <label id="pctToggleLabel" style="margin:0;display:flex;align-items:center;gap:8px;background:#fff;border:1px solid var(--border);border-radius:9px;padding:7px 12px;cursor:pointer;user-select:none;">
          <span class="pct-switch" id="pctSwitch"><i></i></span>
          <span style="font-size:12.5px;color:var(--txt2);font-weight:600;">Show as %</span>
          <input type="checkbox" id="pctToggle" style="display:none;">
        </label>
      </div>
    </div>

    <!-- ===================== OVERVIEW ===================== -->
    <div class="section active" id="sec-overview">
      <div class="note">Yo overview le Target &rarr; Sales &rarr; New Customer &rarr; Billing &rarr; Retention &rarr; Winback &rarr; NS &rarr; Churn &rarr; Active &rarr; Revenue &rarr; Forecast sabai summarize garcha.</div>
      <div class="note" id="ov-date-warning" style="display:none;border-left-color:var(--red);">&#9888; Could not read the expiry dates in this month's forecast file (unrecognized date format), so Retention/Winback may be incorrect. Check the imported forecast file.</div>
      <div class="grid kpi-grid" id="ov-kpis"></div>

      <div class="two-col" style="margin-top:16px;">
        <div class="panel">
          <h3>Target vs Achievement &mdash; Installation, Growth, Churn, Active, Revenue</h3>
          <div class="hint">Selected month, selected OLT (or branch total if All OLT)</div>
          <div id="ov-target-progress"></div>
        </div>
        <div class="panel">
          <h3>Customer Flow Funnel</h3>
          <div class="hint">Forecast due &rarr; Renewed &rarr; Retention / Winback / NS &rarr; New</div>
          <div id="ov-funnel"></div>
        </div>
      </div>

      <div class="three-col">
        <div class="panel">
          <h3>Revenue Trend (Accrual, by BS month)</h3>
          <div class="chart-box"><canvas id="chart-ov-revenue"></canvas></div>
        </div>
        <div class="panel">
          <h3>Active Customers &amp; Net Growth Trend</h3>
          <div class="chart-box"><canvas id="chart-ov-active"></canvas></div>
        </div>
        <div class="panel">
          <h3>Top Performing OLT</h3>
          <div class="hint">By accrual revenue share, selected month</div>
          <div class="chart-box"><canvas id="chart-ov-topolt"></canvas></div>
        </div>
      </div>

      <div class="panel">
        <h3>OLT-wise Snapshot &mdash; selected month</h3>
        <div class="tbl-wrap"><table id="ov-olt-table"><thead></thead><tbody></tbody></table></div>
      </div>

      <div class="panel">
        <h3>Quick Actions</h3>
        <div class="quick-actions" id="ov-quick-actions">
          <button data-tab="targets">&#127919; Manage Targets</button>
          <button data-tab="import">&#8593; Data Import</button>
          <button data-tab="behaviour">&#128100; Customer Behaviour</button>
          <button data-tab="growth">&#128200; Sales &amp; Growth</button>
          <button data-tab="revenue">&#128196; Revenue Report</button>
        </div>
      </div>
    </div>


    <!-- rest of file unchanged... -->

</body>
</html>
