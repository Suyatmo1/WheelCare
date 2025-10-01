# WheelCare
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Inspection → WhatsApp</title>
  <style>
    body{font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial; background:#fffbe8; margin:0; padding:16px; color:#0b3b2e;}
    .card{background:#e7f7ee; border-radius:12px; padding:12px; box-shadow:0 4px 10px rgba(0,0,0,0.08); margin-bottom:14px}
    h1{margin:0 0 8px 0; font-size:20px; color:#2a6b4f}
    label{display:block; margin-top:8px; font-weight:600}
    input[type=text], input[type=date], input[type=number], textarea, select {
      width:100%; padding:10px; border-radius:8px; border:2px solid #9fd9b5; box-sizing:border-box; background:#fff;
    }
    textarea{min-height:80px}
    .row{display:flex; gap:8px}
    .col{flex:1}
    .checkbox-row{display:flex; gap:12px; align-items:center; margin-top:8px}
    .small-btn{padding:8px 10px; border-radius:8px; border:none; background:#fff; box-shadow:0 2px 6px rgba(0,0,0,0.08)}
    .green-btn{background:linear-gradient(90deg,#2ecc71,#27ae60); color:white; padding:12px; border-radius:12px; border:none; width:100%; font-weight:700; font-size:16px}
    .muted{color:#555; font-size:13px}
    .section-title{background:linear-gradient(90deg,#dff6e9,#c7efda); padding:6px 8px; border-radius:8px; font-weight:700; color:#0b6447; margin-top:10px}
    .deviation-list{margin-top:8px}
    .dev-item{background:#fff; padding:8px; border-radius:8px; box-shadow:0 2px 6px rgba(0,0,0,0.06); display:flex; gap:8px; align-items:center; margin-bottom:8px}
    .dev-item input{flex:1}
    .icon-small{font-size:18px}
    footer{margin-top:18px; text-align:center; color:#666; font-size:13px}
    .note{font-size:13px; color:#444; margin-top:6px}
    .flex-between{display:flex; justify-content:space-between; align-items:center}
  </style>
</head>
<body>

  <h1>Inspection → WhatsApp (HD Series)</h1>

  <div class="card">
    <div class="flex-between">
      <div>
        <div class="muted">Form</div>
        <div style="font-weight:800">QA-1 Pre Inspection</div>
      </div>
      <div class="muted" id="clock"></div>
    </div>

    <label>Unit Series</label>
    <select id="unitSeries">
      <option>HD series</option>
      <option>GD series</option>
      <option>Vessel HD785</option>
      <option>Small PC series</option>
    </select>

    <div class="row" style="margin-top:8px">
      <div class="col">
        <label>Code Number (CN)</label>
        <input type="text" id="codeNumber" placeholder="contoh DT4947">
      </div>
      <div style="width:140px">
        <label>Date</label>
        <input type="date" id="dateField">
      </div>
    </div>

    <div class="row" style="margin-top:8px">
      <div class="col">
        <label>Hourmeter</label>
        <input type="number" id="hourmeter" placeholder="35026">
      </div>
      <div style="width:140px">
        <label>PIC / Mekanik</label>
        <input type="text" id="pic" placeholder="History, Ismail, Rasyid">
      </div>
    </div>

    <div class="section-title">Oil Levels</div>
    <div class="checkbox-row">
      <label><input type="checkbox" id="oilEngine" checked> Engine oil level</label>
      <label><input type="checkbox" id="oilTrans" checked> Transmission oil level</label>
      <label><input type="checkbox" id="oilHyd" checked> Hydraulic oil level</label>
    </div>

    <div class="section-title">Engine Area</div>
    <div class="checkbox-row">
      <label><input type="checkbox" id="belt" checked> Belt tension</label>
      <label><input type="checkbox" id="oilLeak" checked> Engine oil leakage</label>
      <label><input type="checkbox" id="crc" checked> Common Rail Connector</label>
      <label><input type="checkbox" id="inj" checked> Injector Tube</label>
    </div>

    <div class="section-title">Cabin Area</div>
    <div class="checkbox-row">
      <label><input type="checkbox" id="fm" checked> FM Radio</label>
      <label><input type="checkbox" id="fatigue" checked> Fatigue Warning</label>
      <label style="display:flex; align-items:center"><span style="margin-right:6px">⚡</span>Power Supply <input id="power" type="text" placeholder="25.7 V" style="width:110px; margin-left:6px"></label>
    </div>
    <div class="checkbox-row" style="margin-top:6px">
      <label style="display:flex; align-items:center"><span style="margin-right:6px">💧</span>Common Rail Pressure (ON) <input id="crp" type="text" placeholder="0 MPa" style="width:100px; margin-left:6px"></label>
      <label style="display:flex; align-items:center; margin-left:6px"><span style="margin-right:6px">🎚</span>Power Window <input id="pw" type="checkbox" checked></label>
    </div>

    <div class="section-title">Frame Area</div>
    <div class="checkbox-row">
      <label><input type="checkbox" id="seat" checked> Operator seat</label>
      <label><input type="checkbox" id="rail" checked> Hand Rail</label>
    </div>

    <div class="section-title">Pressure Suspension (Panel)</div>
    <div class="row">
      <div class="col"><label>FL</label><input type="text" id="fl" placeholder="3.80 MPa"></div>
      <div class="col"><label>FR</label><input type="text" id="fr" placeholder="3.50 MPa"></div>
    </div>
    <div class="row" style="margin-top:6px">
      <div class="col"><label>RL</label><input type="text" id="rl" placeholder="1.90 MPa"></div>
      <div class="col"><label>RR</label><input type="text" id="rr" placeholder="2.09 MPa"></div>
    </div>

    <div class="section-title">Tyre</div>
    <label>Tyre Condition</label>
    <select id="tyreCond">
      <option>Good</option>
      <option>Fair</option>
      <option>Bad</option>
    </select>

    <div class="section-title">Deviation (add as needed)</div>
    <div class="deviation-list" id="devList"></div>
    <div style="display:flex; gap:8px; margin-top:8px">
      <input type="text" id="devInput" placeholder="ketik deviasi lalu klik Add" />
      <button class="small-btn" id="addDevBtn">+ Add</button>
    </div>

    <div class="section-title">Optional / Lainnya</div>
    <label>PIC (person in charge)</label>
    <input type="text" id="picField" placeholder="Nama PIC">

    <label class="note">Nomor WA tujuan (format internasional tanpa +, contoh: 6281234567890). Bisa diubah sebelum kirim.</label>
    <input type="text" id="waNumber" value="6281234567890">

    <div style="margin-top:12px">
      <button class="green-btn" id="btnSend">SEND TO WHATSAPP</button>
    </div>

    <div class="note">Catatan: pesan akan terbuka di WhatsApp; kamu harus menekan tombol Send di WhatsApp untuk benar-benar mengirim.</div>
  </div>

  <footer>HD785-7 WA Sender — HTML Preview</footer>

  <script>
    // set default date to today
    const dateEl = document.getElementById('dateField');
    const today = new Date().toISOString().split('T')[0];
    dateEl.value = today;

    // realtime clock display (optional)
    const clock = document.getElementById('clock');
    setInterval(() => {
      const d = new Date();
      clock.textContent = d.toLocaleString();
    }, 1000);

    // deviation list handling
    const devList = document.getElementById('devList');
    const devInput = document.getElementById('devInput');
    document.getElementById('addDevBtn').addEventListener('click', () => {
      const v = devInput.value.trim();
      if(!v) return;
      const id = 'd' + Date.now();
      const div = document.createElement('div');
      div.className = 'dev-item';
      div.id = id;
      div.innerHTML = '<div style="font-size:18px; padding-right:6px">⚠️</div>' +
                      '<input type="text" value="' + escapeHtml(v) + '" />' +
                      '<button class="small-btn" onclick="removeDev(\\''+id+'\\')">Del</button>';
      // using createElement with innerHTML string escape - safer to build
      devList.appendChild(div);
      // re-create properly to avoid escaped quotes issue:
      const inputEl = div.querySelector('input');
      const btnEl = div.querySelector('button');
      btnEl.addEventListener('click', () => div.remove());
      devInput.value = '';
    });

    function removeDev(id){ const el = document.getElementById(id); if(el) el.remove(); }

    // helper to escape HTML in values
    function escapeHtml(text) {
      return text.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot;");
    }

    // build message and open wa.me
    document.getElementById('btnSend').addEventListener('click', () => {
      // gather fields
      const unit = document.getElementById('unitSeries').value;
      const codeNumber = document.getElementById('codeNumber').value || '-';
      const date = document.getElementById('dateField').value || today;
      const hourmeter = document.getElementById('hourmeter').value || '-';
      const pic = document.getElementById('pic').value || document.getElementById('picField').value || '-';
      const tyre = document.getElementById('tyreCond').value;
      const waNumber = document.getElementById('waNumber').value.trim();

      // checkboxes
      function ok(id){ return document.getElementById(id).checked ? '✅' : '❌'; }
      const oilEngine = ok('oilEngine'), oilTrans = ok('oilTrans'), oilHyd = ok('oilHyd');
      const belt = ok('belt'), oilLeak = ok('oilLeak'), crc = ok('crc'), inj = ok('inj');
      const fm = ok('fm'), fatigue = ok('fatigue'), pw = document.getElementById('pw').checked ? '✅' : '❌';
      const power = document.getElementById('power').value || '-';
      const crp = document.getElementById('crp').value || '-';
      const seat = ok('seat'), rail = ok('rail');
      const fl = document.getElementById('fl').value || '-', fr = document.getElementById('fr').value || '-', rl = document.getElementById('rl').value || '-', rr = document.getElementById('rr').value || '-';

      // deviations gather
      const devNodes = devList.querySelectorAll('input');
      let devText = '';
      if(devNodes.length === 0) devText = 'None';
      else {
        devNodes.forEach((n) => {
          if(n.value.trim()) devText += '⚠ ' + n.value.trim() + '\n';
        });
        if(devText.endsWith('\n')) devText = devText.slice(0,-1);
      }

      // build message (WhatsApp supports *bold* by asterisks)
      let message = '';
      message += '*QA-1 Pre Inspection*' + '\n\n';
      message += 'Tgl : ' + formatDateForDisplay(date) + '\n\n';
      message += '*Mekanik :*' + '\n' + pic + '\n\n';
      message += '🚗 CN : ' + codeNumber + '\n';
      message += '⌛ HM : ' + hourmeter + '\n\n';

      message += '🩸 *Oil Level* 🩸\n';
      message += 'Engine oil level : ' + oilEngine + '\n';
      message += 'Transmission oil level : ' + oilTrans + '\n';
      message += 'Hydraulic oil level : ' + oilHyd + '\n\n';

      message += '⚙ *Engine Area* ⚙\n';
      message += 'Belt tension : ' + belt + '\n';
      message += 'Engine oil leakage : ' + oilLeak + '\n';
      message += 'Common Rail Connector : ' + crc + '\n';
      message += 'Injector Tube : ' + inj + '\n\n';

      message += '🚗 *Cabin Area* 🚗\n';
      message += '📸 FM Radio : ' + fm + '\n';
      message += '⛔ Fatigue Warning : ' + fatigue + '\n';
      message += '⚡ Power Supply : ' + power + '\n';
      message += '💧 Common Rail Pressure (ON) : ' + crp + '\n';
      message += '🎚 Power Window : ' + pw + '\n\n';

      message += '🚗 *Frame Area* 🚗\n';
      message += 'Operator seat : ' + seat + '\n';
      message += 'Hand Rail : ' + rail + '\n\n';

      message += '💧 *Pressure Suspension (Panel)* 💧\n';
      message += 'FL : ' + fl + '\n';
      message += 'FR : ' + fr + '\n';
      message += 'RL : ' + rl + '\n';
      message += 'RR : ' + rr + '\n\n';

      message += '*Tyre condition :*' + '\n';
      message += 'Tyre : Tyre Condition : ' + tyre + '\n\n';

      message += '*Deviation :*' + '\n' + devText + '\n';

      // add unit info at the top or bottom
      message += '\n*Unit Series:* ' + unit;

      // build URL
      const encoded = encodeURIComponent(message);
      // choose wa.me or api.whatsapp.com — wa.me is simpler
      const url = 'https://wa.me/' + waNumber + '?text=' + encoded;

      // open in new tab (mobile will redirect to WhatsApp app)
      window.open(url, '_blank');
    });

    function formatDateForDisplay(d){
      if(!d) return '';
      const parts = d.split('-');
      if(parts.length!==3) return d;
      return parts[2] + '-' + monthName(parts[1]) + '-' + parts[0];
    }
    function monthName(m){
      const a = {'01':'Jan','02':'Feb','03':'Mar','04':'Apr','05':'May','06':'Jun','07':'Jul','08':'Aug','09':'Sep','10':'Oct','11':'Nov','12':'Dec'};
      return a[m] || m;
    }
  </script>
</body>
</html>
