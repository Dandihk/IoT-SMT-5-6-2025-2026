# Aktuator

Aktuator adalah komponen elektronika yang bertugas mengubah sinyal listrik menjadi gerakan mekanis, panas, atau suara. Singkatnya, aktuator adalah perangkat yang membuat sesuatu "bergerak" atau "bekerja" setelah mendapatkan instruksi dari mikrokontroler seperti ESP32.

![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%202/Media/3.png)

## Jenis-Jenis Aktuator yang Sering Digunakan
Dalam proyek IoT atau robotika, berikut adalah beberapa aktuator yang paling umum:

1. Gerakan (Motor)
    - servo Motor: Bergerak ke sudut spesifik (misal 0-180 derajat). Cocok untuk lengan robot atau kunci pintu otomatis (Smart Lock).
    - Motor DC: Berputar terus-menerus. Digunakan untuk roda robot atau kipas angin.
    - Stepper Motor: Bergerak dalam langkah-langkah kecil yang sangat presisi. Digunakan pada mesin 3D printer dan CNC.

2. Sakelar Listrik (Relay)
    - Relay: Berfungsi sebagai sakelar otomatis untuk perangkat bertegangan tinggi (AC 220V). Dengan relay, ESP32 yang kecil bisa menyalakan lampu rumah, pompa air, atau AC.

3. Visual & Suara
    - LED: Mengubah listrik menjadi cahaya (indikator).
    - Buzzer: Mengubah listrik menjadi getaran suara (alarm).

## Bagaimana Sensor Bekerja?
Alur kerja sistem kontrol biasanya mengikuti pola ini:

- Sensor mendeteksi sesuatu (Contoh: Suhu panas).

- Mikrokontroler (ESP32) memproses data dan mengambil keputusan.

- Aktuator melakukan tindakan (Contoh: Menyalakan kipas).



## Contoh penggunaan Aktuator Servo
di ESP32 membutuhkan library **ESP32Servo by Kevin** untuk menggunakan servo 

## pin vcc servo harus 5v

![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%202/Media/4.png)

script

```cpp
#include <ESP32Servo.h>

Servo myservo;  // Membuat objek servo
int servoPin = 13; // Pin GPIO yang digunakan

void setup() {

  myservo.attach(servoPin, 500, 2400);  // Menghubungkan pin ke objek min-max pulse
  myservo.write(90); // merotasi servo 90 derajat
}

void loop() {
myservo.write(0);
delay(1000);
myservo.write(90);
delay(1000);

}
```


