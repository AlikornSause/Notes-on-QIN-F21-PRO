# ⚠️ Modifying the `/system` Partition

> **BE CAREFUL!** Editing the `/system` partition can delete crucial system files and **brick your device**!

If your device is already **rooted**, you can modify anything on the `/system` partition.

---

## 🛠️ Steps to Modify `/system`

### 1. Get a Root Shell

You need a **root shell**. This can be done through a terminal app or via **ADB**.

#### 📱 Option A: Terminal App

1. Install a terminal app like [**Termux**](https://github.com/termux/termux-app)  
2. Open it and type:
   ```
   su
   ```
3. If you have **Magisk root**, you’ll be prompted to grant superuser permission. Grant it.

✅ You now have a **root shell** — your prompt will change from **`$`** to **`#`**.

---

#### 💻 Option B: ADB (Android Debug Bridge)

1. On your PC, run:
   ```
   adb shell
   su
   ```
2. Grant superuser permission when prompted.  
   - You may need to enable **ADB root access** in **Magisk settings**.

✅ You now have a **root shell** via ADB — your prompt will show **`#`** instead of **`$`**.

> ❗ This is **not** the same as using `adb root`, which only works on test builds and may require advanced tweaks.

---

### 2. Remount `/system` as Read/Write

Once in a root shell, run:

```
mount -o rw,remount /
```

This command remounts the root filesystem, making `/system` writable.

---

### 3. Modify as Needed

As long as you’re **root**, you can now modify the `/system` partition.

> 🔁 After a reboot, you’ll need to **remount** `/system` again.

> ⚠️ **BE CAREFUL!** Deleting or modifying system files can lead to bootloops or permanent bricking.
