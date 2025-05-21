# 📦 Removing the 5-Second Delay in Orange State

You might be annoyed by the 5-second delay that extends the boot process.  
The delay can be removed using a method similar to [changing the Orange State warning text](#changing-the-orange-state-warning-text).

---

## 🧰 How to Remove the Delay

### 1. Access Your ROM Backup

If you haven’t made a ROM backup yet, [do it now](#making-a-full-backup)!

- Locate either `lk_a.bin` or `lk_b.bin` in your backup  
  - Choose based on which **slot (A/B)** is currently active  
- **LK** stands for **Little Kernel**, a part of the bootloader

---

### 2. Open the File in a Hex Editor

Use a hex editor like [**HxD**](https://mh-nexus.de/en/hxd/) to open the `lk_*.bin` file.

- You will be editing the file as raw **hex data**

---

### 3. Search for the Target Sequence

Use the search feature to find the following hex sequence:
```
08B50E4B7B441B681B68022B
```

It should look something like this:

![image](https://github.com/user-attachments/assets/5dbe2466-8fb8-4f83-8d29-98751deefcbf)

---

### 4. Replace the Value

To remove the 5-second delay, replace the found value with:
```
08B5002008BD1B681B68022B
```

✅ This value is the **same length**.  
⚠️ **DO NOT** add or remove characters — only **overwrite**!

---

### 5. Save the Modified File

- Save the modified file as `lk.bin`  
- **Do not overwrite your original backup!** Save it as a seperate file.
- Remember to keep the original backup safe.

---

### 6. Flash the Modified File

- Flash the modified file to either the `lk_a` or `lk_b` partition  
  - This depends on your active slot  
- Flash it the same way described in [this step](#rooting) (see point 11)

⚠️ Be very careful to flash **only** `lk_a` or `lk_b` — do **not** touch other partitions.

---

### 7. Reboot and Verify

- Reboot your device  
- If everything was done correctly:
  - The 5-second delay will be gone  
  - The Orange State warning text will not appear  
  - Boot time will be faster 🎉
