# Dell Inspiron N3420 OpenCore

This repository is only meant to provide kexts and config for making the hackintosh installer. I strongly recommend you to read [Opencore laptop guide](https://dortania.github.io/vanilla-laptop-guide/) thoroughly for complete installation guide.

## System configuration

| Model | MacBookPro10,2 | Version | 10.15.1 |
| :-------- | :--------------------------- | :------------- | :------------------ |
| Processor | Intel Core i5-3210M | Graphics | Intel HD 4000 |
| Memory | 1600 MHz DDR3 2x4GB| OS Disk | WD Green 120GB |
| Audio | CS4213 | WiFi/Bluetooth | Dell Wireless 1703 (AR9485) |

## About build

#### Performance
  <!-- + [Geekbench 5](https://browser.geekbench.com/v5/cpu/1927376): 1052 SingleCore, 3935 MultiCore
  + Battery: 57wh with 87% health and 60% brightness (2 NVME and 1 SSD SATA), I got 3h20 screen time when suffering web and light code -->

#### Not working

+ Brightness
+ Power management
+ Sound
  <!-- + Bluetooth kext can be found here: [IntelBluetoothFirmware](https://github.com/zxystd/IntelBluetoothFirmware) -->
+ Thing may never work:
  - Internal Microphone
  - SD Cardreader
  - HDMI
  - Webcam

<!-- #### HDMI blinking at boot

> This will happen when using plug-in HDMI after bootup. This will be fixed after short sleep (about 1min) and never happen again until reboot

- You can fixed this by turn off **com.apple.driver.AppleHDAController** in `Kernel and Kext Patches` on Clover or `Kernel > Patch` on Opencore but **HDMI Audio** will be disabled -->

<!-- ## For building

> This will pull all newest kext and build into zip files

- Clone this repo
- Run follow command: `python3 update.py --build`
- Get your build at Builds folder -->

## Installation

- Follow [Opencore Laptop guide](https://dortania.github.io/vanilla-laptop-guide/) to make a Mac OS boot usb
- Replace OC folder in USB EFI/OC directory with this shipped OC folder.
- Boot into USB and select Mac OS installer
<!-- - After install success, run PostInstall/install.sh in terminal -->
<!-- - Then you need to mount EFI partition and replace it with USB's EFI
- After System EFI replaced by your EFI, Using Opencore Configurator, Clover Configurator or update script to change SMBIOS, generate your serial and MBL
- If you're using intel card, please use NullEthernet for fixing iMess and FaceTime
	- Change MAC in NullEthernet with your new created one, see below -->

<!-- #### Fake ethernet

- Generate your MAC address in SSDT-RMNE if using NullEthernet
- You can make an MacAddress in [Mac generator online](https://www.browserling.com/tools/random-mac)
- Edit SSDT-RMNE.aml with MaciASL and replace MAC with your generated one
- Save as -> ACPI machine language (replace exited one)
- Add it to your bootloader:
  - Kext add in Kexts:
    + Copy kext to kexts/other if using Clover
    + Copy kext to Kexts and add it into Kernel in config.plist (Use OpencoreConfigurator)
  - AML's file add to ACPI folder (Opencore need add to ACPI after copy SSDT file to ACPI, use OpencoreConfigurator)
- Reboot

#### Sleep Wake

```shell
sudo pmset -a hibernatemode 0
sudo pmset -a autopoweroff 0
sudo pmset -a standby 0
sudo pmset -a proximitywake 0
sudo pmset -b tcpkeepalive 0 (optional)
```

> `-b` - Battery `-c` - AC Power `-a` - Both

Please uncheck all options (except `Prevent computer from sleeping...`, which is optional) in the `Energy Saver` panel.

#### Display

If you are using FHD(1080p) display, you may want to enable font smoothing, run this command from terminal:

```
defaults write -g CGFontRenderingFontSmoothingDisabled -bool NO
```

If your laptop display is 4K screen, you should set uiscale to 2:
  + Opencore: NVRAM -> Add -> 4D1EDE05-38C7-4A6A-9CC6-4BCCA8B38C14 -> UIScale -> 2
  + Clover: BootGraphics -> UIScale -> 2 -->

<!-- #### NTFS Writing

Add `UUID=xxx none ntfs rw,auto,nobrowse` to `/etc/fstab`, **xxx** is the UUID of your NTFS partition.

If your NTFS partition has Windows installed, you need to run `powercfg -h off` in powershell in Windows to disable hibernation.

#### Tap Delay

- Turn off `Smart zoom` to avoid two-finger tap delay.

> See [is-it-possible-to-get-rid-of-the-delay-between-right-clicking-and-seeing-the-context-menu](https://apple.stackexchange.com/a/218181)

## BIOS value unlock (Advanced User)

> Big thanks for @Leoing, who found all nessesary value

| Name | Address | Configable value | Default value |
| :----------- | :------ | :--------------- | :------------ |
| CFC-Lock | 0x6F0 | 0x1 or 0x0 | 0x1 |
| DGPU | 0x574 | 0x1 or 0x0 | 0x1 |
| Voltage Lock | 0x78C | 0x1 or 0x0 | 0x1 (1.6.0) |

You can follow [this](https://github.com/Azkali/GPD-P2-MAX-Hackintosh/issues/16#issuecomment-565882180) to change those value

> For Bios 1.6.0 `0x78C` need set to 0x0 so VoltageShift can be used

> You can use mine SmartCPU Script base on VoltageShift for controlling cpu power's usage: [SmartCPU](https://github.com/tctien342/smart-cpu)
<p>
	<img style="border-radius: 8px" src="https://github.com/tctien342/smart-cpu/raw/master/menu.png">
</p>
--!>
