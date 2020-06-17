# Dell Inspiron N3420 OpenCore

This repository is only meant to provide kexts and config for making the hackintosh installer. I strongly recommend you to read [OpenCore laptop guide](https://dortania.github.io/vanilla-laptop-guide/) thoroughly for complete installation guide.

## System configuration

| Model | MacBookPro10,2 | Version | 10.15.1 |
| :-------- | :--------------------------- | :------------- | :------------------ |
| Processor | Intel Core i5-3210M | Graphics | Intel HD 4000 |
| Memory | 1600 MHz DDR3 2x4GB| OS Disk | WD Green 120GB |
| Audio | CS4213 | WiFi/Bluetooth | Dell Wireless 1703 (AR9485) |

## About build

#### Performance

#### Not working

+ Brightness
+ Power management
+ Sound
+ Thing may never work:
  - Internal Microphone
  - SD Cardreader
  - HDMI
  - Webcam

## Installation

- Follow [OpenCore Laptop guide](https://dortania.github.io/vanilla-laptop-guide/) to make a Mac OS boot usb
- Replace OC folder in USB EFI/OC directory with this shipped OC folder.
- Boot into USB and select Mac OS installer

## Contact
If you have any suggestions, please create an issue. Thanks in advance.
