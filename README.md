[index (1).html](https://github.com/user-attachments/files/27811490/index.1.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="theme-color" content="#1c1a17">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="MisFinanzas">
<title>MisFinanzas</title>
<link rel="manifest" href="manifest.json">
<link rel="apple-touch-icon" href="https://placehold.co/192x192/f4a261/1c1a17?text=MF">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Nunito:wght@400;500;600;700&display=swap" rel="stylesheet">

<style>
/* ── TOKENS ─────────────────────────────────────────── */
:root {
  --bg:      #f7f3ee;
  --bg2:     #ede8e1;
  --surface: #ffffff;
  --border:  #ddd7cc;
  --text:    #1c1a17;
  --muted:   #8a8070;
  --green:   #2d7d5a;
  --gl:      #e8f5ee;
  --red:     #c0392b;
  --rl:      #fdecea;
  --yellow:  #b8860b;
  --yl:      #fdf6e3;
  --blue:    #1a5276;
  --bl:      #eaf2fb;
  --orange:  #f4a261;
  --r: 18px;
  --sh: 0 2px 16px rgba(0,0,0,0.07);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{height:100%}
body{
  background:var(--bg);color:var(--text);
  font-family:'Nunito',sans-serif;min-height:100%;
  font-size:15px;-webkit-font-smoothing:antialiased;
  padding-bottom:env(safe-area-inset-bottom);
}

/* ── LOADING ─────────────────────────────────────────── */
#loader{
  position:fixed;inset:0;background:#1c1a17;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  gap:18px;z-index:999;transition:opacity .4s;
}
#loader.gone{opacity:0;pointer-events:none}
.loader-logo{font-family:'Playfair Display',serif;font-size:2.2rem;font-weight:900;color:#fff}
.loader-logo em{color:var(--orange);font-style:normal}
.loader-sub{color:rgba(255,255,255,.45);font-size:.82rem;font-weight:600}
.spinner{width:34px;height:34px;border:3px solid rgba(255,255,255,.12);
  border-top-color:var(--orange);border-radius:50%;animation:spin .8s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}

/* ── SYNC BAR ────────────────────────────────────────── */
#syncBar{
  background:#1c1a17;color:rgba(255,255,255,.55);
  font-size:.72rem;font-weight:700;letter-spacing:.04em;
  padding:5px 16px;display:flex;align-items:center;
  justify-content:center;gap:8px;
}
.sdot{width:7px;height:7px;border-radius:50%;background:#555;transition:background .3s}
.sdot.ok{background:#52b788}
.sdot.busy{background:#ffd166;animation:pulse .8s infinite}
.sdot.err{background:#ff6b6b}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}

/* ── HEADER ──────────────────────────────────────────── */
header{
  background:#1c1a17;color:#fff;
  padding:14px 20px 12px;
  position:sticky;top:0;z-index:100;
}
.hinner{
  max-width:860px;margin:0 auto;
  display:flex;align-items:center;justify-content:space-between;
  gap:12px;flex-wrap:wrap;
}
.logo{font-family:'Playfair Display',serif;font-size:1.35rem;font-weight:900}
.logo em{color:var(--orange);font-style:normal}
.hright{display:flex;align-items:center;gap:10px;flex-wrap:wrap}

.msel{
  display:flex;align-items:center;gap:7px;
  background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.18);
  border-radius:50px;padding:6px 14px;
}
.msel select{
  background:transparent;border:none;color:#fff;
  font-family:'Nunito',sans-serif;font-size:.83rem;font-weight:700;
  outline:none;cursor:pointer;
}
.msel select option{background:#1c1a17}

.btn-hdr{
  background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);
  color:#fff;border-radius:50px;padding:6px 14px;
  font-family:'Nunito',sans-serif;font-size:.78rem;font-weight:700;
  cursor:pointer;display:flex;align-items:center;gap:6px;transition:background .2s;
}
.btn-hdr:hover{background:rgba(255,255,255,.2)}

/* ── SUMMARY ─────────────────────────────────────────── */
.sumbar{
  background:#1c1a17;
  border-bottom:3px solid var(--orange);
  padding:0 20px 16px;
}
.suminner{
  max-width:860px;margin:0 auto;
  display:grid;grid-template-columns:repeat(4,1fr);gap:10px;
}
.sc{
  background:rgba(255,255,255,.07);
  border:1px solid rgba(255,255,255,.1);
  border-radius:13px;padding:10px 12px;text-align:center;
}
.sl{font-size:.68rem;color:rgba(255,255,255,.4);font-weight:700;
  text-transform:uppercase;letter-spacing:.05em;margin-bottom:4px}
.sv{font-size:.95rem;font-weight:700;color:#fff}
.sv.cg{color:#52b788}.sv.cr{color:#ff6b6b}.sv.cy{color:#ffd166}

/* ── MAIN ────────────────────────────────────────────── */
main{max-width:860px;margin:0 auto;padding:22px 16px 90px}

/* ── TABS ────────────────────────────────────────────── */
.tabs{
  display:grid;grid-template-columns:repeat(3,1fr);
  background:var(--surface);border:1px solid var(--border);
  border-radius:14px;overflow:hidden;margin-bottom:24px;box-shadow:var(--sh);
}
.tab{
  padding:13px 6px;border:none;background:transparent;
  color:var(--muted);font-family:'Nunito',sans-serif;
  font-size:.8rem;font-weight:700;cursor:pointer;transition:all .2s;
  text-align:center;border-right:1px solid var(--border);
  display:flex;align-items:center;justify-content:center;gap:5px;
}
.tab:last-child{border-right:none}
.tab.active{color:#fff}
.ti.active{background:var(--green)}
.tb.active{background:var(--blue)}
.tu.active{background:var(--yellow)}

/* ── PANELS ──────────────────────────────────────────── */
.panel{display:none}.panel.active{display:block}

/* ── SECTION HEADER ──────────────────────────────────── */
.sh2{display:flex;align-items:center;justify-content:space-between;
  margin-bottom:16px;flex-wrap:wrap;gap:10px}
.st{font-family:'Playfair Display',serif;font-size:1.18rem;font-weight:700}

/* ── BUTTONS ─────────────────────────────────────────── */
.btn{
  display:inline-flex;align-items:center;gap:6px;
  padding:10px 18px;border-radius:10px;border:none;
  font-family:'Nunito',sans-serif;font-size:.84rem;font-weight:700;
  cursor:pointer;transition:all .18s;
}
.bg{background:var(--green);color:#fff}.bg:hover{background:#235f44;transform:translateY(-1px)}
.bb{background:var(--blue);color:#fff}.bb:hover{background:#133d5b;transform:translateY(-1px)}
.by{background:var(--yellow);color:#fff}.by:hover{background:#8a6409;transform:translateY(-1px)}
.bgh{background:transparent;color:var(--muted);border:1.5px solid var(--border)}
.bgh:hover{border-color:var(--text);color:var(--text)}
.bsm{padding:6px 11px;font-size:.76rem;border-radius:8px}
.bdel{background:transparent;color:var(--red);border:1.5px solid #f5c6c3}
.bdel:hover{background:var(--red);color:#fff}
.bedt{background:transparent;color:var(--muted);border:1.5px solid var(--border)}
.bedt:hover{border-color:var(--blue);color:var(--blue)}

/* ── CARDS ───────────────────────────────────────────── */
.lgrid{display:grid;gap:10px}
.card{
  background:var(--surface);border:1px solid var(--border);
  border-radius:var(--r);padding:14px 18px;
  box-shadow:var(--sh);transition:transform .15s;
}
.card:hover{transform:translateX(3px)}
.card.ci{border-left:4px solid var(--green)}
.card.cb{border-left:4px solid var(--blue)}
.card.cb.paid{border-left-color:var(--green);opacity:.82}
.card.cb.overdue{border-left-color:var(--red)}
.card.cu{border-left:4px solid var(--yellow)}

.cmain{display:flex;align-items:center;gap:12px}
.cicon{
  width:42px;height:42px;border-radius:12px;
  display:flex;align-items:center;justify-content:center;
  font-size:1.1rem;flex-shrink:0;
}
.igh{background:var(--gl)}.ibh{background:var(--bl)}
.iyh{background:var(--yl)}.irh{background:var(--rl)}

.cinfo{flex:1;min-width:0}
.cname{font-weight:700;font-size:.93rem;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.cmeta{font-size:.75rem;color:var(--muted);margin-top:2px}
.cnote{font-size:.76rem;color:var(--muted);font-style:italic;margin-top:3px}

.cright{text-align:right;flex-shrink:0}
.camt{font-weight:700;font-size:.98rem}
.ag{color:var(--green)}.ab{color:var(--blue)}.ay{color:var(--yellow)}

.cfoot{
  display:flex;align-items:center;justify-content:space-between;
  margin-top:10px;padding-top:10px;border-top:1px solid var(--border);
  flex-wrap:wrap;gap:8px;
}
.cacts{display:flex;gap:6px}

/* ── BADGE ───────────────────────────────────────────── */
.badge{display:inline-block;padding:2px 10px;border-radius:20px;
  font-size:.68rem;font-weight:700;text-transform:uppercase;letter-spacing:.04em}
.bpaid{background:var(--gl);color:var(--green)}
.bpend{background:var(--yl);color:var(--yellow)}
.bover{background:var(--rl);color:var(--red)}

/* ── PROGRESS ────────────────────────────────────────── */
.pbox{
  background:var(--surface);border:1px solid var(--border);
  border-radius:var(--r);padding:15px 18px;
  margin-bottom:16px;box-shadow:var(--sh);
}
.phdr{display:flex;justify-content:space-between;margin-bottom:8px}
.plbl{font-size:.76rem;color:var(--muted);font-weight:700}
.ppct{font-size:.8rem;font-weight:700}
.pbg{height:10px;background:var(--bg2);border-radius:10px;overflow:hidden}
.pfill{height:100%;border-radius:10px;transition:width .5s ease}
.fg{background:linear-gradient(90deg,#2d7d5a,#52b788)}
.fy{background:linear-gradient(90deg,#b8860b,#f0c040)}
.fr{background:linear-gradient(90deg,#c0392b,#e74c3c)}

/* ── TOTAL STRIP ─────────────────────────────────────── */
.tstrip{
  background:var(--bg2);border:1px solid var(--border);
  border-radius:12px;padding:12px 18px;
  display:flex;justify-content:space-between;align-items:center;
  margin-top:14px;font-weight:700;
}
.tl{color:var(--muted);font-size:.82rem}
.tv{font-size:1.05rem}

/* ── EMPTY ───────────────────────────────────────────── */
.empty{
  text-align:center;padding:44px 20px;
  background:var(--surface);border:2px dashed var(--border);
  border-radius:var(--r);color:var(--muted);
}
.ei{font-size:2.2rem;margin-bottom:10px}
.empty p{font-size:.87rem}

/* ── MODAL ───────────────────────────────────────────── */
.mover{
  display:none;position:fixed;inset:0;
  background:rgba(0,0,0,.52);backdrop-filter:blur(4px);
  z-index:300;align-items:center;justify-content:center;padding:16px;
}
.mover.open{display:flex}
.modal{
  background:var(--surface);border:1px solid var(--border);
  border-radius:var(--r);padding:24px;width:100%;max-width:460px;
  box-shadow:0 24px 60px rgba(0,0,0,.18);
  animation:popIn .22s ease;
}
@keyframes popIn{from{opacity:0;transform:scale(.95) translateY(10px)}to{opacity:1;transform:scale(1) translateY(0)}}
.mtitle{font-family:'Playfair Display',serif;font-size:1.12rem;font-weight:700;
  margin-bottom:18px;display:flex;align-items:center;gap:8px}
.macts{display:flex;gap:10px;justify-content:flex-end;margin-top:18px;flex-wrap:wrap}

/* ── FORM ────────────────────────────────────────────── */
.fld{margin-bottom:12px}
.fld label{display:block;font-size:.71rem;color:var(--muted);font-weight:700;
  margin-bottom:5px;text-transform:uppercase;letter-spacing:.05em}
.fld input,.fld select,.fld textarea{
  width:100%;background:var(--bg);border:1.5px solid var(--border);
  border-radius:10px;color:var(--text);font-family:'Nunito',sans-serif;
  font-size:.93rem;padding:9px 13px;outline:none;transition:border-color .2s;
}
.fld input:focus,.fld select:focus,.fld textarea:focus{border-color:var(--text);background:#fff}
.fld textarea{resize:vertical;min-height:66px}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:12px}

/* ── DRIVE MODAL ─────────────────────────────────────── */
.drive-step{text-align:center;padding:8px 0}
.drive-step .ds-icon{font-size:2.5rem;margin-bottom:10px}
.drive-step h4{font-family:'Playfair Display',serif;font-size:1.1rem;margin-bottom:8px}
.drive-step p{font-size:.84rem;color:var(--muted);line-height:1.6;margin-bottom:16px}
.drive-step input{
  width:100%;background:var(--bg);border:1.5px solid var(--border);
  border-radius:10px;color:var(--text);font-family:'Nunito',sans-serif;
  font-size:.9rem;padding:10px 14px;outline:none;margin-bottom:8px;
}
.drive-step input:focus{border-color:var(--text);background:#fff}
.drive-note{font-size:.74rem;color:var(--muted);background:var(--bg2);
  border-radius:10px;padding:10px 14px;line-height:1.6;margin-top:8px;text-align:left}
.drive-note strong{color:var(--text)}

/* ── TOAST ───────────────────────────────────────────── */
.toast{
  position:fixed;bottom:24px;left:50%;
  transform:translateX(-50%) translateY(80px);
  background:#1c1a17;color:#fff;
  padding:11px 22px;border-radius:50px;
  font-size:.83rem;font-weight:600;
  box-shadow:0 8px 30px rgba(0,0,0,.2);
  z-index:500;transition:transform .3s ease;white-space:nowrap;
}
.toast.show{transform:translateX(-50%) translateY(0)}

/* ── INSTALL BANNER ──────────────────────────────────── */
#installBanner{
  display:none;
  position:fixed;bottom:0;left:0;right:0;
  background:#1c1a17;color:#fff;
  padding:16px 20px;z-index:200;
  border-top:2px solid var(--orange);
  flex-direction:column;gap:12px;
  box-shadow:0 -8px 30px rgba(0,0,0,.3);
}
#installBanner.show{display:flex}
.ib-top{display:flex;align-items:center;gap:12px}
.ib-icon{font-size:1.8rem}
.ib-text h4{font-weight:700;font-size:.95rem}
.ib-text p{font-size:.78rem;color:rgba(255,255,255,.55);margin-top:2px}
.ib-acts{display:flex;gap:10px}
.ib-install{
  flex:1;background:var(--orange);color:#1c1a17;
  border:none;border-radius:10px;padding:12px;
  font-family:'Nunito',sans-serif;font-size:.88rem;font-weight:700;cursor:pointer;
}
.ib-dismiss{
  background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);
  color:rgba(255,255,255,.6);border-radius:10px;padding:12px 16px;
  font-family:'Nunito',sans-serif;font-size:.82rem;cursor:pointer;
}

/* ── RESPONSIVE ──────────────────────────────────────── */
@media(max-width:600px){
  .suminner{grid-template-columns:1fr 1fr}
  .sv{font-size:.85rem}
  .frow{grid-template-columns:1fr}
  .macts{flex-direction:column-reverse}
  .macts .btn{width:100%;justify-content:center}
  .tab .ttext{display:none}
  .tab{padding:14px 6px}
}
</style>
</head>
<body>

<!-- LOADING -->
<div id="loader">
  <div class="loader-logo">Mis<em>Finanzas</em></div>
  <div class="spinner"></div>
  <div class="loader-sub" id="loaderMsg">Iniciando…</div>
</div>

<!-- SYNC BAR -->
<div id="syncBar"><div class="sdot" id="sdot"></div><span id="smsg">Listo</span></div>

<!-- HEADER -->
<header>
  <div class="hinner">
    <div class="logo">Mis<em>Finanzas</em></div>
    <div class="hright">
      <div class="msel">📅 <select id="monthSel" onchange="changeMonth()"></select></div>
      <button class="btn-hdr" onclick="syncNow()">☁️ Guardar</button>
      <button class="btn-hdr" onclick="openDriveModal()">⚙️</button>
    </div>
  </div>
</header>

<!-- SUMMARY -->
<div class="sumbar">
  <div class="suminner">
    <div class="sc"><div class="sl">💰 Ingresos</div><div class="sv cg" id="hI">$0</div></div>
    <div class="sc"><div class="sl">🏠 Fijas</div><div class="sv cr" id="hB">$0</div></div>
    <div class="sc"><div class="sl">⚡ Imprevistos</div><div class="sv cy" id="hU">$0</div></div>
    <div class="sc"><div class="sl">📊 Balance</div><div class="sv" id="hBal">$0</div></div>
  </div>
</div>

<!-- MAIN -->
<main>
  <div class="tabs">
    <button class="tab ti active" onclick="switchTab('income')"><span>💰</span><span class="ttext">Ingresos</span></button>
    <button class="tab tb" onclick="switchTab('bills')"><span>🏠</span><span class="ttext">Cuentas fijas</span></button>
    <button class="tab tu" onclick="switchTab('unexpected')"><span>⚡</span><span class="ttext">Imprevistos</span></button>
  </div>

  <!-- INGRESOS -->
  <div class="panel active" id="panel-income">
    <div class="sh2"><div class="st">💰 Ingresos del mes</div><button class="btn bg" onclick="openModal('income')">+ Agregar</button></div>
    <div class="lgrid" id="incomeList"></div>
    <div class="tstrip" id="iTot" style="display:none"><span class="tl">Total ingresos</span><span class="tv ag" id="iTotV">$0</span></div>
  </div>

  <!-- CUENTAS FIJAS -->
  <div class="panel" id="panel-bills">
    <div class="sh2"><div class="st">🏠 Cuentas fijas</div><button class="btn bb" onclick="openModal('bill')">+ Agregar</button></div>
    <div class="pbox" id="bProg" style="display:none">
      <div class="phdr"><span class="plbl">Cuentas pagadas</span><span class="ppct" id="bPct">0%</span></div>
      <div class="pbg"><div class="pfill fg" id="bBar" style="width:0%"></div></div>
    </div>
    <div class="lgrid" id="billsList"></div>
    <div class="tstrip" id="bTot" style="display:none"><span class="tl">Total comprometido</span><span class="tv ab" id="bTotV">$0</span></div>
  </div>

  <!-- IMPREVISTOS -->
  <div class="panel" id="panel-unexpected">
    <div class="sh2"><div class="st">⚡ Gastos imprevistos</div><button class="btn by" onclick="openModal('unexpected')">+ Registrar</button></div>
    <div class="lgrid" id="unexpectedList"></div>
    <div class="tstrip" id="uTot" style="display:none"><span class="tl">Total imprevistos</span><span class="tv ay" id="uTotV">$0</span></div>
  </div>
</main>

<!-- ═══ MODAL INGRESO ═══ -->
<div class="mover" id="modal-income">
  <div class="modal">
    <div class="mtitle">💰 <span id="iMT">Nuevo ingreso</span></div>
    <input type="hidden" id="iEId">
    <div class="fld"><label>Concepto / Origen</label><input type="text" id="iName" placeholder="Ej: Salario, freelance, arriendo…"></div>
    <div class="frow">
      <div class="fld"><label>Monto</label><input type="number" id="iAmt" placeholder="0" min="0"></div>
      <div class="fld"><label>Fecha recibido</label><input type="date" id="iDate"></div>
    </div>
    <div class="fld"><label>Tipo</label>
      <select id="iType">
        <option value="salary">💼 Salario / Sueldo</option>
        <option value="freelance">💻 Freelance / Extra</option>
        <option value="rent">🏘️ Arriendo / Alquiler</option>
        <option value="business">🏪 Negocio / Ventas</option>
        <option value="transfer">📲 Transferencia recibida</option>
        <option value="other">📌 Otro</option>
      </select>
    </div>
    <div class="fld"><label>Notas (opcional)</label><textarea id="iNote" placeholder="Ej: Quincena de mayo, proyecto X…"></textarea></div>
    <div class="macts">
      <button class="btn bgh" onclick="closeModal('income')">Cancelar</button>
      <button class="btn bg" onclick="saveIncome()">Guardar</button>
    </div>
  </div>
</div>

<!-- ═══ MODAL CUENTA FIJA ═══ -->
<div class="mover" id="modal-bill">
  <div class="modal">
    <div class="mtitle">🏠 <span id="bMT">Nueva cuenta fija</span></div>
    <input type="hidden" id="bEId">
    <div class="fld"><label>Nombre de la cuenta</label><input type="text" id="bName" placeholder="Ej: Arriendo, luz, internet…"></div>
    <div class="frow">
      <div class="fld"><label>Monto</label><input type="number" id="bAmt" placeholder="0" min="0"></div>
      <div class="fld"><label>Día de vencimiento</label><input type="number" id="bDue" placeholder="Ej: 15" min="1" max="31"></div>
    </div>
    <div class="frow">
      <div class="fld"><label>Categoría</label>
        <select id="bCat">
          <option value="housing">🏠 Vivienda / Arriendo</option>
          <option value="utilities">💡 Servicios públicos</option>
          <option value="internet">📶 Internet / TV / Teléfono</option>
          <option value="insurance">🛡️ Seguros</option>
          <option value="transport">🚗 Transporte</option>
          <option value="education">📚 Educación</option>
          <option value="health">🏥 Salud</option>
          <option value="subscription">📱 Suscripciones</option>
          <option value="loan">💳 Crédito / Préstamo</option>
          <option value="other">📌 Otro</option>
        </select>
      </div>
      <div class="fld"><label>Estado</label>
        <select id="bStat">
          <option value="pending">⏳ Pendiente</option>
          <option value="paid">✅ Pagado</option>
          <option value="overdue">🔴 Vencido</option>
        </select>
      </div>
    </div>
    <div class="fld"><label>Fecha de pago (si ya pagaste)</label><input type="date" id="bPaidDate"></div>
    <div class="fld"><label>Notas (opcional)</label><textarea id="bNote" placeholder="Número de cuenta, observaciones…"></textarea></div>
    <div class="macts">
      <button class="btn bgh" onclick="closeModal('bill')">Cancelar</button>
      <button class="btn bb" onclick="saveBill()">Guardar</button>
    </div>
  </div>
</div>

<!-- ═══ MODAL IMPREVISTO ═══ -->
<div class="mover" id="modal-unexpected">
  <div class="modal">
    <div class="mtitle">⚡ <span id="uMT">Nuevo imprevisto</span></div>
    <input type="hidden" id="uEId">
    <div class="fld"><label>Descripción</label><input type="text" id="uName" placeholder="Ej: Médico urgente, arreglo carro…"></div>
    <div class="frow">
      <div class="fld"><label>Monto</label><input type="number" id="uAmt" placeholder="0" min="0"></div>
      <div class="fld"><label>Fecha</label><input type="date" id="uDate"></div>
    </div>
    <div class="fld"><label>Categoría</label>
      <select id="uCat">
        <option value="health">🏥 Salud / Médico</option>
        <option value="repair">🔧 Reparación</option>
        <option value="transport">🚗 Transporte urgente</option>
        <option value="food">🍽️ Alimentación extra</option>
        <option value="family">👨‍👩‍👧 Familia</option>
        <option value="home">🏠 Hogar</option>
        <option value="fine">📋 Multa / Recargo</option>
        <option value="other">📌 Otro</option>
      </select>
    </div>
    <div class="fld"><label>Notas (opcional)</label><textarea id="uNote" placeholder="Detalle del gasto…"></textarea></div>
    <div class="macts">
      <button class="btn bgh" onclick="closeModal('unexpected')">Cancelar</button>
      <button class="btn by" onclick="saveUnexpected()">Guardar</button>
    </div>
  </div>
</div>

<!-- ═══ MODAL DRIVE ═══ -->
<div class="mover" id="modal-drive">
  <div class="modal">
    <div class="mtitle">☁️ Conexión con Google Drive</div>
    <div class="drive-step">
      <div class="ds-icon">📄</div>
      <h4>ID del archivo en Drive</h4>
      <p>MisFinanzas guarda todos tus datos en un archivo JSON en tu Google Drive. Pega aquí el ID del archivo (lo creas una sola vez).</p>
      <input type="text" id="driveFileId" placeholder="Ej: 1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgVE2upms">
      <div class="drive-note">
        <strong>¿Cómo obtener el ID?</strong><br>
        1. Ve a <strong>drive.google.com</strong><br>
        2. Crea un archivo nuevo → "Documento de texto" → nómbralo <em>misfinanzas.json</em><br>
        3. Ábrelo, reemplaza todo el contenido con: <code>{}</code> y guárdalo<br>
        4. Copia el ID de la URL (la parte larga entre /d/ y /edit)<br>
        5. Pégalo arriba y presiona Guardar
      </div>
    </div>
    <div class="macts">
      <button class="btn bgh" onclick="closeModal('drive')">Cancelar</button>
      <button class="btn bg" onclick="saveDriveId()">Guardar ID</button>
    </div>
  </div>
</div>

<!-- INSTALL BANNER -->
<div id="installBanner">
  <div class="ib-top">
    <div class="ib-icon">📲</div>
    <div class="ib-text">
      <h4>Instalar MisFinanzas</h4>
      <p>Agrégala a tu pantalla de inicio para usarla como app</p>
    </div>
  </div>
  <div class="ib-acts">
    <button class="ib-install" onclick="installApp()">Instalar app</button>
    <button class="ib-dismiss" onclick="dismissInstall()">Ahora no</button>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- ═══════════════════════════════════════
     JAVASCRIPT
════════════════════════════════════════ -->
<script>
// ── STATE ──────────────────────────────────────────────
let db = { income:{}, bills:{}, unexpected:{} };
let currentMonth = new Date().toISOString().slice(0,7);
let driveFileId = localStorage.getItem('mf_drive_id') || '';
let deferredInstall = null;
let syncTimer = null;

const ICONS = {
  income: { salary:'💼', freelance:'💻', rent:'🏘️', business:'🏪', transfer:'📲', other:'📌' },
  bills:  { housing:'🏠', utilities:'💡', internet:'📶', insurance:'🛡️', transport:'🚗',
            education:'📚', health:'🏥', subscription:'📱', loan:'💳', other:'📌' },
  unexpected: { health:'🏥', repair:'🔧', transport:'🚗', food:'🍽️', family:'👨‍👩‍👧',
               home:'🏠', fine:'📋', other:'📌' }
};

// ── INIT ───────────────────────────────────────────────
window.addEventListener('DOMContentLoaded', async () => {
  buildMonthSel();
  registerSW();
  setupInstallPrompt();

  if (driveFileId) {
    setLoader('Cargando datos desde Drive…');
    await loadFromDrive();
  } else {
    // Load from localStorage fallback
    const local = localStorage.getItem('mf_data');
    if (local) db = JSON.parse(local);
    setLoader('Sin Drive configurado. Usando datos locales.');
    await sleep(900);
  }

  hideLoader();
  renderAll();
});

function sleep(ms){ return new Promise(r => setTimeout(r,ms)); }
function setLoader(msg){ document.getElementById('loaderMsg').textContent = msg; }
function hideLoader(){
  const l = document.getElementById('loader');
  l.classList.add('gone');
  setTimeout(()=>l.style.display='none', 500);
}

// ── SERVICE WORKER ─────────────────────────────────────
function registerSW(){
  if('serviceWorker' in navigator){
    navigator.serviceWorker.register('sw.js').catch(()=>{});
  }
}

// ── INSTALL PROMPT ─────────────────────────────────────
function setupInstallPrompt(){
  window.addEventListener('beforeinstallprompt', e => {
    e.preventDefault();
    deferredInstall = e;
    if(!localStorage.getItem('mf_install_dismissed')){
      document.getElementById('installBanner').classList.add('show');
    }
  });
  window.addEventListener('appinstalled', () => {
    document.getElementById('installBanner').classList.remove('show');
    showToast('✅ App instalada correctamente');
  });
}
function installApp(){
  if(deferredInstall){ deferredInstall.prompt(); }
  document.getElementById('installBanner').classList.remove('show');
}
function dismissInstall(){
  document.getElementById('installBanner').classList.remove('show');
  localStorage.setItem('mf_install_dismissed','1');
}

// ── MONTH SELECTOR ─────────────────────────────────────
function buildMonthSel(){
  const sel = document.getElementById('monthSel');
  const months=['Enero','Febrero','Marzo','Abril','Mayo','Junio',
                'Julio','Agosto','Septiembre','Octubre','Noviembre','Diciembre'];
  const now = new Date();
  for(let i=-6;i<=3;i++){
    const d = new Date(now.getFullYear(), now.getMonth()+i, 1);
    const val = d.toISOString().slice(0,7);
    const opt = document.createElement('option');
    opt.value = val;
    opt.textContent = `${months[d.getMonth()]} ${d.getFullYear()}`;
    if(val===currentMonth) opt.selected=true;
    sel.appendChild(opt);
  }
}
function changeMonth(){ currentMonth=document.getElementById('monthSel').value; renderAll(); }

// ── FORMAT ─────────────────────────────────────────────
function fmt(n){ return '$'+Number(n||0).toLocaleString('es-CO',{minimumFractionDigits:0}); }
function fmtDate(d){
  if(!d) return '';
  const [y,m,day]=d.split('-');
  const ms=['ene','feb','mar','abr','may','jun','jul','ago','sep','oct','nov','dic'];
  return `${parseInt(day)} ${ms[parseInt(m)-1]} ${y}`;
}

// ── TABS ────────────────────────────────────────────────
function switchTab(t){
  document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
  document.querySelectorAll('.panel').forEach(x=>x.classList.remove('active'));
  document.querySelector('.t'+t[0]).classList.add('active');
  document.getElementById('panel-'+t).classList.add('active');
}

// ── MONTH DATA ──────────────────────────────────────────
function md(type){ if(!db[type][currentMonth]) db[type][currentMonth]=[]; return db[type][currentMonth]; }

// ── RENDER ──────────────────────────────────────────────
function renderAll(){ renderIncome(); renderBills(); renderUnexpected(); renderSummary(); }

function renderSummary(){
  const inc = md('income').reduce((a,x)=>a+Number(x.amount),0);
  const bil = md('bills').reduce((a,x)=>a+Number(x.amount),0);
  const unx = md('unexpected').reduce((a,x)=>a+Number(x.amount),0);
  const bal = inc - bil - unx;
  document.getElementById('hI').textContent = fmt(inc);
  document.getElementById('hB').textContent = fmt(bil);
  document.getElementById('hU').textContent = fmt(unx);
  const hb = document.getElementById('hBal');
  hb.textContent = fmt(bal);
  hb.className = 'sv ' + (bal>=0?'cg':'cr');
}

function renderIncome(){
  const list = md('income');
  const el = document.getElementById('incomeList');
  const tot = document.getElementById('iTot');
  const totv = document.getElementById('iTotV');
  if(!list.length){
    el.innerHTML = `<div class="empty"><div class="ei">💰</div><p>Sin ingresos registrados este mes.<br>Toca "+ Agregar" para empezar.</p></div>`;
    tot.style.display='none'; return;
  }
  el.innerHTML = list.map(x => `
    <div class="card ci">
      <div class="cmain">
        <div class="cicon igh">${ICONS.income[x.type]||'📌'}</div>
        <div class="cinfo">
          <div class="cname">${esc(x.name)}</div>
          <div class="cmeta">${fmtDate(x.date)}</div>
          ${x.note?`<div class="cnote">${esc(x.note)}</div>`:''}
        </div>
        <div class="cright"><div class="camt ag">${fmt(x.amount)}</div></div>
      </div>
      <div class="cfoot">
        <span></span>
        <div class="cacts">
          <button class="btn bedt bsm" onclick="openModal('income','${x.id}')">✏️ Editar</button>
          <button class="btn bdel bsm" onclick="delItem('income','${x.id}')">🗑️</button>
        </div>
      </div>
    </div>`).join('');
  const total = list.reduce((a,x)=>a+Number(x.amount),0);
  totv.textContent = fmt(total);
  tot.style.display='flex';
}

function renderBills(){
  const list = md('bills');
  const el = document.getElementById('billsList');
  const prog = document.getElementById('bProg');
  const tot = document.getElementById('bTot');
  if(!list.length){
    el.innerHTML = `<div class="empty"><div class="ei">🏠</div><p>Sin cuentas fijas registradas.<br>Toca "+ Agregar" para empezar.</p></div>`;
    prog.style.display='none'; tot.style.display='none'; return;
  }
  // Progress
  const paid = list.filter(x=>x.status==='paid').length;
  const pct = Math.round((paid/list.length)*100);
  document.getElementById('bPct').textContent = pct+'%';
  const bar = document.getElementById('bBar');
  bar.style.width = pct+'%';
  bar.className = 'pfill '+(pct===100?'fg':pct>=50?'fy':'fr');
  prog.style.display='block';

  el.innerHTML = list.map(x => {
    const stMap = {paid:'✅ Pagado',pending:'⏳ Pendiente',overdue:'🔴 Vencido'};
    const bdgMap = {paid:'bpaid',pending:'bpend',overdue:'bover'};
    return `
    <div class="card cb ${x.status}">
      <div class="cmain">
        <div class="cicon ibh">${ICONS.bills[x.category]||'📌'}</div>
        <div class="cinfo">
          <div class="cname">${esc(x.name)}</div>
          <div class="cmeta">${x.dueDay?'Vence día '+x.dueDay:''}${x.paidDate?' · Pagado '+fmtDate(x.paidDate):''}</div>
          ${x.note?`<div class="cnote">${esc(x.note)}</div>`:''}
        </div>
        <div class="cright"><div class="camt ab">${fmt(x.amount)}</div></div>
      </div>
      <div class="cfoot">
        <span class="badge ${bdgMap[x.status]}">${stMap[x.status]}</span>
        <div class="cacts">
          ${x.status!=='paid'?`<button class="btn bg bsm" onclick="markPaid('${x.id}')">✅ Pagar</button>`:''}
          <button class="btn bedt bsm" onclick="openModal('bill','${x.id}')">✏️</button>
          <button class="btn bdel bsm" onclick="delItem('bills','${x.id}')">🗑️</button>
        </div>
      </div>
    </div>`;
  }).join('');
  const total = list.reduce((a,x)=>a+Number(x.amount),0);
  document.getElementById('bTotV').textContent = fmt(total);
  tot.style.display='flex';
}

function renderUnexpected(){
  const list = md('unexpected');
  const el = document.getElementById('unexpectedList');
  const tot = document.getElementById('uTot');
  if(!list.length){
    el.innerHTML = `<div class="empty"><div class="ei">⚡</div><p>Sin imprevistos registrados este mes.<br>Toca "+ Registrar" para agregar uno.</p></div>`;
    tot.style.display='none'; return;
  }
  el.innerHTML = list.map(x=>`
    <div class="card cu">
      <div class="cmain">
        <div class="cicon iyh">${ICONS.unexpected[x.category]||'📌'}</div>
        <div class="cinfo">
          <div class="cname">${esc(x.name)}</div>
          <div class="cmeta">${fmtDate(x.date)}</div>
          ${x.note?`<div class="cnote">${esc(x.note)}</div>`:''}
        </div>
        <div class="cright"><div class="camt ay">${fmt(x.amount)}</div></div>
      </div>
      <div class="cfoot">
        <span></span>
        <div class="cacts">
          <button class="btn bedt bsm" onclick="openModal('unexpected','${x.id}')">✏️ Editar</button>
          <button class="btn bdel bsm" onclick="delItem('unexpected','${x.id}')">🗑️</button>
        </div>
      </div>
    </div>`).join('');
  const total = list.reduce((a,x)=>a+Number(x.amount),0);
  document.getElementById('uTotV').textContent = fmt(total);
  tot.style.display='flex';
}

// ── MARK PAID ───────────────────────────────────────────
function markPaid(id){
  const item = md('bills').find(x=>x.id===id);
  if(item){ item.status='paid'; item.paidDate=new Date().toISOString().slice(0,10); }
  saveLocal(); scheduleDriveSync(); renderAll(); showToast('✅ Cuenta marcada como pagada');
}

// ── ESCAPE HTML ─────────────────────────────────────────
function esc(s){ const d=document.createElement('div'); d.textContent=s; return d.innerHTML; }

// ── MODALS ──────────────────────────────────────────────
function openModal(type, id){
  const today = new Date().toISOString().slice(0,10);
  document.getElementById('modal-'+type).classList.add('open');

  if(type==='income'){
    const eid = document.getElementById('iEId');
    eid.value = id||'';
    if(id){
      const x = md('income').find(i=>i.id===id);
      document.getElementById('iMT').textContent='Editar ingreso';
      document.getElementById('iName').value=x.name;
      document.getElementById('iAmt').value=x.amount;
      document.getElementById('iDate').value=x.date;
      document.getElementById('iType').value=x.type;
      document.getElementById('iNote').value=x.note||'';
    } else {
      document.getElementById('iMT').textContent='Nuevo ingreso';
      document.getElementById('iName').value='';
      document.getElementById('iAmt').value='';
      document.getElementById('iDate').value=today;
      document.getElementById('iType').value='salary';
      document.getElementById('iNote').value='';
    }
  }
  if(type==='bill'){
    document.getElementById('bEId').value=id||'';
    if(id){
      const x=md('bills').find(i=>i.id===id);
      document.getElementById('bMT').textContent='Editar cuenta';
      document.getElementById('bName').value=x.name;
      document.getElementById('bAmt').value=x.amount;
      document.getElementById('bDue').value=x.dueDay||'';
      document.getElementById('bCat').value=x.category;
      document.getElementById('bStat').value=x.status;
      document.getElementById('bPaidDate').value=x.paidDate||'';
      document.getElementById('bNote').value=x.note||'';
    } else {
      document.getElementById('bMT').textContent='Nueva cuenta fija';
      ['bName','bAmt','bDue','bPaidDate','bNote'].forEach(i=>document.getElementById(i).value='');
      document.getElementById('bCat').value='housing';
      document.getElementById('bStat').value='pending';
    }
  }
  if(type==='unexpected'){
    document.getElementById('uEId').value=id||'';
    if(id){
      const x=md('unexpected').find(i=>i.id===id);
      document.getElementById('uMT').textContent='Editar imprevisto';
      document.getElementById('uName').value=x.name;
      document.getElementById('uAmt').value=x.amount;
      document.getElementById('uDate').value=x.date;
      document.getElementById('uCat').value=x.category;
      document.getElementById('uNote').value=x.note||'';
    } else {
      document.getElementById('uMT').textContent='Nuevo imprevisto';
      ['uName','uAmt','uNote'].forEach(i=>document.getElementById(i).value='');
      document.getElementById('uDate').value=today;
      document.getElementById('uCat').value='health';
    }
  }
}
function closeModal(t){ document.getElementById('modal-'+t).classList.remove('open'); }
document.querySelectorAll('.mover').forEach(o=>o.addEventListener('click',e=>{if(e.target===o)o.classList.remove('open')}));

// ── DRIVE MODAL ─────────────────────────────────────────
function openDriveModal(){
  document.getElementById('driveFileId').value = driveFileId;
  document.getElementById('modal-drive').classList.add('open');
}
function saveDriveId(){
  const val = document.getElementById('driveFileId').value.trim();
  if(!val){ showToast('⚠️ Pega el ID del archivo'); return; }
  driveFileId = val;
  localStorage.setItem('mf_drive_id', val);
  closeModal('drive');
  showToast('☁️ ID guardado. Sincronizando…');
  syncNow();
}

// ── SAVE INCOME ─────────────────────────────────────────
function saveIncome(){
  const name=document.getElementById('iName').value.trim();
  const amount=parseFloat(document.getElementById('iAmt').value);
  if(!name||!amount){showToast('⚠️ Completa nombre y monto');return;}
  const eid=document.getElementById('iEId').value;
  const item={id:eid||Date.now().toString(),name,amount,
    date:document.getElementById('iDate').value,
    type:document.getElementById('iType').value,
    note:document.getElementById('iNote').value.trim()};
  const list=md('income');
  if(eid){ const i=list.findIndex(x=>x.id===eid); list[i]=item; showToast('✅ Ingreso actualizado'); }
  else { list.push(item); showToast('✅ Ingreso registrado'); }
  saveLocal(); scheduleDriveSync(); renderAll(); closeModal('income');
}

// ── SAVE BILL ────────────────────────────────────────────
function saveBill(){
  const name=document.getElementById('bName').value.trim();
  const amount=parseFloat(document.getElementById('bAmt').value);
  if(!name||!amount){showToast('⚠️ Completa nombre y monto');return;}
  const eid=document.getElementById('bEId').value;
  const item={id:eid||Date.now().toString(),name,amount,
    dueDay:document.getElementById('bDue').value,
    category:document.getElementById('bCat').value,
    status:document.getElementById('bStat').value,
    paidDate:document.getElementById('bPaidDate').value,
    note:document.getElementById('bNote').value.trim()};
  const list=md('bills');
  if(eid){ const i=list.findIndex(x=>x.id===eid); list[i]=item; showToast('✅ Cuenta actualizada'); }
  else { list.push(item); showToast('✅ Cuenta registrada'); }
  saveLocal(); scheduleDriveSync(); renderAll(); closeModal('bill');
}

// ── SAVE UNEXPECTED ──────────────────────────────────────
function saveUnexpected(){
  const name=document.getElementById('uName').value.trim();
  const amount=parseFloat(document.getElementById('uAmt').value);
  if(!name||!amount){showToast('⚠️ Completa descripción y monto');return;}
  const eid=document.getElementById('uEId').value;
  const item={id:eid||Date.now().toString(),name,amount,
    date:document.getElementById('uDate').value,
    category:document.getElementById('uCat').value,
    note:document.getElementById('uNote').value.trim()};
  const list=md('unexpected');
  if(eid){ const i=list.findIndex(x=>x.id===eid); list[i]=item; showToast('✅ Imprevisto actualizado'); }
  else { list.push(item); showToast('✅ Imprevisto registrado'); }
  saveLocal(); scheduleDriveSync(); renderAll(); closeModal('unexpected');
}

// ── DELETE ────────────────────────────────────────────────
function delItem(type,id){
  if(!confirm('¿Eliminar este registro?')) return;
  db[type][currentMonth] = db[type][currentMonth].filter(x=>x.id!==id);
  saveLocal(); scheduleDriveSync(); renderAll(); showToast('🗑️ Eliminado');
}

// ── LOCAL STORAGE ─────────────────────────────────────────
function saveLocal(){ localStorage.setItem('mf_data', JSON.stringify(db)); }

// ── DRIVE SYNC ────────────────────────────────────────────
function setSyncStatus(state, msg){
  const dot=document.getElementById('sdot');
  const sm=document.getElementById('smsg');
  dot.className='sdot '+state;
  sm.textContent=msg;
}

async function loadFromDrive(){
  if(!driveFileId){ setSyncStatus('','Sin Drive configurado'); return; }
  setSyncStatus('busy','Cargando desde Drive…');
  try {
    const res = await gFetch(`https://www.googleapis.com/drive/v3/files/${driveFileId}?alt=media`);
    if(res.ok){
      const text = await res.text();
      if(text.trim()) db = JSON.parse(text);
      saveLocal();
      setSyncStatus('ok','Sincronizado ✓');
    } else {
      throw new Error('HTTP '+res.status);
    }
  } catch(e){
    // Fallback to local
    const local=localStorage.getItem('mf_data');
    if(local) db=JSON.parse(local);
    setSyncStatus('err','Sin conexión — datos locales');
  }
}

async function syncNow(){
  if(!driveFileId){
    openDriveModal(); return;
  }
  setSyncStatus('busy','Guardando en Drive…');
  try {
    const json = JSON.stringify(db, null, 2);
    const res = await gFetch(
      `https://www.googleapis.com/upload/drive/v3/files/${driveFileId}?uploadType=media`,
      { method:'PATCH', headers:{'Content-Type':'application/json'}, body:json }
    );
    if(res.ok){
      setSyncStatus('ok','Guardado en Drive ✓ · '+new Date().toLocaleTimeString('es-CO',{hour:'2-digit',minute:'2-digit'}));
      showToast('☁️ Guardado en Google Drive');
    } else {
      throw new Error('HTTP '+res.status);
    }
  } catch(e){
    setSyncStatus('err','Error al guardar — revisa el ID');
    showToast('❌ Error al guardar en Drive');
  }
}

// Auto-sync 3 seconds after last change
function scheduleDriveSync(){
  clearTimeout(syncTimer);
  if(driveFileId) syncTimer = setTimeout(syncNow, 3000);
}

// ── GOOGLE API FETCH ──────────────────────────────────────
// Uses gapi token if available, else prompts sign-in
let gapiToken = null;

async function gFetch(url, opts={}){
  // Try with existing token
  if(gapiToken){
    const r = await fetch(url, { ...opts, headers:{...(opts.headers||{}), Authorization:'Bearer '+gapiToken}});
    if(r.status!==401) return r;
  }
  // Need to get token via Google Sign-In
  gapiToken = await getGoogleToken();
  return fetch(url, { ...opts, headers:{...(opts.headers||{}), Authorization:'Bearer '+gapiToken}});
}

function getGoogleToken(){
  return new Promise((resolve, reject)=>{
    // Use Google Identity Services
    if(!window.google){ loadGIS().then(()=>getGoogleToken().then(resolve).catch(reject)); return; }
    const client = google.accounts.oauth2.initTokenClient({
      client_id: '748914899891-placeholder.apps.googleusercontent.com', // ← Reemplazar con tu Client ID
      scope: 'https://www.googleapis.com/auth/drive.file',
      callback: (r)=>{ if(r.error){ reject(r.error); return; } gapiToken=r.access_token; resolve(r.access_token); }
    });
    client.requestAccessToken();
  });
}

function loadGIS(){
  return new Promise(resolve=>{
    const s=document.createElement('script');
    s.src='https://accounts.google.com/gsi/client';
    s.onload=resolve;
    document.head.appendChild(s);
  });
}

// ── TOAST ─────────────────────────────────────────────────
function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg; t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2800);
}
</script>
</body>
</html>
