<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Instalacja Windowsa

### Wymagania
- [Windows dla ARM](https://worproject.com/esd)
  
- [Sterowniki](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg (naprawia dotyk)](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

- [Obraz UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

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
> [!WARNING]
> NIE USUWAJ ŻADNYCH PARTYCJI W DISKPART!!!! TO USUNIE CAŁĄ TWOJĄ UFS!!!! OZNACZA TO, ŻE TWOJE URZĄDZENIE ZOSTANIE TRWAŁE USZKODZONE BEZ ROZWIĄZANIA! (z wyjątkiem zabrania urządzenia do Xiaomi lub flashowania go za pomocą EDL)
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

#### Wybieranie Partycji ESP
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **ESPPOLARIS**
```diskpart
select volume $
```

#### Dodaj literę do ESP
```cmd
assign letter y
```

#### Wyjdź z Diskpart
```cmd
exit
```

### Instalowanie Windowsa
> Zamień `path\to\install.esd` na rzeczywistą ścieżkę do pliku install.esd (może on również nosić nazwę install.wim)
```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> Jeśli pojawi się komunikat `Błąd 87`, sprawdź indeks obrazu za pomocą polecenia `dism /get-imageinfo /ImageFile:path\to\install.esd`, a następnie zastąp `index:6` rzeczywistym numerem indeksu systemu **Windows 11 Pro** na Twoim obrazie

### Copying your boot.img into Windows
- Drag and drop the **magisk_patched.img** into the **WINPOLARIS** disk in Windows Explorer, then rename it to **boot.img**.

### Instalowanie Sterowników
- Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd` (if an error shows up, run `OfflineUpdaterFix.cmd` instead)
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINPOLARIS** (która powinna być **X**), a następnie naciśnij enter.

#### Utwórz pliki bootloadera systemu Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Włącz tryb testowy
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Wyłączanie odzyskiwania
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Wyłączanie sprawdzania integralności
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Usuń przypisanie litery dysku
> Żeby nie pozostał tam po odłączeniu urządzenia
```cmd
diskpart
```

#### Wybierz głośność systemu Windows w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **WINPOLARIS**
```część dysku
sel vol $
```

#### Usuń przypisanie litery X
```część dysku
remove letter x
```

#### Wybierz głośność systemu ESP w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień `$` na rzeczywistą liczbę **ESPPOLARIS**
```część dysku
sel vol $
```

#### Usuń przypisanie litery Y
```część dysku
remove letter y
```

#### Wyjdź z dysku
```część dysku
exit
```

### Uruchom ponownie fastboot
> Przytrzymaj **zmniejszanie głośności** + **zasilanie**, aby wymusić ponowne uruchomienie telefonu w trybie fastboot

#### Naprawianie dotyku
> Zastąp `path\to\devcfg-polaris.img` rzeczywistą ścieżką obrazu
```cmd
fastboot flash devcfg_ab path\to\devcfg-polaris.img
```

#### Uruchom do UEFI
> Zastąp `path\to\polaris-uefi.img` rzeczywistą ścieżką obrazu UEFI
```cmd
fastboot boot path\to\polaris-uefi.img
```

### Uruchom ponownie do Androida
Your device should reboot by itself after +- 10 minutes of waiting, after which you will be booted into Android, for the last step.

## [Ostatni Krok: Ustawianie dualboot](dualboot.md)

















