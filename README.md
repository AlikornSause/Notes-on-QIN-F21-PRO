# Notes on QIN F21 PRO
## Table of Contents
- [Disclaimer](#disclaimer)
- [Introduction to the phone](#the-phone)
- [Device variants](#versions)
    - [Hardware variants](#hardware-versions)
    - [Software variants (ROMs)](#software-versions)
    - [Differences](#differences)
    - [Custom ROMs](#custom-roms)
- [Hardware modes](#hardware-modes)
    - [Normal mode](#normal-mode)
    - [Recovery mode](#recovery-mode)
    - [Fastboot/Bootloader Mode](#fastbootbootloader-mode)
- [Keypad and buttons](#keypad-and-buttons)
- [Software](#software)
    - [Preinstalled apps](#preinstalled-apps)
- [Debloating the system](#debloating-the-system)
- [Hacking the device](#hacking-the-device)
    - [Disclaimer](#before-you-start)
    - [Making a full backup](#making-a-full-backup)
    - [Rooting](#rooting)
    - [Modifing the /system partition](#modifing-the-system-partition)
    - [Debloating](#debloating)
    - [Installing GAPPS](#installing-gapps)
    - [Installing custom ROMs](#installing-custom-roms)
    - [Changing the Orange Stare Warning text](#changing-the-orange-state-warning-text)
    - [Removing the Orange Stare Warning text](#removing-the-orange-state-warning-text)
    - [Removing the 5 Second Delay in Orange State](#removing-the-5-second-delay-in-orange-state)
      
## Disclaimer
I am an amateur, and everything I say here should be taken with a grain of salt. The information presented here was gathered through my research and from the amazing [XDA Forums](https://xdaforums.com/)! I do not take responsibility for bricking your device, losing your data, or any other issues that may arise. The information presented here **might not be 100% true** and some of it is my subjective opinion. If in any case I am wrong i would greatly appreciate your feedback so that everything here be a great source of info for other people.

It is very possible that you will encounter difficulties when rooting, flashing custom ROMs, or modifying your device. However, the good news is that there is a lot of support online, and most mistakes have already been made and fixed. Good luck hacking!



---



# The Phone
The **Qin F21 Pro** is a half-touchscreen, half-button phone running **Android 11**. It features:
- **2.8-inch 640 x 480px IPS capacitive touchscreen**
- **5MP rear camera** with a **2MP front camera**
- **GSM networks:** 850/900/1800/1900MHz
- **4G network support**

The device is available in different configurations.



---



# Versions
### Hardware versions
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

### Software versions
The phone comes with at least three different ROM versions:
- **Original Factory ROM:** Chinese + English, bootloader locked, no Google Play.
- **Hacked Version:** Chinese + English, bootloader unlocked, Google Play present, supposedly Google certified.
- **International ROM:** Multi-language support, bootloader unlocked, Google Play present, NOT Google certified.

**Privacy concerns**
These stock ROMs are not to be trusted as they send weird packets directly to China.
Some of them were sent to NTP servers in China which isn't that weird but others point to duoqin.com, xiaomi and others.
A list of all URLs that are/ can be sent information:
  - connect.rom.miui.com
  - wifi.vivo.com.cn
  - connectivitycheck.platform.hicloud.com
  - cn.ntp.org.cn
  - dq-avatar.duoqin.com
  - loc.map.baidu.com
<ins>At least thats what my PCAPdroid said</ins>. I used it with root access so it should see literally everything sent from the device. I hope thats the case.
The privacy topic will be discussed more later in this document.

### Differences
The **64+4GB version** seems to be **easier to root and install custom ROMs**. I personally have a **32+3GB black English original ROM** and have confirmed that it's possible to modify and root this version. 

For hacking purposes, the **most important factor** is whether you have the **64+4GB or 32+3GB version** and whether **the bootloader is unlocked**—other differences don't matter as much.

### Custom ROMs
 There are also some custom ROMs for this phone:
 - **LineageOS 18.1:** Custom ROM posted by @a9381 user on [XDA Forums here](https://xdaforums.com/t/rom-beta-unoffical-lineageos-18-1-for-xiaomi-qin-f21s-pro-by-a-i-v.4431693/), it contains some bugs such as the keypad backlight being always on, no access to /data partition by twrp, VOLTE problems and the wifi and bluetooth being on by default. These bugs seem to be fixable and possibly already fixed in the newer versions of this rom. I haven't tested it yet but it seems like a great alternative to the stock ROMs. I haven't tested this ROM yet but it is reported to work on the 32+3GB version.
<br>
   Update : I tested this rom on the 32+3GB version and so far it does not work.
   
 - **AOSP13BETA QinF21PRO AIV:** A custom rom found on 4pda.to. I tested it but couldn't get it to work.
   
 - **Some kosher ROMs for for the religious people from Israel** made by @Ashi Vered. You can find more info in [his GitHub page](https://github.com/AshiVered/Android-custom-ROMs).



---



# Hardware Modes
The phone can be booted into several modes, all of which require the device to be **TURNED OFF**.

### **Normal Mode**
Entered by pressing the **power button** for a few seconds until the logo appears.

<img src="https://github.com/user-attachments/assets/fd88e24c-d9e9-4881-8113-91b7e388cf6f" width="200">

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

<img src="https://github.com/user-attachments/assets/85496ee0-80f1-4552-ac21-1b2465d80fcf" width="200">

After entering Recovery Mode, you will see this screen:

<img src="https://github.com/user-attachments/assets/51cc821b-59e7-48a0-a0bd-fc692de65811" width="200">

To enter the menu, **hold down the power/hangup button and press the up button on the "joystick"**:

<img src="https://github.com/user-attachments/assets/c80d086b-f327-4733-b43a-26f6bcef1f44" width="200">

You will then see this menu:

<img src="https://github.com/user-attachments/assets/243b470e-849d-4587-ae87-5ba379ebf61d" width="200">

#### **Navigation**
- Use the **joystick buttons** to navigate.
- Use the **power button** to select.

#### **Recovery Menu Options**
- **Reboot to system now:** Reboots into normal mode.
- **Reboot to bootloader:** Reboots into fastboot mode.
- **Enter fastboot:** Enters fastbootd mode with options to reboot, return to recovery, enter fastboot, or power off. This mode can also be accessed via:```adb reboot fastboot```.
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
  *(This did not work for me, but it is reported to work)*

<img src="https://github.com/user-attachments/assets/d2637828-6242-426c-b2c8-bc555096ebe2" width="200">

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
  
  ---

### **Preloader mode**
  It is used in mtkclient or spflash tool
  When using these 2 tools, you might want to put the phone in this mode
  To do this, simply connect the phone to your computer with a USB cable when the tool is running without pressing any keys.
  This should put the phone in preloader mode.

  The view from mtkclient:
  
  <img src="https://github.com/user-attachments/assets/20b574fd-3f11-4afe-ac0e-2ebb3a4fed44" width="300">

  This mode together with these tools can be used to dump the rom, make backups, flash the rom and many other things
  
---
  
### **BROM (bootrom) mode**
  It is used in mtkclient or spflash tool
  When using these 2 tools, you might want to put the phone in this mode
  To do this, hold the Owl/Heart/Qinguard button and back button and connect the device to your computer, while mtkclient or spflashtool is running
  
 <img src="https://github.com/user-attachments/assets/0b3f8312-71f7-4ac1-b2d1-e6e21251a2b4" width="200">
 
The view from mtkclient:
 
 <img src="https://github.com/user-attachments/assets/f6b7e5ef-7db0-4b38-9b40-26b05f0f6661" width="300">


---



## Keypad and buttons

- Pressing the **4, 7,** keys at the same time gives the same keycode as the back button. This is probably caused by how the keyboard distinguishes buttons, either by a row-column matrix or by having different resistances for each key. It could mean that the 3 keys' resistances add up to be the same as the back button's resistance.

- When experimenting with settings in the stock locked ROM, I was very interested in the "Quick Settings" tab (which is responsible for selecting hotkeys for different actions such as vol+, vol-, opening an app, speed dial, flashlight, or opening any other app. The action is invoked when a chosen button is long pressed), and I discovered a couple of things.  
    - **First discovery:** The hotkeys only work with the default launcher. I am using a custom open-source minimalist launcher which can be found [here](https://github.com/DroidWorksStudio/EasyLauncher). I will discuss useful software for the phone later.  
      
      So the hotkeys don't work with my launcher **EXCEPT** for vol+ and vol-. I later discovered that the value of the button for these two actions is stored in the global table as **volume_down_shotcut_keycode**. (Not *shortcut* but *shotcut*.) This isn't the case for any other actions, which suggests that they are handled differently.  

      The value of the setting changes depending on which key we choose, although from the settings we can only choose the number keys. After some tweaking with ADB, changing the value, and testing it out, I came up with this "key map":

      ```
      "0"    : none
      "1"    : none
      "2"    : none
      "3"    : none
      "4"    : back button
      "5"    : call button
      "6"    : none
      "7"    : 0 number key
      "8"    : 1 number key
      "9"    : 2 number key
      "10"   : 3 number key
      "11"   : 4 number key
      "12"   : 5 number key
      "13"   : 6 number key
      "14"   : 7 number key
      "15"   : 8 number key
      "16"   : 9 number key
      "17"   : *
      "18"   : #
      "19"   : up (on the "joystick")
      "20"   : down (on the "joystick")
      "21"   : left (on the "joystick")
      "22"   : right (on the "joystick")
      "23"   : middle (big round button)
      "24"   : none
      "26"   : untested
      ```
      To get the current value, use ```adb shell settings get global volume_down_shotcut_keycode``` and to change it use ```adb shell settings put global volume_down_shotcut_keycode 4```
      Of course, change the *volume_down_shotcut_keycode* to *volume_up_shotcut_keycode* and the value (e.g. 4) accordingly.
      This can **only** be done using adb or with some tweaking with a custom settings database editor like [this one](https://github.com/MuntashirAkon/SetEdit).
      
      This key map **can** be useful if you use the stock rom and want to set your volume keys to any of the buttons... exept for the power button... and the **Owl/Heart/Qinguard button** 🤔
      It turns out that at least to my knowlege these two cannot be mapped using the stock settings (and with the help of adb). While the power button makes sense since it has a crucial role of powering on and off, the other one doesn't make any sense.

      With this out of the way I strongly suggest using [this KeyMapper](https://github.com/keymapperorg/KeyMapper) app. It is free, open source and works great, allows for a lot more tweaking and supports the **Owl/Heart/Qinguard button** lol.
      
    - **Second discovery:** It turns out the **Owl/Heart/Qinguard button** is handled diffirently than the other keys. When you connect your phone to a computer and run ```adb shell getevent -lq``` it will output the actions that happen in the device.
      When you most of the buttons you get something like this:
      
         In this case **button 1** pressed:
         ```/dev/input/event0: EV_KEY       KEY_1                DOWN                
            /dev/input/event0: EV_SYN       SYN_REPORT           00000000            
            /dev/input/event0: EV_KEY       KEY_1                UP                  
            /dev/input/event0: EV_SYN       SYN_REPORT           00000000
         ```
         When the **power button** is pressed:
         ```
            /dev/input/event1: EV_KEY       KEY_POWER            DOWN                
            /dev/input/event1: EV_SYN       SYN_REPORT           00000000            
            /dev/input/event1: EV_KEY       KEY_POWER            UP                  
            /dev/input/event1: EV_SYN       SYN_REPORT           00000000
         ```
         And when the **Owl/Heart/Qinguard button**
         ```
            /dev/input/event3: EV_KEY       KEY_MENU             DOWN                
            /dev/input/event3: EV_SYN       SYN_REPORT           00000000            
            /dev/input/event3: EV_KEY       KEY_MENU             UP                  
            /dev/input/event3: EV_SYN       SYN_REPORT           00000000
         ```

         Notice how the /dev/input/event**X** differs depending on the keys. From this we know that the **power button** and the **Owl/Heart/Qinguard button** are both handled differently than the rest.

      
---



# Software
The software on the phone may vary. What I present here is based on the **Original Factory ROM** Build number 2.3.6, which is the newest as of March 2025.  
It contains a lot of bloatware and possibly spyware. Some of it can be removed **without root**, while removing others **does require root**.  
Some system apps **can** be deleted and the phone will still function, while others **cannot** be removed!

### Preinstalled Apps
A list of apps installed by default that aren't part of Android or MTK apps:

```
- com.baidu.map.location         : NetworkLocation          /system/app/Baidu_Location/Baidu_Location.apk
- com.duoqin.inputmethod         : Voice input method       /system/priv-app/VoiceInput/VoiceInput.apk
- com.duoqin.inputmethod.pinyin  : (Chinese characters)     /system/app/DuoqinIme/DuoqinIme.apk  
- com.duoqin.pinyin              : Keypad input method      /system/app/DuoqinIme_new/DuoqinIme_new.apk
- com.duoqin.promarket           : App Market               /system/priv-app/Market/Market.apk   
- com.duoqin.qweather            : Weather                  /system/app/Weather/Weather.apk
- com.duoqin.remoteservice       : Duoqin Remote Service    /system/priv-app/RemoteService/RemoteService.apk  
- com.duoqin.syncassistant       : Sync Assistant           /system/app/Baidu_Location/Baidu_Location.apk
- com.duoqin.translator          : Duoqin Translator        /system/app/Translator/Translator.apk
- com.iqqijni.dv12key            : 12Key-Keyboard           /system/app/KikaIME/KikaIME.apk
- com.wapi.wapicertmanager       : WAPI certificate         /system/priv-app/WapiCertManager/WapiCertManager.apk
```

#### Be Careful When Removing!
Most of this is useless and can be removed with the device still booting **EXCEPT FOR THE WEATHER APP!**  
This <ins>wasn't tested by me</ins>, but people reported the phone **entering a bootloop** after removing the weather app!
## Debloating the System
There are multiple ways to debloat the system or delete the apps:
### **Disabling Some of the Apps**
It's not possible to uninstall the bloatware, but you can disable some of the apps in the settings. You can also strip them of background data permissions and other permissions, but they will technically still be there. This **does not** require root but isn't very effective.
### **Uninstalling the Apps with a Debloater**
You can uninstall all the apps **if your phone is rooted** using a system app remover/debloater like [this one](https://github.com/sunilpaulmathew/De-Bloater). However, for me, they only seemed to be removed temporarily but actually stayed there like nothing happened. This was very irritating. It might be just me using the app incorrectly, but I think it **isn't the best option**, considering that you **already need root to do this**.
### **Uninstalling the Apps with ADB**
On a normal Android device, you could uninstall system apps like this:
```
adb shell
su
pm uninstall -k --user 0 <package-name>
```
This does not work for this phone, though 🙂. Whenever any `pm` command is sent, it just says:
```
Failure
```
It seems like the `pm` command was deliberately modified by the manufacturer to not work. Either way, this method **would require root**.
### **Manually Removing Apps**
You can remove apps from the filesystem if your phone is rooted. For example:
```
adb shell
su
rm /system/path/to/an/app -r
```
You would need to first find the path, but this way, the app will literally cease to exist. This is my preferred method 🙂. Of course, you will **need root** for this.

---

## Original ROM unpacked
It's posssible to unpack the original ROM provided by the manufacturer.\
I did this by first [doing a backup](#making-a-full-backup) (rom dump).\
This left me with a folder with many .bin files:

<img src="https://github.com/user-attachments/assets/1b332f5f-9d1f-45c0-82c4-28bf610d63da" width="800">

**Here's the list of them, explained briefly (I skipped A/B versions like boot_a.bin and boot_b.bin as they are ussually copies)**

```
boot_a.bin:                        These partitions contain the boot image, including the kernel and ramdisk, essential for booting the device.
boot_para.bin:                     Would likely store boot parameters or configuration data but is empty.​
dtbo_a.bin:                        Contains the Device Tree Blob Overlay, which provides hardware configuration data to the kernel.
expdb.bin:                         Seems to contain some boot logs.
flashinfo.bin:                     May hold information about the flash storage but is mostly empty
frp.bin:                           Should store Factory Reset Protection data but is almost empty.
gpt_backup.bin / gpt.bin:          These files represent the GUID Partition Table (GPT) and its backup, defining the partition layout on the storage device.​
gz_a.bin:                          Could be related to the 'gz' partition, possibly containing the Gzip-compressed kernel. For me it is completely empty though.
lk_a.bin:                          Contains the Little Kernel bootloader, responsible for initializing hardware and starting the main kernel.
logo.bin:                          Holds the boot logo displayed during device startup.​
md_udc.bin:                        I belive it contains the userdata partition decryption keys altough it is mostly empty
md1img_a.bin:                      Seems to store modem firmware images, crucial for cellular communication. 
metadata.bin:                      Unknown, empty file
nvcfg.bin:                         Likely holds NV (Non-Volatile) configuration data, such as radio or network settings.​
nvdata.bin:                        Stores NV (Non-Volatile) data, which may include IMEI numbers, calibration data, and other persistent settings.​
nvram.bin:                         Contains Non-Volatile RAM data, essential for storing persistent system settings and configurations.​
otp.bin:                           Unknown, empty file
para.bin:                          Unknown, almost empty file
proinfo.bin:                       Contains the serial number and some hardware information. Almost empty
protect1.bin:                      Unknown, contains some data
scp_a.bin:                         Unknown, contains a lot of binary data and some readable strings.
sec1.bin:                          Unknown, empty file
seccfg.bin:                        Likely contains security configuration settings for the device.​ Mostly empty file
spmfw_a.bin:                       Could be related to the System Power Management Firmware. Contains some code but is mostlu empty
sspm_a.bin:                        Unknown, contains the string tinysys-sspm at the beggining.
super.bin:                         Contains the system etc.
tee_a.bin:                         Unknown.
userdata.bin:                      Stores user data, including installed applications and personal files.​
vbmeta_a.bin:                      Contain Verified Boot metadata, used for veryfing image before booting.
vbmeta_system_a.bin:               Seems to store some system metadata like com.android.build.product.security_patch
vbmeta_vendor_a.bin:               Seems to store some system metadata like com.android.build.product.security_patch
vendor_boot_a.bin:                 Unknown, empty file.
[read preloader]boot1.bin:         Contains the preloader or initial bootloader code, responsible for early hardware initialization before handing control forward.
```

**For me the most interesting files will be:**
   - boot_a.bin
   - super.bin
   - lk_a.bin
   - logo.bin

I will try to unpack each of them and then maybe try to modify later.

## boot_a.bin
This file contains the **boot image** including the **kernel** and the **ramdisk**.\
We can unpack it using the amazing [Android Image Kitchen](https://xdaforums.com/t/tool-android-image-kitchen-unpack-repack-kernel-ramdisk-win-android-linux-mac.2073775/).\
When we have the Android Image Kitchen ready, simply **drag and drop** your **boot_a.bin** onto **unpackimg.bat**

![image](https://github.com/user-attachments/assets/731e9d06-5fb9-4a1e-b715-7eecc1a6fa36)

We will now have 2 new folders:

![image](https://github.com/user-attachments/assets/22263e74-4754-4537-98d8-52eefaa3ba46)

The **split_img** folder contains the **boot_a.bin** individual parts.

![image](https://github.com/user-attachments/assets/34456fa9-109c-4845-aef3-1097054c6f5f)

The most interesting files are **boot_a.bin-kernel** and **boot_a.bin-ramdisk.cpio.gz**\
The first one, of course is the **kernel** and contains just binary data.\
The second one contains the **ramdisk** and can be <ins>opened</ins>.\
But <ins> this </ins> was already done for us and the ramdisk contents are already in the **ramdisk** folder.

![image](https://github.com/user-attachments/assets/c20fe1a4-5f5a-420a-8c20-9b961ba5f3b5)

Folders that are empty were marked with **red**.\
They are mostly folders that will be **mountpoints**,\
or will contain **processes, devices etc** when the system is running.

Folders that are marked with **green** contain various files.
These include:
   - libraries
   - binaries
   - fstab configs
   - init files
   - images
   - others


![image](https://github.com/user-attachments/assets/36a05ff3-3be3-41f6-9945-da998c6cf29b)
---
![image](https://github.com/user-attachments/assets/ab4bace5-3cd0-40d5-aef7-6974048dfc71)
---
![image](https://github.com/user-attachments/assets/1fdb57a1-6b8c-45e6-bb6d-2ad9f6371b56)


---


# Hacking the Device

## Before You Start
Now that you know a lot of technical details about the system, you can try to hack it. There are many things you can do, but no matter what you try, **you should be very careful**, as everything past this point **<ins>may</ins> lead to you bricking your device**. All the information given by me was gathered by my research and the work of many other people. Using this information i succeded in hacking this phone but I cannot guarantee that you will succeed.

Before doing **anything**, you must make a backup of your original ROM. This could come **very handy** when you realize you bricked your device.
> **DO YOUR BACKUPS AND KEEP THEM SAFE!**

---

## Making a Full Backup

### Requirements
To make a full device backup, you will need [mtkclient](https://github.com/bkerler/mtkclient). I will be using **mtkclient GUI**. It's a tool used for:
- Exploitation
- Reading/Writing flash
- Unlocking/Locking the bootloader
- And more

I **will not go into details on how to install it**. You can find installation guides on the internet. You will also need to install some drivers.

#### Alternative Method
If you do not want to install everything manually, you can use this **[ready-to-use ISO file](https://androidfilehost.com/?fid=15664248565197184488)**:
1. Burn the ISO onto a flash drive or use [Ventoy](https://www.ventoy.net/en/index.html).
2. Boot from the USB drive.
3. Select **Boot Live System**.
4. After booting, you will see **mtkclient GUI** on the desktop. This is what I used mostly.
<img src="https://github.com/user-attachments/assets/8697a9f8-c64c-4d28-8930-8165ca1b9615" width="300">

<br>

### Either way, you need to run **mtkclient GUI**!

<br>

### Steps to Make a Backup
1. Run **mtkclient GUI**.
2. Power off your device and connect it in **[BROM mode](#brom-bootrom-mode)**. Alternatively, you can try to do the same in [preloader mode](#preloader-mode).
   - To enter BROM mode, follow [this guide](#brom-bootrom-mode).
   - If successful, you should see a confirmation message.
     
     <img src="https://github.com/user-attachments/assets/f6b7e5ef-7db0-4b38-9b40-26b05f0f6661" width="300">
        
   - If not, check:
     - Your cable
     - Your connection
     - Whether you have the correct drivers installed
     - If the USB device is recognized at all


3. Proceed with the backup:
   - Open the **Read partition(s)** tab.
   - Click **Select all partitions**.
   - You <ins>can</ins> unselect **userdata** from the list:
     - This partition contains user data. If your phone is factory reset, there is no need to back this up.
     - If your phone is not factory reset and you want to keep your data, leave the box checked.
     - However, be aware that **userdata is encrypted**.
     - If the decryption keys are lost (their location is unknown to me), you may not be able to decrypt it later, resulting in data loss.
     - If you are flashing other ROMs, assume you will lose userdata.
   - Enable **Dump GPT**.
   - Press **Read Partition(s)** and select a safe place to store the backup.
   - Click **OK** and wait for the process to complete.

     <img src="https://github.com/user-attachments/assets/0ca80eec-4827-429b-9ba9-ec3a00ba5556" width="300">

> **DO NOT touch anything, move the cable, or interrupt the process!**
 4. When it says its **done** you should have a bunch of files in the directory you chose\
     Again, **keep them safe**
5. Now, we will backup the **Preloader**\
    I am not yet sure if this is essential but it doesn't hurt to backup it anyway\
    If you backup it, you might then **unbrick your device easier** so it is worth it
   - Open the **Flash Tools** tab.
   - Click **Read preloader**
   - Select a safe place to store it.
     - I like to rename it from ```boot1.bin``` to ```[preloader]boot1.bin```
6. Success! You should now have an entire system backup\
   It can be reflashed later in case of a brick or you wanting to go back to its original ROM\
   To reflash use the **Write Partition(s)** tab

     <img src="https://github.com/user-attachments/assets/1b332f5f-9d1f-45c0-82c4-28bf610d63da" width="600">

   Note: in step 3. you could also use the option **Read flash** from the **Flash Tools** tab to read the whole flash (?)

---

## Rooting
To root the device you will need to **patch the boot image**.\
Before doing that, you need to know **which slot is active**. For this you will need **fastboot** installed\
Note: This tutorial is based on [this](https://xdaforums.com/t/guide-xiaomi-qin-f21-pro-mt6761-global-rooted-with-play-store.4425811/) tutorial, my experience and research and other info on [XDA Forums](https://xdaforums.com/).

**The steps needed to root the phone:**
1. **Boot into** [fastboot](#fastbootbootloader-mode) using the information [here](#fastbootbootloader-mode).
2. **Connect to a computer with fastboot installed** and run:
   ```
   fastboot getvar current-slot
   ```
   - This will output either slot ```a``` or slot ```b```.
   - Remember which one it is.
     
3. **Go into your ROM backup.** If you haven't done it, [do it now](#making-a-full-backup)!
   - Find the following file: ```boot_a.bin``` or ```boot_b.bin``` **depending on which slot was active**.
   - ```boot_a.bin``` for slot a active and ```boot_b.bin``` for slot b active.

4. **Copy that file** to the phone's internal memory by connecting it with a cable to your computer or by ```adb push```
   - Put it somewhere that you will find later.
   - It's the file that you will patch with magisk.

5. **Download Magisk** [latest .apk file](https://github.com/topjohnwu/Magisk/releases) 
    - It should be named app-release.apk
    - You also need to copy this file to your phone's internal memory

6. **Install Magisk app** from the .apk file you put in your memory
   - For this you will need to find it in file explorer and click on it and install.
   - If you cannot install it, you might need to put it in **/Internal shared storage/Android/obb** folder
   - If you still cannot install the app, you will need to find help online.

7. **Open the Magisk app** once installed and patch the boot image
   - You should see an **Install** button. Click it.
   - Now, you will have to select the ```boot_a.bin``` or ```boot_b.bin``` file from before.
   - Once selected click **LET'S GO ->**. It will now proceed to patch the boot image.
   - The patched image should be saved somewhere in the phone's memory, usually in **/Internal shared storage/Downloads**.
   - The exact location should be printed out (it's cut off in the screenshot but you can swipe to see it).
     
     <img src="https://github.com/user-attachments/assets/8f7f9a83-36a4-40ff-afe4-a533367a7765" width="300">

8. **Copy the patched boot image** back to your computer using a cable or ```adb pull```
   - This file will need to be flashed as **boot_a** or **boot_b** partition using mtkclient.
   - For this, you need to copy it from the device to the computer.
   - **You should change the file extension to .bin** so that mtkclient recognizes it.

9. **Run mtkclient gui and unlock the bootloader**
   - Power off your device and connect it in BROM mode to mtclient.
   - If you don't know how to enter BROM mode, follow [this guide](#brom-bootrom-mode).
   - Go into the **Flashing** tab and press **Unlock Bootloader**
   - This should unlock your phone's bootloader.

10. **Download [this vbmeta](https://github.com/AlikornSause/Notes-on-QIN-F21-PRO/blob/main/vbmeta_a.bin) file**
    - This file is needed to enable booting the patched image.
    - It comes from [this](https://xdaforums.com/t/guide-xiaomi-qin-f21-pro-mt6761-global-rooted-with-play-store.4425811/post-88203539) post from XDA Forums. The author of the post, @-gloim- claims that the file comes from [this](https://xdaforums.com/t/guide-xiaomi-qin-f21-pro-custom-firmware-root-playstore-certified.4405615/) tutorial.
    - This file solved this issue apearing on the screen:
      ```
      dm-verity corruption
      Your device is corrupt.
      It can't be trusted and may not work properly
      Press power button to continue.
      Or, device will power off in 5s
      ```
      I think it's caused by the bootloader not accepting the boot image, because it can't verify it.
    - Some people suggested that flashing an empty file instead of this vbmeta file works but **I can't advise that, as it didn't work for me**
    - It did not work for me because it probably didn't even flash the file. The mtkclient gui kept freezing when flashing an empty file.
    - It might be that the empty file is just not accepted and it declines and freezes.
    - Someone might have found a solution to that. He used this command to flash the empty file:
      ```fastboot --disable-verity --disable-verification flash vbmeta_a vbmeta_a.bin```

    - It may have worked for him but **I did not use that method. I just used [the file](https://github.com/AlikornSause/Notes-on-QIN-F21-PRO/blob/main/vbmeta_a.bin) i provided above** and thats what I advise everyone to do
    
11. **Flash the patched boot image and vbmeta file**
    - Open the **Write Partition(s)** tab.
    - Find **boot_a** or **boot_b** (depending on your **active slot**) in the list.
    - Click **Set** next to the **boot_a** or **boot_b** and select your magisk patched image.
    - Find **vbmeta_a** or **vbmeta_b** in this list.
    - Click **Set** next to the **vbmeta_a** or **vbmeta_b** (depending on your **active slot**) and select [the vbmeta file](https://github.com/AlikornSause/Notes-on-QIN-F21-PRO/blob/main/vbmeta_a.bin) you downloaded earlier.
    - **MAKE SURE NO OTHER PARTITION IS SELECTED!**
    - Click **Write partition** and let it do its thing
   
    ![image](https://github.com/user-attachments/assets/6f414421-bad4-4652-b5e8-09e28aba5845)


> **DO NOT touch anything, move the cable, or interrupt the process!**

12. **When it says its done, unplug your phone**.
    - The process should now be done!

13. **Power your device up**
    - You should see an **Orange state warning**. This is **normal**. It means the bootloader is unlocked.
    - The message should not be worrying. The phone will boot in 5 seconds.
    - The message can also be [changed](#changing-the-orange-state-warning-text) or [removed](#removing-the-orange-state-warning-text).
    - The 5 second delay can albo be [removed](#removing-the-5-second-delay-in-orange-state).

14. **Your phone should now be rooted!**
    - After powering on, launch the magisk app. You should see a screen similar to this:

      <img src="https://github.com/user-attachments/assets/ccc552ff-64b5-456c-b2d8-ac1d2148c825" width="300">
      
---


## Modifing the /system partition
**BE CAREFUL!** When editing the /system partition you can delete crucial system files and brick your device!
<br><br>
If your device is already rooted you can edit anything on the /system partition.\

The steps to do this:
1. You need to get a root shell. This can be done through a terminal app or through adb.
   - If you want to use a terminal app you will need to grant superuser permission when using it.\
     To do this, simply open up a command line [(termux)](https://github.com/termux/termux-app) or something similar and type in:
     ```
     su
     ```
     This will prompt for superuser permission if you have working magisk root. Grant this permission.\
     Now you have a root shell on your device. This can be seen as a **#** at the end of your command prompt instead of a **$**
     
   - If you want to use adb, run:
     ```
     adb shell
     su
     ```
     You will probably be also prompted for superuser permission. **It might also require enabling adb root access in magisk settings**.\
     Now you have a root shell using adb. This can be seen as a **#** at the end of your command prompt instead of a **$**
     
     Note: This is **NOT** the same as doing ```adb root```, which is only available on test builds and would require some tweaking to work on this device

2. Remount the /system partition:
   ```
   mount -o rw,remount /
   ```
   This will make the /system partition writable.
   
3. You can modify anything as long **as you are root**. After a reboot you will need to remount it again\
   **BE CAREFUL!** When editing the /system partition you can delete crucial system files and brick your device!


---


## Debloating

---


## Installing GAPPS
TO BE ADDED LATER
---
## Installing custom ROMs
TO BE ADDED LATER
---
## Changing the Orange State Warning text
**You might me annoyed by this text that appears when booting:**
```
Orange State
Your device has been unlocked and can't be trusted
Your device will boot in 5 seconds
```
You can change it to say something else.

**The steps to change the text:**
1. **Go into your ROM backup.** If you haven't done it, [do it now](#making-a-full-backup)!
   - Find the following file: ```lk_a.bin``` or ```lk_b.bin``` **depending on which slot is active**.
   - **LK** stands for **Little Kernel** and is a kind of bootloader.
     
2. **Open the file with a hex editor** like [HxD](https://mh-nexus.de/en/hxd/)
   - We will need to edit the file as hex information
     
3. **Find the string**
   - Do a text search for **"orange"** or **"state"**.
   - You will probably see a couple of strings containing the word **"orange"** but you need to find the one with the whole string.
   - It should look like this:
     
     ![image](https://github.com/user-attachments/assets/ac62515e-c21c-4e28-8b25-a27abb9777fa)

4. **Edit the string**
   - Now you can edit the string **BUT BE VERY CAREFUL!**.
   - You **shouldn't add** any text but **overwrite** the text to be displayed that's already in there.
   - It should look something like this.
     
     ![image](https://github.com/user-attachments/assets/cbca998f-463e-4090-8b92-ccb0e69922d6)

   - Notice how I zeroed the rest of the text area and didn't put spaces in there.
   - Make sure you **don't** put 0 as a character because it will display 0's on the screen.
   - Make sure you **don't** put spaces in there.
   - Put ```00```'s in **HEX** and **not** "0"s as characters!

5. **MAKE SURE you didn't overwrite anything**
   - You have to be sure that you didn't overwrite anything that was in there.
   - You can **only overwrite the text that would be displayed**.
   - Make sure the text you put there together with the ```00's``` isn't longer than the original text.
   - **You really shouldn't overwrite anything other than the text displayed!**
     
6. **Save the file somewhere else as lk.bin**
   - Make sure **not to overwrite your backup file!**
     
7. **Flash the file**
   - Flash the file to either ```lk_a``` or ```lk_b``` partitions **depending on which slot is active**
   - You should do the flashing the same way as in [here](#rooting) point 11 using mtkclient.
   - Again, **make sure you only overwrite the lk_a or lk_b**.
     
8. **Reboot**
   - If done corectly, the text should be changed accordingly 🙂
   - This can also be used to change other strings.
   - This includes the **Red state** warning and other warnings.
   - The process should be very similar although **I haven't tested that**.
   - But always, be **very carefull** when modifing these files.

**If the device behaves weirdly, you might have made an error when editing, try to reflash the original backup of lk**
---
## Removing the Orange State Warning text
**You might me annoyed by this text that appears when booting:**
```
Orange State
Your device has been unlocked and can't be trusted
Your device will boot in 5 seconds
```
You can remove it the same way as editing it [here](#changing-the-orange-state-warning-text).
You will just need to put ```00's``` in place of all of the characters.
This should look like this.

![image](https://github.com/user-attachments/assets/81b220f4-4862-47d9-b9a8-acd1ef875ce3)

Other than that, the steps with removing the text are the same as [changing it](#changing-the-orange-state-warning-text).

**If the device behaves weirdly, you might have made an error when editing, try to reflash the original backup of lk**
---
## Removing the 5 second delay in Orange State
**You might me annoyed by the 5 second delay that slows down the booting process when in Orange State**
It can be deleted easily and involves the same steps as [changing the orange state warning text](#changing-the-orange-state-warning-text).

The process involves these steps:
1. **Go into your ROM backup.** If you haven't done it, [do it now](#making-a-full-backup)!
   - Find the following file: ```lk_a.bin``` or ```lk_b.bin``` **depending on which slot is active**.
   - **LK** stands for **Little Kernel** and is a kind of bootloader.
     
2. **Open the file with a hex editor** like [HxD](https://mh-nexus.de/en/hxd/)
   - We will need to edit the file as hex information
     
3. **Find the needed value**
   - Do a text search for ```08B50E4B7B441B681B68022B``` in hex.
   - It should look like this:
     
     ![image](https://github.com/user-attachments/assets/5dbe2466-8fb8-4f83-8d29-98751deefcbf)
     
4. **Change the value**
   - To remove the 5 second delay, you will need to **OVERWRITE** this value.
   - The value to put in its place is ```08B5002008BD1B681B68022B```
   - They are the same lenght.
   - **MAKE SURE not to add more characters**

5. **Save the file somewhere else as lk.bin**
   - Make sure **not to overwrite your backup file!**
     
6. **Flash the file**
   - Flash the file to either ```lk_a``` or ```lk_b``` partitions **depending on which slot is active**
   - You should do the flashing the same way as in [here](#rooting) point 11.
   - Again, **make sure you only overwrite the lk_a or lk_b**.
     
7. **Reboot**
   - If you did everything correctly, it should now be fixed.
   - Now there will be no additional delay.
   - There will also be no text.
   - The boot time will be shorter by 5 seconds 🙂
   

**If the device behaves weirdly, you might have made an error when editing, try to reflash the original backup of lk**

---

# Errors you can encounter
TO BE ADDED LATER




# TODO:
Document:
- Editing boot_a.bin
- TWRP installation
- installing gapps
Make work:
- /userdata decryption
- /system auto writable mount
- change logo.bin
- make twrp boot image work with sound
- make custom roms work with 32/3 version

