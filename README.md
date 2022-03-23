# Mi LED Desk Lamp 1S (MJTD01SYL)
Reverse engineering

## Hardware
Board ESP-WROOM-32D (chip ESP32-D0WD)  
Подробнее https://docs.espressif.com/projects/esp-idf/en/v4.3/esp32/hw-reference/modules-and-boards.html  
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

# recovery firmware
$ esptool.py -b 115200 --port COM3 --before default_reset write_flash 0x00000 flash_dump_4M.bin

# Читаем mac адрес
$ esptool.py -b 115200 --port COM3 read_mac
Serial port COM3
Connecting...
Detecting chip type... Unsupported detection protocol, switching and trying again...
Connecting...
Detecting chip type... ESP32
Chip is unknown ESP32 (revision 1)
Features: WiFi, BT, Single Core, 240MHz, VRef calibration in efuse, Coding Scheme 3/4
Crystal is 40MHz
MAC: 54:48:e6:de:4a:9a
Stub is already running. No upload is necessary.
MAC: 54:48:e6:de:4a:9a
Hard resetting via RTS pin...

# Читаем chip id
$ esptool.py -b 115200 --port COM3 chip_id
Serial port COM3
Connecting...
Detecting chip type... Unsupported detection protocol, switching and trying again...
Connecting...
Detecting chip type... ESP32
Chip is unknown ESP32 (revision 1)
Features: WiFi, BT, Single Core, 240MHz, VRef calibration in efuse, Coding Scheme 3/4
Crystal is 40MHz
MAC: 54:48:e6:de:4a:9a
Stub is already running. No upload is necessary.
Warning: ESP32 has no Chip ID. Reading MAC instead.
MAC: 54:48:e6:de:4a:9a
Hard resetting via RTS pin...
```

## Прошивка Tasmota
Скачиваем прошивку http://ota.tasmota.com/tasmota32/release/tasmota32solo1.bin  
Скачиваем программу для прошивки https://github.com/Jason2866/ESP_Flasher/releases  
Прошиваем  
```log
Using 'COM3' as serial port.
Connecting......
Detecting chip type... ESP32
Connecting...

Chip Info:
 - Chip Family: ESP32
 - Chip Model: ESP32-S0WD-OEM (revision 1)
 - Number of Cores: 1
 - Max CPU Frequency: 240MHz
 - Has Bluetooth: YES
 - Has Embedded Flash: NO
 - Has Factory-Calibrated ADC: YES
 - MAC Address: 54:48:E6:DE:4A:9A
Uploading stub...
Running stub...
Stub running...
Changing baud rate to 460800
Changed.
 - Flash Size: 4MB
 - Flash Mode: dout
 - Flash Frequency: 40MHz
Erasing flash (this may take a while)...
Chip erase completed successfully in 16.5s
Flash will be erased from 0x00001000 to 0x00005fff...
Flash will be erased from 0x00008000 to 0x00008fff...
Flash will be erased from 0x0000e000 to 0x0000ffff...
Flash will be erased from 0x00010000 to 0x0015dfff...
Compressed 17104 bytes to 11191...
Writing at 0x00001000... (100 %)
Wrote 17104 bytes (11191 compressed) at 0x00001000 in 0.5 seconds (effective 261.6 kbit/s)...
Hash of data verified.
Compressed 3072 bytes to 129...
Writing at 0x00008000... (100 %)
Wrote 3072 bytes (129 compressed) at 0x00008000 in 0.1 seconds (effective 455.1 kbit/s)...
Hash of data verified.
Compressed 8192 bytes to 47...
Writing at 0x0000e000... (100 %)
Wrote 8192 bytes (47 compressed) at 0x0000e000 in 0.1 seconds (effective 559.9 kbit/s)...
Hash of data verified.
Compressed 1365120 bytes to 961084...
Writing at 0x00010000... (1 %)
Writing at 0x0001695a... (3 %)
Writing at 0x0001f4b5... (5 %)
Writing at 0x0002559e... (6 %)
Writing at 0x0002ddc9... (8 %)
Writing at 0x00035b4d... (10 %)
Writing at 0x00040296... (11 %)
Writing at 0x0004a30f... (13 %)
Writing at 0x00052428... (15 %)
Writing at 0x00057490... (16 %)
Writing at 0x0005c4f7... (18 %)
Writing at 0x0006172b... (20 %)
Writing at 0x0006693a... (22 %)
Writing at 0x0006bef5... (23 %)
Writing at 0x000715da... (25 %)
Writing at 0x00076fe4... (27 %)
Writing at 0x0007c294... (28 %)
Writing at 0x00081917... (30 %)
Writing at 0x00086bba... (32 %)
Writing at 0x0008bb42... (33 %)
Writing at 0x000910bd... (35 %)
Writing at 0x00096234... (37 %)
Writing at 0x0009b775... (38 %)
Writing at 0x000a07e9... (40 %)
Writing at 0x000a55ff... (42 %)
Writing at 0x000aa37e... (44 %)
Writing at 0x000af4ec... (45 %)
Writing at 0x000b43f4... (47 %)
Writing at 0x000b9146... (49 %)
Writing at 0x000bdf42... (50 %)
Writing at 0x000c2bd9... (52 %)
Writing at 0x000c7d28... (54 %)
Writing at 0x000ccd2e... (55 %)
Writing at 0x000d2929... (57 %)
Writing at 0x000d8316... (59 %)
Writing at 0x000ddd20... (61 %)
Writing at 0x000e2fdb... (62 %)
Writing at 0x000e8436... (64 %)
Writing at 0x000ed76b... (66 %)
Writing at 0x000f2ac5... (67 %)
Writing at 0x000f7e09... (69 %)
Writing at 0x000fce53... (71 %)
Writing at 0x00101f79... (72 %)
Writing at 0x001074ca... (74 %)
Writing at 0x0010d371... (76 %)
Writing at 0x001128f2... (77 %)
Writing at 0x00117b03... (79 %)
Writing at 0x0011cf10... (81 %)
Writing at 0x001223d1... (83 %)
Writing at 0x00127b11... (84 %)
Writing at 0x0012d2ca... (86 %)
Writing at 0x001330bd... (88 %)
Writing at 0x00138983... (89 %)
Writing at 0x0013de61... (91 %)
Writing at 0x0014375b... (93 %)
Writing at 0x00148b08... (94 %)
Writing at 0x0014e736... (96 %)
Writing at 0x00153c87... (98 %)
Writing at 0x00159528... (100 %)
Wrote 1365120 bytes (961084 compressed) at 0x00010000 in 23.5 seconds (effective 464.3 kbit/s)...
Hash of data verified.

Leaving...
Hard Resetting...
Hard resetting via RTS pin...
Done! Flashing is complete!
```

## Tasmota
```log
[22:16:05]ets Jun  8 2016 00:22:57
[22:16:05]
[22:16:05]rst:0x1 (POWERON_RESET),boot:0x13 (SPI_FAST_FLASH_BOOT)
[22:16:05]configsip: 0, SPIWP:0xee
[22:16:05]clk_drv:0x00,q_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
[22:16:05]mode:DOUT, clock div:2
[22:16:05]load:0x3fff0018,len:4
[22:16:05]load:0x3fff001c,len:1044
[22:16:05]load:0x40078000,len:10124
[22:16:05]load:0x40080400,len:5828
[22:16:05]entry 0x400806a8
[22:16:05]
[22:16:05]00:00:00.003-223/45 HDW: ESP32-S0WD-OEM 
[22:16:05]./components/esp_littlefs/src/littlefs/lfs.c:1071:error: Corrupted dir pair at {0x0, 0x1}
[22:16:07]00:00:00.442-226/46 UFS: FlashFS mounted with 312 kB free
[22:16:07]00:00:00.448-226/46 CFG: Use defaults
[22:16:07]00:00:00.592 QPC: Reset
[22:16:07]00:00:00.650 BRY: Berry initialized, RAM used=3930 bytes
[22:16:07]00:00:00.674 Project tasmota - Tasmota Version 11.0.0(tasmota)-2_0_2_2(2022-02-12T14:14:00)
[22:16:07]00:00:00.983 WIF: WifiManager active for 3 minutes
[22:16:08]00:00:01.228 HTP: Web server active on tasmota-DE4A9A-2714 with IP address 192.168.4.1
```
 Подключаемся к wifi точке котрую создала лампа tasmota-DE4A9A-2714 и открываем 192.168.4.1  


## Using
https://github.com/espressif/esptool
