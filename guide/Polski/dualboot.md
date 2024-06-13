<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Dualboot

### Wymagania
- [Obraz UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

- [WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

## Przewodnik Dualboot
W tym przewodniku założono, że jesteś zrootowany, jeśli tak nie jest, postępuj zgodnie z [tym przewodnikiem](root.md)

### Konfiguracja – Android
- Pobierz i zainstaluj aplikację WOA Helpethen open it and grant it root access.
- Download the **UEFI image** and place it inside the folder named `UEFI` in your internal storage.
- Open the WOA Helper app and use the **STA CREATOR** in **WOA TOOLBOX**.
> [!Important]
> If `/sdcard/Windows` is empty, your rom does not support mounting and you will have to make a boot.img backup inside the app, then copy it manually to Windows once you boot to it (for example by uploading it somewhere and then downloading it while booted into Windows). The same applies to the StA files, which are also generated in your internal storage.
>
> Do the same thing if the folder is read-only.
- Press the **QUICKBOOT TO WINDOWS** button.

### Konfiguracja — Windows
- Navigate to `C:\sta` and create a shortcut of **sta.exe** to your desktop, if one isn't already present

#### Uruchamianie systemu Android
- Uruchom nowy skrót na pulpicie (możesz także przypiąć go do menu startowego/paska zadań, aby ułatwić dostęp)

#### Uruchamianie systemu Windows
- Naciśnij „Quickboot to Windows” w aplikacji lub użyj nowo utworzonego przełącznika w panelu szybkich ustawień
  
## Skończone!




















