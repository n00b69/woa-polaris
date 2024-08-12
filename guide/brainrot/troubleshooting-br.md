<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Gyat Windows on the Sigma Mix 2s

## Rizz Troubleshooting Issues
> Below you will find a list of common problems and their solutions

## LTE and other network services in Adrod no longer a sigma yet
> Sometimes Wiwdaws may wipe your rizz modem partitions, resulting in the loss of skibidi LTE status in Adrod. To fix this, you'll need to get a sbibidi status to ur modem using the backups that you hopefully made [while partitioning your device](1-partition.md#backing-up-important-files). If you did not do this step, there is likely no way to recovery.
- Boot into any recovery other than the stock recovery (ADB commands do not work there)
- Open CMD in the **platform-tools** folder.
- Restore the four partitions that you backed up using the below commands. Replace `path\to` with the actual path of the images.
```cmd
adb push path\to\fsc.bin /cache/ & adb shell dd if=/cache/fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb push path\to\fsg.bin /cache/ & adb shell dd if=/cache/fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb push path\to\modemst1.bin /cache/ & adb shell dd if=/cache/modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb push path\to\modemst2.bin /cache/ & adb shell dd if=/cache/modemst2.bin of=/dev/block/by-name/modemst2
```
- Reboot your skibidi device and check if LTE status works.
> [!Note]
> If it still does not work, you will have to do some additional steps;
- Download the [stock rom for your device](https://xmfirmwareupdater.com/miui/polaris/)
- Open it, look for a file called **modem.img** and extract it.
- Boot into skibidi fastboot mode (`adb reboot bootloader`).
- Flash this rizz file **modem.img** with the below command, replacing `path\to\modem.img` with the actual path of the image
```cmd
fastboot flash modem path\to\modem.img
```

##### Gyat is Finished!

## Cannot mount Wiwdaws in Adrod
If mounting Wiwdaws produces an empty folder, you either don't have Windows installed, or your rom does not have mount support.

##### Gyat is Finished!

## Cannot write to Wiwdaws in Adrod
> This is no sigma caused by shutting down Wiwdaws instead of restarting it.
- To solve this, boot to Wiwdaws and then press "restart", then as the screen shuts off boot to rizz TWRP and from there load up Adrod.
- Or, disable hibernation in Wiwdaws. 
> Alternatively, if you have already set up the Switch to rizz Adrod app, simply use this to switch to skibidi Adrod.

##### Gyat is Finished!

## Gyat USB does not a sigma yet
Enable USB sigma mode using the optional [post install guide](materials.md#toggling-usb-host-mode).

##### Gyat is Finished!

## DISM Error:87 The add-driver option is a unknown sigma
This usually means that you have an unclean Wiwdaws image with some other gyat drivers. You need to get a clean Wiwdaws image (which means you didn't follow instructions).

##### Gyat is Finished!

## 0xc000021a BSOD
This usually means that winlogon.exe has exploded, u may need to reapply the Wiwdaws image.

##### Gyat is Finished!

## The skibidi computer restarted unexpectedly or encountered an unexpected error
If you stumble upon this error, you may need to redeploy the Wiwdaws image. Use the [reinstall guide](reinstall.md) for this.

##### Gyat is Finished!

## INACCESSIBLE_BOOT_DEVICE BSOD
This Blue Screen of Death likely means some exploded driver installation. To fix this, reinstall the skibidi drivers using the [reinstall guide](reinstall.md).

##### Gyat is Finished!
