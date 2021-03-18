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

### 2. Untuk Setting Wifi dan FTP ikuti langkar berikut: 
- Buka file [.ino].
- Untuk Setting wifi ganti parameter berikut sesuai dengan wifi yangg digunakan: 
 ```
  const char* ssid = "nama wifi";
  const char* password = "password wifi";
 ```
- Untuk setting FTP ganti parameter berikut sesuai dengan FTP yang digunakan:
 ```
  char ftp_server[] = "FTP IP";
  char ftp_user[]   = "FTP user";
  char ftp_pass[]   = "FTP password";
 ```
  Dan untuk setting directory FTP ganti parameter berikut sesuai dengan FTP yang digunakan:
 ```
  ftp.ChangeWorkDir("/nama directory/");
 ```
- Save.


### 3. Untuk Upload program ikuti langkah berikut:
- Pastikan board yang digunakan adalah ESP 32 -> **AI Thinker ESP32-CAM**
- Tentukan Port yang digunakan, 
  - Windows : Pilih port yang digunakan dengan nama COM , untuk menentukan port ESP dapat dilihat di Device Manager -> Ports (COMN & LPT) -> Sambungkan ESP ke Komputer maka akan ada port baru yang muncul. Port itulah yang akan digunakan pada Arduino IDE.
  - Linux : Pilih port yang digunakan dengan /dev/ttyUSB, untuk menentukan port ESP dapat dilihat di dengan perintah `dmesg | tail -f`.
- Upload program dengan menekan tombol panah pada Arduino IDE, atau dengan shortcut `Ctrl + U`.
