<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Windows na Xiaomi Mix 2s

## Rozwiązywanie problemów
> Poniżej znajdziesz listę typowych problemów i ich rozwiązań

## LTE and other network services in Android no longer work
> Sometimes Windows may wipe your modem partitions, resulting in the loss of LTE in Android. To fix this, you'll need to restore your modem using the backups that you hopefully made [while partitioning your device](1-partition.md#backing-up-important-files). If you did not do this step, there is likely no way to recover.
- Boot into any recovery other than the stock recovery (ADB commands do not work there)
- Open CMD in the **platform-tools** folder.
- Restore the four partitions that you backed up using the below commands. Replace `path\to` with the actual path of the images.
```cmd
adb shell dd if=path\to\fsc.bin of=/dev/block/by-name/fsc
```

```cmd
adb shell dd if=path\to\fsg.bin of=/dev/block/by-name/fsg
```

```cmd
adb shell dd if=path\to\modemst1.bin of=/dev/block/by-name/modemst1
```

```cmd
adb shell dd if=path\to\modemst2.bin of=/dev/block/by-name/modemst2
```
- Reboot your device and check if LTE works.
> [!Note]
> If it still does not work, you will have to do some additional steps;
- Download the [stock rom for your device](https://xmfirmwareupdater.com/miui/polaris/)
- Open it, look for a file called **modem.img** and extract it.
- Boot into fastboot mode (`adb reboot bootloader`).
- Flash this **modem.img** with the below command, replacing `path\to\modem.img` with the actual path of the image
```cmd
fastboot flash modem path\to\modem.img
```

##### Finished!

## Nie można zamontować systemu Windows w systemie Android
> Dzieje się tak, gdy zamykasz system Windows zamiast go ponownie uruchamiać.
- Aby rozwiązać ten problem, uruchom system Windows, a następnie naciśnij „Uruchom ponownie”, a następnie, gdy ekran się wyłączy, uruchom system TWRP i stamtąd załaduj system Android.
> Alternatywnie, jeśli masz już skonfigurowaną aplikację Przełącz na Androida, po prostu użyj jej, aby przejść na Androida.

##### Skończone!

## USB nie działa
Włącz tryb hosta USB, korzystając z [przewodnika dotyczącego przełączania trybu hosta USB](materials.md#przełączanie-trybu-hosta-usb).

##### Skończone!

## Błąd DISM: 87 Opcja dodawania sterownika jest nieznana
Zwykle oznacza to, że masz nieczysty obraz systemu Windows z innymi sterownikami. Musisz uzyskać czysty obraz systemu Windows (co oznacza, że ​​nie postępowałeś zgodnie z instrukcjami).

##### Skończone!

## BSOD 0xc000021a
Zwykle oznacza to, że plik winlogon.exe nie powiódł się i może być konieczne ponowne zastosowanie obrazu systemu Windows.

##### Skończone!

## Komputer nieoczekiwanie uruchomił się ponownie lub napotkał nieoczekiwany błąd
Jeśli natkniesz się na ten błąd, może być konieczne ponowne wdrożenie obrazu systemu Windows. Skorzystaj w tym celu z [przewodnika ponownej instalacji](2-install.md).

##### Skończone!

## INACCESSIBLE_BOOT_DEVICE BSOD
Ten niebieski ekran śmierci prawdopodobnie oznacza uszkodzoną instalację sterownika. Aby rozwiązać ten problem, zainstaluj ponownie sterowniki, korzystając z [przewodnika ponownej instalacji](2-install.md).

##### Skończone!



















