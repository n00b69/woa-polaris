<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Dualboot guide

### Требования
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [Образ UEFI](https://github.com/n00b69/woa-polaris/releases/tag/UEFI)

- [Приложение WOA Helper](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)

## Руководство по настройке двойной загрузки
В этом руководстве предполагается, что у вас есть root-права, если это не так, пожалуйста, сначала следуйте [этому руководству](root-ru.md).

### Установка - Android
- Загрузите и установите приложение **WOA Helper**, затем откройте его и предоставьте ему root-доступ.
- Загрузите изображение **UEFI** и поместите его в папку с именем `UEFI` в вашем внутреннем хранилище.
- Open the **WOA Helper** app and use the **STA CREATOR** in **WOA TOOLBOX**.
> [!Important]
> Если папка `/sdcard/Windows` пустая, ваше ПЗУ не поддерживает монтирование, и вам придётся создать резервную копию boot.img внутри приложения, а затем вручную скопировать её в Windows после загрузки (например, загрузив её куда-нибудь, а затем скачав после загрузки в Windows). The same applies to the StA files, which are also generated in your internal storage.
>
> Сделайте тоже самое если папка доступна только для чтения.
- Вернитесь в приложение WOA Helper и нажмите кнопку `БЫСТРАЯ ЗАГРУЗКА В WINDOWS`.
  
### Установка - Windows
> [!Tip]
> If this is your first time booting Windows and you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.
- Перейдите к C:\sta и создайте ярлык `sta.exe` на своём рабочем столе, if one isn't already present

#### Загрузка на Android
- Запустите новый ярлык на своем рабочем столе (вы также можете прикрепить его к меню "Пуск" / панели задач для удобства доступа).

#### Загрузка в Windows
- Нажмите `БЫСТРАЯ ЗАГРУЗКА В WINDOWS` в приложении или воспользуйтесь только что созданным переключателем на панели быстрых настроек.
  
## Готово!


