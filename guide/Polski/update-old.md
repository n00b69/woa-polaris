<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Aktualizowanie sterowników

### Wymagania
- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Sterowniki](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Obraz UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

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

#### Dodaj literę do systemu Windows
```cmd
assign letter x
```

#### Wyjdź z Diskpart
```cmd
exit
```

### Instalowanie sterowników
> Wypakuj archiwum ze sterownikami, potem otwórz plik `OfflineUpdater.cmd`
 
> Jeśli poprosi Cię o podanie litery, wpisz literę dysku **WINPOLARIS** (która powinna być X), a następnie naciśnij enter.

### Uruchom ponownie system Windows
> Uruchom ponownie urządzenie, aby ponownie uruchomić system Windows. Jeśli spowoduje to uruchomienie systemu Android, ponownie wykonaj flashowanie obrazu UEFI poprzez fastboot lub za pomocą aplikacji WOA Helper


## Skończone!















