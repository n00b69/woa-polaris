<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Tworzenie partycji

### Wymagania
- Mózg (najważniejsze ze wszystkich)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Notes
> [!Warning]  
> 
> NIE URUCHAMIAJ PONOWNIE TELEFONU! Jeśli uważasz, że popełniłeś błąd, poproś o pomoc na [czacie telegramowym](https://t.me/WinOnMIX2S).
> 
> Nie uruchamiaj wszystkich poleceń na raz, wykonuj je po kolei!
>
> MOŻESZ ZNISZCZYĆ SWOJE URZĄDZENIE ZA POMOCĄ PONIŻSZYCH POLECEŃ, JEŚLI ZROBISZ JE ŹLE!!!

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

### Przewodnik dotyczący partycjonowania
> Twój Xiaomi Mix 2s może mieć różne rozmiary pamięci. Ten przewodnik używa wartości modelu 128GB jako przykładu. W razie potrzeby przewodnik wspomni, czy można lub należy użyć innych wartości.

#### Odmontuj dane
```cmd
adb shell umount /dev/block/sda21
```

#### Przygotowanie do partycjonowania
```cmd
adb shell parted /dev/block/sda
```

#### Wyświetlanie aktualnej tablicy partycji
> Parted wyświetli listę partycji, "userdata" powinenen być ostatnią partycją na liście.
```cmd
print
```

#### Usuwanie userdata
> Zamień **$** na numer partycji **userdata**, który powinien wynosić **21**
```cmd
rm $
```

#### Ponowne utworzenie userdata
> Zamień **1611MB** na poprzednią wartość początkową **userdata**, którą właśnie usunęliśmy (prawdopodobnie jest to 1611MB)
>
> Zastąp **32GB** wartością końcową, jaką chcesz mieć dla **userdata**
```cmd
mkpart userdata ext4 1611MB 32GB
```

#### Tworzenie partycji ESP 
> Zamień **32GB** na końcową wartość **userdata**
>
> Zastąp **32.3GB** wartością, której użyłeś wcześniej, dodając do niej **0.3GB**
```cmd
mkpart esp fat32 32GB 32.3GB
```

#### Tworzenie partycji Windows
> Zastąp **32.3GB** wartością końcową **esp**
>
> Zamień **123GB** na końcową wartość dysku, użyj `p free`, aby go znaleźć
```cmd
mkpart win ntfs 32.3GB 123GB
```

#### Tworzenie bootowalnego ESP
> Użyj `print`, aby zobaczyć wszystkie partycje. Zamień „$” na numer partycji ESP, który powinien wynosić 22
```cmd
set $ esp on
```

#### Wyjdź z parted
```cmd
quit
```

#### Formatowanie danych
- Sformatuj wszystkie dane w OFOX, w przeciwnym razie Android nie uruchomi się.
- (Idź do Wyczyść > Formatuj dane > wpisz yes)

#### Sprawdź, czy Android nadal się uruchamia
- Po prostu uruchom ponownie telefon i sprawdź, czy Android nadal działa


## [Następny Krok](2-install.md)





















