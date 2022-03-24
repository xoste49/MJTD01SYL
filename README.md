# Xiaomi Mi LED Desk Lamp 1S (MJTD01SYL)
Reverse engineering and firmware Tasmota

## Hardware
Board ESP-WROOM-32D (chip ESP32-D0WD)  
Подробнее https://docs.espressif.com/projects/esp-idf/en/v4.3/esp32/hw-reference/modules-and-boards.html  
![UW7g0Cw](https://user-images.githubusercontent.com/7299412/159749461-8de5ecc4-f47c-4fe9-b2a0-d89b2eecec2c.jpeg)
![IMG_20220323_172951](https://user-images.githubusercontent.com/7299412/159749481-2a7beabb-daa3-4161-8e19-b79daed45d7b.jpg)
![IMG_20220323_173131](https://user-images.githubusercontent.com/7299412/159749515-72e5212f-d7d3-42cf-9000-adb90c4e3f26.jpg)
![q0yuSrk](https://user-images.githubusercontent.com/7299412/159749577-7cc6ba02-05ac-4623-851c-42d4d3be00c2.jpeg)

## Original firmware
Boot log of the original firmware [bootload.log](bootload.log).  
```log
_|      _|  _|_|_|  _|_|_|    _|_|
_|_|  _|_|    _|      _|    _|    _|
_|  _|  _|    _|      _|    _|    _|
_|      _|    _|      _|    _|    _|
_|      _|  _|_|_|  _|_|_|    _|_|
JENKINS BUILD NUMBER: N/A
BUILD TIME: Sep  2 2021,06:17:10
BUILT BY: N/A
MIIO APP VER: 2.1.7_0017
MIIO MCU VER:
MIIO DID: 394523575
MIIO WIFI MAC: 5448e6de4a9a
MIIO MODEL: yeelink.light.lamp4
ARCH TYPE: esp32,0x0000a601
ARCH VER: fb7e59c
FLASH INFO: manufacturer(0x20), memory type(0x40), capacity(0x16)
I (1010) wifi:wifi driver task: 3ffde5d4, prio:23, stack:6656, core=0
I (1010) wifi:wifi firmware version: 76686f3
I (1010) wifi:config NVS flash: enabled
I (1010) wifi:config nano formating: disabled
I (1010) wifi:Init data frame dynamic rx buffer num: 32
I (1020) wifi:Init management frame dynamic rx buffer num: 32
I (1030) wifi:Init management short buffer num: 32
I (1030) wifi:Init dynamic tx buffer num: 32
I (1030) wifi:Init static rx buffer size: 1600
I (1040) wifi:Init static rx buffer num: 10
I (1040) wifi:Init dynamic rx buffer num: 32
I (1070) wifi:set country: cc=RU schan=1 nchan=13 policy=1

I (1070) wifi:Set ps type: 1

I (1160) wifi:mode : sta (54:48:e6:de:4a:9a)
I (1170) wifi:Set ps type: 0

Keystore initialised
Accessory is not Paired with any controller
Database initialised. Accessory Device ID: 7D:6C:41:F5:C2:38
HAP Initialization succeeded. Version : 4.0-fb7e59c
W (1180) YGLC_HAP: has token HAP_MFI_AUTH_SW
Enabling SW Token Authentication
Setup ID: 9XCR
Getting setup info from factory NVS
HAP Main Loop Started
mDNS initialised
Registering HomeKit web handlers
Announcing _hap._tcp mDNS service
Setup ID: 9XCR
I (4340) wifi:new:<5,2>, old:<1,0>, ap:<255,255>, sta:<5,2>, prof:1
I (5210) wifi:state: init -> auth (b0)
I (5220) wifi:state: auth -> assoc (0)
I (5230) wifi:state: assoc -> run (10)
I (5240) wifi:connected with kv410, aid = 2, channel 5, 40D, bssid = 08:55:31:22:f5:7d
I (5240) wifi:security: WPA2-PSK, phy: bgn, rssi: -61
I (5240) wifi:pm start, type: 0

Stopping SoftAP.
I (5360) wifi:AP's beacon interval = 102400 us, DTIM period = 1

************************
Wifi ip=192.168.88.23,mask=255.255.255.0,gw=192.168.88.1
************************

Value Changed
Value Changed
03:00:05.420 [W] ots: httpdns resolve start failed, -12 (ots_cloud_host_update,1022)
03:00:05.430 [I] otu: Opened.
Re-announcing _hap._tcp mDNS service
03:00:05.490 [I] ots: ru.ots.io.mi.com resolved to 107.155.51.105.
03:00:05.490 [I] ots: ots connect 107.155.51.105::443...
03:00:05.510 [I] tls: connect to server Mijia Cloud, domain is 107.155.51.105, port is 443.
03:00:05.690 [W] tls: timeout[100]! mbedtls_ssl_handshake returned -0x6800 (d0_tls_open,389)
03:00:05.850 [W] tls: timeout[200]! mbedtls_ssl_handshake returned -0x6800 (d0_tls_open,389)
03:00:05.960 [W] tls: timeout[300]! mbedtls_ssl_handshake returned -0x6800 (d0_tls_open,389)
03:00:06.040 [I] ots: Connected.
03:00:06.040 [I] ots: -->sync sent.
03:00:06.060 [I] ots: <--sync ack.
18:45:57.040 [I] ots: -->login sent.
18:45:57.100 [I] ots: <--login ack, code=0.
18:45:57.100 [I] miio_ot: info(ots) will start in 0 ms...
18:45:57.140 [I] miio_ot: -->info(ots).
18:45:57.230 [I] miio_ot: <--info ack(ots).
18:45:58.100 [I] miio_ot: -->pull ip list sent.
18:46:00.040 [I] ots: -->sync sent.
18:46:00.060 [I] ots: <--sync ack.
18:46:08.040 [I] ots: -->sync sent.
18:46:08.050 [I] ots: <--sync ack.
18:46:14.310 [I] ots: -->kplv sent.
18:46:14.340 [I] ots: <--kplv ack.
18:46:24.040 [I] ots: -->sync sent.
18:46:24.090 [I] ots: <--sync ack.
18:46:30.340 [I] ots: -->kplv sent.
18:46:30.370 [I] ots: <--kplv ack.
18:46:46.370 [I] ots: -->kplv sent.
18:46:46.390 [I] ots: <--kplv ack.
18:46:56.040 [I] ots: -->sync sent.
18:46:56.060 [I] ots: <--sync ack.
18:47:02.390 [I] ots: -->kplv sent.
18:47:02.750 [I] ots: <--kplv ack.
18:47:18.750 [I] ots: -->kplv sent.
18:47:18.760 [I] ots: <--kplv ack.
```
Настройки подключения  
![2022-03-23_184921](https://user-images.githubusercontent.com/7299412/159749940-7e65e552-5700-482f-a036-7aded1ebdb23.png)


## Схема подключения для режима Download
| ESP Pin    | Serial Pin |
| ---------- | ---------- |
| GND        | GND        |
| 3.3V       | GND        |
| TXD        | RXD        |
| RXD        | TXD        |
| EN         | RTS        |
| GPIO0      | GND        |

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
```

## Прошивка Tasmota
Flash only with [tasmota32solo1.bin](http://ota.tasmota.com/tasmota32/release/tasmota32solo1.bin  ) build for ESP32-SOLO-1. [Flashing instructions](https://tasmota.github.io/docs/ESP32/#flashing) for tasmota32 firmware.  
I used [ESP flasher](https://github.com/Jason2866/ESP_Flasher/releases)  
Log    
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
Настраем подключение к домашней сети wifi.  
Заходим на новый адрес который сообщит tasmota.  
Импортируем template (https://tasmota.github.io/docs/Templates/#importing-templates) 
```
{"NAME":"Mi LED Desk Lamp 1S","GPIO":[6212,0,416,0,417,0,0,0,3840,0,0,0,160,640,608,0,0,0,0,0,0,0,3264,3296,0,0,0,0,0,32,0,0,0,0,0,0],"FLAG":3,"BASE":66,"CMND":"DimmerRange 30,100|Fade 1|PowerOnFade 1|Speed 2"}
```
Консольные команды можно посмотреть здесь https://tasmota.github.io/docs/Commands/#light
## Profit!  
![2022-03-23_225944](https://user-images.githubusercontent.com/7299412/159785571-fff39e1c-9396-410b-9476-cf7ef66c019f.png)  
