<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Aktualizowanie sterowników

### Warunki wstępne
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Sterowniki](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Skrypt Msc](https://github.com/n00b69/woa-polaris/releases/download/Files/msc.sh)
  
- [TWRP](https://github.com/n00b69/woa-polaris/releases/download/Files/twrp.img) (powinno już być zainstalowane)

#### Uruchom do TWRP
> Jeśli Xiaomi zastąpiło Twoje recovery z powrotem do stanu magazynowego, sflashuj je ponownie w trybie fastboot za pomocą:
```cmd
fastboot flash \path\to\twrp.img
```

#### Uruchamianie skryptu msc
> Umieść msc.sh w folderze platform-tools, a następnie uruchom:
```cmd
adb push msc.sh / && adb shell sh msc.sh
```

### Część dysku
```cmd
część dysku
```

#### Lista woluminów urządzeń
> Aby wydrukować listę wszystkich podłączonych woluminów, uruchom
```cmd
objętość listy
```

#### Wybierz wolumin systemu Windows
> Zastąp $ rzeczywistą liczbą **WINPOLARIS**
```cmd
wybierz głośność $
```

#### Przypisz literę do systemu Windows
```cmd
przypisz literę x
```

### Wyjdź z dysku
```cmd
Wyjście
```

### Instalowanie sterowników
> Wyodrębnij folder sterowników z archiwum, a następnie uruchom następujące polecenie, zastępując „<ścieżkę\do\sterowników>” rzeczywistą ścieżką folderu sterowników
```cmd
dism /image:X:\ /add-driver /driver:<ścieżka\do\sterowników> /recurse
```

### Usuń przypisanie litery dysku
> Żeby nie pozostał tam po odłączeniu urządzenia
```cmd
część dysku
```

#### Wybierz głośność systemu Windows w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **WINPOLARIS**
```część dysku
wybierz głośność $
```

#### Usuń przypisanie litery X
```część dysku
usuń literę x
```

#### Wyjdź z dysku
```część dysku
Wyjście
```

#### Uruchom ponownie system Windows
> Uruchom ponownie urządzenie, aby ponownie uruchomić system Windows. Jeśli spowoduje to uruchomienie systemu Android, ponownie wykonaj flashowanie obrazu UEFI poprzez fastboot lub za pomocą aplikacji WOA Helper


## Skończone!















