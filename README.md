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
    button { background: green; color: white; border: none; cursor: pointer; font-weight: bold; margin-top: 20px; padding: 10px; border-radius: 5px; }
    button:hover { background: darkgreen; }
    fieldset { margin-top: 15px; padding: 10px; border: 1px solid #ccc; }
    legend { font-weight: bold; }
    #preview { 
      white-space: pre-wrap; 
      background: #1c1c1c; 
      color: #e6e6e6; 
      padding: 15px; 
      border-radius: 10px; 
      margin-top: 20px; 
      font-family: monospace;
    }
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

  <fieldset>
    <legend>🩸 Oil Level</legend>
    Engine oil level:
    <select id="engineOil"><option>✅</option><option>❌</option></select><br>
    Transmission oil level:
    <select id="transOil"><option>✅</option><option>❌</option></select><br>
    Hydraulic oil level:
    <select id="hydOil"><option>✅</option><option>❌</option></select>
  </fieldset>

  <fieldset>
    <legend>⚙ Engine Area</legend>
    Belt tension:
    <select id="beltTension"><option>✅</option><option>❌</option></select><br>
    Engine oil leakage:
    <select id="oilLeak"><option>✅</option><option>❌</option></select><br>
    Common Rail Connector:
    <select id="crc"><option>✅</option><option>❌</option></select><br>
    Injector Tube:
    <select id="injector"><option>✅</option><option>❌</option></select>
  </fieldset>

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

  <button onclick="sendReport()">SEND TO WHATSAPP</button>

  <script>
    let pesan = "";
    function previewReport() {
      let codeNumber = document.getElementById("codeNumber").value;
      let date = document.getElementById("date").value;
      let hourMeter = document.getElementById("hourMeter").value;
      let mekanik = document.getElementById("mekanik").value;
      let tyre = document.getElementById("tyre").value;
      let deviation = document.getElementById("deviation").value;

      let engineOil = document.getElementById("engineOil").value;
      let transOil = document.getElementById("transOil").value;
      let hydOil = document.getElementById("hydOil").value;
      let beltTension = document.getElementById("beltTension").value;
      let oilLeak = document.getElementById("oilLeak").value;
      let crc = document.getElementById("crc").value;
      let injector = document.getElementById("injector").value;

      pesan =
`*QA-1 Pre Inspection*

📅 Tgl : ${date}
👷 Mekanik : ${mekanik}

🚗 CN : ${codeNumber}
⌛ HM : ${hourMeter}

🩸 *Oil Level* 🩸
Engine oil level : ${engineOil}
Transmission oil level : ${transOil}
Hydraulic oil level : ${hydOil}

⚙ *Engine Area* ⚙
Belt tension : ${beltTension}
Engine oil leakage : ${oilLeak}
Common Rail Connector : ${crc}
Injector Tube : ${injector}

*Tyre condition :* ${tyre}

*Deviation :*
${deviation}`;

      document.getElementById("preview").innerText = pesan;

      // Auto copy ke clipboard
      navigator.clipboard.writeText(pesan).then(() => {
        alert("✅ Teks laporan sudah di-copy ke clipboard!");
      });
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
  </script>
</body>
</html>
