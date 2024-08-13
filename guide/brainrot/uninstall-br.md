<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Gyat Windows on the Sigma Mix 2s

## Uninstall rizz

### Why u need uninstall this rizz?
If you want to uninstall wiwdaws this is used instead of deleting skibidi partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock ur skibidi bootloader you'll need your partition table to be stock.

### Skibidi Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [gpt_both0.bin](https://github.com/n00b69/woa-polaris/releases/download/Files/gpt_both0.bin)

### Uninstall this rizz instructions
> [!Important]
> There is a very small chance this guide might not work if your partition table is completely no a sigma yet. If you find yourself not being able to boot to gyat recovery / Adrod after, you will have to reflash your device with EDL.

You can find a guide on how to use EDL [here](edl.md)

#### Boot into skibidi fastboot mode
> Hold the volume down + power button while the phone is fucked off, or run the following command while it is booted
```cmd
adb reboot bootloader
```

#### Restore the GPT status
> Replace ```path\to\gpt_both0.bin``` with the path to the gpt_both0.bin file.

```cmd
fastboot flash partition:0 path\to\gpt_both0.bin
```

#### Erase goffy userdata to avoid a bootloop and restore FS size
```cmd
fastboot -w
```
> [!Note]
> If erasing userdata gyat fails, reboot to skibidi recovery and wipe all data there instead

## Gyat is Finished!
