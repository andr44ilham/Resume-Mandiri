1. Peran Mikrokontroler dalam Robot

Mikrokontroler merupakan pusat kendali (brain) dalam sistem robotika. Semua proses pengolahan input, pengambilan keputusan, dan pengiriman output dilakukan oleh mikrokontroler. Perangkat ini menerima data dari sensor, memprosesnya berdasarkan program yang ditanamkan, kemudian mengontrol aktuator seperti motor, servo, atau LED.

Dalam sistem robot bergerak, mikrokontroler bertugas untuk:

Membaca input dari joystick atau sensor

Mengatur arah dan kecepatan motor

Mengimplementasikan logika navigasi

Mengontrol sistem komunikasi dan monitoring

Tanpa mikrokontroler, robot tidak memiliki sistem kendali terstruktur.

2. Struktur Program (setup() dan loop())

Dalam pemrograman berbasis Arduino atau mikrokontroler sejenis, struktur program utama terdiri dari dua bagian penting:

setup()

Fungsi setup() dijalankan satu kali saat sistem pertama kali dinyalakan atau di-reset. Bagian ini digunakan untuk:

Inisialisasi pin (input/output)

Mengaktifkan komunikasi serial

Mengatur mode kerja awal

Contoh fungsi setup:

pinMode()

Serial.begin()

loop()

Fungsi loop() akan berjalan terus-menerus selama mikrokontroler aktif. Semua logika utama robot diletakkan pada bagian ini, seperti:

Membaca joystick

Mengatur motor

Mengontrol arah pergerakan

Struktur ini memastikan sistem robot bekerja secara kontinu dan responsif.

3. Digital dan Analog I/O

I/O (Input/Output) adalah jalur komunikasi antara mikrokontroler dan perangkat eksternal.

Digital I/O

Digital hanya memiliki dua kondisi:

HIGH (1 / 5V)

LOW (0 / 0V)

Contoh penggunaan:

Tombol

LED

Driver motor (arah putaran)

Fungsi yang digunakan:

digitalRead()

digitalWrite()

Analog I/O

Analog memiliki nilai dalam rentang tertentu (biasanya 0–1023 pada Arduino).

Digunakan untuk:

Membaca joystick

Sensor jarak analog

Sensor cahaya

Fungsi yang digunakan:

analogRead()

Analog memungkinkan pembacaan nilai yang lebih presisi dibanding digital.

4. PWM dan Kecepatan Motor

PWM (Pulse Width Modulation) adalah teknik untuk mengatur daya rata-rata yang diberikan ke motor dengan cara mengatur lebar pulsa sinyal digital.

Walaupun pin PWM hanya HIGH dan LOW, variasi lebar pulsa membuat motor seolah-olah menerima tegangan berbeda.

Nilai PWM biasanya:

0 → motor mati

255 → kecepatan maksimum

Fungsi yang digunakan:

analogWrite()

Dengan PWM, robot dapat:

Bergerak pelan

Bergerak cepat

Berakselerasi secara halus

5. Dead Zone dan Offset
Dead Zone

Dead zone adalah area kecil di sekitar nilai tengah joystick yang diabaikan untuk mencegah gerakan tidak sengaja akibat noise atau ketidakstabilan pembacaan.

Contoh:
Jika nilai tengah joystick = 512, maka dead zone bisa dibuat:
500 – 524 → dianggap netral

Hal ini membuat robot lebih stabil saat joystick tidak digerakkan.

Offset

Offset adalah nilai koreksi yang ditambahkan untuk menyesuaikan perbedaan performa motor kanan dan kiri.

Karena motor tidak selalu identik, offset digunakan agar robot bergerak lurus dengan lebih akurat.

6. Kinematika Robot

Kinematika adalah studi tentang gerakan tanpa memperhatikan gaya penyebabnya.

Differential Drive

Robot memiliki dua roda utama (kanan dan kiri).

Karakteristik:

Jika kedua roda maju dengan kecepatan sama → robot maju lurus

Jika satu roda berhenti → robot berbelok

Jika roda berlawanan arah → robot berputar di tempat

Sederhana dan banyak digunakan pada robot line follower dan robot edukasi.

Mecanum Wheel

Menggunakan roda khusus dengan roller miring.

Keunggulan:

Bisa bergerak ke samping (strafe)

Bisa diagonal

Bisa rotasi dan translasi bersamaan

Lebih kompleks, tetapi fleksibel untuk manuver.

7. Mapping Joystick (Maju, Mundur, Belok)

Joystick memiliki dua sumbu utama:

Sumbu X → kanan dan kiri

Sumbu Y → maju dan mundur

Mapping dilakukan dengan cara:

Membaca nilai analog joystick

Mengubah nilai 0–1023 menjadi rentang kecepatan motor

Mengatur arah dan PWM motor berdasarkan kombinasi X dan Y

Contoh logika dasar:

Y tinggi → robot maju

Y rendah → robot mundur

X tinggi → belok kanan

X rendah → belok kiri

Pada sistem differential:
Kecepatan motor kiri dan kanan dihitung berdasarkan kombinasi nilai X dan Y.

Mapping yang baik membuat kontrol robot terasa halus dan responsif.
