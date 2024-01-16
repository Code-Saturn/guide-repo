# What is this?

>Thanks to [UAD](https://github.com/0x192/universal-android-debloater/), [Shizuku](https://github.com/RikkaApps/Shizuku), [aShell](https://gitlab.com/sunilpaulmathew/ashell) and [Package Manager](https://github.com/SmartPack/PackageManager).

This guide shows you how to uninstall system apps and ultimately debloat android on non root devices.

>[!WARNING]
>This is safe, but only in the sense that you can't brick your phone. You shouldn't encounter bootloop but... **it can't be guaranteed 100%**.The UAD dev and contributors tried to list all the packages they came across. Even those you should not delete. Those are classified in the unsafe list. This way, you know the purpose of each package.

>[!NOTE]
>Unfortunately, only android 11+.

>[!IMPORTANT]
>Before starting I would advise you have some basic knowledge of stuff. Something is being written for that too.

## TUI methods:

Methods using the command line, less user friendly.

### Method 1

Using aShell.
#### Steps:
 1. Install [shizuku](https://github.com/RikkaApps/Shizuku/releases) and [aShell](https://f-droid.org/en/packages/in.sunilpaulmathew.ashell/).
 2. [Configure shizuku](https://shizuku.rikka.app/guide/setup/).
 3. Open aShell once Shizuku is configured.
 4. You should get a prompt asking for shizuku access, always allow. **If you missed it** go to the shizuku app and tap on `Authorized X apps` then authorize aShell manually.
 5. Use [this](https://github.com/0x192/universal-android-debloater/wiki/FAQ#what-are-the-adb-commands-used-by-uad) from the [UAD wiki](https://github.com/0x192/universal-android-debloater/wiki) as a guide for the adb commands. **This should educate you on what command to use as per your need**
 6. A guide on how to know what is safe to uninstall is given at the bottom of this page

>[!NOTE]
>Since aShell is adb shell you can just input your commands there on the top bar.
### Method 2.1.1

Using Termux and Shizuku

#### Steps:
1. Follow Steps 1 and 2 from Method 1 above.
2. Install [termux](https://f-droid.org/packages/com.termux/) or [termux monet](https://github.com/HardcodedCat/termux-monet)
3. Open shizuku 
4. Tap on `Use Shizuku in terminal apps` 
5. Now, the next steps should be written there but I'll just write it in a simple way for ya
6. To export the required files tap on the `export files` then choose a preferable empty directory you don't plan on storing anything else and isn't a crucial directory for any other system function or app
7. Now you have 2 files `rish` and `rish_shuzuki.dex` in that selected folder
8. Now, use a text editor to edit `rish` and replace wherever its written `PKG` with `com.termux`
9. Open termux, execute the command `termux-setup-storage` and grant it storage permission 
10. Now navigate to `storage/shared`
11. You are in your internal storage now.
12. From there navigate to where you stored your files on step 6
13. Now execute `./rish` 
14. You should get a prompt asking for shizuku access, always allow. **If you missed it** go to the shizuku app and tap on `Authorized X apps` then authorize termux manually.
15. Welcome to ADB shell
16. Use [this](https://github.com/0x192/universal-android-debloater/wiki/FAQ#what-are-the-adb-commands-used-by-uad) from the [UAD wiki](https://github.com/0x192/universal-android-debloater/wiki) as a guide for the adb commands. **This should educate you on what command to use as per your need.**
17. A guide on how to know what is safe to uninstall is given at the bottom of this page


### Method 2.1.2

Using termux and the `android tools` package

#### Steps:
1. Install [termux](https://f-droid.org/packages/com.termux/) or [termux monet](https://github.com/HardcodedCat/termux-monet)
2. Open termux and execute `pkg install android-tools -y`
3. Go to your developer settings
4. Scroll down to wireless debugging, enable it
5. Tap on wireless debugging
6. Tap on `pair device with pairing code`   
7. You would see `Wi-Fi Pairing code` and `IP Address and port`
8. Now go back to termux and execute `adb pair <ip address from the above step>:<port from the above step> <wifi pairing code>`
9. Go back the wireless debugging settings you will see `device settings` and `ip address and port` as one of the first things being written on the page
10. Now execute `adb connect <the ip address>:<the port>` and you will connect to your device
11. Execute `adb shell`
12. Welcome to ADB shell
13. Use [this](https://github.com/0x192/universal-android-debloater/wiki/FAQ#what-are-the-adb-commands-used-by-uad) from the [UAD wiki](https://github.com/0x192/universal-android-debloater/wiki) as a guide for the adb commands. **This should educate you on what command to use as per your need.**
14. A guide on how to know what is safe to uninstall is given at the bottom of this page

## GUI Methods:

Methods using graphical interface, more user friendly.

### Method 1

By using an app called "Package Manager".

#### Steps:
 1. Install [shizuku](https://github.com/RikkaApps/Shizuku/releases) and [Package Manager](https://f-droid.org/packages/com.smartpack.packagemanager/).
 2. [Configure shizuku](https://shizuku.rikka.app/guide/setup/).
 3. Open package manager, it should request shizuku permission so grant that, if you missed dialog, authorize from Shizuku app.
 4. Go to system tab, now uninstall the bloatware but only if your sure of what you are doing.

### Method 2

By using [App Manager](https://github.com/MuntashirAkon/AppManager)

>[!NOTE]
>Shizuku, nor the UAD wiki is needed for this method.

#### Steps:
1. Install [App Manager](https://github.com/MuntashirAkon/AppManager/releases)
2. Click 3 dots on top, then go to settings, you will see `mode of operation`, tap that and change it to `wireless debugging`
3. Then go back to home page, tap 3 dots again, go to debloater
4. Stuff that are safe to remove are going to be marked `safe to remove`
5. Always read the info that's written here before uninstalling to know if you are OK with uninstalling it:![1000103587](https://github.com/rickdtc/debloat-android-without-pc/assets/74096544/9a140bbc-7370-40cf-ad8d-fd7bb64c5c6e)



## How to be sure what to uninstall?
Search for your packages by package id which you want to uninstall [here](https://github.com/0x192/universal-android-debloater/blob/main/resources/assets/uad_lists.json).
You would see the app entries formatted like
```JSON
{
    "id": "...",
    "list": "...",
    "description": "...",
    "dependencies": [],
    "neededBy": [],
    "labels": [],
    "removal": "Unsafe/Expert/Advanced/Reccomended"
 },
 ```

Check for `"removal":"<entry>"`.

If `<entry>` is - 

1. **Recommended** -- Pointless or outright negative packages, and/or apps available through Google Play.
2. **Advanced** -- Breaks obscure or minor parts of functionality, or apps that aren't easily enabled/installed through Settings/Google Play. This category is also used for apps that are useful (default keyboard/gallery/launcher/music app.) but that can easily be replaced by a better alternative.
3. **Expert** -- Breaks widespread and/or important functionality, but nothing important to the basic operation of the operating system. Removing an Expert package should not bootloop the device (unless mentioned in the description) but we can't guarantee it 100%.
4. **Unsafe** -- Can break vital parts of the operating system. Removing an Unsafe package have an extremely high risk of bootlooping your device.
