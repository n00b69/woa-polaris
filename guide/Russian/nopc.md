<img align="right" src="https://github.com/n00b69/woa-dipper/blob/main/dipper.png" width="350" alt="Windows 11 running on a Redmi K20 Pro">

# Running Windows on the Xiaomi Mi 8

## Installing Windows without a PC

### Prerequisites
- A rooted Xiaomi Mi 8

- [Modded recovery](https://github.com/n00b69/woa-dipper/releases/tag/Recovery)

- [Dipper WinInstaller](https://github.com/n00b69/woa-dipper/releases/download/Files/DipperWinInstaller.zip)

- [Windows on ARM image](https://arkt-7.github.io/woawin/)

- [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK)

- Optional: a USB stick

### Notes
> [!WARNING]  
> All your data will be erased! Back up now if needed.
> 
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/woadipper).

> [!Important]
> This guide assumes you have already unlocked your bootloader and are already rooted, if this is not the case, you'll still need a PC to do that.

### Flash the modded recovery
> If you have a custom recovery installed, you can install the modified recovery through there instead
- Download the modified recovery image, rename it to **recovery.img**, and leave in the `Download` folder **of your internal storage**.
- Download **Termux**, open it, and grant it root access.
- Run the below command in Termux to flash the modified recovery:
```cmd
su -c dd if=/sdcard/Download/recovery.img of=/dev/block/by-name/recovery
```
- Run the below command in Termux to reboot into the modified recovery:
```cmd
su -c reboot recovery
```

### Checking if decryption works
- Once the recovery boots, enter your password if it asks you to.
- Open the file explorer in the recovery, then navigate to your internal storage.
> If your files are not there and your internal storage is displayed as **(0MB)**, there will be some additional steps which will be explained later in this guide.

#### Opening recovery terminal
- Press the **Advanced** button on the bottom right of the screen, then press **Terminal**.

### Run the partitioning script
> After running the script, enter the size (in GB) that you want Windows to be
>
> Do not write **GB**, just the number (for example **50**)
```cmd
partition
``` 

### Check if Android still starts
- Just restart the phone, and see if Android still works

### Preparing necessary files
- Download the Windows image and make sure it remains in the `Download` folder of your **internal storage**.
> [!Important]
> For performance reasons, it is recommended to use Windows 11 24H2 (builds that start with 261XX, such as 26100.2454)

> If the recovery is not able to read/decrypt your internal storage, create a folder on your **USB stick** named `WOA` and put the **.esd** file in there
>
> Alternatively, find another recovery image online that can actually decrypt and use it instead
- Download **WinInstaller.zip** and keep it in the `Download` folder as well.
- Download and install the [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK), then open it and grant it root access. Do not do anything else inside the app yet.

#### Booting into the modded recovery
- Press the `Reboot to Recovery` button in the top right of Magisk.
- Once booted into the recovery, enter your password if it asks you to.

### Flashing WinInstaller
- In the modified recovery, select **Install** and then locate **WinInstaller.zip** and flash it.
- Once you're given the option to reboot, do so.
> [!Note]
> Wait until all processes complete and your device boots into Windows. This will take around 15-20 minutes.

> [!Tip]
> If you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.

#### Booting to Android
- Run the **Android** shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access).

#### Booting to Windows
> If it says "UEFI NOT FOUND", download the [UEFI image](https://github.com/n00b69/woa-dipper/releases/tag/UEFI) and place it in the `UEFI` folder in your internal storage.
- Press **QUICKBOOT TO WINDOWS** inside the WOA Helper app, or use the newly created toggle in your quick settings panel.

## Finished!

























