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
      padding: 8px; 
      margin-top: 5px; 
      width: 100%; 
      box-sizing: border-box;
    }
    button { background: green; color: white; border: none; cursor: pointer; font-weight: bold; }
    button:hover { background: darkgreen; }
  </style>
</head>
<body>
  <h2>Inspection Report HD</h2>

  <label>Code Number:</label>
  <input type="text" id="codeNumber" placeholder="Masukkan Code Number">

  <label>Date:</label>
  <input type="date" id="date">

  <label>Hourmeter:</label>
  <input type="text" id="hourMeter" placeholder="Masukkan HM">

  <label>Mekanik:</label>
  <input type="text" id="mekanik" placeholder="Nama mekanik">

  <label>Tyre Condition:</label>
  <input type="text" id="tyre" placeholder="Contoh: Good">

  <label>Deviation:</label>
  <textarea id="deviation" rows="4" placeholder="Tulis deviation di sini..."></textarea>

  <label>Pilih Tujuan Kirim:</label>
  <select id="tujuan">
    <option value="6281234567890">Supervisor</option>
    <option value="6289876543210">Admin Group</option>
    <option value="6281122334455">Personal Lain</option>
  </select>

  <br><br>
  <button onclick="sendReport()">SEND TO WHATSAPP</button>

  <script>
    function sendReport() {
      let codeNumber = document.getElementById("codeNumber").value;
      let date = document.getElementById("date").value;
      let hourMeter = document.getElementById("hourMeter").value;
      let mekanik = document.getElementById("mekanik").value;
      let tyre = document.getElementById("tyre").value;
      let deviation = document.getElementById("deviation").value;
      let tujuan = document.getElementById("tujuan").value;

      let pesan = 
`*QA-1 Pre Inspection*

Tgl : ${date}

*Mekanik :*
${mekanik}

🚗CN : ${codeNumber}
⌛HM : ${hourMeter}

🩸 *Oil Level* 🩸
Engine oil level : ✅
Transmission oil level : ✅
Hydraulic oil level : ✅

⚙ *Engine Area* ⚙
Belt tension : ✅
Engine oil leakage : ✅
Common Rail Connector : ✅
Injector Tube : ✅

🚗 *Cabin Area* 🚗
📸FM Radio : ✅
⛔Fatigue Warning : ✅
⚡Power Supply : 27.7 V
💧Common Rail Pressure (ON) : 0 MPa
🎚Power Window : ✅

🚗 *Frame Area* 🚗
Operator seat : ✅
Hand Rail : ✅

💧 *Pressure Suspension (Panel)* 💧
FL : 4.10 MPa
FR : 4.10 MPa
RL : 2.10 MPa
RR : 2.10 MPa

*Tyre condition :*
Tyre Condition : ${tyre}

*Deviation :*
${deviation}`;

      let url = "https://wa.me/" + tujuan + "?text=" + encodeURIComponent(pesan);
      window.open(url, "_blank");
    }
  </script>
</body>
</html>
