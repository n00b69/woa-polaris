<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Исправление Проблем 
> Ниже вы найдете список распространенных проблем и путей их решения

## Touch внезапно перестает работать
> Это может быть связано, с настройками энергосбережения:

- Откройте **Device Manager** на телефоне когда находитесь в Windows.
- Откройте пункт **Human Interface Devices** > **Synaptics RMI4 over Function 12 (2D Multifinger Pointing/Pen) Digitizer (S3708)**.
- Нажмите на **Power Mangament** и отключите **"Allow the computer to turn off this device to save power"**.

##### Вы молодец!

## Интернет в android перестал работать
> Иногда windows может сстреть раздел modem, в результате чего вы теряете доступ к интернету из android. Что бы исправить это вам нужно восстановить раздел используя бекап который вы сделали [когда размечали ваше устройство](https://github.com/tvorogo/woa-polaris/blob/main/guide/Russian/1-partition-ru.md). Если вы не сделали это, скорее всего нету возможности для восстановления.
- Загрузитесь в любое рекавери, отличное от стокового (ADB команды не работают тут)
- Откройте командную строку в папке **platform-tools**.
- Восстановите разделы этими командами. Замените `path\to` на путь к образу.
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
- Перезагрузитесь и проверьте работу интернета.
> [!Дополнительно]
> 
> Если интернет не начал работать;
- Скачайте [стоковую прошивку](https://xmfirmwareupdater.com/miui/polaris/)
- откройте, вы должны найти файл с названием **modem.img** достаньте его.
- Загрузитесь в режим fastboot(`adb reboot bootloader`).
- Прошейте **modem.img** этой командой, заменив `path\to\modem.img` на путь к образу
```cmd
fastboot flash modem path\to\modem.img
```

##### Вы молодец!

## LTE in Windows does not work
> [!Note]
> Сначало надо пройти шаги по восстановлению раздела modem!
- в андройд, найдите ваши APN settings. Iони должны находится в `Connections` > `Mobile Networks` > `Access Point Names`.
- Запишите где то данные, затем загрузитесь в Windows.
- В `Cellular Settings`, нажмите на `Mobile operator settings` > `APN settings` и добавьте ваши данные которые вы ранее записали.
- Включите **Cellular**. windows может сказать `No Internet Access`, но он должен работать 

##### Finished!

## Телефон не определяется в компьютере
> Скорее всего у вас не установлены, установлены неправиьно драйвера
- Скачайте [QUD.zip](https://github.com/n00b69/woa-betalm/releases/download/Qfil/QUD.zip) и распакуйте.
- Откройте диспетчер устройств aи найдите неизвестное устройство cили устройство с ошибкой и названием **Android**, **ADB Interface**, или **QUSB_BULK**.
- Правой кнопкой мыши, выберите "Update Drivers" > "Browse files", и потом выберите **QUD folder** которое вы распаковали ранее.

##### Вы молодец!

## Не удается смонтировать Windows в Android
Если при монтировании Windows образуется пустая папка, значит у вас не установлена Windows, либо в вашем ПЗУ нет поддержки монтирования.

##### Готово!

## Не удается выполнить запись в Windows из Android
> Это вызвано выключением Windows вместо её перезапуска.
- Чтобы решить эту проблему, загрузитесь в Windows и затем нажмите "перезагрузка", затем, когда экран выключится, загрузитесь в TWRP и оттуда загрузите Android.
- Или, отключите режим гибернации в Windows используя [этот](https://github.com/n00b69/woa-beryllium/releases/tag/1.0) скрипт 
> В качестве альтернативы, если вы уже настроили приложение Switch to Android, просто используйте его для переключения на Android.

##### Готово!

## USB не работает 
Включите режим USB хост ипользуя инструкцию на странице [полезные приложения и инструкции](materials-ru.md).

##### Готово!

## 0xc000021a BSOD
Обычно это означает, что произошел сбой winlogon.exe, и вам, возможно, потребуется повторно применить образ Windows.

##### Готово!

## Компьютер неожиданно перезагрузился или возникла непредвиденная ошибка
Если вы столкнётесь с этой проблемой, возможно, вам потребуется повторно развернуть образ Windows. Для этого воспользуйтесь [руководством по переустановке](reinstall-ru.md).

##### Готово!

## INACCESSIBLE_BOOT_DEVICE BSOD
Этот синий экран смерти, вероятно, означает сбой в установке какого-либо драйвера. Чтобы исправить это, переустановите драйверы, используя [руководство по переустановке драйверов](update-ru.md).

##### Готово!
