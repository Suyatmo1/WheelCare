# WheelCare
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Inspection Report</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; }
    label { margin-top: 10px; display: block; font-weight: bold; }
    .section { border: 1px solid #ccc; padding: 10px; margin-top: 15px; border-radius: 8px; }
    .item { display: flex; justify-content: space-between; margin: 5px 0; }
    select, input, textarea, button {
      padding: 6px; margin-top: 5px; width: 100%; box-sizing: border-box;
    }
    button { margin-top: 15px; border-radius: 5px; border: none; font-weight: bold; cursor: pointer; }
    .wa { background: green; color: white; padding: 10px; }
    .copy { background: #444; color: white; padding: 10px; }
    #preview { white-space: pre-wrap; background: #1c1c1c; color: #e6e6e6; padding: 15px; border-radius: 10px; margin-top: 20px; font-family: monospace; }
    .actions { margin-top: 20px; display: flex; gap: 10px; }
    .opt { width: auto; margin-left: 10px; }
  </style>
</head>
<body>
  <h2>Inspection Report HD785-7</h2>

  <label>Pilih Jenis Inspection:</label>
  <select id="jenisQA">
    <option value="QA-1">QA-1 Pre Inspection</option>
    <option value="QA-7">QA-7 Final Inspection</option>
  </select>

  <label>Code Number:</label>
  <input type="text" id="codeNumber">

  <label>Date:</label>
  <input type="date" id="date">

  <label>Hourmeter:</label>
  <input type="text" id="hourMeter">

  <label>Mekanik:</label>
  <input type="text" id="mekanik">

  <!-- Oil Level -->
  <div class="section">
    <label>🩸 Oil Level</label>
    <div class="item">Engine oil level:
      <select id="oil_engine" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Transmission oil level:
      <select id="oil_trans" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Hydraulic oil level:
      <select id="oil_hyd" class="opt"><option>✅</option><option>❌</option></select>
    </div>
  </div>

  <!-- Engine Area -->
  <div class="section">
    <label>⚙ Engine Area</label>
    <div class="item">Belt tension:
      <select id="eng_belt" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Engine oil leakage:
      <select id="eng_leak" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Common Rail Connector:
      <select id="eng_cr" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Injector Tube:
      <select id="eng_inj" class="opt"><option>✅</option><option>❌</option></select>
    </div>
  </div>

  <!-- Cabin Area -->
  <div class="section">
    <label>🚗 Cabin Area</label>
    <div class="item">FM Radio:
      <select id="cab_radio" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Fatigue Warning:
      <select id="cab_fatigue" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Power Supply:
      <input type="text" id="cab_power" placeholder="contoh: 25.7 V" class="opt">
    </div>
    <div class="item">Common Rail Pressure (ON):
      <input type="text" id="cab_crpress" placeholder="contoh: 0 MPa" class="opt">
    </div>
    <div class="item">Power Window:
      <select id="cab_window" class="opt"><option>✅</option><option>❌</option></select>
    </div>
  </div>


  <!-- Frame Area -->
  <div class="section">
    <label>🚗 Frame Area</label>
    <div class="item">Operator seat:
      <select id="fr_seat" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Hand Rail:
      <select id="fr_hand" class="opt"><option>✅</option><option>❌</option></select>
    </div>
  </div>

  <!-- Suspension -->
  <div class="section">
    <label>💧 Pressure Suspension (Panel)</label>
    <div class="item">FL: <input type="text" id="sus_fl" placeholder="contoh: 3.80 MPa" class="opt"></div>
    <div class="item">FR: <input type="text" id="sus_fr" placeholder="contoh: 3.50 MPa" class="opt"></div>
    <div class="item">RL: <input type="text" id="sus_rl" placeholder="contoh: 2.00 MPa" class="opt"></div>
    <div class="item">RR: <input type="text" id="sus_rr" placeholder="contoh: 2.09 MPa" class="opt"></div>
  </div>

  <label>Tyre Condition:</label>
  <input type="text" id="tyre" placeholder="Good / Worn / dll">

  <label>Deviation:</label>
  <textarea id="deviation" rows="3"></textarea>

  <div class="actions"
   <!-- Validasi dan kelengkapan Check list Service-->
  <div class="section">
    <label>  Validasi dan kelengkapan Check list Service </label>
    <div class="item"> Job Card & Cover Check List:
      <select id="cab_radio" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Fatigue Warning:
      <select id="cab_fatigue" class="opt"><option>✅</option><option>❌</option></select>
    </div>
    <div class="item">Power Supply:
      <input type="text" id="cab_power" placeholder="contoh: 25.7 V" class="opt">
    </div>
    <div class="item">Common Rail Pressure (ON):
      <input type="text" id="cab_crpress" placeholder="contoh: 0 MPa" class="opt">
    </div>
    <div class="item">Power Window:
      <select id="cab_window" class="opt"><option>✅</option><option>❌</option></select>
    </div>
  </div>
   
    <button onclick="previewReport()">🔍 PREVIEW</button>
  </div>

    

  <h3>📋 Preview Report:</h3>
  <div id="preview">Belum ada data...</div>

  <div class="actions">
    <button class="wa" onclick="sendReport()">📲 Send to WhatsApp</button>
    <button class="copy" onclick="copyReport()">📋 Copy to Clipboard</button>
  </div>

  <script>
    let pesan = "";
    function previewReport() {
      let jenisQA = document.getElementById("jenisQA").value;
      let codeNumber = document.getElementById("codeNumber").value;
      let date = document.getElementById("date").value;
      let hourMeter = document.getElementById("hourMeter").value;
      let mekanik = document.getElementById("mekanik").value;

      // oil level
      let oil_engine = document.getElementById("oil_engine").value;
      let oil_trans = document.getElementById("oil_trans").value;
      let oil_hyd = document.getElementById("oil_hyd").value;

      // engine
      let eng_belt = document.getElementById("eng_belt").value;
      let eng_leak = document.getElementById("eng_leak").value;
      let eng_cr = document.getElementById("eng_cr").value;
      let eng_inj = document.getElementById("eng_inj").value;

      // cabin
      let cab_radio = document.getElementById("cab_radio").value;
      let cab_fatigue = document.getElementById("cab_fatigue").value;
      let cab_power = document.getElementById("cab_power").value;
      let cab_crpress = document.getElementById("cab_crpress").value;
      let cab_window = document.getElementById("cab_window").value;

      // frame
      let fr_seat = document.getElementById("fr_seat").value;
      let fr_hand = document.getElementById("fr_hand").value;

      // suspension
      let sus_fl = document.getElementById("sus_fl").value;
      let sus_fr = document.getElementById("sus_fr").value;
      let sus_rl = document.getElementById("sus_rl").value;
      let sus_rr = document.getElementById("sus_rr").value;

      let tyre = document.getElementById("tyre").value;
      let deviation = document.getElementById("deviation").value;

      pesan =
`*${jenisQA === "QA-1" ? "QA-1 Pre Inspection" : "QA-7 Final Inspection"}*

📅 Tgl : ${date}
👷 Mekanik : ${mekanik}

🚗 CN : ${codeNumber}
⌛ HM : ${hourMeter}

🩸 *Oil Level* 🩸
Engine oil level : ${oil_engine}
Transmission oil level : ${oil_trans}
Hydraulic oil level : ${oil_hyd}

⚙ *Engine Area* ⚙
Belt tension : ${eng_belt}
Engine oil leakage : ${eng_leak}
Common Rail Connector : ${eng_cr}
Injector Tube : ${eng_inj}

🚗 *Cabin Area*🚗
📸 FM Radio : ${cab_radio}
⛔ Fatigue Warning : ${cab_fatigue}
⚡ Power Supply : ${cab_power}
💧 Common Rail Pressure (ON) : ${cab_crpress}
🎚 Power Window : ${cab_window}

🚗 *Frame Area* 🚗
Operator seat : ${fr_seat}
Hand Rail : ${fr_hand}

💧 *Pressure Suspension (Panel)* 💧
FL : ${sus_fl}
FR : ${sus_fr}
RL : ${sus_rl}
RR : ${sus_rr}

*Tyre condition :*
Tyre : ${tyre}

*Deviation :*
${deviation}`;

      document.getElementById("preview").innerText = pesan;
    }

    function sendReport() {
      if (!pesan) { alert("Klik PREVIEW dulu sebelum kirim WA!"); return; }
      let url = "https://wa.me/?text=" + encodeURIComponent(pesan);
      window.open(url, "_blank");
    }

    function copyReport() {
      if (!pesan) { alert("Klik PREVIEW dulu untuk generate pesan!"); return; }
      navigator.clipboard.writeText(pesan).then(() => {
        alert("✅ Pesan sudah disalin, tinggal paste ke WhatsApp!");
      });
    }
  </script>
</body>
</html>
