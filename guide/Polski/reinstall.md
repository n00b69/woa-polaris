<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Ponowna instalacja Windows

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/modded-ofox-polaris.img)

### Uruchomienie recovery OFOX
> Jeśli recovery zostało zastąpione recovery domyślnym, sflashuj go ponownie za pomocą
```cmd
fastboot flash recovery ścieżka\do\modded-ofox-polaris.img reboot recovery
```

#### Formatowanie Windows
```cmd
adb shell format
```

## [Następny krok: Ponowna instalacja Windows](3-install.md)















