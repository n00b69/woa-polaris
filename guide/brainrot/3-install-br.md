<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Gyat Windows on the Sigma Mix 2s

## Gyatt instructions. Installing Wiwdaws

### Skibidi Prerequisites
- [Wiwdaws on ARM image](https://worproject.com/esd)
  
- [Goffy ahh Drivers](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg (touch fix)](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [Skibidi Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)
  
- [Rizz UEFI image](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Boot to Skibidi OFOX recovery
> If your recovery has been bombed by stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Enabling skibidi sigma storage mode
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> DO NOT ERASE, CREATE OR OTHERWISE MODIFY ANY PARTITION WHILE IN DISKPART!!!! U CAN MADE NUCLEAR WAR IN UR UFS OR PREVENT YOU FROM BOOTING TO FASTBOOT!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY FUCKED UP WITH NO SOLUTION! (except for flashing it with EDL)
```cmd
diskpart
```

#### Selecting the Wiwdaws partition
> Use `list volume` to find it, replace `$` with the actual number of **WINPOLARIS**
```diskpart
select volume $
```

#### Add letter to Wiwdaws
```cmd
assign letter x
```

#### Selecting the ESP partition
> Use `list volume` to find it, replace `$` with the actual number of **ESPPOLARIS**
```diskpart
select volume $
```

#### Add letter to ESP
```cmd
assign letter y
```

#### Exit diskpart
```cmd
exit
```

### Installing Wiwdaws
> Replace `path\to\install.esd` with the actual path of install.esd (it may also be named install.wim or 22631.2861.XXXXXXX.esd)

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:path\to\install.esd`, then replace `index:6` with the actual index number of **Windows 11 Pro** in your image

### Copying ur skibidi boot.img into Wiwdaws
- Drag and drop the **root.img** from the **platform-tools** folder into the **WINPOLARIS** disk in Windows Explorer, then rename it to **boot.img**.

### Installing skibidi Drivers
- Unpack the driver archive, then open the `OfflineUpdater.cmd` file (if an error shows up, run `OfflineUpdaterFix.cmd` instead)

> If it asks you to enter a letter, enter the drive letter of **WINPOLARIS** (which should be **X**), then press enter

#### Create Wiwdaws bootloader files
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Enabling test signing
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Disabling gyat recovery
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Disabling rizz integrity checks
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

#### Remove no sigma drive letter for ESP
> If this does not work, ignore it and skip to the next command. This phantom drive will disappear the next time you reboot your PC.
```cmd
mountvol y: /d
```

### Reboot to skibidi fastboot
> Hold **volume down** + **power** to force reboot ur sigma phone into goffy fastboot mode

#### Fixing goffy ahh touch
> Replace `path\to\devcfg-polaris.img` with the actual path to the skibidi image
```cmd
fastboot flash devcfg_ab path\to\devcfg-polaris.img
```

#### Boot into the rizz UEFI
> Replace `path\to\polaris-uefi.img` with the actual path of the rizz UEFI image
```cmd
fastboot boot path\to\polaris-uefi.img
```

### Reboot to Adrod
Ur skibidi device should reboot by itself after +- 10 minutes of waiting, after which you will be booted into Adrod, for the last step.

## [Last gyat: Skibidi dualboot setup](4-dualboot-br.md)
