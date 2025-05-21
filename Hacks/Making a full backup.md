# 📦 Making a Full Backup with MTKclient

## ✅ Requirements
- A Windows / Linux / macOS computer  
- MTKclient (GUI version preferred)  
- A USB cable to connect the phone  

---

## 📝 How to Make a Backup

### 1. Launch **MTKclient GUI**
This guide assumes you're using the GUI version. The command-line version can also be used, but it's not covered here.

---

### 2. Power Off & Connect the Device  
Power off your device and connect it in either:  
- [**BROM mode**](https://github.com/AlikornSause/Notes-on-QIN-F21-PRO/blob/main/Hacks/BROM%20mode.md), or  
- [**Preloader mode**](https://github.com/AlikornSause/Notes-on-QIN-F21-PRO/blob/main/Hacks/Preloader%20mode.md)  

If successful, you should see a confirmation message:

<img src="https://github.com/user-attachments/assets/f6b7e5ef-7db0-4b38-9b40-26b05f0f6661" width="400">

---

### 3. Proceed with the Backup  
1. Go to the **Read Partition(s)** tab  
2. Click **Select all partitions**  
3. You *can* uncheck **userdata**:  
   - This partition contains user data  
   - If your phone is **factory reset**, you can skip backing this up  
   - If your phone is **not factory reset** and you want to keep your data, leave it checked  
   ⚠️ **Note**:  
   - Userdata is **encrypted**  
   - If the decryption keys are lost, you may not be able to decrypt it later — this could result in **permanent data loss**  
4. Enable **Dump GPT**  
5. Press **Read Partition(s)** and choose a safe location to store the backup  
6. Click **OK** and wait for the process to finish  

<img src="https://github.com/user-attachments/assets/0ca80eec-4827-429b-9ba9-ec3a00ba5556" width="300">
<br>
⚠️ **DO NOT** touch anything, move the cable, or interrupt the process!

---

### 4. Verify Backup Files  
Once it says **Done**, you should see a number of files in your chosen backup folder.  
✅ **Keep them safe!**

---

### 5. Backup the **Preloader**  
While it's not yet confirmed whether this is essential, backing it up can make unbricking easier.  
1. Go to the **Flash Tools** tab  
2. Click **Read Preloader**  
3. Save the file somewhere secure  
   - (Optional) Rename it from `boot1.bin` to `[preloader]boot1.bin` for clarity

---

### 6. ✅ Success!
You now have a complete system backup. This can be reflashed using the **Write Partition(s)** tab if you ever need to recover from a brick or restore the stock ROM.

<img src="https://github.com/user-attachments/assets/1b332f5f-9d1f-45c0-82c4-28bf610d63da" width="1000">
