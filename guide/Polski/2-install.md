<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Instalacja Windowsa

### Wymagania
- [Windows dla ARM](https://worproject.com/esd)
  
- [Sterowniki](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg (naprawia dotyk)](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [obraz UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Uruchom do UEFI
> Zastąp **<path\to\polaris-uefi.img>** rzeczywistą ścieżką obrazu UEFI
```cmd
fastboot boot <path\to\polaris-uefi.img>
```

#### Włączanie trybu pamięci masowej
> Po uruchomieniu systemu UEFI użyj przycisków głośności do poruszania się po menu i przycisku zasilania, aby potwierdzić
- Wybierz **UEFI Boot Menu**.
- Wybierz **USB Attached SCSI (UAS) Storage**.
- Naciśnij przycisk dwa razy aby potwierdzić.

### Diskpart
> [!WARNING]
> NIE USUWAJ ŻADNYCH PARTYCJI W DISKPART!!!! TO USUNIE CAŁĄ TWOJĄ UFS!!!! OZNACZA TO, ŻE TWOJE URZĄDZENIE ZOSTANIE TRWAŁE USZKODZONE BEZ ROZWIĄZANIA! (z wyjątkiem zabrania urządzenia do Xiaomi lub flashowania go za pomocą EDL, co prawdopodobnie będzie kosztować)
```cmd
diskpart
```

#### Znajdowanie telefonu
> Spowoduje to wyświetlenie listy wszystkich podłączonych dysków
```cmd
lis dis
```

#### Wybieranie telefonu
> Zastąp $ rzeczywistym numerem partycji telefonu (powinien być ostatnim)
```cmd
sel dis $
```

#### Lista partycji Twojego telefonu
> Spowoduje to wyświetlenie listy partycji urządzenia
```cmd
lis par
```

#### Wybór partycji Windows
> Zastąp $ numerem partycji systemu Windows (powinno być 23)
```cmd
sel par $
```

#### Formatowanie dysku z systemem Windows
```cmd
format quick fs=ntfs label="WINPOLARIS"
```

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Wybieranie Partycji ESP
> Zamień $ na numer partycji ESP (powinno być 22)
```cmd
sel par $
```

#### Formatowanie ESP
```cmd
format quick fs=fat32 label="ESPPOLARIS"
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
> Zamień `<path\to\install.esd>` na rzeczywistą ścieżkę do pliku install.esd (może on również nosić nazwę install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> Jeśli pojawi się komunikat `Błąd 87`, sprawdź indeks obrazu za pomocą polecenia `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, a następnie zastąp `index:6` rzeczywistym numerem indeksu systemu Windows 11 Pro na Twoim obrazie

### Instalowanie Sterowników
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> If it asks you to enter a letter, enter the drive letter of **WINPOLARIS** (which should be X), then press enter

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

### Usuń przypisanie liter dysku
> So that they don't stay there after disconnecting the device
```cmd
diskpart
```

#### Wybierz partycję Windows
> Użyj `list Volume`, aby go znaleźć, zamień „$” na rzeczywistą liczbę **WINPOLARIS**
```diskpart
select volume $
```

#### Usuń przypisanie litery X
```diskpart
remove letter x
```

#### Wybierz partycję ESP
> Use `list volume` to find it, replace "$" with the actual number of **ESPPOLARIS**
```diskpart
select volume $
```

#### Usuń przypisanie litery Y
```diskpart
remove letter y
```

#### Wyjdź z diskpart
```diskpart
exit
```

### Naprawianie dotyku
> Uruchom ponownie telefon w trybie fastboot, a następnie zamień **path\to** rzeczywistą ścieżką do obrazu devcfg (który pobrałeś wczesniej)
```cmd
fastboot flash devcfg_ab path\to\devcgf-polaris.img
```

### Uruchom ponownie system Windows
> Zastąp **<path\to\firstboot.img>** rzeczywistą ścieżką obrazu UEFI
```cmd
fastboot boot <path\to\firstboot.img>
```
> [!Important]
> Po uruchomieniu systemu Windows i zakończeniu konfiguracji systemu Windows naciśnij **Uruchom ponownie** w menu Start, aby w ostatnim kroku ponownie uruchomić system Android

## [Ostatni Krok: Ustawianie dualboot](dualboot.md)

















