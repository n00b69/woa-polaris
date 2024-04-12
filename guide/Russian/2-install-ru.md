<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Установка Windows

### Требования
- [ARM образ Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

- [Devcfg исправления touch](https://github.com/n00b69/woa-polaris/releases/download/Files/devcfg-polaris.img)
  
- [образ UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Загрузка в UEFI
> Замените **<путь\к\polaris-uefi.img>** с актуальным путём к образу UEFI
```cmd
fastboot boot <путь\к\polaris-uefi.img>
```

#### Включение режима mass storage
> После загрузки в UEFI используйте кнопки регулировки громкости для навигации по меню и кнопку питания для подтверждения
- Выберите **UEFI Boot Menu**.
- Выберите **USB Attached SCSI (UAS) Storage**.
- Нажмите кнопку **питания** дважды чтобы подтвердить.

### Diskpart
> [!WARNING]
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его перепрошивки с помощью EDL, и то, и другое, скорее всего, будет стоить денег)
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
> Замените `<путь\к\install.esd>` актуальным путём к install.esd (он также может называться install.wim)
```cmd
dism /apply-image /ImageFile:<путь\к\install.esd> /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:<путь\к\install.esd>`, затем замените `index:6` действтельным индексом Windows 11 Pro в вашем образе

### Установка драйверов
> Извлеките папку с драйверами из архива, затем выполните следующую команду, заменяя `<path\to\drivers>` путём к папке с драйверами
```cmd
dism /image:X:\ /add-driver /driver:<path\to\drivers> /recurse
```
  
#### Создать файлы загрузчика Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Включение тестовой подписи
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Выключение восстановления 
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Отключение проверки целостности
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Отвязать буквы дисков
> Чтобы они не остались после отключения устройства
```cmd
diskpart
```

#### Выбрать раздел Windows телефона
> Используйте `list volume` чтобы найти его, замените `$` номером **WINPOLARIS**
```diskpart
select volume $
```

#### Отвязать букву X
```diskpart
remove letter x
```

#### Выбрать раздел ESP телефна
> Используйте `list volume` чтобы найти его, замените `$` номером **ESPPOLARIS**
```diskpart
select volume $
```

#### Отвязать букву Y
```diskpart
remove letter y
```

#### Выйти из diskpart
```diskpart
exit
```

### Исправить touch
> Перезагрузитесь в fastboot, затем замените **path\to** путём к образу
```cmd
fastboot flash devcfg_ab path\to\devcgf-polaris.img
```

### Перезагрузка в Android
> Чтобы настроить двойную загрузку

## [Последний шаг: Настройка двойной загрузки](dualboot-ru.md)
