# WheelCare
String pesan = "*QA-1 Pre Inspection*\n\n" +
"Tgl : 01-Oct-2025\n\n" +
"*Mekanik :*\n" +
"a.aziz.h, rico\n\n" +
"🚗CN : DT4958\n" +
"⌛HM : 27761\n\n" +
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

String nomorTujuan = "628xxxxxxxxxx"; // ganti dengan nomor WA tujuan

Uri uri = Uri.parse("https://wa.me/" + nomorTujuan + "?text=" + Uri.encode(pesan));
Intent i = new Intent(Intent.ACTION_VIEW, uri);
startActivity(i);
