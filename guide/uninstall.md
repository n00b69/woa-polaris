<img align="right" src="https://github.com/n00b69/woapolaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mi Mix 2s

## Uninstallation

### Why is this needed?
If you want to uninstall windows this is used instead of deleting partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock your bootloader you'll need your partition table to be stock.

### Prerequisites

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [gpt_both0.bin]() FILE NEEDED

### Uninstall instructions
> [!Important]
> This guide will likely not work, it needs to be updated

#### Boot into fastboot mode
> Hold the volume down + power button while the phone is turned off, or run the following command while it is booted
```cmd
adb reboot bootloader
```

#### Restore GPT
> Replace ```path\to\gpt_both0.bin``` with the path to the gpt_both0.bin file.

```cmd
fastboot flash partition:0 path\to\gpt_both0.bin
```

#### Erase userdata to avoid a bootloop and restore FS size
```cmd
fastboot -w
```
> [!Note]
> If erasing userdata fails, reboot to recovery and wipe all data there instead

## Finished!













