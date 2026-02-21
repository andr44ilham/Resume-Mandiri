# Apa Itu Mikrokontroler?
Mikrokontroler adalah sebuah sistem komputer mini dalam satu chip IC (Integrated Circuit) yang dirancang untuk mengendalikan fungsi spesifik dalam sistem tertanam (embedded system). Komponen ini menyatukan CPU, RAM, ROM, dan I/O port. Mikro kontroler dirancang khusus untuk embedded system, menjadikannya komponen utama pada perangkat otomatis, peralatan rumah tangga, robotika, dan perangkat IoT. 

# Komponen utama mikrokontroler
Umumnya mikrokontroler memiliki komponen utama sebagai berikut:

1. CPU (Central Processing Unit)
   Otak sistem yang mengeksekusi program.

2. Memori

-Flash → menyimpan program

-RAM → menyimpan data sementara

-EEPROM → menyimpan data permanen kecil

3. GPIO (General Purpose Input Output)

-Pin yang bisa digunakan sebagai:

-Input (membaca sensor, tombol)

-Output (menggerakkan LED, relay, motor)

4. Peripheral Tambahan

-ADC (Analog to Digital Converter)

-PWM (Pulse Width Modulation)

-UART, I2C, SPI (komunikasi data)

-Timer

# Peran Mikrokontroler
Mikrokontroler berperan sebagai pusat kendali dalam robotika yang mengatur proses pembacaan sensor, pengolahan data, serta pengendalian aktuator seperti motor dan servo. Melalui program yang ditanamkan, mikrokontroler memungkinkan robot mengambil keputusan secara otomatis, misalnya untuk navigasi, menjaga keseimbangan, atau menghindari rintangan. Selain itu, mikrokontroler juga mengatur komunikasi dan sinkronisasi antar komponen sehingga sistem robot dapat bekerja secara stabil, efisien, dan responsif terhadap perubahan lingkungan.

Pemilihan jenis pengendali sangat memengaruhi kemampuan robot. Untuk robot sederhana, papan 8-bit seperti Arduino Uno sudah memadai. Robot dengan kebutuhan konektivitas dan pemrosesan lebih cepat cocok menggunakan ESP32, sedangkan sistem yang membutuhkan kontrol presisi tinggi sering memakai keluarga STM32. Pada robot yang lebih kompleks, terutama yang melibatkan pemrosesan citra dan kecerdasan buatan, sering digunakan single-board computer seperti Raspberry Pi yang memiliki kemampuan komputasi lebih tinggi dibanding mikrokontroler biasa. Dengan demikian, kompleksitas tugas robot menentukan jenis pengendali yang paling tepat digunakan.
