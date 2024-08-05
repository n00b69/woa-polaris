<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Tworzenie partycji

### Wymagania
- Mózg (najważniejsze ze wszystkich)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Zmodyfikowane recovery OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Notes
> [!Warning]  
> 
> NIE URUCHAMIAJ PONOWNIE TELEFONU! Jeśli uważasz, że popełniłeś błąd, poproś o pomoc na [czacie telegramowym](https://t.me/WinOnMIX2S).
> 
> Nie uruchamiaj wszystkich poleceń na raz, wykonuj je po kolei!

### Otwieranie CMD jako administrator
> Pobierz **platform-tools** i wypakuj gdzieś folder, a następnie otwórz CMD jako **administrator**.
>
> Zaleca się pozostawienie tego okna otwartego i korzystanie z niego przez cały przewodnik.
> 
> Zastąp `path\to\platform-tools` rzeczywistą ścieżką do folderu platform-tools, na przykład **C:\platform-tools**.
```cmd
cd path\to\platform-tools
```

#### Zflashuj OFOX
> Otwórz okno CMD w folderze platform-tools, a następnie (gdy telefon jest w trybie szybkiego uruchamiania) uruchom
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Tworzenie kopii zapasowych ważnych plików
> Spowoduje to utworzenie kopii zapasowej plików **fsc**, **fsg**, **modemst1** i **modemst2** w bieżącej ścieżce, w której otwarto CMD (na przykład **C:\platform-tools**). Przed kontynuowaniem upewnij się, że te pliki rzeczywiście tam są.
>
> Jeśli chcesz utworzyć kopię zapasową czegoś innego, zrób to teraz. Twoje dane Androida zostaną usunięte w kolejnych krokach.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

### Backing up your boot image
> This will back up your current boot image in the current directory
```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Uruchom skrypt partycjonowania
> Zastąp **$** ilością miejsca, jaką ma mieć system Windows (nie dodawaj GB, po prostu wpisz liczbę)
> 
> Jeśli poprosi Cię o ponowne uruchomienie, zrób to
```cmd
adb shell partition $
```

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa

## [Next step: Rooting your phone](2-root.md)





















