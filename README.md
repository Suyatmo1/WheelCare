# WheelCare
<!DOCTYPE html>
<html>
<head>
  <title>Kirim WhatsApp</title>
</head>
<body>
  <input type="text" id="pesan" placeholder="Tulis pesan...">
  <button onclick="kirim()">Kirim ke WhatsApp</button>

  <script>
    function kirim() {
      let pesan = document.getElementById("pesan").value;
      let nomor = "6281234567890"; // nomor tujuan
      let url = "https://wa.me/" + nomor + "?text=" + encodeURIComponent(pesan);
      window.open(url, "_blank");
    }
  </script>
</body>
</html>
