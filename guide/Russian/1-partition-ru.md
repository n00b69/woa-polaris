<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Разметка устройства 

### Требования 
- Разблокированный Загрузчик

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Модифицированный OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Заметки 
> [!WARNING]  
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ТЕЛЕФОН! Если вы считаете, что допустили ошибку, обратитесь за помощью в [Telegram чате](https://t.me/WinOnMIX2S).
> 
> Не выполняйте все команды сразу, выполняйте их по порядку!

### Открыть CMD от имени администратора
> Скачайте **platform-tools** и распакуйте его куда-нибудь, затем откройте CMD от имени **администратора**.
>
> Рекомендуется держать CMD открытым и использовать его на протяжении всего руководства.
> 
> Замените `путь\к\platform-tools` на путь к папке platform-tools, например **C:\platform-tools**.
```cmd
cd путь\к\platform-tools
```

> [!Note]
> If your device is not detected in fastboot or recovery mode, you'll have to install USB drivers [using this guide](troubleshooting-ru.md#device-is-not-recognized-in-fastboot-or-recovery)

#### Прошейте OFOX recovery
> Откройте окно CMD внутри папки platform-tools, затем (пока ваш телефон находится в режиме fastboot) выполните 
```cmd
fastboot flash recovery путь\к\ofox.img reboot recovery
```

### Создание резервной копии важных файлов
> Это создаст бэкап **fsc**, **fsg**, **modemst1** и **modemst2** в текущем расположении, где открыта ваша командная строка (например **C:\platform-tools**). Убедитесь, что эти файлы действительно сдесь, прежде чем продолжить.
>
> Сохраните эти резервные копии в надежном месте. Если программное обеспечение вашего устройства однажды будет уничтожено, вам могут понадобиться эти резервные копии, иначе ваш телефон может потерять возможности сотовой связи.
>
> Если вы хотите создать резервную копию чего-либо ещё, сделайте это сейчас. Ваши данные в Android будут удалены в ходе следующих действий.
```cmd
cmd /c "for %i in (fsg,fsc,modemst1,modemst2) do (adb shell dd if=/dev/block/by-name/%i of=/tmp/%i.bin & adb pull /tmp/%i.bin)"
```

#### Бэкап вашего boot образа
> Это позволит создать резервную копию вашего текущего загрузочного образа в текущем каталоге.
```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Запустите скрипт разметки 
> Замените **$** объёмом памяти, который вы хотите выделить для Windows (не добавляйте ГБ, просто введите число).
> 
> Если скрипт попросит запустить его ещё раз, то так и сделайте
```cmd
adb shell partition $
```

### Проверьте, запускается ли Android 
- Просто перезагрузите телефон и посмотрите, загружается ли Android

## [Следующий шаг: Получение root прав](2-root-ru.md)














