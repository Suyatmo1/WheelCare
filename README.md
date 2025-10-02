# WheelCare
<!DOCTYPE html>
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
      display: block;
      margin: 8px 0 4px;
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
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 12px;
    }
    .checkbox-group label {
      font-weight: normal;
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
      <label>Engine oil <input type="checkbox" id="engineOil"></label>
      <label>Transmission oil <input type="checkbox" id="transOil"></label>
      <label>Hydraulic oil <input type="checkbox" id="hydOil"></label>
    </div>

    <h3>⚙ Engine Area</h3>
    <div class="checkbox-group">
      <label>Belt tension <input type="checkbox" id="belt"></label>
      <label>Oil leakage <input type="checkbox" id="oilLeak"></label>
      <label>Common Rail Connector <input type="checkbox" id="crc"></label>
      <label>Injector Tube <input type="checkbox" id="injector"></label>
    </div>

    <h3>🚗 Cabin Area</h3>
    <div class="checkbox-group">
      <label>FM Radio <input type="checkbox" id="radio"></label>
      <label>Fatigue Warning <input type="checkbox" id="fatigue"></label>
      <label>Power Window <input type="checkbox" id="pw"></label>
    </div>
    <label>⚡ Power Supply</label>
    <input type="text" id="powerSupply" placeholder="contoh: 27.7 V">
    <label>💧 Common Rail Pressure (ON)</label>
    <input type="text" id="crp" placeholder="contoh: 0 MPa">

    <h3>🚗 Frame Area</h3>
    <div class="checkbox-group">
      <label>Operator seat <input type="checkbox" id="seat"></label>
      <label>Hand Rail <input type="checkbox" id="rail"></label>
    </div>

    <h3>💧 Pressure Suspension (Panel)</h3>
    <label>FL</label><input type="text" id="fl">
    <label>FR</label><input type="text" id="fr">
    <label>RL</label><input type="text" id="rl">
    <label>RR</label><input type="text" id="rr">

    <h3>📝 Validasi & Kelengkapan Service</h3>
    <div class="checkbox-group">
      <label>Job Card & Cover Checklist <input type="checkbox" id="jobCard"></label>
      <label>Form Observasi Redo PS <input type="checkbox" id="redo"></label>
      <label>Form QA 1 & QA 7 <input type="checkbox" id="qaForm"></label>
      <label>Form PPM <input type="checkbox" id="ppm"></label>
      <label>Checklist A <input type="checkbox" id="a"></label>
      <label>Checklist B <input type="checkbox" id="b"></label>
      <label>Checklist C <input type="checkbox" id="c"></label>
      <label>Backlog <input type="checkbox" id="backlog"></label>
      <label>FUI <input type="checkbox" id="fui"></label>
      <label>Repair Order <input type="checkbox" id="ro"></label>
      <label>Combine Maintenance <input type="checkbox" id="combine"></label>
      <label>Service Activity Report <input type="checkbox" id="sar"></label>
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
