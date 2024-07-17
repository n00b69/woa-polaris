<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Установка Windows

### Требования
- [Образ ARM Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg исправления touch](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

- [Образ UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Прошейте OFOX recovery
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Включите режим mass storage
> Если он попросит вас запустить его ещё раз, сделайте это
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его перепрошивки с помощью EDL, и то, и другое, скорее всего, будет стоить денег)
```cmd
diskpart
```

#### Выбрать раздел Windows 
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **WINPOLARIS**
```diskpart
select volume $
```

#### Добавить букву к разделу Windows
```cmd
assign letter X
```

#### Выбhfnm раздел ESP
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **ESPPOLARIS**
```diskpart
select volume $
```

#### Добавьте букву к ESP
```cmd
assign letter Y
```

#### Выйти из diskpart
```cmd
exit
```

### Установка Windows
> Замените `путь\к\install.esd` актуальным путём к install.esd (файл также может называться install.wim)
```cmd
dism /apply-image /ImageFile:путь\к\install.esd /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:путь\к\install.esd`, затем замените `index:6` действтельным индексом **Windows 11 Pro** в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` (Если появляется ошибка, запустите  `OfflineUpdaterFix.cmd`)

> Введите букву диска **WINPOLARIS** (должна быть **X**) затем нажмите Enter

> [!WARNING]
> НЕ ИСПОЛЬЗУЙТЕ DISM++
  
#### Создать файлы загрузчика Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Включение тестовой подпись
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Отключите восстановление
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Отключите проверку целостности
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Отвяжите буквы дисков
> Чтобы они не остались после отключения устройства
```cmd
diskpart
```

#### Выберите раздел Windows телефона
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **WINPOLARIS**
```cmd
select volume $
```

#### Отвяжите букву X
```cmd
remove letter x
```

#### Выберите раздел ESP телефна
> Используйте `list volume` чтобы найти его, замените `$` номером раздела **ESPPOLARIS**
```cmd
select volume $
```

#### Отвяжите букву Y
```cmd
remove letter y
```

#### Выйдите из diskpart
```cmd
exit
```

### Перезагрузитесь в fastboot
> Удерживайте кнопку **уменьшение громкости** + **питание**, чтобы перезагрузить телефон в режим fastboot

#### Исправить touch
> Замените `путь\к\devcfg-polaris.img` актуальным путём к образу
```cmd
fastboot flash devcfg_ab путь\к\devcfg-polaris.img
```

#### Загрузитесь в UEFI
> Замените `путь\к\polaris-uefi.img` актуальным путём к образу UEFI
```cmd
fastboot boot путь\к\polaris-uefi.img
```

### Reboot to Android
Your device should reboot by itself after +- 10 minutes of waiting, after which you will be booted into Android, for the last step.

## [Последний шаг: Настройка двойной загрузки](dualboot-ru.md)











