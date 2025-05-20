## Rooting
To root the device you will need to **patch the boot image**.\
Before doing that, you need to know **which slot is active**. For this you will need **fastboot** installed\
Note: This tutorial is based on [this](https://xdaforums.com/t/guide-xiaomi-qin-f21-pro-mt6761-global-rooted-with-play-store.4425811/) tutorial, my experience and research and other info on [XDA Forums](https://xdaforums.com/).

## The steps needed to root the phone:**
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
    - This file solved this issue appearing on the screen:
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
    - It seems like the empty file is not accepted, causing the process to freeze.
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
    - You should see an **Orange state warning**. This is **normal**. It means the bootloader is unlocked.\
      [NOTE: some googled devices seem to not show this message]
    - The message should not be worrying. The phone will boot in 5 seconds.
    - The message can also be [changed](#changing-the-orange-state-warning-text) or [removed](#removing-the-orange-state-warning-text).
    - The 5 second delay can also be [removed](#removing-the-5-second-delay-in-orange-state).

14. **Your phone should now be rooted!**
    - After powering on, launch the magisk app. You should see a screen similar to this:

      <img src="https://github.com/user-attachments/assets/ccc552ff-64b5-456c-b2d8-ac1d2148c825" width="300">
      
---

