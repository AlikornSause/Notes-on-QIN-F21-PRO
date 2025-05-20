# Making a Full Backup
## Requirements
To make a full backup, you need to have mtkclient running.\
In this tutorial, I'm using mtkclient gui.\
If you don't know how to use mtkclient, look [here]().

## How to Make a Backup
1. Run **mtkclient GUI**.
2. Power off your device and connect it in [BROM mode](#brom-bootrom-mode) or in [preloader mode](#preloader-mode).
   - To enter BROM mode, follow [this guide](#brom-bootrom-mode).
   - If successful, you should see a confirmation message.
     
     <img src="https://github.com/user-attachments/assets/f6b7e5ef-7db0-4b38-9b40-26b05f0f6661" width="400">

4. Proceed with the backup:
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
