# Scripting di Arduino IDE

Setiap file program di Arduino IDE disebut sebagai Sketch. Secara standar, setiap sketch memiliki dua fungsi utama yang wajib ada:

**void setup()**: Bagian ini dijalankan hanya satu kali saat Arduino pertama kali dinyalakan atau direset. Biasanya digunakan untuk inisialisasi pin (input/output) atau memulai komunikasi serial.

**void loop()**: Bagian ini dijalankan secara terus-menerus (berulang) setelah fungsi setup() selesai. Di sinilah logika utama program Anda berada.

## Perintah Dasar yang Sering Digunakan
Untuk mengendalikan microcontroller, ada beberapa yang hampir selalu digunakan:

| Fungsi | Deskripsi |
| :--- | :--- |
| **`#define NAMA NILAI`** | Konstanta pra-prosesor untuk mendefinisikan nama alias bagi angka atau pin. Tidak menggunakan titik koma (`;`). |
| **`pinMode(pin, MODE)`** | Mengatur apakah sebuah kaki (pin) menjadi `INPUT` atau `OUTPUT`. |
| **`digitalWrite(pin, VALUE)`** | Memberikan sinyal digital `HIGH` (nyala/5V) atau `LOW` (mati/0V) pada pin. |
| **`analogRead(pin)`** | Membaca nilai sensor analog (range 0-1023). |
| **`delay(ms)`** | Memberhentikan program selama waktu tertentu (dalam milidetik). |
| **`Serial.begin(9600)`** | Membuka jalur komunikasi antara Arduino dan Komputer untuk pengiriman data. |

## Tips

- Case Sensitive: Arduino membedakan huruf besar dan kecil. digitalWrite berbeda dengan digitalwrite.

- Titik Koma ( ; ): Setiap baris perintah harus diakhiri dengan titik koma.

- Komentar: Gunakan // untuk catatan satu baris agar kode Anda lebih mudah dibaca oleh orang lain atau diri sendiri di masa depan.

## Contoh Program: LED Blink (Sederhana)
```cpp
#define LED_PIN 2

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(1000);
  digitalWrite(LED_PIN, LOW);
  delay(1000);
}
```

## Penjelasan per Baris
- `#define LED_PIN 2` → Mendefinisikan Variable, setiap `LED_PIN` akan digantikan angka `2` saat kompilasi.

- `void setup()` → Fungsi yang berjalan **sekali** saat board dinyalakan atau di-reset. Tempat menginisialisasi pin, komunikasi serial, dll.

- `pinMode(LED_PIN, OUTPUT);` → Mengatur pin sebagai **output** sehingga bisa memberi tegangan ke LED.

- `void loop()` → Fungsi yang berjalan **berulang-ulang** selama board hidup. Semua logika utama diletakkan di sini.

- `digitalWrite(LED_PIN, HIGH);` → Menyalakan pin (naikkan tegangan), LED menyala.

- `digitalWrite(LED_PIN, LOW);` → Mematikan pin (turunkan tegangan), LED mati.

- `delay(1000);` → Menghentikan eksekusi selama 1000 ms (1 detik). Fungsi ini **blocking** — kode lain tidak dijalankan selama delay.



