# WheelCare
btnSendWA.setOnClickListener(v -> {
    // Ambil data dari form
    String codeNumber = edtCodeNumber.getText().toString();
    String date = edtDate.getText().toString();
    String hourMeter = edtHourMeter.getText().toString();
    String tyreCondition = edtTyre.getText().toString();
    String deviation = edtDeviation.getText().toString();
    String pic = edtPIC.getText().toString();

    // Format pesan laporan
    String pesan = "*QA-1 Pre Inspection*\n\n" +
            "Tgl : " + date + "\n\n" +
            "*Mekanik :*\n" + pic + "\n\n" +
            "🚗CN : " + codeNumber + "\n" +
            "⌛HM : " + hourMeter + "\n\n" +
            "🩸 *Oil Level* 🩸\n" +
            "Engine oil level : ✅\n" +
            "Transmission oil level : ✅\n" +
            "Hydraulic oil level : ✅\n\n" +
            "⚙ *Engine Area* ⚙\n" +
            "Belt tension : ✅\n" +
            "Engine oil leakage : ✅\n" +
            "Common Rail Connector : ✅\n" +
            "Injector Tube : ✅\n\n" +
            "🚗 *Cabin Area* 🚗\n" +
            "📸FM Radio : ✅\n" +
            "⛔Fatigue Warning : ✅\n" +
            "⚡Power Supply : 25.7 V\n" +
            "💧Common Rail Pressure (ON) : 0 MPa\n" +
            "🎚Power Window : ✅\n\n" +
            "🚗 *Frame Area* 🚗\n" +
            "Operator seat : ✅\n" +
            "Hand Rail : ✅\n\n" +
            "💧 *Pressure Suspension (Panel)* 💧\n" +
            "FL : 3.80 MPa\n" +
            "FR : 3.50 MPa\n" +
            "RL : 1.90 MPa\n" +
            "RR : 2.09 MPa\n\n" +
            "*Tyre condition :*\n" +
            "Tyre : " + tyreCondition + "\n\n" +
            "*Deviation :*\n" +
            deviation + "\n";

    // Nomor WA tujuan (ganti dengan grup/nomor tujuan)
    String nomorTujuan = "6281234567890";

    try {
        Uri uri = Uri.parse("https://wa.me/" + nomorTujuan + "?text=" + Uri.encode(pesan));
        Intent i = new Intent(Intent.ACTION_VIEW, uri);
        startActivity(i);
    } catch (Exception e) {
        Toast.makeText(this, "WhatsApp tidak terpasang", Toast.LENGTH_SHORT).show();
    }
});
