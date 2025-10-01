# WheelCare
Button btnSendWA = findViewById(R.id.btnSendWA);

btnSendWA.setOnClickListener(v -> {
    // ambil data dari inputan form
    String codeNumber = edtCodeNumber.getText().toString();
    String date = edtDate.getText().toString();
    String hourMeter = edtHourMeter.getText().toString();

    // format pesan sesuai template
    String pesan = "*QA-1 Pre Inspection*\n\n" +
            "Tgl : " + date + "\n\n" +
            "*Mekanik :*\n" +
            "a.aziz.h, rico\n\n" +
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
            "🚗 *Cabin Area*🚗\n" +
            "📸FM Radio : ✅\n" +
            "⛔Fatigue Warning : ✅\n" +
            "⚡Power Supply : 27.7 V\n" +
            "💧Common Rail Pressure (ON) : 0 MPa\n" +
            "🎚Power Window : ✅\n\n" +
            "🚗 *Frame Area* 🚗\n" +
            "Operator seat : ✅\n" +
            "Hand Rail : ✅\n\n" +
            "💧 *Pressure Suspension (Panel)* 💧\n" +
            "FL : 4.10 MPa\n" +
            "FR : 4.10 MPa\n" +
            "RL : 2.10 MPa\n" +
            "RR : 2.10 MPa\n\n" +
            "*Tyre condition :*\n" +
            "Tyre : Tyre Condition : Good\n\n" +
            "*Deviation :*\n" +
            "⚠ sun visor Rh damage\n" +
            "⚠ rear plate Rh crack\n" +
            "⚠ spacer cover ALT lost\n" +
            "⚠ hose output hyd pump crack\n";

    // nomor tujuan WhatsApp
    String nomorTujuan = "6281234567890"; // ganti dengan nomor WA tujuan

    try {
        Uri uri = Uri.parse("https://wa.me/" + nomorTujuan + "?text=" + Uri.encode(pesan));
        Intent i = new Intent(Intent.ACTION_VIEW, uri);
        startActivity(i);
    } catch (Exception e) {
        Toast.makeText(this, "WhatsApp tidak terpasang", Toast.LENGTH_SHORT).show();
    }
});
