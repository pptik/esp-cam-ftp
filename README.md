# ESP32 Camera FTP
## Deskripsi ESP32-CAM FTP
> Mengambil gambar setiap waktu (waktu dapat diatur) dan mengirimkan gambar tersebut ke FTP server yangtersedia (FTP server dapat di atur) melalui jaringan internet.

## Cara setting Microcontroller mikrokontroller ESP32-CAM FTP

### Software yang diperlukan : 
- Arduino IDE (Terbaru).

### Library dan BooardArduino IDE yang diperlukan:
- Board menggunakan ESP32. Untuk instalasi dapat dilihat pada [Panduan Install Board ESP32](https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-windows-instructions/).

#### Hardware yang digunakan: 
- ESP32CAM.
- Micro USB Data.
- 1 Kabel Jumper Female-Female.
- USB TTL FT232RL. 

### 1. Untuk menginstall ikuti langkah berikut: 
- Download File [Source code ESP-CAM](https://github.com/pptik/esp-cam-ftp.git).
- Buka aplikasi Arduino IDE.
- Pilih board denggan membuka tab 
    > pada aplikasi Arduino IDE Buka -> Tools -> Board -> ESP 32 Arduino -> Pilih AI Thinker ESP32-CAM.
- Buka file [.ino](https://github.com/pptik/esp-cam-ftp/blob/main/esp32_CameraWebServer/esp32_CameraWebServer.ino) yang telah didownload. 

### 1. Untuk Setting Wifi dan FTP ikuti langkar berikut: 
- Buka file [.ino].
- Untuk Setting wifi ganti parameter berikut sesuai dengan wifi yangg digunakan: 

 ```
  const char* ssid = "nama wifi";
  const char* password = "password wifi";
 ```
  
