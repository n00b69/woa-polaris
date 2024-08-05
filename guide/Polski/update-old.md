<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Aktualizowanie sterowników

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Sterowniki](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Uruchom recovery OFOX
> Jeśli Twój recovery został zastąpiony recovery domyślnym, sflashuj go ponownie za pomocą
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Włączanie trybu pamięci masowej
> Jeżeli ci mówi aby wykonać polecenie jescze raz to zrób to
```cmd
adb shell msc
```

### Diskpart
```cmd
diskpart
```

#### Wybór partycji Windows
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **WINPOLARIS**
```diskpart
select volume $
```

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Wyjdź z Diskpart
```cmd
exit
```

### Instalowanie sterowników
- Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd` (if an error shows up, run `OfflineUpdaterFix.cmd` instead)
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINPOLARIS** (która powinna być X), a następnie naciśnij enter.

### Uruchom ponownie system Windows
> Uruchom ponownie urządzenie, aby ponownie uruchomić system Windows. Jeśli spowoduje to uruchomienie systemu Android, ponownie wykonaj flashowanie obrazu UEFI poprzez fastboot lub za pomocą aplikacji WOA Helper

## Skończone!















