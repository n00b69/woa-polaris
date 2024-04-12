<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Dualboot

### Wymagania
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [Obraz UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

- [WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

- [StA](https://github.com/n00b69/woa-polaris/releases/download/Files/polaris-sta.zip)

## Przewodnik Dualboot
W tym przewodniku założono, że jesteś zrootowany, jeśli tak nie jest, postępuj zgodnie z [tym przewodnikiem](root.md)

### Konfiguracja – Android
- Pobierz i zainstaluj aplikację WOA Helper, a następnie otwórz ją i przyznaj uprawnienia roota.
- Pobierz obraz UEFI i umieść go w folderze o nazwie `UEFI` w pamięci wewnętrznej.
- Naciśnij przycisk `Zamontuj system Windows`, aby zamontować system Windows w pamięci wewnętrznej w `/sdcard/Windows`
> [!Important]
> If `/sdcard/Windows` is empty, your rom does not support mounting and you will have to make a boot.img backup inside the app, then copy it manually to Windows once you boot to it (for example by uploading it somewhere and then downloading it while booted into Windows). The same applies to the STA files.
>
> Do the same thing if the folder is read-only.
- Utwórz folder o nazwie `sta` w systemie Windows i rozpakuj dwa pliki w pliku `Przełącz na pakiet Android` tutaj (pliki powinny trafić do `/sdcard/Windows/sta`
- Wróć do aplikacji WOA Helper i naciśnij przycisk `Quickboot`.

### Konfiguracja — Windows
- Przejdź do C:\sta i utwórz skrót `sta.exe` na pulpicie.

#### Uruchamianie systemu Android
- Uruchom nowy skrót na pulpicie (możesz także przypiąć go do menu startowego/paska zadań, aby ułatwić dostęp)

#### Uruchamianie systemu Windows
- Naciśnij „Quickboot to Windows” w aplikacji lub użyj nowo utworzonego przełącznika w panelu szybkich ustawień
  
## Skończone!




















