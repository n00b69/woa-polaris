<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Rozwiązywanie problemów
> Poniżej znajdziesz listę typowych problemów i ich rozwiązań

## Dotyk czasami przestaje działać
> Przyczyną mogą być ustawienia oszczędzania energii urządzenia. Aby (miejmy nadzieję) rozwiązać ten problem, wykonaj następujące czynności:

- Otwórz **Menedżer urządzeń** na urządzeniu w systemie Windows.
- Przejdź do **Urządzenia interfejsu HID** > **Synaptics RMI4 over Function 12 (2D Multifinger Pointing/Pen) Digitizer (S3708)**.
- Kliknij **Zarządzanie energią** i odznacz opcję **„Zezwalaj komputerowi na wyłączanie tego urządzenia w celu oszczędzania energii”**.

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

## LTE w systemie Windows nie działa
> [!Note]
> Aby przywrócić modem, konieczne może być wykonanie powyższych kroków.
- W systemie Android znajdź ustawienia APN. Powinny one znajdować się w „Połączenia” > „Sieci komórkowe” > „Nazwy punktów dostępu”.
- Zapisz informacje o bieżących ustawieniach APN, a następnie uruchom system Windows.
- W „Ustawieniach sieci komórkowej” kliknij „Ustawienia operatora komórkowego” > „Ustawienia APN” i dodaj zapisane wcześniej ustawienia APN.
- Włącz **Sieć komórkową**. Może pojawić się komunikat „Brak dostępu do internetu”, ale nadal powinno działać.

##### Skończone!

## Urządzenie nie jest rozpoznawane w trybie fastboot ani recovery
> Prawdopodobnie oznacza to, że nie masz zainstalowanych (prawidłowych) sterowników USB.
- Pobierz plik [QUD.zip](https://github.com/n00b69/woa-betalm/releases/download/Qfil/QUD.zip) tutaj i rozpakuj go.
- Otwórz Menedżera urządzeń i znajdź nieznane urządzenie lub urządzenie z błędami, które może nazywać się **Android**, **ADB Interface** lub **QUSB_BULK**.
- Kliknij prawym przyciskiem myszy to urządzenie, wybierz „Aktualizuj sterowniki” > „Przeglądaj pliki”, a następnie wybierz wcześniej rozpakowany folder **QUD**.

##### Gotowe!

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



















