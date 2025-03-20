<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mix 2s

## Installing Windows without a PC

### Prerequisites
- A rooted Xiaomi Mix 2s

- [Modified OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/modded-ofox-polaris.img)

- [Polaris WinInstaller](https://github.com/n00b69/woa-polaris/releases/download/Files/PolarisWinInstaller.zip)

- [Windows on ARM image](https://arkt-7.github.io/woawin/)

- [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK)

- Optional: a USB stick

### Notes
> [!WARNING]  
> All your data will be erased! Back up now if needed.
> 
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/WinOnMix2s).

> [!Important]
> This guide assumes you have already unlocked your bootloader and are already rooted, if this is not the case, you'll still need a PC to do that.

### Flash the modified OFOX
> If you have a custom recovery installed, you can install the modified OFOX through there instead
- Download the modified OFOX, rename it to **OFOX.img**, and leave in the `Download` folder **of your internal storage**.
- Download **Termux**, open it, and grant it root access.
- Run the below command in Termux to flash OFOX:
```cmd
su -c dd if=/sdcard/Download/OFOX.img of=/dev/block/by-name/recovery
```
- Run the below command in Termux to reboot into OFOX:
```cmd
su -c reboot recovery
```

### Checking if decryption works
- Once OFOX boots, enter your password if it asks you to.
- Open the file explorer in OFOX, then navigate to your internal storage.
> If your files are not there and your internal storage is displayed as **(0MB)**, there will be some additional steps which will be explained later in this guide.

#### Opening OFOX terminal
- Press the **Advanced** button on the bottom right of the screen, then press **Terminal**.

### Run the partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
partition $
``` 

### Check if Android still starts
- Just restart the phone, and see if Android still works

### Preparing necessary files
- Download the Windows image and make sure it remains in the `Download` folder of your **internal storage**.
> [!Important]
> If OFOX is not able to read/decrypt your internal storage, create a folder on your **USB stick** named `WOA` and put the **.esd** file in there
>
> Alternatively, find another OFOX image online that can actually decrypt and use it instead
- Download **WinInstaller.zip** and keep it in the `Download` folder as well.
- Download and install the [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK), then open it and grant it root access. Do not do anything else inside the app yet.

#### Booting into OFOX
- Press the `Reboot to Recovery` button in the top right of Magisk.
- Once booted into OFOX, enter your password if it asks you to.

### Flashing WinInstaller
- In OFOX, select **Install** and then locate **WinInstaller.zip** and flash it.
- Once you're given the option to reboot, do so.
> [!Note]
> Wait until all processes complete and your device boots into Windows. This will take around 15-20 minutes.

> [!Tip]
> It is recommended to skip the Microsoft Account login. To do this,  press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.

#### Booting to Android
- Run the **Android** shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access).

#### Booting to Windows
> If it says "UEFI NOT FOUND", download the [UEFI image](https://github.com/n00b69/woa-polaris/releases/tag/UEFI) and place it in the `UEFI` folder in your internal storage.
- Press **QUICKBOOT TO WINDOWS** inside the WOA Helper app, or use the newly created toggle in your quick settings panel.

## Finished!

























