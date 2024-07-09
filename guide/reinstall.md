<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Running Windows on the Xiaomi Mix 2s

## Reinstalling Windows

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Boot into OFOX
> If MIUI has replaced your recovery, boot to fastboot and run
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Formatting the Windows partition
```cmd
adb shell format
```

## [Next step: Reinstalling Windows](2-install.md)












