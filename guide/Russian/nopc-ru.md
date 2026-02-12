<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on a Mi mix 2s">

# Запуск Windows на Xiaomi Mi mix 2s

## Установка Windows без компьютера 

### Требования
- Рут на Xiaomi Mi 8

- [Модифицированное рекавери](https://github.com/n00b69/woa-polaris/releases/tag/Recovery)

- [Dipper WinInstaller](https://github.com/n00b69/woa-polaris/releases/download/Files/polarisWinInstaller.zip)

- [Windows on ARM image](https://arkt-7.github.io/woawin/)

- [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK)

- Опционально: наличие USB флешки

### Notes
> [!WARNING]  
> Все данные будут стерты! сделайте резервную копию сейчас, если требуется 
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ВАШ ТЕЛЕФОН если вы думаете что, что то сделали не так, попросите помощи в [Telegram чате](https://t.me/woadipper).

> [!Important]
> Это гайд предпологает что у вас уже разблокирован загрузчик и есть root права, если этого нету, то вам необходим PC
### Прошейте модифицированное рекавери
> Если у вас уже есть модифицированное рекавери, то вы можете использовать его для установки нового 
- Скачайте образ модифицированного рекавери, переименуйте его в **recovery.img**, он должен находиться в `Download` папке **вашего внутреннего хранилища**.
- скачайте **Termux**, откройте его, и дайте eму права root доступа.
- Выполните жту команду что бы прошить модифицированное рекавери:
```cmd
su -c dd if=/sdcard/Download/recovery.img of=/dev/block/by-name/recovery
```
- Запустите эту команду что бы попасть в это рекавери:
```cmd
su -c reboot recovery
```

### Проверьте работает ли расшифровка 
- Единожды введите пароль в рекавери если попросит
- Откройте ыайловый мкнеджер и найдите internal storage 
> Если ваших файлов тут нет и вес равняется **(0MB)**, тогда вам нужны дополнительные шаги которые будут расписаны позже в этой инструкции 
#### Opening recovery terminal
- нажмите на  **Advanced** кнопку внизу в правой части экрана, а после нажмите на **Terminal**.

### Запуск скрипта разметки 
> После запуска скрипта укажите сколько хотите выделить для Windows например 50
>
> Не пишите **GB**, только цифры (для примера  **50**)
```cmd
partition
``` 

### Проверьте запускается ли android 
- Перезагрузите телефон и проверьте запускается ли android 

### Подготовка необходимых файлов
- Скачайте образ Windows он должен находиться в папке `Download`
> [!Important]
> По присинам производительности рекомендуется использовать 11 25H2 (Версии которые начинаются на 262XX, например 26200.7171)

> Если рекавери не может прочитать/расшифровать ваше хранилище, создайте папку на вашем **USB устройстве** названное `WOA` и положите файл **.esd** в него
>
- Скачайте **WinInstaller.zip** и оставьте его в папке `Download`.
- Скачайте и установите [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK), зайдите в нкго и дайте права root доступа и больше ничего.

#### Перезагрузитесь в recovery 
- нажмите на  `Reboot to Recovery` наверху в правой части экрана в магиск.
- загрузитесь в recovery, введите ваш пароль, еали попросит.

### Установка WinInstaller 
- В recovery, выберите **Install** и выберите **WinInstaller.zip**, затем прошейте его
> [!Note]
> Ожидайте пока ваш девайс загрузится в Windows этот процесс может занять 15-20 минут.
> [!Tip]
> если вы хотите пропустить Microsoft Account , нажмите **I don't have internet** когда находитесь на меню выбора WiFi.

#### Загрузка в Android
- запустите **Android** ярлык на вашем рабочем столе.

#### Загрузка в Windows
> Если программа пишет "UEFI NOT FOUND", download the [UEFI image](https://github.com/n00b69/woa-polaris/releases/tag/UEFI) и разместите в папке `UEFI`
- Нажмите на **QUICKBOOT TO WINDOWS** в WOA Helper app.

## Конец!

























