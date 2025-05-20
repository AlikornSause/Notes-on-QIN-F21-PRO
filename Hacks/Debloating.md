# Debloating
There are multiple ways to debloat the system or delete the apps:
## **Disabling Some of the Apps**
It's not possible to uninstall the bloatware, but you can disable some of the apps in the settings. You can also strip them of background data permissions and other permissions, but they will technically still be there. This **does not** require root but isn't very effective.

## **Uninstalling the Apps with a Debloater**
You can uninstall all the apps **if your phone is rooted** using a system app remover/debloater like [this one](https://github.com/sunilpaulmathew/De-Bloater).\
**I do not recommend using this method though!**\
For me it didn't work for some of the apps and they stayed even though it said they were gone.\
And knowing that you **need root for this**, you can use a different method.\
I recommend using [the last method](#manually-removing-apps).

## **Uninstalling the Apps with ADB**
<ins>Note: this method doesn't work!</ins>
On a normal Android device, you could uninstall system apps like this:
```
adb shell
su
pm uninstall -k --user 0 <package-name>
```
This does not work for this phone, though 🙂. Whenever any `pm` command is sent, it just says:
```
Failure
```
It seems like the `pm` command was deliberately modified by the manufacturer to not work. Either way, this method **would require root**.

## **Manually Removing Apps**
Disclaimer:\
Doing this **can brick your device**!\
Before deleting an app, **be absolute sure** that you can delete it!\
Some apps can be safely deleted while others cannot!\
You might delete an app responsible for a critical system service!
This might **brick your device** or in some cases **cause a bootloop**!
Make sure to [have a backup](#making-a-full-backup)!

You can remove apps from the filesystem if your phone is rooted.\
For example:
```
adb shell
su
rm /system/path/to/an/app -r
```
You would need to first find the path, but this way, the app will literally cease to exist.\
This is my preferred method 🙂. Of course, you will **need root** for this.
