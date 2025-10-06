# WheelCare
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Inspection Report</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(to right, #f0f4ff, #d9e4ff);
      margin: 0;
      padding: 20px;
    }
    .card {
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
      padding: 20px;
      margin-bottom: 20px;
    }
    h2 {
      text-align: center;
      color: #2c3e50;
      margin-bottom: 15px;
    }
    label {
      font-weight: bold;
      color: #333;
    }
    input, select, textarea {
      width: 100%;
      padding: 8px;
      border: 1px solid #aaa;
      border-radius: 8px;
      margin-bottom: 12px;
    }
    .checkbox-group {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 8px;
      margin-bottom: 12px;
    }
    .checkbox-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #f9f9f9;
      border: 1px solid #ddd;
      border-radius: 6px;
      padding: 6px 10px;
    }
    .checkbox-item label {
      font-weight: normal;
      flex: 1;
    }
    .checkbox-item input {
      transform: scale(1.2);
      margin-left: 8px;
    }
    button {
      padding: 12px;
      margin: 5px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      color: #fff;
    }
    .btn-wa { background: #25d366; }
    .btn-copy { background: #3498db; }
    .output {
      white-space: pre-wrap;
      background: #f9f9f9;
      border-radius: 8px;
      padding: 15px;
      margin-top: 20px;
      border: 1px solid #ccc;
    }
  </style>
</head>
<body>

  <div class="card">
    <h2>Form Inspection</h2>

    <label>Pilih Jenis QA</label>
    <select id="qaType">
      <option value="QA-1 Pre Inspection">QA-1 Pre Inspection</option>
      <option value="QA-7 Final Inspection">QA-7 Final Inspection</option>
    </select>

    <label>📅 Tanggal</label>
    <input type="date" id="tanggal">

    <label>👷 Mekanik</label>
    <input type="text" id="mekanik" placeholder="contoh: Mario, Jovan">

    <label>🚗 CN</label>
    <input type="text" id="cn">

    <label>⌛ HM</label>
    <input type="text" id="hm">

    <h3>🩸 Oil Level</h3>
    <div class="checkbox-group">
      <div class="checkbox-item"><label>Engine oil</label><input type="checkbox" id="engineOil"></div>
      <div class="checkbox-item"><label>Transmission oil</label><input type="checkbox" id="transOil"></div>
      <div class="checkbox-item"><label>Hydraulic oil</label><input type="checkbox" id="hydOil"></div>
    </div>

    <h3>⚙ Engine Area</h3>
    <div class="checkbox-group">
      <div class="checkbox-item"><label>Belt tension</label><input type="checkbox" id="belt"></div>
      <div class="checkbox-item"><label>Oil leakage</label><input type="checkbox" id="oilLeak"></div>
      <div class="checkbox-item"><label>Common Rail Connector</label><input type="checkbox" id="crc"></div>
      <div class="checkbox-item"><label>Injector Tube</label><input type="checkbox" id="injector"></div>
    </div>

    <h3>🚗 Cabin Area</h3>
    <div class="checkbox-group">
      <div class="checkbox-item"><label>FM Radio</label><input type="checkbox" id="radio"></div>
      <div class="checkbox-item"><label>Fatigue Warning</label><input type="checkbox" id="fatigue"></div>
      <div class="checkbox-item"><label>Power Window</label><input type="checkbox" id="pw"></div>
    </div>
    <label>⚡ Power Supply</label>
    <input type="text" id="powerSupply" placeholder="contoh: 27.7 V">
    <label>💧 Common Rail Pressure (ON)</label>
    <input type="text" id="crp" placeholder="contoh: 0 MPa">

    <h3>🚗 Frame Area</h3>
    <div class="checkbox-group">
      <div class="checkbox-item"><label>Operator seat</label><input type="checkbox" id="seat"></div>
      <div class="checkbox-item"><label>Hand Rail</label><input type="checkbox" id="rail"></div>
    </div>

    <h3>💧 Pressure Suspension (Panel)</h3>
    <label>FL</label><input type="text" id="fl">
    <label>FR</label><input type="text" id="fr">
    <label>RL</label><input type="text" id="rl">
    <label>RR</label><input type="text" id="rr">

    <h3>📝 Validasi & Kelengkapan Service</h3>
    <div class="checkbox-group">
      <div class="checkbox-item"><label>Job Card & Cover Checklist</label><input type="checkbox" id="jobCard"></div>
      <div class="checkbox-item"><label>Form Observasi Redo PS</label><input type="checkbox" id="redo"></div>
      <div class="checkbox-item"><label>Form QA 1 & QA 7</label><input type="checkbox" id="qaForm"></div>
      <div class="checkbox-item"><label>Form PPM</label><input type="checkbox" id="ppm"></div>
      <div class="checkbox-item"><label>Checklist A</label><input type="checkbox" id="a"></div>
      <div class="checkbox-item"><label>Checklist B</label><input type="checkbox" id="b"></div>
      <div class="checkbox-item"><label>Checklist C</label><input type="checkbox" id="c"></div>
      <div class="checkbox-item"><label>Backlog</label><input type="checkbox" id="backlog"></div>
      <div class="checkbox-item"><label>FUI</label><input type="checkbox" id="fui"></div>
      <div class="checkbox-item"><label>Repair Order</label><input type="checkbox" id="ro"></div>
      <div class="checkbox-item"><label>Combine Maintenance</label><input type="checkbox" id="combine"></div>
      <div class="checkbox-item"><label>Service Activity Report</label><input type="checkbox" id="sar"></div>
    </div>

    <label>*Tyre Condition*</label>
    <input type="text" id="tyre" placeholder="Good / Replace">

    <label>*Deviation*</label>
    <textarea id="deviation" rows="3"></textarea>

    <button class="btn-wa" onclick="sendWA()">📤 Send to WA</button>
    <button class="btn-copy" onclick="copyText()">📋 Copy</button>

    <div class="output" id="output"></div>
  </div>

<script>
function getCheck(id){ return document.getElementById(id).checked ? "✅" : "❌"; }

function generateText(){
  let text = `*${document.getElementById('qaType').value}*\n\n` +
  `📅 Tgl : ${document.getElementById('tanggal').value}\n` +
  `👷 Mekanik : ${document.getElementById('mekanik').value}\n\n` +
  `🚗 CN : ${document.getElementById('cn').value}\n` +
  `⌛ HM : ${document.getElementById('hm').value}\n\n` +
  `🩸 *Oil Level* 🩸\n` +
  `Engine oil level : ${getCheck('engineOil')}\n` +
  `Transmission oil level : ${getCheck('transOil')}\n` +
  `Hydraulic oil level : ${getCheck('hydOil')}\n\n` +
  `⚙ *Engine Area* ⚙\n` +
  `Belt tension : ${getCheck('belt')}\n` +
  `Engine oil leakage : ${getCheck('oilLeak')}\n` +
  `Common Rail Connector : ${getCheck('crc')}\n` +
  `Injector Tube : ${getCheck('injector')}\n\n` +
  `🚗 *Cabin Area* 🚗\n` +
  `📸 FM Radio : ${getCheck('radio')}\n` +
  `⛔ Fatigue Warning : ${getCheck('fatigue')}\n` +
  `⚡ Power Supply : ${document.getElementById('powerSupply').value}\n` +
  `💧 Common Rail Pressure (ON) : ${document.getElementById('crp').value}\n` +
  `🖼️ Power Window : ${getCheck('pw')}\n\n` +
  `🚗 *Frame Area* 🚗\n` +
  `Operator seat : ${getCheck('seat')}\n` +
  `Hand Rail : ${getCheck('rail')}\n\n` +
  `💧 *Pressure Suspension (Panel)* 💧\n` +
  `FL : ${document.getElementById('fl').value}\n` +
  `FR : ${document.getElementById('fr').value}\n` +
  `RL : ${document.getElementById('rl').value}\n` +
  `RR : ${document.getElementById('rr').value}\n\n` +
  `📝 Validasi & Kelengkapan Check list Service :\n` +
  `- Job Card & Cover Checklist ${getCheck('jobCard')}\n` +
  `- Form Observasi Redo PS ${getCheck('redo')}\n` +
  `- Form QA 1 & QA 7 ${getCheck('qaForm')}\n` +
  `- Form PPM ${getCheck('ppm')}\n` +
  `- Form Checklist A ${getCheck('a')}\n` +
  `- Form Checklist B ${getCheck('b')}\n` +
  `- Form Checklist C ${getCheck('c')}\n` +
  `- Form Backlog ${getCheck('backlog')}\n` +
  `- Form FUI ${getCheck('fui')}\n` +
  `- Form Repair Order ${getCheck('ro')}\n` +
  `- Form Combine Maintenance ${getCheck('combine')}\n` +
  `- Form Service Activity Report ${getCheck('sar')}\n\n` +
  `*Tyre condition :*\nTyre : ${document.getElementById('tyre').value}\n\n` +
  `*Deviation :*\n${document.getElementById('deviation').value}`;
  
  document.getElementById("output").innerText = text;
  return text;
}

function sendWA(){
  let text = generateText();
  let url = "https://wa.me/?text=" + encodeURIComponent(text);
  window.open(url, "_blank");
}

function copyText(){
  let text = generateText();
  navigator.clipboard.writeText(text).then(()=>{
    alert("✅ Teks berhasil disalin, tinggal tempel di WhatsApp.");
  });
}
</script>

</body>
</html>
