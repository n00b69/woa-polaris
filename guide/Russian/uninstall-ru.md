<img align="right" src="https://github.com/n00b69/woa-polaris/blob/main/polaris.png" width="350" alt="Windows 11 running on polaris">


# Запуск Windows на Xiaomi Mix 2s

## Удаление

### Зачем это нужно?
Если вы хотите удалить Windows, этот гайд используется вместо удаления разделов вручную, чтобы избежать ошибки + написания целого специального руководства по просто деинсталляции.

If you want to relock your bootloader you'll need your partition table to be stock.

### Требования
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [gpt_both0.bin](https://github.com/n00b69/woa-polaris/releases/download/Files/gpt_both0.bin)

### Загрузитесь в fastboot 
> Удерживайте нажатой кнопку уменьшения громкости + включения, пока телефон выключен, или выполните следующую команду когда он загружен 
```cmd
adb reboot bootloader
```

#### Восстановите GPT
> Замните ```путь\к\gpt_both0.bin``` с указанием пути к файлу gpt_both 0.bin.

```cmd
fastboot flash partition:0 путь\к\gpt_both0.bin
```

#### Отформатируйте userdata, чтобы избежать сбоя при загрузке и восстановить размер FS
```cmd
fastboot -w
```
> [!Note]
> Если форматирование userdata завершится неудачно, перезагрузтесь в recovery и сделайте wipe data там вместо этого

## Готово!
