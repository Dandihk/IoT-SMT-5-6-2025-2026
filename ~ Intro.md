# Internet of Things (IoT) <br> TJKT SMK THP 25-26 

## Pembelajaran SMT 5/6
- **[TP 1](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%201/0-Index.md)** Memahami Konsep Internet of Things 
- **TP 2** Menerapkan perangkat IoT mikroposessor dan mikrocontroller
- **TP 3** Mendokumentasikan dan mengomunikasikan hasil sistem IoT

## Tugas

- **[TP 1](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%201/Tugas/)** 
- **TP 2** Menerapkan perangkat IoT mikroposessor dan mikrocontroller
- **TP 3** Mendokumentasikan dan mengomunikasikan hasil sistem IoT


# Microcontroller

## 🔍 Pengertian
**Microcontroller** adalah sebuah komputer kecil yang terintegrasi dalam satu chip. Biasanya terdiri dari **CPU**, **memori** (Flash untuk program dan SRAM untuk data), dan berbagai **periferal** seperti GPIO, ADC, timer, UART, I2C, SPI, dan PWM. Microcontroller dirancang untuk mengendalikan perangkat elektronik atau menjalankan tugas khusus di sistem Contohnya ***IOT***.

![1](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%201/Media/1.png)

## Perbedaan Microcontroller (SoC) vs Microprocessor (CPU)
- **Microcontroller:** Komponen lengkap (CPU + memori + periferal) dalam satu chip — cocok untuk tugas terdedikasi dan hemat biaya.
- **Microprocessor:** Hanya CPU; membutuhkan komponen eksternal (RAM, ROM, I/O) — cocok untuk komputer umum dengan kebutuhan komputasi tinggi.


## Isi Microcontroller
- GPIO (General Purpose Input/Output)
- ADC (Analog-to-Digital Converter)
- Timer / Counter
- Komunikasi serial: UART, SPI, I2C
- PWM (Pulse Width Modulation)
- Interface untuk sensor dan aktuator

## Pengaplikasian 
- IoT (mengirim data sensor ke server)
- Otomasi rumah dan industri
- Robotika dan kendali motor
- Pengukuran dan monitoring (mis. data logger)

## Contoh Microcontroller
> ![Arduino](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%201/Media/2.png)- **Arduino (ATmega328P)** — mudah dipelajari, banyak contoh untuk pemula

>![alt text](/TP1%20Memahami%20Konsep%20Internet%20of%20Things/Pertemuan%201/Media/3.png)- **ESP8266 / ESP32** — dilengkapi Wi‑Fi (dan Bluetooth pada ESP32), sangat populer untuk proyek IoT

>- **STM32 (ARM Cortex‑M)** — performa tinggi dan banyak varian untuk aplikasi profesional

##  Cara Memprogram Microcontroller
- Bahasa : **C / C++**; untuk pemula menggunakan **Arduino IDE**
- Tools: **Arduino IDE**
- Langkah build: tulis kode → compile → upload ke microcontroller → monitor hasil
 
>***Dipembelajaran Semester ini kita akan menggunakan ESP32 Devkit V1***


