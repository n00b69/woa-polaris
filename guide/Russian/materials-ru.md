<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Дополнительные материалы
> Ниже вы найдете список настроек и материалов для Windows на вашем устройстве ARM

### Спиок поддерживаемых программ и игр на ARM
> Это далеко не все приложения что могут быть запущены, но это все программы что были проверенны комьюнити

- [Renegade Google Sheets list](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

- [ARM Repo (native ARM software)](https://armrepo.ver.lt/)

- [News & supported applications](https://windowsonarm.org/)

#### Finished!


### Отключение USB host mode
> [!Warning]
> Отклюите USB host mode только если используете usb hub с дополнительным питанием, иначе оно может повредить устройство. Если у вас нет usb hub с дополнительным питанием, включитe USB host mode или вы не сможете использовать любые usb девайсы.

- Запустите [USB Host Control](https://github.com/Misha803/My-Scripts/releases/tag/USB-Host-Mode-Control) что бы включить\выключить USB host mode, и подтвердите что вы хотите выключить\включить USB host mode.
- Если USB host mode уже включен и USB устройства не работают, выключите и включите обратно.

#### Конец!


### Установка Microsoft Office
- Перейдите на [Gravesoft's Office installer page](https://gravesoft.dev/office_c2r_links).
- Скачайте инсталлер на ваш выбор. убедитесь что вы выбрали `Online x64`.
- Откройте `setup.exe` и следуйте инструкции внутри нее.

#### Конец!


### Активация Windows / Office
- Используйте инструкцию Massgravel [here](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Конец!


### Как сделать клавиатуру плавующей
> [!WARNING]  
> Убедитесь что вы делаете эти шаги на устройстве, не на компьютере!

- Откройте командую строку от имени администратора и выполните команду ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Намите `y`, а после enter.
- Перезагрузите.

##### Конец!


















