<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">

# Запуск Windows на Xiaomi Mix 2s

## Переустановка Windows

### Требования
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded OFOX](https://github.com/n00b69/woa-polaris/releases/download/Files/ofox.img)

### Прошейте OFOX recovery
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery path\to\ofox.img reboot recovery
```

#### Отформатировать раздел Windows
```cmd
adb shell format
```

## [Следующий шаг: Установка Windows](3-install-ru.md)



















