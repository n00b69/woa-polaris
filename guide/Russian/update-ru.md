<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Обновление драйверов 

### Требования
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Драйвера](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)
  
- [Образ UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

### Запуск UEFI
> Замените **<путь\к\polaris-uefi.img>** путём к образу UEFI 
```cmd
fastboot boot <путь\к\polaris-uefi.img>
```

#### Включение режима mass storage 
> После загрузки в UEFI используйте кнопки регулировки громкости для навигации по меню и кнопку питания для подтверждения
- Выберите **UEFI Boot Menu**.
- Выберите **USB Attached SCSI (UAS) Storage**.
- Нажмите кнопку **питания** дважды чтобы подтвердить.

### Diskpart
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

#### Привязать букву к WINPOLARIS
```cmd
assign letter X
```

#### Выйти из diskpart
```cmd
exit
```

### Установка драйверов 
> Извлеките папку с драйверами из архива, затем выполните следующую команду, заменяя `<path\to\drivers>` путём к папке с драйверами
```cmd
dism /image:X:\ /add-driver /driver:<path\to\drivers> /recurse
```

#### Загрузка обратно в Windows
> Перезагрузите устройство, чтобы снова загрузиться в Windows. Если после этого планшет загрузится в Android, перепрошейте образ UEFI с помощью fastboot или с помощью приложения WOA Helper

## Готово!
