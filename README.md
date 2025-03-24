# Notes on QIN F21 PRO
## Table of Contents
- [Disclaimer](#disclaimer)
- [Introduction to the phone](#the-phone)
- [Device variants](#versions)
    - [Hardware variants](#hardware-versions)
    - [Software variants (ROMs)](#software-versions)
    - [Custom ROMs](#custom-roms)
    - [Differences](#differences)
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
      
## Disclaimer
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

### Custom ROMs
 There are also some custom ROMs for this phone:
 - **LineageOS 18.1:** Custom ROM posted by @a9381 user on [XDA Forums here](https://xdaforums.com/t/rom-beta-unoffical-lineageos-18-1-for-xiaomi-qin-f21s-pro-by-a-i-v.4431693/), it contains some bugs such as the keypad backlight being always on, no access to /data partition by twrp, VOLTE problems and the wifi and bluetooth being on by default. These bugs seem to be fixable and possibly already fixed in the newer versions of this rom. I haven't tested it yet but it seems like a great alternative to the stock ROMs. I haven't tested this ROM yet but it is reported to work on the 32+3GB version.
 - **Some kosher ROMs for for the religious people from Israel** made by @Ashi Vered. You can find more info in [his GitHub page](https://github.com/AshiVered/Android-custom-ROMs).

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
   The privacy topic will be discussed more later in this document.

### Differences
The **64+4GB version** seems to be **easier to root and install custom ROMs**. I personally have a **32+3GB black English original ROM** and have confirmed that it's possible to modify and root this version. 

For hacking purposes, the **most important factor** is whether you have the **64+4GB or 32+3GB version** and whether **the bootloader is unlocked**—other differences don't matter as much.



---



## Hardware Modes
The phone can be booted into several modes, all of which require the device to be **TURNED OFF**.

#### **Normal Mode**
Entered by pressing the **power button** for a few seconds until the logo appears.

<img src="https://github.com/user-attachments/assets/fd88e24c-d9e9-4881-8113-91b7e388cf6f" width="300">

#### **Recovery Mode**
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

<img src="https://github.com/user-attachments/assets/c80d086b-f327-4733-b43a-26f6bcef1f44" width="300">

You will then see this menu:

<img src="https://github.com/user-attachments/assets/243b470e-849d-4587-ae87-5ba379ebf61d" width="300">

##### **Navigation**
- Use the **joystick buttons** to navigate.
- Use the **power button** to select.

##### **Recovery Menu Options**
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

#### **Fastboot/Bootloader Mode**
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

<img src="https://github.com/user-attachments/assets/d2637828-6242-426c-b2c8-bc555096ebe2" width="300">

##### **Fastboot Commands**
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
#### **Preloader mode**
  It is used in mtkclient or spflash tool
  When using these 2 tools, you might want to put the phone in this mode
  To do this, simply connect the phone to your computer with a USB cable when the tool is running without pressing any keys.
  This should put the phone in preloader mode.

  The view from mtkclient:
  
  <img src="https://github.com/user-attachments/assets/20b574fd-3f11-4afe-ac0e-2ebb3a4fed44" width="300">

  This mode together with these tools can be used to dump the rom, make backups, flash the rom and many other things
  
#### **BROM (bootrom) mode**
  It is used in mtkclient or spflash tool
  When using these 2 tools, you might want to put the phone in this mode
  To do this, hold the Owl/Heart/Qinguard button and back button and connect the device to your computer, while mtkclient or spflashtool is running
  
 <img src="https://github.com/user-attachments/assets/0b3f8312-71f7-4ac1-b2d1-e6e21251a2b4" width="300">
 
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



## Software
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


## Hacking the device
### Before you start
   Now that you know a lot of technical details of the system you can try to hack it.\
   There are many things you can do but no matter what you try **you should be very careful**\
   as everything I talk about past this point **<ins>may</ins> lead to you bricking your device**
   
### Making a full backup
Before doing **anything** you want to make sure you have a backup of your original ROM.\
This could come **very handy** when you realise you bricked your device.
**DO YOUR BACKUPS AND KEEP THEM SAFE!**

1. To make a full device backup you will need [mtkclient](https://github.com/bkerler/mtkclient), i will be using mtkclient gui.\
    It's a tool used for exploitation, reading/writing flash, unlocking/locking the bootloader and others.
    
    I **will not go into details how to install it**, you can find that on the internet.\
    You will also need to install some drivers.
    
    If you do not want to play with installing everything, you can use [this ready to use ISO file](https://androidfilehost.com/?fid=15664248565197184488)\
    You will need to boot from it (by first burning it onto a flash drive or using [ventoy](https://www.ventoy.net/en/index.html)), then select Boot Live system\
    After it boots you will see **mtkclient gui** on the desktop and thats what I used mostly\
    #### Either way you need to run mtkclient gui!

2. When it's running, power off your device and connect the device in the [BROM mode](#brom-bootrom-mode)\
    to do this, use [this](#brom-bootrom-mode).\
    You should see the message: (If you don't, check cable, check connection, check if you have drivers, check if the usb device is recognised at all)

 <img src="https://github.com/user-attachments/assets/f6b7e5ef-7db0-4b38-9b40-26b05f0f6661" width="300">

3. Now we will proceed to make a full backup.\
    Make sure you're in the **Read partition(s)** tab\
    Press **Select all partitions**\
    You <ins>can</ins> unselect **userdata** from the list.\
        This would contain all user data but if your phone is factory reset there's no need to backup this\
        If it isn't factory reset and you have some data that you want to backup, then leave the box checked\
        
        Either way I am not 100% sure if you can save userdata after flashing other ROMs etc. because this partition is encrypted\
        This means that if somehow the decryption keys are lost (and I do not know where they are stored) it will not dectypt it, making you lose data.\
        So if you're planning to flash other ROMs, you probably will lose userdata.
    Make sure **Dump GPT** is enabled\
    Press **Read Partition(s)**. You might be prompted for output directory, select a safe place to store the backup
    Click okay and now it should dump all the selected partitions.
    Dont touch anything, don't move the cable and wait for it to do its thing

### Rooting
### Modifing the /system partition
### Debloating
### Installing GAPPS
### Installing custom ROMs
