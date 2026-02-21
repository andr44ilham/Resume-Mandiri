# Mapping Joystick
Merupakan proses konversi atau penerjemahan nilai mentah (raw data) dari sensor analog joystick menjadi nilai yang dapat dimengerti oleh sistem kendali robot, seperti kecepatan motor atau sudut servo. Karena joystick bekerja menggunakan potensiometer, nilai yang dihasilkan biasanya memiliki rentang tertentu (misalnya 0 hingga 1023 pada Arduino) yang harus dipetakan ulang agar sesuai dengan rentang input penggerak robot (misalnya -255 hingga 255 untuk arah motor).

# Cara Mapping Joystick

Joystick PS3 dan PS4 umum dilakukan sebagai perangkat pengatur gerak robot. Melakukan mapping joystick PS3 ke ESP32 melibatkan proses sinkronisasi nirkabel (Bluetooth) dan penerjemahan data digital menjadi perintah motorik. Berikut adalah tahapan singkatnya:

**Tahap Koneksi** dan Pairing dimulai dengan menyamakan alamat MAC Bluetooth antara controller PS3 dan ESP32 menggunakan bantuan software di PC seperti SixaxisPairTool. Karena ESP32 bertindak sebagai host, ia harus mengenali alamat fisik controller agar bisa melakukan jabat tangan (handshake) secara nirkabel melalui library khusus (seperti Ps3Controller.h). Setelah alamat MAC cocok, ESP32 akan secara otomatis mendeteksi koneksi setiap kali controller dinyalakan, yang ditandai dengan lampu indikator pada PS3 yang berhenti berkedip.

**Tahap Ekstraksi** Data Analog terjadi saat program membaca posisi stick joystick yang memiliki rentang nilai mentah dari -128 hingga 127. Nilai ini harus diproses melalui fungsi pemetaan (mapping) untuk diubah menjadi rentang PWM motor, misalnya 0 hingga 255. Dalam tahap ini, sangat penting untuk menerapkan logika deadzone agar robot tidak bergerak sendiri saat stick berada di posisi tengah akibat gangguan sinyal kecil atau ketidakteraturan mekanik pada controller tua.
