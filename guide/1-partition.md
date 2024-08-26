<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mix 2s

## Partitioning your device

### Prerequisites
- A brain (most important of all)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Notes
> [!WARNING]  
> 
> DO NOT REBOOT YOUR PHONE! If you think you made a mistake, ask for help in the [Telegram chat](https://t.me/WinOnMIX2S).
> 
> Do not run all commands at once, execute them in order!

### Opening CMD as an admin
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
> 
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

#### Flash the modded OFOX recovery
> Open a CMD window inside the platform-tools folder, then (while your phone is in fastboot mode) run the following command, replacing `path\to\ofox.img` with the actual path of the image
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

### Backing up important files
> This will back up **fsc**, **fsg**, **modemst1** and **modemst2** to the current path your CMD is opened in (for example **C:\platform-tools**). Confirm these files are actually there before proceeding.
>
> Keep these backups in a safe place. If your device's software ever gets destroyed, you might need these backups or your phone could lose cellular capabilities.
>
> If you've got anything else you want to back up, do this now. Your Android data will be erased in the next steps.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

#### Backing up your boot image
> This will back up your boot image in the current directory
```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Run the partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
adb shell partition $
```

### Check if Android still starts
- Just restart the phone, and see if Android still works

## [Next step: Rooting your phone](/guide/2-root.md)





















