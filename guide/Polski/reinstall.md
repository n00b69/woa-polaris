<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Ponowna instalacja Windows

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/modded-ofox-polaris.img)

### Uruchom recovery OFOX
> Jeśli Twoje recovery zostało zastąpione recovery domyślnym, zainstaluj go ponownie za pomocą
```cmd
fastboot flash recovery path\to\modded-ofox-polaris.img reboot recovery
```

#### Formatowanie Windows
```cmd
adb shell format
```

## [Następny krok: Ponowna instalacja Windows](3-install.md)















