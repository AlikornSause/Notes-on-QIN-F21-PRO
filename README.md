# Notes-on-QIN-F21-PRO
# Disclaimer
I am an amateur and everything i say here should be taked with a grain of salt.
The information presented here was gathered by my research and the amazing [xdaforums.com](https://xdaforums.com/)!
I do not take responsibility for you bricking your device, losing your data or anything similar,
it is very much possible that you will encounter difficulties along the way of rooting, flashing
custom ROMs or modifing your device. The good part is that theres a lot of support online and most
mistakes have already been made and fixed. Good luck hacking!

# The phone
The Qin F21 Pro is a half-touchscreen, half-button phone running Android 11.
The phone features a 2.8-inch 640 x 480px IPS capacitive touchscreen and a 5MP rear camera with a 2MP front camera.
It is compatible with GSM networks 850/900/1800/1900MHz and supports 4G networks.
The device is available in different configurations

# Versions
There are 2 main hardware versions of the phone:
- The 64+4GB version
- The 32+3GB version

they also vary in color, there is:
- A white version
- A black version

and also in keyboard language:
- English
- Russian
- Hebrew

The phone also varies very much in software, there seem to be at least 3 rom versions that you could get:
-Original factory rom: Chinese + English, without Google Play and bootloader locked
-Hacked version: Chinese + English, bootloader unlocked, Google Play present and supposedly Google certified 
-International ROM with Google Play: Many languages supported, bootloader unlocked, Google Play present but NOT-Google certified

# Differences
The 64+4GB seems to be easier to root/ install custom roms.
I have a 32+3GB black english original rom and proved that it's possible to modify the device and root it and I
will mostly focus on this version. What matters most is if you have 64+4GB or 32+3GB version and all the other parameters don't mean as
much for hacking purposes.

# Hardware modes
The phone can be booted into a couple of modes, all of which start from the device being TURNED OFF
- Normal mode entered by pressing the power button for a couple of seconds until you see the logo

![normal](https://github.com/user-attachments/assets/fd88e24c-d9e9-4881-8113-91b7e388cf6f)


- Recovery mode entered by holding down the following buttons: * , owl/heart/qinguard , power/hangup.
  When you see the boot menu, stop pressing the power/hangup button but keep pressing the 2 other.
  If you were to keep pressing the power button the phone would just reboot

  ![recovery](https://github.com/user-attachments/assets/85496ee0-80f1-4552-ac21-1b2465d80fcf)

 You will then be granted with this screen:

 ![image](https://github.com/user-attachments/assets/51cc821b-59e7-48a0-a0bd-fc692de65811)

 To enter the menu, you will need to hold down the power/hangup button and press the up button on the "joystick":

 ![recovery](https://github.com/user-attachments/assets/a6db75fb-3d77-4a43-ae24-dc5f90d402d2)

 Now you will see this menu:
 
![485080215_696675326047670_489383135115806802_n](https://github.com/user-attachments/assets/243b470e-849d-4587-ae87-5ba379ebf61d)

Use the "joystick" buttons to navigate ang the power button to select
What the options do:
-Reboot to system now : reboots to normal mode
-Reboot to bootloader : reboots to fastboot mode
-Enter fastboot : enters a fastboot-like environment
-Apply update from ADB : ? untested
-Apply update from SD card : ? untested (phone also has no SD card slot lol)
-Wipe data/ factory reset : wipes all user data (99% works haven't tested it though)
-Mount /system : says "Mounted /system." at the bottom of the screen, unknown if it can be useful
-Viev recovery logs : opens a dialog with a file that you can open and read, contains recovery logs
-G : performs a graphics test, displaying multiple images including the broken android  "No command" image", data clearing animation and a couple of others, then goes back to the main menu
