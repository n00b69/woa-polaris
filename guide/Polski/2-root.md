<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Przewodnik po rootowaniu

### Wymagania
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Copying your boot image to Android
- Connect your phone to your computer (with USB debugging enabled).
- Click the prompt on your phone to allow your computer to access your phone's data. If no prompt appears, go to your notification panel and click the USB notification, then change the connection type to **transferring files**.
- Copy the **boot.img** file from the **platform-tools** folder into your internal storage.

#### Patching the boot image
- Download and install **Magisk**, then open it.
- Press **Install** > **Patch a file** and select the **boot.img** you just copied.
- Once the patching has finished, locate  **magisk_patched-27000_XXXX.img** in your **Downloads** folder and copy it into the **platform-tools** folder on your computer.
- Rename

### Reboot to fastboot mode
```cmd
adb reboot bootloader
```

#### Flashing your rooted boot image
> Replace `path\to\magisk_patched.img` with the actual path of the image
```cmd
fastboot flash boot path\to\magisk_patched.img
```

### Reboot to Android
```cmd
fastboot reboot
```

#### Finishing setup
- Open the **Magisk** app again.
- Follow the instructions on the screen, and your device should reboot after a few seconds.
- Now boot back into fastboot mode for the last section of the guide.

## [Next step: Installing Windows](3-install.md)












































