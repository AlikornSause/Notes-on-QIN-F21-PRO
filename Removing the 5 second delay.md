# Removing the 5 second delay in Orange State
**You might be annoyed by the 5-second delay that extends the boot process**
It can be deleted easily and involves the same steps as [changing the orange state warning text](#changing-the-orange-state-warning-text).

## How to remove the 5 second delay in Orange State
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
