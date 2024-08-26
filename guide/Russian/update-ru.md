<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Обновление драйверов 

### Требования
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

- [Драйвера](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)
  
- [Образ UEFI](https://github.com/n00b69/woa-beryllium/releases/tag/UEFI)



### Diskpart
```cmd
diskpart
```

#### Отобразить разделы устройства
> Чтобы отобразить список всех подключенных разделов, используйте
```cmd
list volume
```

#### Выберите раздел Windows 
> Замените `$` номером раздела **WINF1**
```cmd
select volume $
```

#### Привязать букву к WINF1
```cmd
assign letter X
```

### Выйти из diskpart
```cmd
exit
```

### Установка драйверов 
> Распакуйте архив с драйверами, затем откройте файл `OfflineUpdater.cmd`

> Введите букву диска **WINF1**, должна быть X, затем нажмите enter

#### Загрузка обратно в Windows
> Перезагрузите устройство, чтобы снова загрузиться в Windows. Если после этого планшет загрузится в Android, перепрошейте образ UEFI с помощью fastboot или с помощью приложения WOA Helper


## Готово!
