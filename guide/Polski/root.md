<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Przewodnik po rootowaniu

### Wymagania
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB i Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/modded-ofox-polaris.img)

### Uruchom OFOX
> Jeśli Twoje recovery zostało przywrócone do stanu fabrycznego, wykonaj flashowanie ponownie w trybie fastboot za pomocą:
```cmd
fastboot flash path\to\modded-ofox-polaris.img reboot recovery
```

#### Tworzenie kopii zapasowej obrazu rozruchowego
> Czasami flashowanie Magiska może spowodować bootloop. Aby to naprawić, musisz przywrócić kopię zapasową pliku boot.img.

Użyj funkcji tworzenia kopii zapasowych OFOX, aby utworzyć kopię zapasową partycji rozruchowej.

#### Flashowanie Magiska
- Zflashuj plik magisk.apk (być może będziesz musiał zmienić jego nazwę na magisk.zip) i zrestartuj telefon.
- Po uruchomieniu zlokalizuj aplikację Magisk i otwórz ją.
- Postępuj zgodnie z otrzymanymi instrukcjami. Wybierz metodę instalacji bezpośredniej, jeśli dostępnych jest kilka metod.

Twój telefon uruchomi się ponownie i pomyślnie go zrootowałeś.

> [!Important]
> Po zrootowaniu telefonu utwórz nową kopię zapasową pliku boot.img w systemie Android i Windows (za pomocą aplikacji WOA Helper) i usuń wszelkie pozostałe utworzone wcześniej kopie zapasowe pliku boot.img. Jeśli tego nie zrobisz, przejście na Androida spowoduje zrestartowanie telefonu.
>
> Po aktualizacji lub zmianie ROMu (i ponownym uruchomieniu) będziesz musiał powtórzyć wszystkie kroki opisane na tej stronie.

## Skończone!
