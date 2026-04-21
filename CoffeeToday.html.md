  
<html lang="th">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
<title>Coffee Today — บันทึกการเข้างาน</title>  
<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&family=Prompt:wght@400;600;700&display=swap" rel="stylesheet">  
<style>  
:root{--ink:#1a1a2e;--deep:#16213e;--mid:#0f3460;--accent:#e94560;--gold:#f5a623;--teal:#00b4d8;--pale:#f0f4ff;--surface:#fff;--muted:#8892b0;--border:#e2e8f0;--success:#10b981;--warning:#f59e0b;--danger:#ef4444;--radius:12px;--shadow:0 4px 24px rgba(26,26,46,.10);--shadow-lg:0 8px 40px rgba(26,26,46,.16)}  
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}html{scroll-behavior:smooth}  
body{font-family:'Sarabun',sans-serif;background:var(--pale);color:var(--ink);min-height:100vh;font-size:15px}  
.topbar{background:var(--ink);color:#fff;display:flex;align-items:center;justify-content:space-between;padding:0 20px;height:60px;position:sticky;top:0;z-index:100;box-shadow:0 2px 12px rgba(0,0,0,.18);gap:12px}  
.topbar-brand{font-family:'Prompt',sans-serif;font-size:18px;font-weight:700;white-space:nowrap;display:flex;align-items:center;gap:6px}  
.topbar-brand span.dot{color:var(--accent)}  
.topbar-center{flex:1;display:flex;justify-content:center}  
.branch-sel{background:rgba(255,255,255,.12);border:1.5px solid rgba(255,255,255,.25);color:#fff;font-family:'Sarabun',sans-serif;font-size:14px;font-weight:600;padding:6px 14px;border-radius:20px;cursor:pointer;outline:none;min-width:190px;text-align:center}  
.branch-sel option{background:var(--ink)}  
.topbar-nav{display:flex;gap:6px;white-space:nowrap}  
.nav-btn{background:none;border:none;color:rgba(255,255,255,.65);font-family:'Sarabun',sans-serif;font-size:14px;font-weight:500;padding:6px 14px;border-radius:20px;cursor:pointer;transition:all .2s}  
.nav-btn:hover,.nav-btn.active{background:rgba(255,255,255,.12);color:#fff}  
.nav-btn.active{background:var(--accent)!important;color:#fff!important}  
/* SYNC STATUS */  
.sync-bar{background:#0f3460;color:rgba(255,255,255,.8);font-size:12px;text-align:center;padding:4px 16px;display:flex;align-items:center;justify-content:center;gap:8px}  
.sync-dot{width:8px;height:8px;border-radius:50%;background:var(--success);display:inline-block}  
.sync-dot.syncing{background:var(--gold);animation:pulse 1s infinite}  
.sync-dot.error{background:var(--danger)}  
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}  
/* SETUP BANNER */  
.setup-banner{background:linear-gradient(135deg,#fef3c7,#fff);border:2px solid #fcd34d;border-radius:var(--radius);padding:20px 22px;margin-bottom:20px}  
/* PAGES */  
.page{display:none;padding:24px;max-width:1100px;margin:0 auto}  
.page.active{display:block;animation:fadeUp .3s ease}  
@keyframes fadeUp{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}  
/* HERO */  
.clock-hero{background:linear-gradient(135deg,var(--ink) 0%,var(--mid) 100%);border-radius:20px;color:#fff;padding:36px;margin-bottom:20px;position:relative;overflow:hidden}  
.clock-hero::after{content:'';position:absolute;right:-60px;top:-60px;width:260px;height:260px;border-radius:50%;background:rgba(255,255,255,.04)}  
.clock-hero::before{content:'';position:absolute;right:60px;bottom:-80px;width:180px;height:180px;border-radius:50%;background:rgba(233,69,96,.12)}  
.clock-time{font-family:'Prompt',sans-serif;font-size:52px;font-weight:700;letter-spacing:2px;line-height:1;margin-bottom:4px}  
.clock-date{font-size:15px;opacity:.7;margin-bottom:6px}  
.ph-today{display:none;background:rgba(245,166,35,.2);border:1px solid rgba(245,166,35,.5);color:#fde68a;font-size:13px;font-weight:600;padding:4px 12px;border-radius:20px;margin-bottom:10px;width:fit-content}  
.clock-actions{display:flex;gap:12px;flex-wrap:wrap;margin-top:14px}  
.branch-badge-hero{display:none;background:rgba(0,180,216,.18);border:1px solid rgba(0,180,216,.4);color:var(--teal);font-size:12px;font-weight:700;padding:3px 10px;border-radius:20px;margin-bottom:8px;width:fit-content}  
.btn{display:inline-flex;align-items:center;gap:8px;padding:10px 22px;border-radius:8px;border:none;font-family:'Sarabun',sans-serif;font-size:15px;font-weight:600;cursor:pointer;transition:all .2s;white-space:nowrap}  
.btn-primary{background:var(--accent);color:#fff}.btn-primary:hover{background:#c73352;transform:translateY(-1px)}  
.btn-outline{background:transparent;border:1.5px solid rgba(255,255,255,.35);color:#fff}.btn-outline:hover{background:rgba(255,255,255,.1)}  
.btn-success{background:var(--success);color:#fff}.btn-success:hover{background:#059669}  
.btn-danger{background:var(--danger);color:#fff}.btn-danger:hover{background:#dc2626}  
.btn-dark{background:var(--ink);color:#fff}.btn-dark:hover{background:#0f0f1a}  
.btn-teal{background:var(--teal);color:#fff}.btn-teal:hover{background:#0096b5}  
.btn-gold{background:var(--gold);color:#fff}.btn-gold:hover{background:#d4891c}  
.btn-ghost{background:rgba(0,0,0,.06);color:var(--ink);border:none}.btn-ghost:hover{background:rgba(0,0,0,.1)}  
.btn-sm{padding:5px 12px;font-size:12px}  
.card{background:var(--surface);border-radius:var(--radius);box-shadow:var(--shadow);padding:20px 22px;margin-bottom:18px}  
.card-title{font-family:'Prompt',sans-serif;font-size:16px;font-weight:600;color:var(--deep);margin-bottom:14px;display:flex;align-items:center;gap:8px}  
.select-emp{background:var(--surface);border-radius:var(--radius);padding:20px 22px;box-shadow:var(--shadow);margin-bottom:18px}  
.select-emp>label{display:block;font-weight:600;margin-bottom:10px;font-size:15px;color:var(--deep)}  
.emp-cards{display:flex;gap:12px;flex-wrap:wrap}  
.emp-card{border:2px solid var(--border);border-radius:10px;padding:12px 18px;cursor:pointer;transition:all .2s;text-align:center;min-width:120px;background:var(--pale)}  
.emp-card:hover{border-color:var(--teal);background:#e8f8fc}.emp-card.selected{border-color:var(--accent);background:#fff0f3}  
.emp-avatar{width:40px;height:40px;border-radius:50%;background:linear-gradient(135deg,var(--mid),var(--teal));color:#fff;font-family:'Prompt',sans-serif;font-size:16px;font-weight:700;display:flex;align-items:center;justify-content:center;margin:0 auto 7px}  
.emp-name{font-weight:600;font-size:13px}  
.comm-card{background:linear-gradient(135deg,#fff7ed,#fff);border:2px solid #fed7aa;border-radius:var(--radius);padding:20px 22px;margin-bottom:18px}  
.send-card{background:linear-gradient(135deg,#f0f9ff,#fff);border:2px solid #bae6fd;border-radius:var(--radius);padding:20px 22px;margin-bottom:18px}  
.stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:12px;margin-bottom:18px}  
.stat-card{background:var(--surface);border-radius:var(--radius);padding:14px;box-shadow:var(--shadow);text-align:center;border-top:4px solid var(--border);transition:transform .2s}  
.stat-card:hover{transform:translateY(-2px)}  
.stat-card.c1{border-top-color:var(--teal)}.stat-card.c2{border-top-color:var(--gold)}.stat-card.c3{border-top-color:var(--accent)}.stat-card.c4{border-top-color:#8b5cf6}.stat-card.c5{border-top-color:var(--success)}  
.stat-num{font-family:'Prompt',sans-serif;font-size:24px;font-weight:700;color:var(--ink)}  
.stat-label{font-size:11px;color:var(--muted);margin-top:3px;font-weight:500}  
.table-wrap{overflow-x:auto;border-radius:10px}  
table{width:100%;border-collapse:collapse;font-size:13px}  
thead tr{background:var(--ink);color:#fff}  
thead th{padding:10px 12px;text-align:left;font-weight:600;white-space:nowrap;font-size:12px}  
tbody tr{border-bottom:1px solid var(--border);transition:background .15s}  
tbody tr:hover{background:#f8faff}td{padding:9px 12px;vertical-align:middle}  
.badge{display:inline-block;padding:2px 9px;border-radius:20px;font-size:11px;font-weight:600;white-space:nowrap}  
.badge-normal{background:#e0f2fe;color:#0369a1}.badge-ot{background:#fef3c7;color:#b45309}  
.badge-holiday{background:#fce7f3;color:#9d174d}.badge-ph{background:#ede9fe;color:#5b21b6}  
.badge-hw{background:#fff7ed;color:#c2410c}.badge-commission{background:#d1fae5;color:#065f46}  
.badge-in{background:#d1fae5;color:#065f46}.badge-out{background:#fee2e2;color:#991b1b}  
.badge-phday{background:#fef3c7;color:#92400e}  
.badge-pending{background:#fef9c3;color:#854d0e}.badge-sent{background:#dcfce7;color:#166534}  
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:12px}  
.form-row.full{grid-template-columns:1fr}.form-row.three{grid-template-columns:1fr 1fr 1fr}  
.form-group{display:flex;flex-direction:column;gap:4px}  
.form-group label{font-size:12px;font-weight:600;color:var(--deep)}  
.form-group input,.form-group select{border:1.5px solid var(--border);border-radius:8px;padding:8px 11px;font-family:'Sarabun',sans-serif;font-size:14px;color:var(--ink);background:var(--pale);transition:border .2s;outline:none}  
.form-group input:focus,.form-group select:focus{border-color:var(--teal);background:#fff}  
input.big-num{font-size:22px;font-family:'Prompt',sans-serif;font-weight:700;text-align:center;padding:12px}  
.tab-row{display:flex;gap:6px;margin-bottom:20px;flex-wrap:wrap}  
.tab-btn{border:none;background:var(--border);border-radius:8px;padding:7px 16px;cursor:pointer;font-family:'Sarabun',sans-serif;font-size:13px;font-weight:600;color:var(--muted);transition:all .2s}  
.tab-btn:hover{background:#cdd4e0;color:var(--ink)}.tab-btn.active{background:var(--ink);color:#fff}  
.tab-content{display:none}.tab-content.active{display:block}  
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:200;align-items:center;justify-content:center;backdrop-filter:blur(4px)}  
.modal-overlay.open{display:flex;animation:fadeIn .2s}  
@keyframes fadeIn{from{opacity:0}to{opacity:1}}  
.modal{background:var(--surface);border-radius:16px;padding:26px 28px;width:100%;max-width:500px;box-shadow:var(--shadow-lg);animation:slideUp .25s ease;margin:16px}  
.modal.wide{max-width:660px}  
@keyframes slideUp{from{transform:translateY(30px);opacity:0}to{transform:translateY(0);opacity:1}}  
.modal-title{font-family:'Prompt',sans-serif;font-size:18px;font-weight:700;color:var(--deep);margin-bottom:18px}  
.modal-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:18px}  
.filter-row{display:flex;gap:10px;flex-wrap:wrap;align-items:flex-end;margin-bottom:16px}  
.filter-row .form-group{min-width:130px}  
.section-title{font-family:'Prompt',sans-serif;font-size:22px;font-weight:700;color:var(--deep);margin-bottom:4px}  
.section-sub{font-size:13px;color:var(--muted);margin-bottom:20px}  
.info-box{background:#f0fdf4;border:1.5px solid #86efac;border-radius:8px;padding:9px 13px;font-size:12px;color:#166534;margin-bottom:12px;line-height:1.7;display:none}  
.ph-warning{background:#fffbeb;border:1.5px solid #fcd34d;border-radius:8px;padding:9px 13px;font-size:12px;color:#92400e;margin-bottom:12px;display:none}  
/* PIN */  
.pin-screen{position:fixed;inset:0;background:var(--ink);display:flex;align-items:center;justify-content:center;z-index:500;flex-direction:column;gap:16px}  
.pin-screen.hidden{display:none}  
.pin-logo{font-family:'Prompt',sans-serif;font-size:28px;font-weight:700;color:#fff}  
.pin-logo span{color:var(--accent)}  
.pin-sub{color:rgba(255,255,255,.5);font-size:14px}  
.pin-input{width:200px;background:rgba(255,255,255,.1);border:2px solid rgba(255,255,255,.2);border-radius:12px;color:#fff;font-family:'Prompt',sans-serif;font-size:28px;font-weight:700;letter-spacing:12px;text-align:center;padding:14px;outline:none;transition:border .2s}  
.pin-input:focus{border-color:var(--teal)}.pin-input.error{border-color:var(--accent);animation:shake .3s}  
@keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-8px)}75%{transform:translateX(8px)}}  
.pin-btn{background:var(--teal);color:#fff;border:none;border-radius:10px;padding:12px 36px;font-family:'Prompt',sans-serif;font-size:16px;font-weight:700;cursor:pointer}  
.pin-btn:hover{background:#0096b5;transform:translateY(-1px)}  
.pin-error{color:var(--accent);font-size:13px;font-weight:600;height:20px;text-align:center}  
/* LOADING */  
.loading-spinner{display:inline-block;width:18px;height:18px;border:2.5px solid rgba(255,255,255,.3);border-top-color:#fff;border-radius:50%;animation:spin .8s linear infinite;vertical-align:middle;margin-right:6px}  
@keyframes spin{to{transform:rotate(360deg)}}  
/* SUMMARY */  
.summary-report{background:#fff;border-radius:var(--radius);padding:22px;border:2px solid var(--border)}  
.summary-report-header{text-align:center;margin-bottom:18px;padding-bottom:14px;border-bottom:2px solid var(--border)}  
.sum-total-box{background:linear-gradient(135deg,var(--ink),var(--mid));color:#fff;border-radius:10px;padding:16px 20px;text-align:center;margin-top:16px}  
.sum-total-box .amount{font-family:'Prompt',sans-serif;font-size:30px;font-weight:700}  
.ph-row{background:#fffbeb!important}  
/* SETUP STEPS */  
.step{display:flex;gap:14px;margin-bottom:16px;align-items:flex-start}  
.step-num{width:28px;height:28px;border-radius:50%;background:var(--teal);color:#fff;font-family:'Prompt',sans-serif;font-weight:700;font-size:14px;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:2px}  
.step-body{flex:1}  
.step-title{font-weight:700;color:var(--deep);margin-bottom:3px}  
.step-desc{font-size:13px;color:var(--muted);line-height:1.6}  
code{background:#f1f5f9;padding:2px 7px;border-radius:5px;font-size:12px;font-family:monospace;color:var(--accent)}  
#toast{position:fixed;bottom:24px;right:24px;background:var(--ink);color:#fff;padding:11px 20px;border-radius:10px;font-size:14px;font-weight:600;box-shadow:var(--shadow-lg);z-index:999;display:none}  
#toast.show{display:block;animation:fadeUp .3s ease}  
#toast.success{background:var(--success)}#toast.error{background:var(--danger)}  
.empty-state{text-align:center;padding:36px 20px;color:var(--muted)}  
.empty-state .ei{font-size:38px;margin-bottom:8px}  
@media(max-width:640px){  
  .page{padding:14px}.clock-time{font-size:36px}  
  .form-row,.form-row.three{grid-template-columns:1fr}  
  .stats-row{grid-template-columns:repeat(2,1fr)}  
  .topbar{padding:0 12px;gap:8px}.topbar-brand{font-size:15px}  
}  
</style>  
</head>  
<body>  
  
<!-- PIN -->  
  
<div class="pin-screen hidden" id="pinScreen">  
  <div class="pin-logo">☕ Coffee<span>Today</span></div>  
  <div class="pin-sub">🔐 ระบบฝ่ายบุคคล</div>  
  <input class="pin-input" id="pinInput" type="password" maxlength="4" placeholder="••••"  
    oninput="document.getElementById('pinError').textContent='';this.classList.remove('error')"  
    onkeydown="if(event.key==='Enter')checkPin()">  
  <div class="pin-error" id="pinError"></div>  
  <button class="pin-btn" onclick="checkPin()">เข้าสู่ระบบ HR</button>  
</div>  
  
<!-- TOPBAR -->  
  
<div class="topbar">  
  <div class="topbar-brand">☕ Coffee<span class="dot">Today</span></div>  
  <div class="topbar-center">  
    <select id="branchSelect" onchange="onBranchChange()" class="branch-sel">  
      <option value="">— เลือกสาขา —</option>  
      <option value="lotus">สาขาโลตัสระยอง</option>  
      <option value="passion">สาขาแพชชั่นระยอง</option>  
    </select>  
  </div>  
  <div class="topbar-nav">  
    <button class="nav-btn active" id="navClock" onclick="showPage('clock',this)">🕐 บันทึก</button>  
    <button class="nav-btn" id="navHR" onclick="requireHRPin(this)">🗂 HR</button>  
  </div>  
</div>  
<div class="sync-bar" id="syncBar">  
  <span class="sync-dot" id="syncDot"></span>  
  <span id="syncText">กำลังเชื่อมต่อ...</span>  
</div>  
  
<!-- PAGE: EMPLOYEE -->  
  
<div class="page active" id="page-clock">  
  
  <!-- SETUP BANNER (shown when no API URL set) -->  
  
  <div class="setup-banner" id="setupBanner" style="display:none">  
    <div style="font-family:'Prompt',sans-serif;font-size:17px;font-weight:700;color:#92400e;margin-bottom:14px">⚙️ ตั้งค่าการเชื่อมต่อ Google Sheets</div>  
    <div class="step">  
      <div class="step-num">1</div>  
      <div class="step-body">  
        <div class="step-title">สร้าง Google Sheet ใหม่</div>  
        <div class="step-desc">เปิด <a href="https://sheets.google.com" target="_blank" style="color:var(--teal)">sheets.google.com</a> แล้วสร้าง Spreadsheet ว่างๆ ตั้งชื่อว่า "Coffee Today Attendance"</div>  
      </div>  
    </div>  
    <div class="step">  
      <div class="step-num">2</div>  
      <div class="step-body">  
        <div class="step-title">เปิด Apps Script</div>  
        <div class="step-desc">ในเมนู <strong>Extensions → Apps Script</strong> จากนั้นลบโค้ดเดิมออกแล้ววางโค้ดจากไฟล์ <code>Code.gs</code> แทน</div>  
      </div>  
    </div>  
    <div class="step">  
      <div class="step-num">3</div>  
      <div class="step-body">  
        <div class="step-title">Deploy เป็น Web App</div>  
        <div class="step-desc">กด <strong>Deploy → New deployment</strong> เลือก Type = <strong>Web app</strong>, Execute as = <strong>Me</strong>, Who has access = <strong>Anyone</strong> แล้วกด Deploy</div>  
      </div>  
    </div>  
    <div class="step">  
      <div class="step-num">4</div>  
      <div class="step-body">  
        <div class="step-title">วาง URL ด้านล่าง</div>  
        <div class="step-desc">Copy "Web app URL" ที่ได้มา แล้ววางในช่องด้านล่าง</div>  
      </div>  
    </div>  
    <div style="display:flex;gap:10px;align-items:center;margin-top:4px;flex-wrap:wrap">  
      <input type="text" id="apiUrlInput" placeholder="https://script.google.com/macros/s/xxxxx/exec"  
        style="flex:1;min-width:250px;border:2px solid #fcd34d;border-radius:8px;padding:10px 12px;font-family:'Sarabun',sans-serif;font-size:13px;background:#fffbeb;outline:none">  
      <button class="btn btn-gold" onclick="saveApiUrl()">💾 บันทึก URL</button>  
    </div>  
  </div>  
  
  <div class="clock-hero">  
    <div class="branch-badge-hero" id="heroBranchBadge">📍 <span id="heroBranchName"></span></div>  
    <div class="clock-time" id="liveClock">--:--:--</div>  
    <div class="clock-date" id="liveDate">--</div>  
    <div class="ph-today" id="phToday"></div>  
    <div class="clock-actions">  
      <button class="btn btn-primary" onclick="openClockModal('in')">✅ เข้างาน</button>  
      <button class="btn btn-outline" onclick="openClockModal('out')">🚪 ออกงาน</button>  
    </div>  
  </div>  
  
  <div class="select-emp">  
    <label>👤 เลือกพนักงาน</label>  
    <div class="emp-cards" id="empCards"></div>  
  </div>  
  
  <div class="comm-card" id="commCard" style="display:none">  
    <div class="card-title" style="color:#c2410c">🧾 บันทึกยอดขาย (คำนวณค่าคอมอัตโนมัติ)</div>  
    <div id="commTierInfo" style="font-size:12px;color:#92400e;background:#fff7ed;border-radius:8px;padding:10px 12px;margin-bottom:14px;line-height:2"></div>  
    <div class="form-row">  
      <div class="form-group"><label>วันที่ (บันทึกย้อนหลังได้)</label><input type="date" id="commDate"></div>  
      <div class="form-group"><label>ยอดขาย (฿)</label><input type="number" id="commSales" class="big-num" placeholder="0" min="0" oninput="onSalesInput()"></div>  
    </div>  
    <div id="commCalcResult" style="display:none;background:#f0fdf4;border:2px solid #86efac;border-radius:10px;padding:14px;margin-bottom:14px">  
      <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;text-align:center;margin-bottom:10px">  
        <div style="background:#fff;border-radius:8px;padding:8px 4px">  
          <div style="font-size:11px;color:var(--muted)">ยอดขาย</div>  
          <div style="font-family:'Prompt',sans-serif;font-size:18px;font-weight:700;color:var(--ink)">฿<span id="commSalesDisplay">0</span></div>  
        </div>  
        <div style="background:#fff;border-radius:8px;padding:8px 4px">  
          <div style="font-size:11px;color:var(--muted)">− ยอดขั้นต่ำ tier</div>  
          <div style="font-family:'Prompt',sans-serif;font-size:18px;font-weight:700;color:var(--danger)">฿<span id="commMinDisplay">0</span></div>  
        </div>  
        <div style="background:#fff;border-radius:8px;padding:8px 4px">  
          <div style="font-size:11px;color:var(--muted)">= ส่วนต่าง</div>  
          <div style="font-family:'Prompt',sans-serif;font-size:18px;font-weight:700;color:var(--mid)">฿<span id="commDiffDisplay">0</span></div>  
        </div>  
      </div>  
      <div style="text-align:center;border-top:1px solid #bbf7d0;padding-top:10px">  
        <span style="font-size:13px;color:var(--muted)">ส่วนต่าง × <strong id="commRateDisplay">0%</strong> =</span>  
        <div style="font-family:'Prompt',sans-serif;font-size:32px;font-weight:700;color:var(--success);margin-top:2px">฿<span id="commAmountDisplay">0</span></div>  
        <div style="font-size:11px;color:var(--muted);margin-top:2px" id="commCalcFormula"></div>  
      </div>  
    </div>  
    <div id="commNoTier" style="display:none;background:#fef9c3;border:1.5px solid #fcd34d;border-radius:8px;padding:10px 12px;font-size:13px;color:#854d0e;margin-bottom:14px">⚠️ ยอดขายยังไม่ถึงขั้นต่ำสำหรับค่าคอมมิชชั่น</div>  
    <div class="form-row full"><div class="form-group"><label>หมายเหตุ</label><input type="text" id="commNote" placeholder="หมายเหตุ..."></div></div>  
    <button class="btn btn-gold" onclick="saveCommission()">💰 บันทึกยอดขาย</button>  
  </div>  
  
  <div class="send-card" id="sendHRCard" style="display:none">  
    <div class="card-title" style="color:#0369a1">📤 ส่งสรุปให้ฝ่ายบุคคล</div>  
    <p style="font-size:13px;color:var(--muted);margin-bottom:14px">ส่งสรุปชั่วโมงทำงาน ค่าล่วงเวลา และค่าคอมมิชชั่นให้ HR ตรวจสอบ</p>  
    <div class="form-group" style="max-width:300px;margin-bottom:14px">  
      <label>เลือกรอบเงินเดือน</label>  
      <select id="empSendPeriod"></select>  
    </div>  
    <button class="btn btn-teal" onclick="openSendSummaryModal()">📋 ดูสรุปและส่งให้ HR</button>  
  </div>  
  
  <div class="card">  
    <div class="card-title">📋 บันทึกการเข้างานของฉัน</div>  
    <div class="table-wrap">  
      <table>  
        <thead><tr><th>วันที่</th><th>สาขา</th><th>เข้า</th><th>ออก</th><th>ชม.ปกติ</th><th>OT</th><th>ประเภท</th><th>ยอดขาย/คอม</th><th>หมายเหตุ</th></tr></thead>  
        <tbody id="myLogTable"><tr><td colspan="9" style="text-align:center;padding:20px;color:var(--muted)">กำลังโหลด...</td></tr></tbody>  
      </table>  
    </div>  
  </div>  
</div>  
  
<!-- PAGE: HR -->  
  
<div class="page" id="page-hr">  
  <div style="display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;margin-bottom:4px">  
    <div class="section-title">🗂 ระบบฝ่ายบุคคล</div>  
    <button class="btn btn-ghost btn-sm" onclick="logoutHR()">🔒 ออกจากระบบ HR</button>  
  </div>  
  <div class="section-sub">Coffee Today — จัดการพนักงาน บันทึกเวลา และสรุปเงินเดือน</div>  
  <div class="tab-row">  
    <button class="tab-btn active" onclick="showTab('dashboard',this)">📊 Dashboard</button>  
    <button class="tab-btn" onclick="showTab('allLogs',this)">📋 บันทึกทั้งหมด</button>  
    <button class="tab-btn" onclick="showTab('summary',this)">💰 สรุปรายรอบ</button>  
    <button class="tab-btn" onclick="showTab('submissions',this)">📬 รับสรุปจากพนักงาน</button>  
    <button class="tab-btn" onclick="showTab('employees',this)">👥 พนักงาน</button>  
    <button class="tab-btn" onclick="showTab('manual',this)">✏️ บันทึกเอง</button>  
    <button class="tab-btn" onclick="showTab('holidays',this)">📅 วันหยุด</button>  
  </div>  
  
  <div class="tab-content active" id="tab-dashboard">  
    <div id="statsRow" class="stats-row"></div>  
    <div class="card"><div class="card-title">📈 สรุปพนักงานแต่ละคน (รอบปัจจุบัน)</div>  
      <div class="table-wrap"><table>  
        <thead><tr><th>พนักงาน</th><th>สาขา</th><th>ชม.ปกติ</th><th>OT</th><th>OT วันหยุด</th><th>วันหยุด×2</th><th>ยอดขายรวม</th><th>คอมมิชชั่น</th><th>วันทำงาน</th></tr></thead>  
        <tbody id="empSummaryTable"></tbody>  
      </table></div>  
    </div>  
  </div>  
  
  <div class="tab-content" id="tab-allLogs">  
    <div class="filter-row">  
      <div class="form-group"><label>สาขา</label><select id="filterBranch" onchange="renderAllLogs()"><option value="">ทั้งหมด</option><option value="lotus">โลตัสระยอง</option><option value="passion">แพชชั่นระยอง</option></select></div>  
      <div class="form-group"><label>พนักงาน</label><select id="filterEmp" onchange="renderAllLogs()"><option value="">ทั้งหมด</option></select></div>  
      <div class="form-group"><label>รอบเงินเดือน</label><select id="filterPayPeriod" onchange="renderAllLogs()"><option value="">ทั้งหมด</option></select></div>  
    </div>  
    <div class="card"><div class="card-title">📋 รายการบันทึกเวลา</div>  
      <div class="table-wrap"><table>  
        <thead><tr><th>วันที่</th><th>สาขา</th><th>พนักงาน</th><th>เข้า</th><th>ออก</th><th>ชม.</th><th>OT</th><th>ประเภท</th><th>ยอดขาย/คอม</th><th>หมายเหตุ</th><th>ลบ</th></tr></thead>  
        <tbody id="allLogsTable"></tbody>  
      </table></div>  
    </div>  
  </div>  
  
  <div class="tab-content" id="tab-summary">  
    <div class="filter-row">  
      <div class="form-group"><label>รอบเงินเดือน</label><select id="summaryPayPeriod" onchange="renderSummary()"><option value="">เลือกรอบ...</option></select></div>  
      <div class="form-group"><label>สาขา</label><select id="summaryBranch" onchange="renderSummary()"><option value="">ทั้งหมด</option><option value="lotus">โลตัสระยอง</option><option value="passion">แพชชั่นระยอง</option></select></div>  
      <div class="form-group"><label>พนักงาน</label><select id="summaryEmp" onchange="renderSummary()"><option value="">ทั้งหมด</option></select></div>  
    </div>  
    <div id="summaryCards"></div>  
  </div>  
  
  <div class="tab-content" id="tab-submissions">  
    <div class="card"><div class="card-title">📬 สรุปที่พนักงานส่งมา</div>  
      <div class="table-wrap"><table>  
        <thead><tr><th>วันที่ส่ง</th><th>พนักงาน</th><th>สาขา</th><th>รอบ</th><th>ชม.</th><th>OT</th><th>คอมมิชชั่น</th><th>สถานะ</th><th>จัดการ</th></tr></thead>  
        <tbody id="submissionsTable"></tbody>  
      </table></div>  
    </div>  
  </div>  
  
  <div class="tab-content" id="tab-employees">  
    <div style="margin-bottom:14px"><button class="btn btn-primary" onclick="openAddEmpModal()">➕ เพิ่มพนักงาน</button></div>  
    <div class="card"><div class="card-title">👥 รายชื่อพนักงาน</div>  
      <div class="table-wrap"><table>  
        <thead><tr><th>ชื่อ</th><th>สาขา</th><th>ตำแหน่ง</th><th>เงินเดือน</th><th>ค่าแรงวันหยุด/วัน×2</th><th>OT/ชม</th><th>OT วันหยุด/ชม</th><th>สถานะ</th><th>จัดการ</th></tr></thead>  
        <tbody id="empTable"></tbody>  
      </table></div>  
    </div>  
  </div>  
  
  <div class="tab-content" id="tab-manual">  
    <div class="card"><div class="card-title">✏️ บันทึกเวลาด้วยตนเอง (HR)</div>  
      <div class="form-row">  
        <div class="form-group"><label>พนักงาน *</label><select id="manEmp"></select></div>  
        <div class="form-group"><label>สาขา *</label><select id="manBranch"><option value="lotus">โลตัสระยอง</option><option value="passion">แพชชั่นระยอง</option></select></div>  
      </div>  
      <div class="form-row full"><div class="form-group"><label>วันที่ *</label><input type="date" id="manDate"></div></div>  
      <div class="form-row">  
        <div class="form-group"><label>เข้างาน *</label><input type="time" id="manIn"></div>  
        <div class="form-group"><label>ออกงาน</label><input type="time" id="manOut"></div>  
      </div>  
      <div class="form-row">  
        <div class="form-group"><label>ประเภท</label>  
          <select id="manType"><option value="normal">ปกติ (ตัด OT อัตโนมัติ)</option><option value="holiday_ot">OT วันหยุด</option><option value="public_holiday">วันนักขัตฤกษ์</option><option value="holiday_work">ทำงานวันหยุด ×2</option></select></div>  
        <div class="form-group"><label>ยอดขาย (฿) สำหรับคอม</label><input type="number" id="manSales" placeholder="0" min="0"></div>  
      </div>  
      <div class="form-row full"><div class="form-group"><label>หมายเหตุ</label><input type="text" id="manNote" placeholder="หมายเหตุ..."></div></div>  
      <button class="btn btn-success" onclick="saveManual()">💾 บันทึก</button>  
    </div>  
  </div>  
  
  <div class="tab-content" id="tab-holidays">  
    <div class="card"><div class="card-title">📅 วันหยุดนักขัตฤกษ์ ปี 2569</div>  
      <p style="font-size:13px;color:var(--muted);margin-bottom:14px">อ้างอิงจากประกาศสำนักงาน อัปเดต 05/01/69</p>  
      <div class="table-wrap"><table>  
        <thead><tr><th>#</th><th>วันที่</th><th>วันหยุด</th></tr></thead>  
        <tbody id="phTable"></tbody>  
      </table></div>  
    </div>  
  </div>  
</div>  
  
<!-- MODALS -->  
  
<div class="modal-overlay" id="clockModal">  
  <div class="modal">  
    <div class="modal-title" id="clockModalTitle">บันทึกเวลา</div>  
    <div class="form-row full"><div class="form-group"><label>พนักงาน *</label><select id="modalEmp" onchange="onModalEmpChange()"></select></div></div>  
    <div class="ph-warning" id="phWarning">⚠️ วันนี้เป็นวันหยุดนักขัตฤกษ์: <strong id="phWarningName"></strong></div>  
    <div class="info-box" id="clockInfoBox"></div>  
    <div class="form-row full"><div class="form-group"><label>หมายเหตุ</label><input type="text" id="modalNote" placeholder="ไม่บังคับ..."></div></div>  
    <div class="modal-actions">  
      <button class="btn btn-ghost" onclick="closeModal('clockModal')">ยกเลิก</button>  
      <button class="btn btn-primary" id="clockModalBtn" onclick="submitClock()">บันทึก</button>  
    </div>  
  </div>  
</div>  
  
<div class="modal-overlay" id="addEmpModal">  
  <div class="modal">  
    <div class="modal-title" id="addEmpTitle">เพิ่มพนักงานใหม่</div>  
    <input type="hidden" id="editEmpId">  
    <div class="form-row">  
      <div class="form-group"><label>ชื่อ-นามสกุล *</label><input type="text" id="newEmpName" placeholder="ชื่อพนักงาน"></div>  
      <div class="form-group"><label>สาขาประจำ</label><select id="newEmpBranch"><option value="lotus">โลตัสระยอง</option><option value="passion">แพชชั่นระยอง</option></select></div>  
    </div>  
    <div class="form-row">  
      <div class="form-group"><label>ตำแหน่ง</label><input type="text" id="newEmpRole" placeholder="เช่น พนักงาน"></div>  
      <div class="form-group"><label>เงินเดือนฐาน (฿)</label><input type="number" id="newEmpSalary" placeholder="0"></div>  
    </div>  
    <div class="form-row three">  
      <div class="form-group"><label>ค่าแรงวันหยุด/วัน <span style="color:var(--accent);font-size:10px">×2</span></label><input type="number" id="newEmpDailyWage" placeholder="500"></div>  
      <div class="form-group"><label>OT ปกติ/ชม (฿)</label><input type="number" id="newEmpOTRate" placeholder="50"></div>  
      <div class="form-group"><label>OT วันหยุด/ชม (฿)</label><input type="number" id="newEmpHolidayRate" placeholder="100"></div>  
    </div>  
    <div class="modal-actions">  
      <button class="btn btn-ghost" onclick="closeModal('addEmpModal')">ยกเลิก</button>  
      <button class="btn btn-success" onclick="saveEmployee()">💾 บันทึก</button>  
    </div>  
  </div>  
</div>  
  
<div class="modal-overlay" id="sendSummaryModal">  
  <div class="modal wide">  
    <div class="modal-title">📤 ดูสรุปและส่งให้ฝ่ายบุคคล</div>  
    <div id="sendSummaryContent"></div>  
    <div class="modal-actions">  
      <button class="btn btn-ghost" onclick="closeModal('sendSummaryModal')">ยกเลิก</button>  
      <button class="btn btn-teal" onclick="confirmSendSummary()">✅ ยืนยันส่ง</button>  
    </div>  
  </div>  
</div>  
  
<div class="modal-overlay" id="viewSubmissionModal">  
  <div class="modal wide">  
    <div class="modal-title">📋 รายละเอียดสรุปที่ส่งมา</div>  
    <div id="viewSubmissionContent"></div>  
    <div class="modal-actions">  
      <button class="btn btn-ghost" onclick="closeModal('viewSubmissionModal')">ปิด</button>  
    </div>  
  </div>  
</div>  
  
<div id="toast"></div>  
  
<script>  
// ============================================================  
//  CONFIG — ใส่ URL ของ Apps Script Web App ที่นี่  
// ============================================================  
let API_URL = 'https://script.google.com/macros/s/AKfycbw4fXghaBjjU_9PvBCFmI14kGROL_rWOp-AyqJ09HAtzZZz6EgXtWf5SY-5rukLJnoyfA/exec';  
localStorage.setItem('ct_api_url', API_URL);  
  
// ============================================================  
//  PUBLIC HOLIDAYS 2569  
// ============================================================  
const PH=[  
  {date:'2026-01-01',name:'วันขึ้นปีใหม่'},{date:'2026-03-03',name:'วันมาฆบูชา'},  
  {date:'2026-04-13',name:'วันสงกรานต์'},{date:'2026-04-14',name:'วันสงกรานต์'},{date:'2026-04-15',name:'วันสงกรานต์'},  
  {date:'2026-05-01',name:'วันแรงงานแห่งชาติ'},{date:'2026-06-01',name:'ชดเชยวันวิสาขบูชา'},  
  {date:'2026-06-03',name:'วันเฉลิมฯ พระบรมราชินี'},{date:'2026-07-28',name:'วันเฉลิมพระชนมพรรษา ร.10'},  
  {date:'2026-07-29',name:'วันอาสาฬหบูชา'},{date:'2026-08-12',name:'วันแม่แห่งชาติ'},  
  {date:'2026-10-13',name:'วันคล้ายวันสวรรคต ร.9'},{date:'2026-12-05',name:'วันคล้ายวันพระบรมราชสมภพ ร.9'},  
  {date:'2026-12-31',name:'วันสิ้นปี'}  
];  
function getPH(d){return PH.find(h=>h.date===d)||null;}  
  
// ============================================================  
//  STATE (in-memory cache, synced from Sheets)  
// ============================================================  
let employees=[],logs=[],submissions=[];  
let selectedEmpId=null,clockAction='in',currentBranch=localStorage.getItem('ct_branch')||'',hrUnlocked=false;  
const BRANCHES={lotus:'โลตัสระยอง',passion:'แพชชั่นระยอง'};  
const OT_THRESHOLD=8,HR_PIN='9999';  
const COMM_TIERS={  
  lotus:[{min:6000,rate:.08,label:'8%'},{min:3500,rate:.04,label:'4%'},{min:2500,rate:.02,label:'2%'}],  
  passion:[{min:5000,rate:.08,label:'8%'},{min:2500,rate:.04,label:'4%'},{min:1500,rate:.02,label:'2%'}]  
};  
  
// หา tier ที่ยอดขายตกอยู่ (highest matching)  
function getCommTier(branch,sales){  
  const t=COMM_TIERS[branch]||[];  
  for(const x of t){if(sales>=x.min)return x;}  
  return null;  
}  
  
// คำนวณค่าคอม = (ยอดขาย - ยอดขั้นต่ำของ tier) × อัตรา  
function calcCommission(branch,sales){  
  const tier=getCommTier(branch,sales);  
  if(!tier)return{commission:0,tier:null,diff:0};  
  const diff=sales-tier.min;   // ส่วนต่างที่เกินจากขั้นต่ำ  
  const commission=Math.round(diff*tier.rate);  
  return{commission,tier,diff};  
}  
  
function getTierInfoHTML(branch){  
  const t=COMM_TIERS[branch];  
  if(!t)return'กรุณาเลือกสาขาก่อน';  
  const rows=[...t].reverse().map(x=>`<span style="margin-right:12px">≥฿${x.min.toLocaleString()} → ส่วนต่าง×<strong>${x.label}</strong></span>`).join('');  
  return`📊 อัตราค่าคอม${BRANCHES[branch]?'สาขา'+BRANCHES[branch]:''}: ${rows}<br><span style="font-size:11px;color:#b45309">คอมคำนวณจาก (ยอดขาย − ยอดขั้นต่ำของ tier) × อัตรา</span>`;  
}  
function genId(){return 'id'+Date.now()+Math.random().toString(36).slice(2,6);}  
  
// ============================================================  
//  API CALLS  
// ============================================================  
function setSyncStatus(state,msg){  
  const dot=document.getElementById('syncDot'),txt=document.getElementById('syncText');  
  dot.className='sync-dot'+(state==='syncing'?' syncing':state==='error'?' error':'');  
  txt.textContent=msg;  
}  
  
async function api(action,data={}){  
  if(!API_URL) throw new Error('ยังไม่ได้ตั้งค่า API URL');  
  setSyncStatus('syncing','กำลังซิงค์...');  
  try{  
    let url=API_URL+'?action='+action;  
    const isWrite=['addLog','updateLog','deleteLog','saveEmployee','deleteEmployee','addSubmission','updateSubmission'].includes(action);  
    let resp;  
    if(isWrite){  
      resp=await fetch(url,{method:'POST',body:JSON.stringify({action,...data})});  
    } else {  
      const qs=Object.entries(data).map(([k,v])=>`${k}=${encodeURIComponent(v)}`).join('&');  
      resp=await fetch(url+(qs?'&'+qs:''));  
    }  
    const json=await resp.json();  
    if(json.error) throw new Error(json.error);  
    setSyncStatus('ok','เชื่อมต่อแล้ว · '+new Date().toLocaleTimeString('th-TH'));  
    return json;  
  } catch(e){  
    setSyncStatus('error','เชื่อมต่อล้มเหลว: '+e.message);  
    throw e;  
  }  
}  
  
async function loadAll(){  
  if(!API_URL){  
    document.getElementById('setupBanner').style.display='block';  
    setSyncStatus('error','ยังไม่ได้ตั้งค่า URL');  
    return;  
  }  
  document.getElementById('setupBanner').style.display='none';  
  try{  
    const [eRes,lRes,sRes]=await Promise.all([  
      api('getEmployees'),api('getLogs'),api('getSubmissions')  
    ]);  
    employees=eRes.employees||[];  
    logs=lRes.logs||[];  
    submissions=sRes.submissions||[];  
    renderEmpCards();renderMyLog();  
  } catch(e){showToast('โหลดข้อมูลล้มเหลว: '+e.message,'error');}  
}  
  
function saveApiUrl(){  
  const v=document.getElementById('apiUrlInput').value.trim();  
  if(!v){showToast('กรุณากรอก URL','error');return;}  
  API_URL=v;localStorage.setItem('ct_api_url',v);  
  showToast('✅ บันทึก URL สำเร็จ กำลังโหลดข้อมูล...','success');  
  loadAll();  
}  
  
// ============================================================  
//  PIN  
// ============================================================  
function requireHRPin(btn){  
  if(hrUnlocked){showPage('hr',btn);return;}  
  window._hrBtn=btn;  
  document.getElementById('pinScreen').classList.remove('hidden');  
  document.getElementById('pinInput').value='';  
  document.getElementById('pinError').textContent='';  
  setTimeout(()=>document.getElementById('pinInput').focus(),120);  
}  
function checkPin(){  
  const v=document.getElementById('pinInput').value;  
  if(v===HR_PIN){hrUnlocked=true;document.getElementById('pinScreen').classList.add('hidden');showPage('hr',window._hrBtn);}  
  else{const i=document.getElementById('pinInput');i.classList.add('error');document.getElementById('pinError').textContent='รหัสไม่ถูกต้อง';i.value='';setTimeout(()=>i.classList.remove('error'),400);}  
}  
function logoutHR(){hrUnlocked=false;showPage('clock',document.getElementById('navClock'));showToast('ออกจากระบบ HR แล้ว');}  
  
// ============================================================  
//  BRANCH  
// ============================================================  
function onBranchChange(){currentBranch=document.getElementById('branchSelect').value;localStorage.setItem('ct_branch',currentBranch);updateBranchUI();renderEmpCards();}  
function updateBranchUI(){const b=document.getElementById('heroBranchBadge'),n=document.getElementById('heroBranchName');if(currentBranch&&BRANCHES[currentBranch]){b.style.display='inline-flex';n.textContent=BRANCHES[currentBranch];}else b.style.display='none';}  
function brL(b){return BRANCHES[b]||b||'—';}  
  
// ============================================================  
//  PAY PERIODS  
// ============================================================  
function getPayPeriods(){  
  const seen=new Set(),periods=[];  
  const fixed={key:'2026-03',label:'16 มี.ค. 2569 – 15 เม.ย. 2569',start:new Date(2026,2,16),end:new Date(2026,3,15)};  
  periods.push(fixed);seen.add('2026-03');  
  const now=new Date();  
  for(let i=-1;i<=13;i++){  
    const d=new Date(now.getFullYear(),now.getMonth()-i,1);  
    const y=d.getFullYear(),m=d.getMonth(),key=`${y}-${String(m+1).padStart(2,'0')}`;  
    if(seen.has(key))continue;seen.add(key);  
    const s=new Date(y,m,16),e=new Date(y,m+1,15);  
    periods.push({key,label:`${s.toLocaleDateString('th-TH',{day:'numeric',month:'short',year:'numeric'})} – ${e.toLocaleDateString('th-TH',{day:'numeric',month:'short',year:'numeric'})}`,start:s,end:e});  
  }  
  return periods.sort((a,b)=>a.start-b.start);  
}  
function getCurPPKey(){const now=new Date(),y=now.getFullYear(),m=now.getMonth(),pp=now.getDate()>=16?{start:new Date(y,m,16)}:{start:new Date(y,m-1,16)};return `${pp.start.getFullYear()}-${String(pp.start.getMonth()+1).padStart(2,'0')}`;}  
function logsInPP(key){const[y,m]=key.split('-').map(Number),s=new Date(y,m-1,16),e=new Date(y,m,15);return logs.filter(l=>{const d=new Date(l.date+'T00:00:00');return d>=s&&d<=e;});}  
function getPPLabel(key){const p=getPayPeriods().find(x=>x.key===key);return p?p.label:key;}  
function populatePPSelects(){  
  const periods=getPayPeriods(),cur=getCurPPKey();  
  const opts=periods.map(p=>`<option value="${p.key}"${p.key===cur?' selected':''}>${p.label}</option>`).join('');  
  ['filterPayPeriod','summaryPayPeriod'].forEach(id=>{const el=document.getElementById(id);if(el)el.innerHTML=opts;});  
  const ep=document.getElementById('empSendPeriod');if(ep)ep.innerHTML=opts;  
}  
  
// ============================================================  
//  CLOCK  
// ============================================================  
function updateClock(){  
  const now=new Date();  
  document.getElementById('liveClock').textContent=now.toLocaleTimeString('th-TH');  
  document.getElementById('liveDate').textContent=now.toLocaleDateString('th-TH',{weekday:'long',year:'numeric',month:'long',day:'numeric'});  
  const ph=getPH(now.toISOString().split('T')[0]),el=document.getElementById('phToday');  
  if(ph){el.style.display='inline-block';el.textContent='🎌 วันหยุดนักขัตฤกษ์: '+ph.name;}else el.style.display='none';  
}  
setInterval(updateClock,1000);updateClock();  
  
// ============================================================  
//  NAVIGATION  
// ============================================================  
function showPage(p,btn){  
  document.querySelectorAll('.page').forEach(e=>e.classList.remove('active'));  
  document.querySelectorAll('.nav-btn').forEach(e=>e.classList.remove('active'));  
  document.getElementById('page-'+p).classList.add('active');  
  if(btn)btn.classList.add('active');  
  if(p==='hr')refreshHR();  
  if(p==='clock'){renderEmpCards();renderMyLog();populatePPSelects();}  
}  
function showTab(t,btn){  
  document.querySelectorAll('.tab-btn').forEach(e=>e.classList.remove('active'));  
  document.querySelectorAll('.tab-content').forEach(e=>e.classList.remove('active'));  
  document.getElementById('tab-'+t).classList.add('active');if(btn)btn.classList.add('active');  
  if(t==='dashboard')renderDashboard();if(t==='allLogs')renderAllLogs();  
  if(t==='summary')renderSummary();if(t==='submissions')renderSubmissions();  
  if(t==='employees')renderEmpTable();if(t==='manual')populateManualForm();  
  if(t==='holidays')renderHolidayTable();  
}  
  
// ============================================================  
//  EMPLOYEES  
// ============================================================  
function renderEmpCards(){  
  const c=document.getElementById('empCards'),active=employees.filter(e=>e.active);  
  if(!active.length){c.innerHTML='<p style="color:var(--muted);font-size:13px">ยังไม่มีพนักงาน หรือยังไม่ได้ตั้งค่า API</p>';return;}  
  c.innerHTML=active.map(e=>`<div class="emp-card ${selectedEmpId===e.id?'selected':''}" onclick="selectEmp('${e.id}',this)">  
    <div class="emp-avatar">${e.name.charAt(0)}</div>  
    <div class="emp-name">${e.name}</div>  
    <div style="font-size:10px;color:var(--muted);margin-top:2px">${brL(e.branch)}</div>  
  </div>`).join('');  
}  
  
function selectEmp(id,el){  
  selectedEmpId=id;  
  document.querySelectorAll('.emp-card').forEach(c=>c.classList.remove('selected'));el.classList.add('selected');  
  document.getElementById('commCard').style.display='block';  
  document.getElementById('sendHRCard').style.display='block';  
  document.getElementById('commDate').value=new Date().toISOString().split('T')[0];  
  const emp=employees.find(e=>e.id===id);  
  document.getElementById('commTierInfo').innerHTML=getTierInfoHTML(emp?emp.branch:currentBranch);  
  document.getElementById('commSales').value='';  
  document.getElementById('commCalcResult').style.display='none';  
  document.getElementById('commNoTier').style.display='none';  
  populatePPSelects();renderMyLog();  
}  
  
// ============================================================  
//  CLOCK MODAL  
// ============================================================  
function openClockModal(action){  
  clockAction=action;  
  document.getElementById('clockModalTitle').textContent=action==='in'?'✅ บันทึกเข้างาน':'🚪 บันทึกออกงาน';  
  document.getElementById('clockModalBtn').textContent=action==='in'?'บันทึกเข้างาน':'บันทึกออกงาน';  
  populateEmpSel('modalEmp');  
  if(selectedEmpId)document.getElementById('modalEmp').value=selectedEmpId;  
  document.getElementById('modalNote').value='';  
  document.getElementById('clockInfoBox').style.display='none';  
  checkPHWarn();  
  document.getElementById('modalEmp').onchange=()=>onModalEmpChange();  
  if(action==='out')updateCOPreview();  
  openModal('clockModal');  
}  
function onModalEmpChange(){checkPHWarn();if(clockAction==='out')updateCOPreview();}  
function checkPHWarn(){const ph=getPH(new Date().toISOString().split('T')[0]),w=document.getElementById('phWarning');if(ph){w.style.display='block';document.getElementById('phWarningName').textContent=ph.name;}else w.style.display='none';}  
function updateCOPreview(){  
  const empId=document.getElementById('modalEmp').value,box=document.getElementById('clockInfoBox');  
  if(!empId){box.style.display='none';return;}  
  const ds=new Date().toISOString().split('T')[0],ts=new Date().toTimeString().slice(0,5);  
  const entry=logs.find(l=>l.empId===empId&&l.date===ds&&!l.clockOut);  
  if(!entry){box.style.display='none';return;}  
  const total=hRaw(entry.clockIn,ts),norm=Math.min(total,OT_THRESHOLD),ot=Math.max(0,total-OT_THRESHOLD);  
  box.style.display='block';  
  box.innerHTML=`เข้างาน <strong>${entry.clockIn}</strong> → ออก <strong>${ts}</strong><br>ปกติ: <strong>${norm.toFixed(2)} ชม.</strong>${ot>0?' | OT: <strong style="color:#b45309">'+ot.toFixed(2)+' ชม.</strong>':''}`;  
}  
  
async function submitClock(){  
  const empId=document.getElementById('modalEmp').value;  
  if(!empId){showToast('กรุณาเลือกพนักงาน','error');return;}  
  const now=new Date(),ds=now.toISOString().split('T')[0],ts=now.toTimeString().slice(0,5),ph=getPH(ds);  
  const btn=document.getElementById('clockModalBtn');  
  btn.innerHTML='<span class="loading-spinner"></span>กำลังบันทึก...';btn.disabled=true;  
  try{  
    if(clockAction==='in'){  
      if(logs.find(l=>l.empId===empId&&l.date===ds&&!l.clockOut)){showToast('เข้างานแล้ววันนี้','error');return;}  
      const log={id:genId(),empId,date:ds,branch:currentBranch,clockIn:ts,clockOut:'',type:ph?'public_holiday':'normal',sales:'',commission:0,commRate:0,note:document.getElementById('modalNote').value,hours:'',hoursOT:0};  
      await api('addLog',log);logs.push(log);  
      showToast('✅ บันทึกเข้างาน'+(ph?' ('+ph.name+')':''),'success');  
    } else {  
      const entry=logs.find(l=>l.empId===empId&&l.date===ds&&!l.clockOut);  
      if(!entry){showToast('ไม่พบบันทึกเข้างานวันนี้','error');return;}  
      const total=hRaw(entry.clockIn,ts);  
      const sp=['holiday_ot','public_holiday','holiday_work'].includes(entry.type);  
      const hours=sp?+total.toFixed(2):+(Math.min(total,OT_THRESHOLD).toFixed(2));  
      const hoursOT=sp?0:+(Math.max(0,total-OT_THRESHOLD).toFixed(2));  
      const type=(hoursOT>0&&!sp)?'split':entry.type;  
      const note=document.getElementById('modalNote').value;  
      await api('updateLog',{id:entry.id,clockOut:ts,hours,hoursOT,type,note});  
      Object.assign(entry,{clockOut:ts,hours,hoursOT,type,note});  
      showToast('🚪 ออกงาน'+(hoursOT>0?' (OT '+hoursOT+' ชม.)':''),'success');  
    }  
    closeModal('clockModal');renderMyLog();renderEmpCards();  
  } catch(e){showToast('บันทึกล้มเหลว: '+e.message,'error');}  
  finally{btn.innerHTML=clockAction==='in'?'บันทึกเข้างาน':'บันทึกออกงาน';btn.disabled=false;}  
}  
  
// ============================================================  
//  COMMISSION  
// ============================================================  
function onSalesInput(){  
  const sales=parseFloat(document.getElementById('commSales').value)||0;  
  const emp=employees.find(e=>e.id===selectedEmpId);  
  const branch=emp?emp.branch:currentBranch;  
  const calc=document.getElementById('commCalcResult'),noT=document.getElementById('commNoTier');  
  if(sales<=0){calc.style.display='none';noT.style.display='none';return;}  
  const{commission,tier,diff}=calcCommission(branch,sales);  
  if(tier){  
    document.getElementById('commSalesDisplay').textContent=sales.toLocaleString();  
    document.getElementById('commMinDisplay').textContent=tier.min.toLocaleString();  
    document.getElementById('commDiffDisplay').textContent=diff.toLocaleString();  
    document.getElementById('commRateDisplay').textContent=tier.label;  
    document.getElementById('commAmountDisplay').textContent=commission.toLocaleString();  
    document.getElementById('commCalcFormula').textContent=`(${sales.toLocaleString()} − ${tier.min.toLocaleString()}) × ${tier.label} = ฿${commission.toLocaleString()}`;  
    calc.style.display='block';noT.style.display='none';  
  } else {  
    calc.style.display='none';noT.style.display='block';  
  }  
}  
  
async function saveCommission(){  
  if(!selectedEmpId){showToast('กรุณาเลือกพนักงาน','error');return;}  
  const sales=parseFloat(document.getElementById('commSales').value)||0;  
  if(sales<=0){showToast('กรุณากรอกยอดขาย','error');return;}  
  const date=document.getElementById('commDate').value;  
  if(!date){showToast('กรุณาเลือกวันที่','error');return;}  
  const emp=employees.find(e=>e.id===selectedEmpId);  
  const branch=emp?emp.branch:currentBranch;  
  const{commission,tier,diff}=calcCommission(branch,sales);  
  const commRate=tier?tier.rate:0;  
  const note=document.getElementById('commNote').value||(tier?`ยอด ฿${sales.toLocaleString()} ส่วนต่าง ฿${diff.toLocaleString()} × ${tier.label}`:`ยอดขาย ฿${sales.toLocaleString()}`);  
  const log={id:genId(),empId:selectedEmpId,date,branch:currentBranch,  
    clockIn:'00:00',clockOut:'00:00',hours:0,hoursOT:0,type:'commission',  
    sales,commDiff:diff,commission,commRate,note};  
  try{  
    await api('addLog',log);logs.push(log);  
    if(tier) showToast(`💰 ยอด ฿${sales.toLocaleString()} − ฿${tier.min.toLocaleString()} = ฿${diff.toLocaleString()} × ${tier.label} = ค่าคอม ฿${commission.toLocaleString()}`,'success');  
    else showToast(`📋 บันทึกยอด ฿${sales.toLocaleString()} (ยังไม่ถึงขั้นต่ำ)`,'');  
    document.getElementById('commSales').value='';document.getElementById('commNote').value='';  
    document.getElementById('commCalcResult').style.display='none';document.getElementById('commNoTier').style.display='none';  
    renderMyLog();  
  } catch(e){showToast('บันทึกล้มเหลว: '+e.message,'error');}  
}  
  
// ============================================================  
//  SEND SUMMARY  
// ============================================================  
async function openSendSummaryModal(){  
  if(!selectedEmpId){showToast('กรุณาเลือกพนักงาน','error');return;}  
  const ppKey=document.getElementById('empSendPeriod').value;  
  if(!ppKey){showToast('กรุณาเลือกรอบ','error');return;}  
  const emp=employees.find(e=>e.id===selectedEmpId);if(!emp)return;  
  const pl=logsInPP(ppKey).filter(l=>l.empId===selectedEmpId);  
  document.getElementById('sendSummaryContent').innerHTML=buildSummaryHTML(emp,pl,ppKey,false);  
  window._pendingSend={empId:selectedEmpId,ppKey};  
  openModal('sendSummaryModal');  
}  
async function confirmSendSummary(){  
  const{empId,ppKey}=window._pendingSend||{};if(!empId||!ppKey)return;  
  const emp=employees.find(e=>e.id===empId);  
  const pl=logsInPP(ppKey).filter(l=>l.empId===empId);  
  const norm=pl.filter(l=>l.type!=='holiday_work').reduce((s,l)=>s+(Number(l.hours)||0),0);  
  const ot=pl.reduce((s,l)=>s+(Number(l.hoursOT)||0),0);  
  const comm=pl.reduce((s,l)=>s+(Number(l.commission)||0),0);  
  const hwDays=new Set(pl.filter(l=>l.type==='holiday_work').map(l=>l.date)).size;  
  const sub={id:genId(),empId,empName:emp.name,branch:emp.branch,ppKey,sentAt:new Date().toISOString(),status:'pending',norm,ot,comm,hwDays};  
  try{  
    await api('addSubmission',sub);submissions.push(sub);  
    closeModal('sendSummaryModal');showToast('📤 ส่งสรุปให้ HR สำเร็จ','success');  
  } catch(e){showToast('ส่งล้มเหลว: '+e.message,'error');}  
}  
  
// ============================================================  
//  MY LOG  
// ============================================================  
function renderMyLog(){  
  const tbody=document.getElementById('myLogTable');  
  const myLogs=selectedEmpId?[...logs].filter(l=>l.empId===selectedEmpId).reverse().slice(0,50):[...logs].reverse().slice(0,50);  
  if(!myLogs.length){tbody.innerHTML=`<tr><td colspan="9"><div class="empty-state"><div class="ei">📭</div>ยังไม่มีบันทึก</div></td></tr>`;return;}  
  const eMap={};employees.forEach(e=>eMap[e.id]={name:e.name,branch:e.branch});  
  tbody.innerHTML=myLogs.map(l=>{  
    const ei=eMap[l.empId]||{},ph=getPH(l.date);  
    const commDisplay=l.type==='commission'  
      ?(l.sales  
        ?`<span style="font-size:11px;color:var(--muted)">ยอด ฿${Number(l.sales).toLocaleString()}${l.commDiff?` − ฿${Number(l.commDiff).toLocaleString()} ส่วนต่าง`:''}</span><br>`  
        :'')+  
        `<span style="color:var(--success);font-weight:600">฿${Number(l.commission||0).toLocaleString()}</span>`+  
        (l.commRate?` <span style="font-size:10px;color:var(--muted)">(×${Math.round(l.commRate*100)}%)</span>`:'')  
      :'—';  
    return `<tr${ph?' class="ph-row"':''}>  
      <td>${fmtDate(l.date)}${ph?` <span class="badge badge-phday">${ph.name}</span>`:''}</td>  
      <td style="font-size:11px;color:var(--mid);font-weight:600">${brL(l.branch||ei.branch)}</td>  
      <td><span class="badge badge-in">${l.clockIn}</span></td>  
      <td>${l.clockOut&&l.clockOut!=='00:00'?`<span class="badge badge-out">${l.clockOut}</span>`:l.type==='commission'?'—':'<span style="color:var(--warning);font-size:11px">รอ</span>'}</td>  
      <td>${l.hours!=null&&l.hours!==''&&l.type!=='commission'?Number(l.hours)+' ชม.':'—'}</td>  
      <td>${Number(l.hoursOT||0)>0?`<span style="color:#b45309;font-weight:600">${l.hoursOT} ชม.</span>`:'—'}</td>  
      <td>${autoTypeBadge(l)}</td>  
      <td>${commDisplay}</td>  
      <td style="color:var(--muted);font-size:11px">${l.note||'—'}</td>  
    </tr>`;  
  }).join('');  
}  
  
// ============================================================  
//  HR FUNCTIONS  
// ============================================================  
async function refreshHR(){  
  populateFilterSelects();populatePPSelects();  
  // Reload fresh data from Sheets  
  try{  
    const[eRes,lRes,sRes]=await Promise.all([api('getEmployees'),api('getLogs'),api('getSubmissions')]);  
    employees=eRes.employees||[];logs=lRes.logs||[];submissions=sRes.submissions||[];  
    populateFilterSelects();renderDashboard();  
  } catch(e){showToast('โหลดข้อมูล HR ล้มเหลว','error');renderDashboard();}  
}  
  
function populateFilterSelects(){  
  ['filterEmp','summaryEmp'].forEach(id=>{const sel=document.getElementById(id);if(!sel)return;sel.innerHTML='<option value="">ทั้งหมด</option>'+employees.map(e=>`<option value="${e.id}">${e.name}</option>`).join('');});  
}  
  
function renderDashboard(){  
  const ppKey=getCurPPKey(),pl=logsInPP(ppKey);  
  const tN=pl.reduce((s,l)=>s+(Number(l.hours)||0),0),tO=pl.reduce((s,l)=>s+(Number(l.hoursOT)||0),0);  
  const hotH=pl.filter(l=>['holiday_ot','public_holiday'].includes(l.type)).reduce((s,l)=>s+(Number(l.hours)||0),0);  
  const hwD=new Set(pl.filter(l=>l.type==='holiday_work').map(l=>l.date+'_'+l.empId)).size;  
  const wD=new Set(pl.map(l=>l.date)).size;  
  document.getElementById('statsRow').innerHTML=`  
    <div class="stat-card c1"><div class="stat-num">${tN.toFixed(1)}</div><div class="stat-label">ชม.ปกติ (รอบนี้)</div></div>  
    <div class="stat-card c2"><div class="stat-num">${tO.toFixed(1)}</div><div class="stat-label">OT (ชม.)</div></div>  
    <div class="stat-card c3"><div class="stat-num">${hotH.toFixed(1)}</div><div class="stat-label">OT วันหยุด (ชม.)</div></div>  
    <div class="stat-card c4"><div class="stat-num">${hwD}</div><div class="stat-label">ทำงานวันหยุด (วัน×2)</div></div>  
    <div class="stat-card c5"><div class="stat-num">${wD}</div><div class="stat-label">วันทำงาน</div></div>`;  
  document.getElementById('empSummaryTable').innerHTML=employees.filter(e=>e.active).map(e=>{  
    const el=pl.filter(l=>l.empId===e.id);  
    const totalSales=el.filter(l=>l.type==='commission').reduce((s,l)=>s+(Number(l.sales)||0),0);  
    const comm=el.reduce((s,l)=>s+(Number(l.commission)||0),0);  
    return `<tr><td><strong>${e.name}</strong></td><td style="font-size:11px;color:var(--mid);font-weight:600">${brL(e.branch)}</td>  
      <td>${el.reduce((s,l)=>s+(Number(l.hours)||0),0).toFixed(1)}</td>  
      <td>${el.reduce((s,l)=>s+(Number(l.hoursOT)||0),0).toFixed(1)}</td>  
      <td>${el.filter(l=>['holiday_ot','public_holiday'].includes(l.type)).reduce((s,l)=>s+(Number(l.hours)||0),0).toFixed(1)}</td>  
      <td>${new Set(el.filter(l=>l.type==='holiday_work').map(l=>l.date)).size} วัน</td>  
      <td>${totalSales?'฿'+totalSales.toLocaleString():'—'}</td>  
      <td>฿${comm.toLocaleString()}</td>  
      <td>${new Set(el.map(l=>l.date)).size}</td></tr>`;  
  }).join('');  
}  
  
function renderAllLogs(){  
  const empF=document.getElementById('filterEmp').value,branchF=document.getElementById('filterBranch').value,ppKey=document.getElementById('filterPayPeriod').value;  
  const eMap={};employees.forEach(e=>eMap[e.id]={name:e.name,branch:e.branch});  
  let filtered=[...logs].reverse();  
  if(empF)filtered=filtered.filter(l=>l.empId===empF);  
  if(branchF)filtered=filtered.filter(l=>(eMap[l.empId]?.branch||l.branch)===branchF);  
  if(ppKey){const pids=new Set(logsInPP(ppKey).map(l=>l.id));filtered=filtered.filter(l=>pids.has(l.id));}  
  const tbody=document.getElementById('allLogsTable');  
  if(!filtered.length){tbody.innerHTML=`<tr><td colspan="11"><div class="empty-state"><div class="ei">📭</div>ไม่พบรายการ</div></td></tr>`;return;}  
  tbody.innerHTML=filtered.map(l=>{  
    const ei=eMap[l.empId]||{},ph=getPH(l.date);  
    const commDisp=l.type==='commission'?(l.sales?`ยอด ฿${Number(l.sales).toLocaleString()} → `:'')+`<span style="color:var(--success);font-weight:600">฿${Number(l.commission||0).toLocaleString()}</span>`+(l.commRate?` <small>(${Math.round(l.commRate*100)}%)</small>`:''):'—';  
    return `<tr${ph?' class="ph-row"':''}>  
      <td>${fmtDate(l.date)}${ph?` <span class="badge badge-phday" style="font-size:10px">${ph.name}</span>`:''}</td>  
      <td style="font-size:11px;color:var(--mid);font-weight:600">${brL(l.branch||ei.branch)}</td>  
      <td><strong>${ei.name||'—'}</strong></td>  
      <td><span class="badge badge-in">${l.clockIn}</span></td>  
      <td>${l.clockOut&&l.clockOut!=='00:00'?`<span class="badge badge-out">${l.clockOut}</span>`:l.type==='commission'?'—':'<span style="color:var(--warning);font-size:11px">รอ</span>'}</td>  
      <td>${l.hours!=null&&l.hours!==''&&l.type!=='commission'?Number(l.hours)+' ชม.':'—'}</td>  
      <td>${Number(l.hoursOT||0)>0?`<span style="color:#b45309;font-weight:600">${l.hoursOT} ชม.</span>`:'—'}</td>  
      <td>${autoTypeBadge(l)}</td>  
      <td>${commDisp}</td>  
      <td style="font-size:11px;color:var(--muted)">${l.note||'—'}</td>  
      <td><button class="btn btn-danger btn-sm" onclick="deleteLogHR('${l.id}')">🗑</button></td>  
    </tr>`;  
  }).join('');  
}  
  
async function deleteLogHR(id){  
  if(!confirm('ลบรายการนี้?'))return;  
  try{await api('deleteLog',{id});logs=logs.filter(l=>l.id!==id);renderAllLogs();renderDashboard();showToast('ลบเรียบร้อย');}  
  catch(e){showToast('ลบล้มเหลว: '+e.message,'error');}  
}  
  
function buildSummaryHTML(emp,el,ppKey,showSent){  
  const norm=el.filter(l=>l.type!=='holiday_work').reduce((s,l)=>s+(Number(l.hours)||0),0);  
  const ot=el.reduce((s,l)=>s+(Number(l.hoursOT)||0),0);  
  const hot=el.filter(l=>l.type==='holiday_ot').reduce((s,l)=>s+(Number(l.hours)||0),0);  
  const ph=el.filter(l=>l.type==='public_holiday').reduce((s,l)=>s+(Number(l.hours)||0),0);  
  const hwDays=new Set(el.filter(l=>l.type==='holiday_work').map(l=>l.date)).size;  
  const hwPay=hwDays*(emp.dailyWage||0)*2;  
  const commLogs=el.filter(l=>l.type==='commission');  
  const totalSales=commLogs.reduce((s,l)=>s+(Number(l.sales)||0),0);  
  const comm=commLogs.reduce((s,l)=>s+(Number(l.commission)||0),0);  
  const otPay=ot*(emp.otRate||50),hotPay=(hot+ph)*(emp.holidayRate||100);  
  const days=new Set(el.map(l=>l.date)).size;  
  const total=(emp.salary||0)+otPay+hotPay+hwPay+comm;  
  return `<div class="summary-report">  
    <div class="summary-report-header">  
      <div style="font-family:'Prompt',sans-serif;font-size:20px;font-weight:700">☕ Coffee Today</div>  
      <div style="font-size:14px;color:var(--muted);margin-top:4px">สรุปการทำงาน: <strong>${emp.name}</strong> · ${brL(emp.branch)}</div>  
      <div style="font-size:12px;color:var(--muted)">รอบ: ${getPPLabel(ppKey)}</div>  
      ${showSent?'<div style="margin-top:8px"><span class="badge badge-sent">✅ ส่งให้ HR แล้ว</span></div>':''}  
    </div>  
    <table style="width:100%;font-size:13px;border-collapse:collapse">  
      <tr style="border-bottom:1px solid var(--border)"><td style="padding:8px 4px;color:var(--muted)">วันทำงาน</td><td style="padding:8px 4px;font-weight:600;text-align:right">${days} วัน</td></tr>  
      <tr style="border-bottom:1px solid var(--border)"><td style="padding:8px 4px;color:var(--muted)">ชั่วโมงปกติ</td><td style="padding:8px 4px;font-weight:600;text-align:right">${norm.toFixed(2)} ชม.</td></tr>  
      <tr style="border-bottom:1px solid var(--border)"><td style="padding:8px 4px;color:var(--muted)">OT ปกติ (฿${emp.otRate||50}/ชม.)</td><td style="padding:8px 4px;font-weight:600;text-align:right">${ot.toFixed(2)} ชม. = ฿${otPay.toLocaleString()}</td></tr>  
      <tr style="border-bottom:1px solid var(--border)"><td style="padding:8px 4px;color:var(--muted)">OT วันหยุด/นักขัตฤกษ์ (฿${emp.holidayRate||100}/ชม.)</td><td style="padding:8px 4px;font-weight:600;text-align:right">${(hot+ph).toFixed(2)} ชม. = ฿${hotPay.toLocaleString()}</td></tr>  
      <tr style="border-bottom:1px solid var(--border)"><td style="padding:8px 4px;color:var(--muted)">ทำงานวันหยุด ×2 (฿${emp.dailyWage||0}/วัน)</td><td style="padding:8px 4px;font-weight:600;text-align:right;color:var(--accent)">${hwDays} วัน = ฿${hwPay.toLocaleString()}</td></tr>  
      <tr><td style="padding:8px 4px;color:var(--muted)">ค่าคอมมิชชั่น${totalSales?` (ยอดขายรวม ฿${totalSales.toLocaleString()})`:''}</td><td style="padding:8px 4px;font-weight:600;text-align:right;color:var(--success)">฿${comm.toLocaleString()}</td></tr>  
    </table>  
    <div class="sum-total-box">  
      <div style="font-size:13px;opacity:.7;margin-bottom:4px">เงินเดือนฐาน ฿${(emp.salary||0).toLocaleString()} + รายการต่างๆ</div>  
      <div class="amount">฿${total.toLocaleString()}</div>  
      <div style="font-size:12px;opacity:.6;margin-top:4px">ยอดรวมทั้งสิ้น</div>  
    </div>  
  </div>`;  
}  
  
function renderSummary(){  
  const ppKey=document.getElementById('summaryPayPeriod').value,empF=document.getElementById('summaryEmp').value,branchF=document.getElementById('summaryBranch').value;  
  const container=document.getElementById('summaryCards');  
  if(!ppKey){container.innerHTML='<div class="empty-state"><div class="ei">📅</div>กรุณาเลือกรอบเงินเดือน</div>';return;}  
  const pl=logsInPP(ppKey);  
  let targets=employees.filter(e=>e.active);  
  if(empF)targets=targets.filter(e=>e.id===empF);  
  if(branchF)targets=targets.filter(e=>e.branch===branchF);  
  if(!targets.length){container.innerHTML='<div class="empty-state"><div class="ei">👥</div>ไม่พบพนักงาน</div>';return;}  
  container.innerHTML=targets.map(emp=>`<div class="card">${buildSummaryHTML(emp,pl.filter(l=>l.empId===emp.id),ppKey,false)}</div>`).join('');  
}  
  
async function renderSubmissions(){  
  const tbody=document.getElementById('submissionsTable');  
  if(!submissions.length){tbody.innerHTML=`<tr><td colspan="9"><div class="empty-state"><div class="ei">📬</div>ยังไม่มีการส่งสรุป</div></td></tr>`;return;}  
  tbody.innerHTML=[...submissions].reverse().map(s=>`  
    <tr>  
      <td>${fmtDate(s.sentAt.split('T')[0])}<br><small style="color:var(--muted)">${s.sentAt.split('T')[1]?s.sentAt.split('T')[1].slice(0,5):''}</small></td>  
      <td><strong>${s.empName}</strong></td>  
      <td style="font-size:11px;color:var(--mid);font-weight:600">${brL(s.branch)}</td>  
      <td style="font-size:12px">${getPPLabel(s.ppKey)}</td>  
      <td>${Number(s.norm||0).toFixed(1)} ชม.</td>  
      <td>${Number(s.ot||0).toFixed(1)} ชม.</td>  
      <td>฿${Number(s.comm||0).toLocaleString()}</td>  
      <td><span class="badge ${s.status==='pending'?'badge-pending':'badge-sent'}">${s.status==='pending'?'รอตรวจสอบ':'รับทราบแล้ว'}</span></td>  
      <td style="display:flex;gap:5px">  
        <button class="btn btn-dark btn-sm" onclick="viewSubmission('${s.id}')">📋</button>  
        ${s.status==='pending'?`<button class="btn btn-success btn-sm" onclick="approveSubmission('${s.id}')">✓</button>`:''}  
      </td>  
    </tr>`).join('');  
}  
  
function viewSubmission(id){  
  const s=submissions.find(x=>x.id===id);if(!s)return;  
  const emp=employees.find(e=>e.id===s.empId);if(!emp)return;  
  const pl=logsInPP(s.ppKey).filter(l=>l.empId===s.empId);  
  document.getElementById('viewSubmissionContent').innerHTML=buildSummaryHTML(emp,pl,s.ppKey,s.status!=='pending');  
  openModal('viewSubmissionModal');  
}  
async function approveSubmission(id){  
  try{await api('updateSubmission',{id,status:'approved'});const s=submissions.find(x=>x.id===id);if(s)s.status='approved';renderSubmissions();showToast('✅ รับทราบแล้ว','success');}  
  catch(e){showToast('ล้มเหลว: '+e.message,'error');}  
}  
  
function renderEmpTable(){  
  document.getElementById('empTable').innerHTML=employees.map(e=>`  
    <tr><td><strong>${e.name}</strong></td><td style="font-size:11px;color:var(--mid);font-weight:600">${brL(e.branch)}</td>  
    <td>${e.role}</td><td>฿${Number(e.salary||0).toLocaleString()}</td>  
    <td>฿${Number(e.dailyWage||0).toLocaleString()} <span style="color:var(--accent);font-size:10px;font-weight:700">×2</span></td>  
    <td>฿${e.otRate||50}</td><td>฿${e.holidayRate||100}</td>  
    <td><span class="badge ${e.active?'badge-in':'badge-out'}">${e.active?'ทำงาน':'ระงับ'}</span></td>  
    <td style="display:flex;gap:5px;flex-wrap:wrap">  
      <button class="btn btn-dark btn-sm" onclick="editEmp('${e.id}')">✏️</button>  
      <button class="btn btn-danger btn-sm" onclick="toggleEmpStatus('${e.id}')">${e.active?'🔴':'🟢'}</button>  
      <button class="btn btn-danger btn-sm" onclick="deleteEmp('${e.id}')">🗑</button>  
    </td></tr>`).join('');  
}  
async function toggleEmpStatus(id){  
  const e=employees.find(x=>x.id===id);if(!e)return;  
  e.active=!e.active;  
  try{await api('saveEmployee',{...e});renderEmpTable();renderEmpCards();}  
  catch(err){e.active=!e.active;showToast('ล้มเหลว: '+err.message,'error');}  
}  
async function deleteEmp(id){  
  if(!confirm('ลบพนักงานนี้?'))return;  
  try{await api('deleteEmployee',{id});employees=employees.filter(e=>e.id!==id);renderEmpTable();renderEmpCards();showToast('ลบเรียบร้อย');}  
  catch(e){showToast('ลบล้มเหลว: '+e.message,'error');}  
}  
function openAddEmpModal(){  
  document.getElementById('addEmpTitle').textContent='เพิ่มพนักงานใหม่';document.getElementById('editEmpId').value='';  
  ['newEmpName','newEmpRole','newEmpSalary','newEmpDailyWage','newEmpOTRate','newEmpHolidayRate'].forEach(id=>document.getElementById(id).value='');  
  document.getElementById('newEmpBranch').value='lotus';openModal('addEmpModal');  
}  
function editEmp(id){  
  const e=employees.find(x=>x.id===id);if(!e)return;  
  document.getElementById('addEmpTitle').textContent='แก้ไขข้อมูลพนักงาน';  
  document.getElementById('editEmpId').value=id;document.getElementById('newEmpName').value=e.name;  
  document.getElementById('newEmpRole').value=e.role;document.getElementById('newEmpBranch').value=e.branch||'lotus';  
  document.getElementById('newEmpSalary').value=e.salary||'';document.getElementById('newEmpDailyWage').value=e.dailyWage||'';  
  document.getElementById('newEmpOTRate').value=e.otRate||'';document.getElementById('newEmpHolidayRate').value=e.holidayRate||'';  
  openModal('addEmpModal');  
}  
async function saveEmployee(){  
  const name=document.getElementById('newEmpName').value.trim();if(!name){showToast('กรุณากรอกชื่อ','error');return;}  
  const editId=document.getElementById('editEmpId').value;  
  const data={id:editId||'emp'+Date.now(),name,branch:document.getElementById('newEmpBranch').value||'lotus',  
    role:document.getElementById('newEmpRole').value||'พนักงาน',  
    salary:parseFloat(document.getElementById('newEmpSalary').value)||0,  
    dailyWage:parseFloat(document.getElementById('newEmpDailyWage').value)||0,  
    otRate:parseFloat(document.getElementById('newEmpOTRate').value)||50,  
    holidayRate:parseFloat(document.getElementById('newEmpHolidayRate').value)||100,active:true};  
  try{  
    await api('saveEmployee',data);  
    if(editId){const idx=employees.findIndex(e=>e.id===editId);if(idx>-1)employees[idx]={...employees[idx],...data};}  
    else employees.push(data);  
    showToast(editId?'✅ แก้ไขสำเร็จ':'✅ เพิ่มพนักงานสำเร็จ','success');  
    closeModal('addEmpModal');renderEmpTable();renderEmpCards();  
  } catch(e){showToast('บันทึกล้มเหลว: '+e.message,'error');}  
}  
  
function populateManualForm(){  
  document.getElementById('manEmp').innerHTML=employees.filter(e=>e.active).map(e=>`<option value="${e.id}">${e.name} (${brL(e.branch)})</option>`).join('');  
  document.getElementById('manDate').value=new Date().toISOString().split('T')[0];  
  if(currentBranch)document.getElementById('manBranch').value=currentBranch;  
}  
async function saveManual(){  
  const empId=document.getElementById('manEmp').value,date=document.getElementById('manDate').value;  
  const inT=document.getElementById('manIn').value,outT=document.getElementById('manOut').value;  
  const type=document.getElementById('manType').value,branch=document.getElementById('manBranch').value;  
  const salesVal=parseFloat(document.getElementById('manSales').value)||0;  
  if(!empId||!date||!inT){showToast('กรุณากรอกข้อมูลให้ครบ','error');return;}  
  let hours=null,hoursOT=0;  
  if(outT){const total=hRaw(inT,outT),sp=['holiday_ot','public_holiday','holiday_work'].includes(type);  
    if(sp){hours=+total.toFixed(2);hoursOT=0;}else{hours=+(Math.min(total,OT_THRESHOLD).toFixed(2));hoursOT=+(Math.max(0,total-OT_THRESHOLD).toFixed(2));}}  
  const ft=(hours!==null&&hoursOT>0&&!['holiday_ot','public_holiday','holiday_work'].includes(type))?'split':type;  
  const emp=employees.find(e=>e.id===empId);  
  const{commission:manComm,tier:manTier,diff:manDiff}=salesVal>0?calcCommission(branch,salesVal):{commission:0,tier:null,diff:0};  
  const log={id:genId(),empId,date,branch,clockIn:inT,clockOut:outT||'',hours:hours||'',hoursOT,type:ft,  
    sales:salesVal||'',commDiff:manDiff||'',commission:manComm,commRate:manTier?manTier.rate:0,note:document.getElementById('manNote').value};  
  try{  
    await api('addLog',log);logs.push(log);showToast('✅ บันทึกเรียบร้อย','success');  
    ['manIn','manOut','manSales','manNote'].forEach(id=>document.getElementById(id).value='');  
    renderDashboard();  
  } catch(e){showToast('บันทึกล้มเหลว: '+e.message,'error');}  
}  
  
function renderHolidayTable(){  
  document.getElementById('phTable').innerHTML=PH.map((h,i)=>`<tr><td>${i+1}</td><td><strong>${fmtDate(h.date)}</strong></td><td>${h.name}</td></tr>`).join('');  
}  
  
// HELPERS  
function populateEmpSel(selId){document.getElementById(selId).innerHTML='<option value="">— เลือกพนักงาน —</option>'+employees.filter(e=>e.active).map(e=>`<option value="${e.id}">${e.name} (${brL(e.branch)})</option>`).join('');}  
function hRaw(a,b){const[ah,am]=a.split(':').map(Number),[bh,bm]=b.split(':').map(Number),d=(bh*60+bm)-(ah*60+am);return d>0?d/60:0;}  
function autoTypeBadge(l){  
  if(l.type==='split')return`<span class="badge badge-normal">ปกติ</span><span class="badge badge-ot">+OT</span>`;  
  const m={normal:['badge-normal','ปกติ'],split:['badge-ot','ปกติ+OT'],ot:['badge-ot','OT'],holiday_ot:['badge-holiday','OT วันหยุด'],public_holiday:['badge-ph','นักขัตฤกษ์'],holiday_work:['badge-hw','วันหยุด×2'],commission:['badge-commission','ยอดขาย/คอม']};  
  const[cls,label]=m[l.type]||['badge-normal',l.type];return`<span class="badge ${cls}">${label}</span>`;  
}  
function fmtDate(d){if(!d)return'—';return new Date(d+'T00:00:00').toLocaleDateString('th-TH',{year:'numeric',month:'short',day:'numeric'});}  
function openModal(id){document.getElementById(id).classList.add('open');}  
function closeModal(id){document.getElementById(id).classList.remove('open');}  
let toastTimer;  
function showToast(msg,type=''){const t=document.getElementById('toast');t.textContent=msg;t.className='show '+type;clearTimeout(toastTimer);toastTimer=setTimeout(()=>{t.className='';},4000);}  
document.querySelectorAll('.modal-overlay').forEach(o=>o.addEventListener('click',e=>{if(e.target===o)o.classList.remove('open');}));  
  
// INIT  
if(currentBranch)document.getElementById('branchSelect').value=currentBranch;  
updateBranchUI();populatePPSelects();  
if(API_URL){document.getElementById('setupBanner').style.display='none';loadAll();}  
else{document.getElementById('setupBanner').style.display='block';setSyncStatus('error','ยังไม่ได้ตั้งค่า URL');}  
</script>  
  
</body>  
</html>  
