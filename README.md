# ESP32 Camera FTP
## Deskripsi ESP32-CAM FTP
> Mengambil gambar setiap waktu (waktu dapat diatur) dan mengirimkan gambar tersebut ke FTP server yang tersedia (FTP server dapat di atur) melalui jaringan internet.

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
- Buka file [.ino](https://github.com/pptik/esp-cam-ftp/blob/main/esp32_CameraWebServer/esp32_CameraWebServer.ino).
- Ubah parameter guid device :
  ```
  const char* guidDevice = "b039561a-9b6d-11eb-a8b3-0242ac130003";
  ```
  Guid Devicedapat di dapatkan dengan men-_generate_ di [Generate GUID device](https://www.uuidgenerator.net/version1).
- Untuk Setting wifi ganti parameter berikut sesuai dengan wifi yang digunakan: 
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
  dengan format directory /dir/dir_with_guid_device_name
  ```
  ftp.ChangeWorkDir("/nama directory/guid name");
  ```
  Contoh: 
  ```
  ftp.ChangeWorkDir("/iotdevice/ftpcam/b039561a-9b6d-11eb-a8b3-0242ac130003");
  ```
- Save.
- **PASTIKAN DIREKTORY DI FTP SERVER SUDAH TERSEDIA.**
- Jika belum, download dan install aplikasi **FileZilla Client**, dapat di download di [Download FileZilla Client](https://filezilla-project.org/).
- Login dengan akun FTP. Untuk Port biarkan kosong karena default nya 22.
- Masuk ke direktori tujuan upload.
![Capture](https://user-images.githubusercontent.com/18458955/114655700-ee6e9d00-9d16-11eb-81a3-e3b21e7485e8.PNG)

- Buat direktori dengan nama direktori untuk masing-masing GUID.


### 3. Untuk Upload program ikuti langkah berikut:
- Pastikan board yang digunakan adalah ESP 32 -> **AI Thinker ESP32-CAM**
- Tentukan Port yang digunakan, 
  - Windows : Pilih port yang digunakan dengan nama COM , untuk menentukan port ESP dapat dilihat di Device Manager -> Ports (COMN & LPT) -> Sambungkan ESP ke Komputer maka akan ada port baru yang muncul. Port itulah yang akan digunakan pada Arduino IDE.
  - Linux : Pilih port yang digunakan dengan /dev/ttyUSB, untuk menentukan port ESP dapat dilihat di dengan perintah `dmesg | tail -f`.
- Upload program dengan menekan tombol panah pada Arduino IDE, atau dengan shortcut `Ctrl + U`.

### 4. Additional Features (Trigger Capture dengan button atau sensor)
- Set up input pin, Contoh 
  ```
    pinMode(16, INPUT);
  ```
- Dan set kondisi apa yang akan dilakukan oleh button jika ditekan. Conth menggunakan button mengambil gambar ketika button ditekan dan di gamber dikirim ke FTP: 
  ```
  int value = digitalRead(16);
  // Serial.println(value);
  if(value == 0) {
    capture_ftpupload();
  }
  ```
  


