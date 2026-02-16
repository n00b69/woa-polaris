<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mix 2s

## Installing Windows without a PC

### Prerequisites
- A rooted Xiaomi Mix 2s

- [Modded recovery](https://github.com/n00b69/woa-polaris/releases/tag/Recovery)

- [Polaris WinInstaller](https://github.com/tvorogo/woa-polaris/releases/tag/WinInstaller)

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

### Flash the modified recovery
> If you have a custom recovery installed, you can install the modified OFOX through there instead
- Download the modified recovery, rename it to **recovery.img**, and leave in the `Download` folder **of your internal storage**.
- Download **Termux**, open it, and grant it root access.
- Run the below command in Termux to flash OFOX:
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

### Preparing for partitioning
> [!Note]
> If at any moment in parted you see an error prompting you to type "Yes/No" or "Ignore/Cancel", type `Yes` or `Ignore` depending on the situation to ignore the errors and continue.
>
> If you see any **udevadm** errors, you can ignore these as well.
```cmd
parted /dev/block/sda
```

#### Printing the current partition table
> Parted will print the list of partitions, userdata should be the last partition in the list
```cmd
print
``` 

#### Removing userdata
> Replace **$** with the number of the **userdata** partition, which should be **21**
```cmd
rm $
``` 

#### Recreating userdata
> Replace **1611MB** with the former start value of **userdata** which we just deleted
>
> Replace **32GB** with the end value you want **userdata** to have. In this example your available usable space in Android will be 32GB-1611MB = **30GB**
```cmd
mkpart userdata ext4 1611MB 32GB
``` 

#### Creating ESP partition
> Replace **32GB** with the end value of **userdata**
>
> Replace **32.35GB** with the value you used before, adding **0.35GB** to it
```cmd
mkpart esp fat32 32GB 32.35GB
``` 

#### Creating Windows partition
> Replace **32.35GB** with the end value of **esp**
```cmd
mkpart win ntfs 32.35GB -0MB
``` 

#### Making ESP bootable
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be **22**
```cmd
set $ esp on
```

#### Exit parted
```cmd
quit
```

### Formatting data
- Format all data in recovery, or Android will not boot.
- ( Go to Wipe > Format data > type yes )

### Check if Android still starts
- Just restart the phone, and see if Android still works

### Preparing necessary files
- Download the Windows image and make sure it remains in the `Download` folder of your **internal storage**.
> [!Important]
> If the recovery is not able to read/decrypt your internal storage, create a folder on your **USB stick** named `WOA` and put the **.esd** file in there
>
> Alternatively, find another OFOX or TWRP image online that can actually decrypt and use it instead
- Download **WinInstaller.zip** and keep it in the `Download` folder as well.
- Download and install the [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK), then open it and grant it root access. Do not do anything else inside the app yet.

#### Booting into the modded recovery
- Press the `Reboot to Recovery` button in the top right of Magisk.
- Once booted into the recovery, enter your password if it asks you to.

### Flashing WinInstaller
- In the recovery, select **Install** and then locate **WinInstaller.zip** and flash it.
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

























