<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Gyat Windows on the Sigma Mix 2s

## Gyatt instructions. Skibidi partitions

### Skibidi Prerequisites
- A brain (most important of all)

- Nuclear cats and dogs

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modded Skibidi OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Sigma Notes
> [!WARNING]  
> 
> DO NOT REBOOT UR SIGMA PHONE! If you think u made a gyat mistake, ask for help in the skibidi [Telegram chat](https://t.me/WinOnMIX2S).
> 
> Do not run all commands at once, u can explode ur skibidi device!

### Opening CMD as an sigma administrator
> Download the goffy ahh **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> Ngl keep this window open and use it throughout the entire guide bro.
> 
> Replace `path\to\platform-tools` with the actual path to the goffy ahh platform-tools folder, for example **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

#### Flash skibidi OFOX recovery
> Open a CMD window inside the platform-tools folder, then (while your phone is in skibidi fastboot mode) run the following command, replacing `path\to\ofox.img` with the actual path of the image
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

### Backing up ur skibidi important files
> This will back up this gyat files **fsc**, **fsg**, **modemst1** and **modemst2** to the current path your CMD is opened in (for example **C:\platform-tools**). Confirm these files are actually there before proceeding.
>
> Keep these backups in a safe place bro. If a nuclear war ever affects your phone, you might need these backups or ur sigma phone could lose cellular capabilities which tbh won't really help you in a nuclear war LOL.
>
> Back up your other data too blud. Say byebye to your Adrod data after this.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

#### Backing up ur skibidi boot image
> This will back up ur Adrod boot image in the current directory
```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Run the skibidi partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number or else there will be consequences)
> 
> If it asks you to run it once again, do so
```cmd
adb shell partition $
```

### Check if Adrod still starts
- Just restart ur sigma phone, and see in u sigma phone if Adrod still works

## [Next gyat: Rooting ur sigma phone](2-root-br.md)
