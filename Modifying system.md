## Modifying the /system partition
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

