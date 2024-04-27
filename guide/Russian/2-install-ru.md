<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Установка Windows

### Требования
- [Образ ARM Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg исправления touch](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [Образ UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Загрузитесь в UEFI
> Замените **<путь\к\polaris-uefi.img>** актуальным путём к образу UEFI
```cmd
fastboot boot <путь\к\polaris-uefi.img>
```

#### Включите режим mass storage
> После загрузки в UEFI используйте кнопки регулировки громкости для навигации по меню и кнопку питания для подтверждения
- Выберите **UEFI Boot Menu**.
- Выберите **USB Attached SCSI (UAS) Storage**.
- Нажмите кнопку **питания** дважды чтобы подтвердить.

### Diskpart
> [!WARNING]
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его перепрошивки с помощью EDL, и то, и другое, скорее всего, будет стоить денег)
```cmd
diskpart
```

#### Найдите ваш телефон
> При этом отобразится список всех подключенных дисков
```cmd
lis dis
```

#### Выберите ваш телефон
> Замените `$` актуальным номером вашего телефона (должен быть последним)
```cmd
sel dis $
```

#### Отобразить список разделов вашего телефона
> Это отобразит список разделов вашего телефона 
```cmd
lis par
```

#### Выбрать раздел Windows 
> Замените `$` номером раздела Windows (должен быть 23)
```cmd
sel par $
```

#### Отформатировать раздел Windows
```cmd
format quick fs=ntfs label="WINPOLARIS"
```

#### Добавить букву к разделу Windows
```cmd
assign letter X
```

#### Выбhfnm раздел ESP
> Замените `$` номером раздела ESP (должен быть 22)
```cmd
sel par $
```

#### Отформатировать раздел ESP
```cmd
format quick fs=fat32 label="ESPPOLARIS"
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
> Замените `<путь\к\install.esd>` актуальным путём к install.esd (файл также может называться install.wim)
```cmd
dism /apply-image /ImageFile:<путь\к\install.esd> /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:<путь\к\install.esd>`, затем замените `index:6` действтельным индексом Windows 11 Pro в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` 

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

### Исправить touch
> Перезагрузитесь в fastboot, затем замените **path\to** путём к образу
```cmd
fastboot flash devcfg_ab path\to\devcgf-polaris.img
```

### Перезагрузка в Windows
> Замените **<путь\к\firstboot.img>** актуальным путём к образу UEFI
```cmd
fastboot boot <путь\к\firstboot.img>
```

> После того как Windows загрузится и вы пройдёте первоначальную настройку, нажмите **Перезагрузка** в меню пуск чтобы загрузиться обратно в Android для последнего шага

## [Последний шаг: Настройка двойной загрузки](dualboot-ru.md)
