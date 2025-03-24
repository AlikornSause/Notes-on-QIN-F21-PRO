## Notes on QIN F21 PRO

### Disclaimer
I am an amateur, and everything I say here should be taken with a grain of salt. The information presented here was gathered through my research and from the amazing [XDA Forums](https://xdaforums.com/)! I do not take responsibility for bricking your device, losing your data, or any other issues that may arise. The information presented here **might not be 100% true** and some of it is my subjective opinion. If in any case I am wrong i would greatly appreciate your feedback so that everything here be a great source of info for other people.

It is very possible that you will encounter difficulties when rooting, flashing custom ROMs, or modifying your device. However, the good news is that there is a lot of support online, and most mistakes have already been made and fixed. Good luck hacking!

---

## The Phone
The **Qin F21 Pro** is a half-touchscreen, half-button phone running **Android 11**. It features:
- **2.8-inch 640 x 480px IPS capacitive touchscreen**
- **5MP rear camera** with a **2MP front camera**
- **GSM networks:** 850/900/1800/1900MHz
- **4G network support**

The device is available in different configurations.

---

## Versions
There are **two main hardware versions** of the phone:
- **64+4GB version**
- **32+3GB version**

The phone also varies in **color**:
- White
- Black

Additionally, it has different **keyboard languages**:
- English
- Russian
- Hebrew

### Software Variants
The phone comes with at least three different ROM versions:
- **Original Factory ROM:** Chinese + English, bootloader locked, no Google Play.
- **Hacked Version:** Chinese + English, bootloader unlocked, Google Play present, supposedly Google certified.
- **International ROM:** Multi-language support, bootloader unlocked, Google Play present, NOT Google certified.

    **Privacy**
    These stock ROMs are not to be trusted as they send weird packets directly to China.
    Some of them were sent to NTP servers in China which isn't that weird but others point to duoqin.com, xiaomi and others.
    A list of all URLs that are/ can be sent information:
      - connect.rom.miui.com
      - wifi.vivo.com.cn
      - connectivitycheck.platform.hicloud.com
      - cn.ntp.org.cn
      - dq-avatar.duoqin.com
      - loc.map.baidu.com
    At least thats what my PCAPdroid said. I used it with root access so it should see literally everything sent from the device. I hope thats the case.

 There are also some custom ROMs for this phone:
 - **LineageOS 18.1:** Custom ROM posted by @a9381 user on [XDA Forums here](https://xdaforums.com/t/rom-beta-unoffical-lineageos-18-1-for-xiaomi-qin-f21s-pro-by-a-i-v.4431693/), it contains some bugs such as the keypad backlight being always on, no access to /data partition by twrp, VOLTE problems and the wifi and bluetooth being on by default. These bugs seem to be fixable and possibly already fixed in the newer versions of this rom. I haven't tested it yet but it seems like a great alternative to the stock ROMs. I haven't tested this ROM yet but it is reported to work on the 32+3GB version.
 - **Some kosher ROMs for for the religious people from Israel** made by @Ashi Vered. You can find more info in [his GitHub page](https://github.com/AshiVered/Android-custom-ROMs).
---

## Differences
The **64+4GB version** seems to be **easier to root and install custom ROMs**. I personally have a **32+3GB black English original ROM** and have confirmed that it's possible to modify and root this version. 

For hacking purposes, the **most important factor** is whether you have the **64+4GB or 32+3GB version**—other differences don't matter as much.

---

## Hardware Modes
The phone can be booted into several modes, all of which require the device to be **TURNED OFF**.

### **Normal Mode**
Entered by pressing the **power button** for a few seconds until the logo appears.

<img src="https://github.com/user-attachments/assets/fd88e24c-d9e9-4881-8113-91b7e388cf6f" width="300">

---

### **Recovery Mode**
Entered by holding down the following buttons:
- **Owl/Heart/Qinguard button**
- **Power/Hangup button**
- **`*` (Star) button**

Once the **boot menu** appears, **release the power button but continue holding the other two buttons**. If you keep holding the power button, the phone will simply reboot.

Alternatively, you can enter this mode using:
```sh
adb reboot bootloader
```

<img src="https://github.com/user-attachments/assets/85496ee0-80f1-4552-ac21-1b2465d80fcf" width="300">

After entering Recovery Mode, you will see this screen:

<img src="https://github.com/user-attachments/assets/51cc821b-59e7-48a0-a0bd-fc692de65811" width="300">

To enter the menu, **hold down the power/hangup button and press the up button on the "joystick"**:

<img src="https://github.com/user-attachments/assets/a6db75fb-3d77-4a43-ae24-dc5f90d402d2" width="300">

You will then see this menu:

<img src="https://github.com/user-attachments/assets/243b470e-849d-4587-ae87-5ba379ebf61d" width="300">

#### **Navigation**
- Use the **joystick buttons** to navigate.
- Use the **power button** to select.

#### **Recovery Menu Options**
- **Reboot to system now:** Reboots into normal mode.
- **Reboot to bootloader:** Reboots into fastboot mode.
- **Enter fastboot:** Enters fastbootd mode with options to reboot, return to recovery, enter fastboot, or power off. This can also be accessed via:
  ```sh
  adb reboot fastboot
  ```
- **Apply update from ADB:** Untested.
- **Apply update from SD card:** Untested (the phone lacks an SD card slot).
- **Wipe data/factory reset:** Wipes all user data (**likely works, but untested**).
- **Mount /system:** Displays "Mounted /system." at the bottom, but its usefulness is unclear.
- **View recovery logs:** Displays logs from recovery mode.
- **Run graphics test:** Displays a test of multiple images, including the broken Android "No Command" image and data-clearing animation.
- **Run locale test:** Shows different language versions of system texts such as "No Command," "Installing," and "Erasing."
- **Power off:** Reboots the device (instead of powering it down).

This mode could be useful, but I am not sure exactly how. It **can** be used to enter **fastboot mode**, which is very useful for flashing and modifications.

---

### **Fastboot/Bootloader Mode**
Fastboot mode can be entered in multiple ways:
- From the **Recovery Menu** (as mentioned above)
- Using ADB:
  ```sh
  adb reboot bootloader
  ```
- Using **MTKClient payloads**:
  ```sh
  python mtk payload --metamode FASTBOOT
  ```
  *(This did not work for me, but it worked for others.)*

<img src="https://github.com/user-attachments/assets/d2637828-6242-426c-b2c8-bc555096ebe2" width="300">

#### **Fastboot Commands**
Fastboot mode is used for flashing firmware, unlocking the bootloader, and checking/modifying partitions.
- **Check current slot:**
  ```sh
  fastboot getvar current-slot
  ```
- **Check all information from fastboot:**
  ```sh
  fastboot getvar all
  ```
- **Change active slot:**
  ```sh
  fastboot set_active a
  fastboot set_active b
  ```
### **Preloader mode** used in mtkclient or spflash tool
  When using these 2 tools, you might want to put the phone in this mode
  To do this, simply connect the phone to your computer with a USB cable when the tool is running without pressing any keys.
  This should put the phone in preloader mode.

  This mode together with these tools can be used to dump the rom, make backups, flash the rom and many other things
  
### **BROM (bootrom) mode** used in mtkclient or spflash tool
  When using these 2 tools, you might want to put the phone in this mode
  To do this, hold the Owl/Heart/Qinguard button and back button and connect the device to your computer, while mtkclient or spflashtool is running
  
![brom](https://github.com/user-attachments/assets/0b3f8312-71f7-4ac1-b2d1-e6e21251a2b4)


## Interesting facts about the phone

- Pressing the 4, 7, * keys at the same time 
