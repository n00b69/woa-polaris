<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Переустановка Windows

### Требования
- [Образ ARM Windows](https://worproject.com/esd)
  
- [Драйвера](https://github.com/n00b69/woa-polaris/releases/tag/Drivers)

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

#### Выйдите из diskpart
```cmd
exit
```

#### Отформатируйте раздел Windows
> Перейдите в Проводник Windows > Этот компьютер и выберите **WINPOLARIS**. Щелкните правой кнопкой мыши и отформатируйте как NTFS.

### Установка Windows
> Замените `путь\к\install.esd` актуальным путём к install.esd (файл также может называться install.wim)
```cmd
dism /apply-image /ImageFile:путь\к\install.esd /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вышего образа используя `dism /get-imageinfo /ImageFile:путь\к\install.esd`, затем замените `index:6` действтельным индексом **Windows 11 Pro** в вашем образе

### Установка драйверов
> Распакуйте пакет драйверов, затем откройте файл `OfflineUpdater.cmd` (Если появляется ошибка, запустите  `OfflineUpdaterFix.cmd`)

> Введите букву диска **WINPOLARIS** (должна быть **X**) затем нажмите Enter

### Загрузка в Windows
Перезагрузите телефон. Если в итоге он загрузится в Android, а не в Windows, перепрошейте UEFI заново с помощью WOA Helper.

#### Настройка Windows
> Сейчас Windows на вашем устройстве настроится. Это займёт некоторое время. В конечном итоге телефон перезагрузится, и после этого должна запуститься программа начальной установки (oobe).

> [!Note]
> Если вы не хотите входить в учетную запись Майкрософт, введите "g" в качестве адреса электронной почты и пароля. После этого Windows позволит вам создать локальную учетную запись

## Готово!

















