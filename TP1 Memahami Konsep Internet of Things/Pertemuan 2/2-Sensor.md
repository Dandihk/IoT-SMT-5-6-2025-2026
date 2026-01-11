# Sensor
Sensor adalah sebuah perangkat yang digunakan untuk mendeteksi perubahan fisik atau kimia di lingkungannya dan mengubahnya menjadi sinyal yang dapat dibaca mesin (seperti mikrokontroler).
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%202/Media/1.png)

Jika kita analogikan dengan tubuh manusia, sensor adalah panca indra kita:
- Mata (Sensor Cahaya)
- Kulit (Sensor Suhu/Sentuh)
- Telinga (Sensor Suara)
- Hidung (Sensor Gas/Bau)

## Bagaimana Sensor Bekerja?
Proses kerja sensor umumnya mengikuti alur berikut:

- **Inputan** : Sensor menerima masukan dari lingkungan (seperti panas, cahaya, tekanan, atau gerakan).

- **Ubah energi** : Sensor mengubah energi dari satu bentuk ke bentuk lainnya. Misalnya, sensor suhu mengubah panas menjadi perubahan hambatan listrik.

- **Output** : Perubahan listrik tersebut diubah menjadi sinyal yang dimengerti oleh perangkat elektronik (biasanya berupa tegangan voltase atau data digital).

## Jenis Sensor Berdasarkan Outputnya
Dalam dunia elektronika dan IoT (seperti pada ESP32 yang kita bahas sebelumnya), sensor dibagi menjadi dua kategori utama:

![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%202/Media/2.png)

- **Sensor Analog** gunakan pin 32-39<br>
    - Sensor ini menghasilkan sinyal yang berubah secara kontinu atau bertahap. <br>
    - Contoh: Potensiometer atau LDR (sensor cahaya). <br>
    - Output: Nilainya bisa berkisar dari 0V hingga 3.3V (tergantung tegangan kerja). <br>
    - Pembacaan: Diperlukan fitur ADC (Analog to Digital Converter) pada mikrokontroler untuk menerjemahkan voltase menjadi angka.

- **Sensor Digital** <br>
    - Sensor ini menghasilkan sinyal yang terputus-putus atau berupa data logika (0 dan 1). <br>
    - Contoh: Sensor gerak PIR (mendeteksi ada orang atau tidak) atau sensor suhu digital seperti DHT11. <br>
    - Output: Hanya berupa kondisi HIGH (Ada sinyal) atau LOW (Tidak ada sinyal)atau berupa protokol komunikasi data (seperti I2C/SPI).

## Mengapa Sensor Penting dalam IoT?
Tanpa sensor, sebuah perangkat IoT tidak akan tahu apa yang terjadi di sekitarnya. Sensor memungkinkan otomatisasi terjadi. Contohnya:

- Smart Home: Lampu menyala otomatis karena sensor LDR mendeteksi hari sudah gelap.

- Pertanian: Pompa air menyala otomatis karena sensor kelembapan tanah mendeteksi tanah sedang kering.

- Kesehatan: Jam tangan pintar mendeteksi detak jantung menggunakan sensor optik.

## Contoh penggunaan Sensor DHT (tempratur dan kelembaban)
Pemnggunaan Sensor DHT11 perlu menggunakan library **DHT sensor library by adafruit**

![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%202/Media/5.png)

```cpp
#include "DHT.h"

#define DHTPIN 5     // Pin data sensor
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
}

void loop() {
  float suhu = dht.readTemperature();
  float lembap = dht.readHumidity();

  Serial.print("Suhu: ");
  Serial.print(suhu);
  Serial.println(" C");

  Serial.print("Lembap: ");
  Serial.print(lembap);
  Serial.println(" H");
  
  delay(2000); //tunggu 2 detik refresh
}
```
## Hasil
buka serial monitor di Tool -> serial monitor <br>
Angka 115200 disebut sebagai Baud Rate. Adalah satuan kecepatan pengiriman data dalam bit per detik (bps).

![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%202/Media/6.png)


# *Beberapa Sensor membutuhkan library khusus untuk bekerja*

