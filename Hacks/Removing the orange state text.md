# 📦 Removing the Orange State Warning Text

> ⚠️ **Annoyed by this message during boot?**
```
Orange State
Your device has been unlocked and can't be trusted
Your device will boot in 5 seconds
```
> You can safely modify or remove this message by editing the LK bootloader binary.  
> 📝 *Note: Some Google devices may not show this message at all.*

---

## ✅ How to remove the Orange State Warning

### 1. Access Your ROM Backup

If you haven't created a backup yet, [make one now](#making-a-full-backup)!

- Look for either `lk_a.bin` or `lk_b.bin`, depending on your **active slot**
- **LK** stands for **Little Kernel**, part of the bootloader

---

### 2. Open the LK File in a Hex Editor

- Use a hex editor like [**HxD**](https://mh-nexus.de/en/hxd/)
- Open `lk_a.bin` or `lk_b.bin` for raw hex editing

---

### 3. Search for the Warning String

- Use the **text search** function to look for:
  ```
  orange
  ```
  or:
  ```
  state
  ```

- You may find multiple matches — locate the **full warning string**

You should see something like this:

![image](https://github.com/user-attachments/assets/ac62515e-c21c-4e28-8b25-a27abb9777fa)

---

### 4. Edit the String

> ✏️ Now you can remove the message — but **be extremely careful**!

- Overwrite the displayed characters with `00` in HEX, if you want to remove the text.
- You can also change the text to say something else.
- **Only overwrite** the string — **do not add extra characters**
- After your custom message, **fill the remaining space with `00` in HEX**, not `"0"` or spaces

Example:

![image](https://github.com/user-attachments/assets/cbca998f-463e-4090-8b92-ccb0e69922d6)

✅ Notes:
- Do **not** insert actual zero characters — that will display as `0` on boot
- Do **not** use spaces — fill unused space with `00` in **HEX**
- Keep your new message **shorter or equal in length** to the original string

---

### 5. Double Check the Edit

- Ensure **you only changed the display string**
- Verify that you haven’t accidentally edited nearby data
- ⚠️ **The new string (including HEX padding) must not exceed the original length**

---

### 6. Save the File Safely

- Save the edited file as `lk.bin`
- ✅ **Do not overwrite your backup copy!** Keep it safe in case you need to revert

---

### 7. Flash the Edited LK File

- Flash `lk.bin` to the appropriate partition: `lk_a` or `lk_b` depending on your active slot
- Use the same method as [described here](#rooting), step 11 via **mtkclient**

⚠️ Only flash `lk_a` or `lk_b` — never touch other partitions!

---

### 8. Reboot and Verify

- Reboot your device
- If everything was done correctly:
  - ✅ The new message will appear on boot
  - 🛠️ You can also modify other warning texts (e.g., **Red State**) using the same method  
    > ⚠️ Not all have been tested — proceed carefully!

---

> ❗ If your device behaves oddly or won’t boot, reflash the original backup of your LK file.
