# Deadzone
Deadzone adalah ambang batas atau rentang nilai rendah pada input sensor di mana program sengaja mengabaikan sinyal tersebut agar tidak terjadi respon yang tidak diinginkan. Dalam robotika, hal ini sering diterapkan pada joystick atau sensor analog untuk mengatasi masalah noise atau ketidaksempurnaan mekanis, di mana sensor mungkin mengirimkan sinyal kecil meskipun berada dalam posisi netral. Dengan menetapkan deadzone, robot tidak akan bergerak atau bergetar secara liar akibat fluktuasi sinyal yang sangat halus, sehingga sistem hanya akan bereaksi ketika input telah melewati batas nilai tertentu yang dianggap sebagai perintah nyata.contoh:

# Offset
Offset merupakan nilai kompensasi yang ditambahkan atau dikurangi secara sengaja untuk menyeimbangkan perbedaan antara kondisi ideal dan kondisi fisik yang sebenarnya pada komponen robot. Pada motor penggerak, offset digunakan untuk mengoreksi ketidakseimbangan mekanis, seperti ketika satu motor berputar lebih lambat dari pasangannya sehingga robot cenderung berbelok saat diperintahkan jalan lurus. Dengan memberikan nilai offset pada kode program, kita dapat menyelaraskan kinerja antar perangkat atau mengalibrasi sensor agar titik nol pada perangkat lunak sesuai dengan kondisi fisik di lapangan, memastikan pergerakan robot menjadi lebih akurat dan simetris.


# Contoh 
```cpp
// --- Konfigurasi Parameter --- 
int deadzone  = 30; 
int offsetPWM = 40;

// --- Logika Pemrosesan PWM --- 
if (pwm < deadzone) { 
  // Mematikan output jika berada di dalam zona mati 
  pwm = 0; 
} else { 
  // Sinkronisasi nilai antara batas deadzone dan daya awal motor (offset) 
  pwm = map(pwm, deadzone, 255, offsetPWM, 255); 
}
```

Kode ini berfungsi sebagai sistem kalibrasi otomatis untuk penggerak robot. Pertama, variabel deadzone menentukan batas minimal sinyal agar motor mulai bereaksi, jika nilai PWM yang masuk terlalu kecil (di bawah 30), kode akan memaksa nilai menjadi 0 untuk mencegah motor berdengung atau panas tanpa berputar. Kedua, jika sinyal sudah melewati ambang batas tersebut, fungsi map() akan melakukan lompatan daya awal ke nilai offsetPWM (40) agar motor langsung mendapatkan torsi yang cukup untuk melawan gaya gesek, kemudian menaikkan kecepatannya secara proporsional hingga mencapai batas maksimal (255).
