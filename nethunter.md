# NetHunter

## Install
1. Install factory RAM
   - Donwload ROM (version 8) from ![Google](https://developers.google.com/android/images)
     - Check the compatible version from ![here](https://stats.nethunter.com/nethunter-kernels.html) 
   - Use 'Nexus Root Toolkit' (Flash Stock + Unroot)

2. Activate Bootloader
   - Mobile Menu -> About -> Tap 'Build Number' 7 times
   - Mobile Menu -> Developer Options -> Enable 'Enable USB Debugging' & 'Enable OEM Unlock'

3. Install TWRP
   - Install 'TWRP' on Android
   - Try to find and isntall img for Nexus5x, if not possible, 
     - download from ![here](https://dl.twrp.me/bullhead/)
     - Put the file in 'adb tool' path
     - ```adb reboot bootloader```
     - ```fastboot devices```
     - ```fastboot flash recovery twrp-3.3.1-0-bullhead.img```
       - To be able to enter TWRP with POWER + VOLUP
     - ```fastboot reboot```
   - Go to TWRP
     - ```adb reboot bootloader```
     - ```fastboot boot twrp-3.3.1-0-bullhead.img```
   - If see no command, Use POWER + VOLUP + VOLDOWN
   - To be able to enter TWRP with POWER + VOLUP, put img file in TWRP and select 'Flash to Recovery'

4. Install Magisk
   - Install 'Magisk' from ![Migisk](https://magiskmanager.com/) or ![Github](https://github.com/topjohnwu/Magisk)
   - Chaneg the app extension to 'zip' and install zip file in TWRP with  ```adb reboot bootloader``` & ```fastboot boot twrp.img```
   - Reboot
   - Open Magisk and check if 'Magisk' & 'App' are installed

5. Root checking
   - Install 'Root Checker'
   - Select 'Verify Root'
   - Grant access to Magisk

6. Add linux Commands
   - Install 'BusyBox'

7. Install Nethunter
   - Download Nethunter from ![Kali](https://www.offensive-security.com/kali-linux-nethunter-download/)
   - Transfere the file to mobile with ```adb push nethunter-2020.2-bullhead-oreo-kalifs-full.zip \sdcard```
   - Install the zip file with TWRP (like before)
   - In Magisk app, Choose Shield icon to grant root access to Nethunter
   - Open Nethunter app & select 'kali Chroot Manager' & 'START KALI CHROOT'

## Soft-Break
- Download Factory ROM of ![Nexus5x](https://developers.google.com/android/images)
- Unzip the file and move these 4 files to device
```
...\platform_tools> adb push recovery \sdcard
...\platform_tools> adb push vendor \sdcard
...\platform_tools> adb push boot \sdcard
...\platform_tools> adb push system \sdcard
```
- Boot in Recovery Mode with TWRP and install the 4 files
```
...\platform_tools> flash-all.bat...\platform_tools> flash-all.bat
```
- Use Nexus Root Toolkit => Flash Stock + Unroot
```
...\platform_tools> adb reboot bootloader
...\platform_tools> fastboot boot twrp-3.3.1-0-bullhead.img
...\platform_tools> fastboot reboot
```

## Service
### Kex Manager
- SHOW ADVANCED SETTING -> set the resolution
- SETUP LOCAL SERVER -> set a password
- START SERVER
- OPEN KEX CLIENT
- Enter password
- Connect


## Alfa Network Card
### Install Driver (ne need in new kali)
```
git clone https://github.com/aircrack-ng/rtl8812au
cd rtl8812au
apt update
apt install dkms
./dkms-install.sh
```
### Run
```
airmon-ng check kill
ip link set wlan1 down
iw dev wlan1 set type monitor
ip link set wlan1 up
airmon-ng start wlan1
airodump-ng wlan1
airodump-ng wlan1 --bssid E0:24:81:EF:01:B8 --channel 5 --write test
aircrack-ng test-01.cap -w dic.txt
```
