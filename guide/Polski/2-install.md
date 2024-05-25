<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Instalacja Windowsa

### Wymagania
- [Windows dla ARM](https://worproject.com/esd)
  
- [Sterowniki](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg (naprawia dotyk)](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

- [Obraz UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Boot to OFOX recovery
> If your recovery has been replaced by the stock recovery, flash it again using
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
> NIE USUWAJ ŻADNYCH PARTYCJI W DISKPART!!!! TO USUNIE CAŁĄ TWOJĄ UFS!!!! OZNACZA TO, ŻE TWOJE URZĄDZENIE ZOSTANIE TRWAŁE USZKODZONE BEZ ROZWIĄZANIA! (z wyjątkiem zabrania urządzenia do Xiaomi lub flashowania go za pomocą EDL, co prawdopodobnie będzie kosztować)
```cmd
diskpart
```

#### Wybór partycji Windows
> Use `list volume` to find it, replace `$` with the actual number of the Windows volume (it should be around the same size you picked on the last page)
```diskpart
select volume $
```

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Formatowanie dysku z systemem Windows
```cmd
format quick fs=ntfs label="WINPOLARIS"
```

#### Wybieranie Partycji ESP
> Use `list volume` to find it, replace `$` with the actual number of the ESP volume (it should be around 286MB)
```diskpart
select volume $
```

#### Dodaj literę do ESP
```cmd
assign letter y
```

#### Formatowanie ESP
```cmd
format quick fs=fat32 label="ESPPOLARIS"
```

#### Wyjdź z Diskpart
```cmd
exit
```

### Instalowanie Windowsa
> Zamień `<path\to\install.esd>` na rzeczywistą ścieżkę do pliku install.esd (może on również nosić nazwę install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> Jeśli pojawi się komunikat `Błąd 87`, sprawdź indeks obrazu za pomocą polecenia `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, a następnie zastąp `index:6` rzeczywistym numerem indeksu systemu Windows 11 Pro na Twoim obrazie

### Instalowanie Sterowników
> Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd`
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINPOLARIS** (która powinna być X), a następnie naciśnij enter.

> [!WARNING]
> NIE UŻYWAJ DISM++

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
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **WINPOLARIS**
```część dysku
sel vol $
```

#### Usuń przypisanie litery X
```część dysku
remove letter x
```

#### Wybierz głośność systemu ESP w telefonie
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **ESPPOLARIS**
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

### Naprawianie dotyku
> Uruchom ponownie telefon w trybie fastboot, a następnie zamień **path\to** rzeczywistą ścieżką do obrazu devcfg (który pobrałeś wczesniej)
```cmd
fastboot flash devcfg_ab path\to\devcfg-polaris.img
```

### Uruchom ponownie system Windows
> Zastąp **<path\to\firstboot.img>** rzeczywistą ścieżką obrazu UEFI
```cmd
fastboot boot <path\to\firstboot.img>
```
> [!Important]
> Po uruchomieniu systemu Windows i zakończeniu konfiguracji systemu Windows naciśnij **Uruchom ponownie** w menu Start, aby w ostatnim kroku ponownie uruchomić system Android

## [Ostatni Krok: Ustawianie dualboot](dualboot.md)

















