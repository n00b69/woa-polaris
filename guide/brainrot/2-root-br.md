<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Gyat Windows on the Sigma Mix 2s

## Gyatt instructions. Rooting ur sigma phone

### Skibidi Prerequisites
- [Goffy ahh Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Copying ur skibidi boot image to Adrod
- Connect your sigma phone to your rizz computer (with USB debugging enabled).
- Click the prompt on ur sigma phone to allow your rizz computer to access your phone's data. If no prompt appears, go to your notification panel and click the USB notification, then change the connection type to **transferring files**.
- Copy the **boot.img** file from the **platform-tools** folder into your internal storage.

#### Patching the rizz boot image
- Download and install goffy ahh **Magisk**, then open it.
- Press **Install** > **Patch a file** and select the **boot.img** you just copied.
- Once the patching has gyat finished, locate  **magisk_patched-27000_XXXX.img** in your **Downloads** folder and copy it into the **platform-tools** folder on your rizz computer.

### Reboot to gyat fastboot mode
```cmd
adb reboot bootloader
```

#### Flashing ur skibidi rooted boot image
> Replace `path\to\magisk_patched.img` with the actual path of the image
```cmd
fastboot flash boot path\to\magisk_patched.img
```

### Reboot to Adrod
```cmd
fastboot reboot
```

#### Finishing gyat
- Open the goffy ahh **Magisk** app again.
- Follow the instructions on the screen, and your device should reboot after a few seconds.

### Copying the rooted skibidi boot image
> After ur sigma device has booted

- A superuser request for Shell might appear on your phone's screen. If it does, grant it access.
```cmd
adb shell "su -c cp /dev/block/by-name/boot /sdcard/root.img" & adb pull /sdcard/root.img
```

## [Next gyat: Installing Wiwdaws](3-install-br.md)








