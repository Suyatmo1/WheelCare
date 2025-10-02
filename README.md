# WheelCare
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Inspection Report</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; }
    label { display: block; margin-top: 10px; }
    select, input, button, textarea {
      padding: 8px; margin-top: 5px; width: 100%; box-sizing: border-box;
    }
    button { 
      margin-top: 15px; 
      padding: 10px; 
      border-radius: 5px; 
      border: none; 
      font-weight: bold; 
      cursor: pointer; 
    }
    .wa { background: green; color: white; }
    .copy { background: #444; color: white; }
    #preview { 
      white-space: pre-wrap; 
      background: #1c1c1c; 
      color: #e6e6e6; 
      padding: 15px; 
      border-radius: 10px; 
      margin-top: 20px; 
      font-family: monospace;
    }
    .actions { margin-top: 20px; display: flex; gap: 10px; }
  </style>
</head>
<body>
  <h2>Inspection Report HD</h2>

  <label>Code Number:</label>
  <input type="text" id="codeNumber">

  <label>Date:</label>
  <input type="date" id="date">

  <label>Hourmeter:</label>
  <input type="text" id="hourMeter">

  <label>Mekanik:</label>
  <input type="text" id="mekanik">

  <label>Tyre Condition:</label>
  <input type="text" id="tyre">

  <label>Deviation:</label>
  <textarea id="deviation" rows="3"></textarea>

  <label>Pilih Tujuan Kirim:</label>
  <select id="tujuan">
    <option value="6281234567890">Supervisor</option>
    <option value="6289876543210">Admin Group</option>
    <option value="6281122334455">Personal Lain</option>
  </select>

  <button onclick="previewReport()">PREVIEW</button>

  <h3>📋 Preview Report:</h3>
  <div id="preview">Belum ada data...</div>

  <div class="actions">
    <button class="wa" onclick="sendReport()">📲 Send to WhatsApp</button>
    <button class="copy" onclick="copyReport()">📋 Copy to Clipboard</button>
  </div>

  <script>
    let pesan = "";
    function previewReport() {
      let codeNumber = document.getElementById("codeNumber").value;
      let date = document.getElementById("date").value;
      let hourMeter = document.getElementById("hourMeter").value;
      let mekanik = document.getElementById("mekanik").value;
      let tyre = document.getElementById("tyre").value;
      let deviation = document.getElementById("deviation").value;

      pesan =
`*QA-1 Pre Inspection*

📅 Tgl : ${date}
👷 Mekanik : ${mekanik}

🚗 CN : ${codeNumber}
⌛ HM : ${hourMeter}

🩸 *Oil Level* 🩸
Engine oil level : ✅
Transmission oil level : ✅
Hydraulic oil level : ✅

⚙ *Engine Area* ⚙
Belt tension : ✅
Engine oil leakage : ✅
Common Rail Connector : ✅
Injector Tube : ✅

*Tyre condition :* ${tyre}

*Deviation :*
${deviation}`;

      document.getElementById("preview").innerText = pesan;
    }

    function sendReport() {
      let tujuan = document.getElementById("tujuan").value;
      if (!pesan) {
        alert("Klik PREVIEW dulu sebelum kirim WA!");
        return;
      }
      let url = "https://wa.me/" + tujuan + "?text=" + encodeURIComponent(pesan);
      window.open(url, "_blank");
    }

    function copyReport() {
      if (!pesan) {
        alert("Klik PREVIEW dulu untuk generate pesan!");
        return;
      }
      navigator.clipboard.writeText(pesan).then(() => {
        alert("✅ Pesan sudah disalin, tinggal paste ke WhatsApp!");
      });
    }
  </script>
</body>
</html>
