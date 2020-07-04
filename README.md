# Surface-Pro-6-MacOS-Catalina
## Device Specs
- Model: Surface Pro 6
- Processor: Intel i5-8250u
- GPU: UHD 620
- RAM: 8GB
- Storage: 128GB SAMSUNG KUS020203M-B000 SSD
---
## Functioning 
- Display
- Trackpad
- Keyboard
- Audio
- Keyboard Backlight
## Fixable
- Wifi (Adapter)
- Bluetooth (Adapter)
## Not Working
- Battery % Indicator
- Cameras
- FaceTime & iMessage
---
## Guide

> Creating a Bootable USB is completed using MacOS, this can be achieved through a VMWare. 

**Creating a Bootable USB**

1. Download gibMacOS, and used in to download MacOS Catalina. (I used 10.15.3)
2. Type or paste one of the following commands in Terminal. These assume that the installer is still in your Applications folder, and MyVolume is the name of the USB flash drive or other volume you're using. If it has a different name, replace `MyVolume` in these commands with the name of your volume.

Catalina:
`sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

Youtube Guide: [How to make a Vanilla macOS USB Bootloader for HACKINTOSH the EASY WAY (Mac Version)](https://www.youtube.com/watch?reload=9&v=97C1Rsarto8)

3. Download Clover Configurator. Go to Mount EFI > Mount your USB. 
4. Copy the EFI folder I uploaded into the USB EFI partition. (Replace any other file)

**Setting up partitions for dual boot**

5. Go to windows disk manager, shrink your existing Windows Partition.
6. Create a new partition. (You do not need to format this partition)

**Installing MacOS**

> Before you boot from your USB, ensure Secure Boot is disabled from your surface UEFI. Also make sure USB Drive is set to first in the boot order.

7. In the Clover Bootloader, go to settings > graphics injector and change the platform ID to '0x12345678'
8. Boot the MacOS from USB
9. Enter Disk Utility, and partition the MacOS section to Mac OS Extended.
10. Continue the installation process

> Your laptop may reboot twice. Repeat step 7 and 8 until you can boot into the MacOS partition on your SSD.

11. Boot into MacOS, and go through the setup process. 

**Rebuilding Cache**

> You do not have to change platform ID to '0x12345678' anymore

12. Once you reach the desktop screen, open terminal
13. Type in the following commands in order

`sudo chmod -Rf 755 /S*/L*/E*`

`sudo chmod -Rf 755 /L*/E*`

`sudo chown -Rf 0:0 /S*/L*/E*`

`sudo chown -Rf 0:0 /L*/E*`

`sudo kextcache -i /`

**Trackpad Fix**

15. Download KextBeast
16. Place the kexts I provided on your homescreen, and use KextBeast to install them to `/Library/Extensions`
17. Rebuild Cache, following steps 13.
