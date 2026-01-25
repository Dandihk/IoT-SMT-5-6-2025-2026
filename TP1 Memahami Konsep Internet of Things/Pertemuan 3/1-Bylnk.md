# Blynk
Blynk adalah platform Internet of Things (IoT) yang dirancang untuk memudahkan kita mengontrol perangkat keras (seperti ESP32, Arduino, atau Raspberry Pi) melalui HP atau web dashboard tanpa harus membangun aplikasi Android/iOS dari nol.

**kita akan meread data dari DHT11 dan mengontrol lampu internal esp32 dengan blynk** <br>

Skema Koneksi (Hardware) : <br>

DHT11 VCC -> ESP32 3V3

DHT11 GND -> ESP32 GND

DHT11 DATA -> ESP32 GPIO 13

LED Internal -> Sudah terhubung ke GPIO 2

Library :
Blynk by volodmyr
DTH sensor library by adafruit


1. [blynk.cloud](https://blynk.cloud/) buat akun dan masuk ke dashboard
2. tampilan dasboard blynk
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/dashboardblynk.png)
3. untuk membuat project kita karus ke menu **Developer zone** 
4. Create New template
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/newtem.png)
5. tampilam template
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/templ.png)
6. buat Datastrams **virtual pin** untuk menampung variable yang dikirimkan esp32

    - V0 (Switch): Name: Lampu, Type: Virtual Pin, Data Type: Integer (0-1).

    - V1 (Sensor): Name: Temperatur, Type: Virtual Pin, Data Type: Double, Unit: °C.

    - V2 (Sensor): Name: Kelembapan, Type: Virtual Pin, Data Type: Double, Unit: %.
    ![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/datastrm.png)
7. buat web dashboard pilih **edit** dan masukkan tampilan yang di perlukan
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/webdash.png)
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/dashjadi.png)
8. tambahkan datastream di tiap dashboard dengan cara klik setting pada tiap dashboard
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/sett.png)
9. pilih data stream yang sesuai dengan dashboard
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/datadash.png)
10. kembali ke home dan pilih **add first device**
![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%203/Media/fisrtdef.png)

**setting blynk selesai**

Coding

```cpp

#define BLYNK_TEMPLATE_ID "TMPL6HInQSWg4"
#define BLYNK_TEMPLATE_NAME "HUETEMPLAMP"
#define BLYNK_AUTH_TOKEN    "token"

#include <WiFi.h>
#include <BlynkSimpleEsp32.h>
#include <DHT.h>

// Konfigurasi WiFi
char ssid[] = "ssid";
char pass[] = "123";

// Konfigurasi DHT11
#define DHTPIN 13
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

// Konfigurasi LED
#define LED_PIN 2

BlynkTimer timer;

// Fungsi untuk mengirim data sensor ke Blynk setiap 2 detik
void sendSensorData() {
  float h = dht.readHumidity();
  float t = dht.readTemperature();

  if (isnan(h) || isnan(t)) {
    Serial.println("Gagal membaca sensor DHT11!");
    return;
  }

  // Kirim ke Virtual Pin Blynk
  Blynk.virtualWrite(V1, t); // Temperatur
  Blynk.virtualWrite(V2, h); // Kelembapan
}

// Fungsi kontrol LED dari aplikasi Blynk
BLYNK_WRITE(V0) {
  int statusLampu = param.asInt();
  digitalWrite(LED_PIN, statusLampu);
}

void setup() {
  Serial.begin(115200);
  pinMode(LED_PIN, OUTPUT);
  dht.begin();

  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);

  // Atur interval pengiriman data (2000ms = 2 detik)
  timer.setInterval(2000L, sendSensorData);
}

void loop() {
  Blynk.run();
  timer.run();
}
```
