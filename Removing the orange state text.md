# Changing the Orange State Warning text
**You might be annoyed by this text that appears when booting:**
```
Orange State
Your device has been unlocked and can't be trusted
Your device will boot in 5 seconds
```
[NOTE: some googled devices seem to not show this message]

You can change it to say something else.

## Removing / chaning the orange state warning text
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
   - If done correctly, the text should change as expected 🙂.
   - This can also be used to change other strings.
   - This includes the **Red state** warning and other warnings.
   - The process should be very similar although **I haven't tested that**.
   - But always, be **very carefull** when modifying these files.

**If the device behaves strangely, you might have made an error when editing, try to reflash the original backup of lk**
---
