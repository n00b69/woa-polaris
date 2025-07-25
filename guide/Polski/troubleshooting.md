<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Rozwiązywanie problemów
> Poniżej znajdziesz listę typowych problemów i ich rozwiązań

## Touch sometimes stops working
> This may be caused by the device's power saving settings, to (hopefully) fix this, do the following:

- Open **Device Manager** on the device while in Windows.
- Navigate to **Human Interface Devices** > **Synaptics RMI4 over Function 12 (2D Multifinger Pointing/Pen) Digitizer (S3708)**.
- Click on **Power Mangament** and uncheck **"Allow the computer to turn off this device to save power"**.

##### Finished!

## LTE i inne usługi sieciowe w Androidzie już nie działają
> Czasami system Windows może wyczyścić partycje modemu, powodując utratę LTE w systemie Android. Aby to naprawić, musisz przywrócić modem, korzystając z kopii zapasowych, które, miejmy nadzieję, wykonałeś [podczas partycjonowania urządzenia](1-partition.md#backing-up-important-files). Jeśli nie wykonałeś tego kroku, prawdopodobnie nie będzie możliwości odzyskania funkcji LTE
- Uruchom dowolne recovery inne niż stockowe recovery (polecenia ADB tam nie działają).
- Otwórz CMD w folderze **platform-tools**.
- Przywróć cztery partycje, których kopię zapasową utworzono, używając poniższych poleceń. Zastąp `path\to` rzeczywistą ścieżką obrazów.
```cmd
adb push path\to\fsc.bin /cache/ & adb shell dd if=/cache/fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb push path\to\fsg.bin /cache/ & adb shell dd if=/cache/fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb push path\to\modemst1.bin /cache/ & adb shell dd if=/cache/modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb push path\to\modemst2.bin /cache/ & adb shell dd if=/cache/modemst2.bin of=/dev/block/by-name/modemst2
```
- Uruchom ponownie urządzenie i sprawdź, czy działa LTE.
> [!Note]
> Jeśli to nadal nie zadziała, będziesz musiał wykonać kilka dodatkowych kroków:
- Pobierz [wersję ROM dla swojego urządzenia](https://xmfirmwareupdater.com/miui/polaris/)
- Otwórz go, poszukaj pliku o nazwie **modem.img** i rozpakuj go.
- Uruchom system w trybie fastboot (`adb restart bootloader`).
- Wgraj plik **modem.img** poniższym poleceniem, zastępując `ścieżkę\do` rzeczywistą ścieżką do obrazu.
```cmd
fastboot flash modem ścieżka\do\modem.img
```

##### Skończone!

## LTE in Windows does not work
> [!Note]
> You may have to follow the steps above to restore your modem first
- In Android, find your APN settings. It should be located in `Connections` > `Mobile Networks` > `Access Point Names`.
- Write the information of your current APN settings down, then boot into Windows.
- In `Cellular Settings`, click on `Mobile operator settings` > `APN settings` and add the APN settings you wrote down earlier.
- Enable **Cellular**. It may say `No Internet Access`, but it should still work. 

##### Finished!

## Device is not recognized in fastboot or recovery
> This likely means you don't have (proper) USB drivers installed
- Download [QUD.zip](https://github.com/n00b69/woa-betalm/releases/download/Qfil/QUD.zip) here and extract it.
- Open Device Manager and find an unknown device or device with errors that may be called **Android**, **ADB Interface**, or **QUSB_BULK**.
- Right click this devjce, select "Update Drivers" > "Browse files", then select the **QUD folder** you extracted before.

##### Finished!

## Nie można zamontować systemu Windows w systemie Android
> Dzieje się tak, gdy zamykasz system Windows zamiast go ponownie uruchamiać
- Aby rozwiązać ten problem, uruchom system Windows, a następnie naciśnij „Uruchom ponownie”, a następnie, gdy ekran się wyłączy, uruchom TWRP i stamtąd załaduj system Android.
> Alternatywnie, jeśli masz już skonfigurowaną aplikację Switch to Android, po prostu użyj jej, aby przejść na Androida

##### Skończone!

## USB nie działa
Włącz tryb hosta USB, korzystając z [przewodnika dotyczącego przełączania trybu hosta USB](materials.md#przełączanie-trybu-hosta-usb).

##### Skończone!

## BSOD 0xc000021a
Zwykle oznacza to, że plik winlogon.exe się uszkodził i może być konieczne ponowne zastosowanie obrazu systemu Windows.

##### Skończone!

## Komputer nieoczekiwanie uruchomił się ponownie lub napotkał nieoczekiwany błąd
Jeśli natkniesz się na ten błąd, może być konieczna ponowna instalacja obrazu systemu Windows. Skorzystaj w tym celu z [przewodnika ponownej instalacji](2-install.md).

##### Skończone!

## INACCESSIBLE_BOOT_DEVICE BSOD
Ten niebieski ekran śmierci prawdopodobnie oznacza uszkodzoną instalację sterownika. Aby rozwiązać ten problem, zainstaluj ponownie sterowniki, korzystając z [przewodnika ponownej instalacji](2-install.md).

##### Skończone!



















