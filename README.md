# What is this?

>Thanks to [UAD](https://github.com/0x192/universal-android-debloater/), [Shizuku](https://github.com/RikkaApps/Shizuku), [aShell](https://gitlab.com/sunilpaulmathew/ashell) and [Package Manager](https://github.com/SmartPack/PackageManager).

This guide shows you how to uninstall system apps and ultimately debloat android on non root devices.

>[!WARNING]
>This is safe, but only in the sense that you can't brick your phone. You shouldn't encounter bootloop but... **it can't be guaranteed 100%**.The UAD dev and contributors tried to list all the packages they came across. Even those you should not delete. Those are classified in the unsafe list. This way, you know the purpose of each package.


## Primary method.

Using aShell.

### Steps -
 1. Install [shizuku](https://github.com/RikkaApps/Shizuku/releases) and [aShell](https://f-droid.org/en/packages/in.sunilpaulmathew.ashell/).
 2. [Configure shizuku](https://shizuku.rikka.app/guide/setup/).
 3. Open aShell once Shizuku is configured.
 4. Use [this](https://github.com/0x192/universal-android-debloater/wiki/FAQ#what-are-the-adb-commands-used-by-uad) from the [UAD wiki](https://github.com/0x192/universal-android-debloater/wiki) as a guide for the adb commands.

### Note.

 Since aShell is adb you can just input your commands there on the top bar

## Alternate method.

By using an app called "Package Manager"

### Steps -
 1. Install [shizuku](https://github.com/RikkaApps/Shizuku/releases) and [Package Manager](https://f-droid.org/packages/com.smartpack.packagemanager/).
 2. [Configure shizuku](https://shizuku.rikka.app/guide/setup/).
 3. Open package manager, it should request shizuku permission so grant that, if you missed dialog, authorize from Shizuku app.
 4. Go to system tab, now uninstall the bloatware but only if your sure of what you are doing.

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

