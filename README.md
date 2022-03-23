# Mi LED Desk Lamp 1S (MJTD01SYL)
Reverse engineering

## Hardware
ESP-WROOM-32D
![UW7g0Cw](https://user-images.githubusercontent.com/7299412/159749461-8de5ecc4-f47c-4fe9-b2a0-d89b2eecec2c.jpeg)
![IMG_20220323_172951](https://user-images.githubusercontent.com/7299412/159749481-2a7beabb-daa3-4161-8e19-b79daed45d7b.jpg)
![IMG_20220323_173131](https://user-images.githubusercontent.com/7299412/159749515-72e5212f-d7d3-42cf-9000-adb90c4e3f26.jpg)
![q0yuSrk](https://user-images.githubusercontent.com/7299412/159749577-7cc6ba02-05ac-4623-851c-42d4d3be00c2.jpeg)

## Original firmware
Boot лог оригинальной прошивки [bootload.log](bootload.log).  
![2022-03-23_184958](https://user-images.githubusercontent.com/7299412/159749946-35d36d61-9a2b-47aa-9694-63d8f3dbe30d.png)  
Настройки подключения  
![2022-03-23_184921](https://user-images.githubusercontent.com/7299412/159749940-7e65e552-5700-482f-a036-7aded1ebdb23.png)


## Схема подключения для режима Download
ESP Pin     Serial Pin
GND         GND
3.3V        GND
TXD         RXD
RXD         TXD
EN          RTS
GPIO0       GND

## Режим Download

```sh
# dump firmware 
$ esptool.exe -b 115200 --port COM3 --before default_reset read_flash 0x00000 0x400000 flash_dump_4M.bin
Serial port COM3
Connecting....
Detecting chip type... Unsupported detection protocol, switching and trying again...
Connecting...
Detecting chip type... ESP32
Chip is unknown ESP32 (revision 1)
Features: WiFi, BT, Single Core, 240MHz, VRef calibration in efuse, Coding Scheme 3/4
Crystal is 40MHz
MAC: 54:48:e6:de:4a:9a
Uploading stub...
Running stub...
Stub running...
4194304 (100 %)
4194304 (100 %)
Read 4194304 bytes at 0x0 in 375.7 seconds (89.3 kbit/s)...
Hard resetting via RTS pin...
```


## Using
https://github.com/espressif/esptool
