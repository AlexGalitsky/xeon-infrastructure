## XRay
```bash
# После установки проверить подключение
curl -x http://127.0.0.1:10809 https://ifconfig.me

# Посмотреть логи Xray
journalctl -u xray -f

# Проверить статус
systemctl status xray
```

### Troubleshooting
**failed to parse config** — ошибка в JSON (несмотря на validate, путь к файлу может быть неверным).
**address already in use** — порт 10808 или 10809 уже занят другим процессом.
**permission denied** — у пользователя xray нет прав на чтение конфига или запись логов.

```bash
# может ли пользователь xray запустить этот бинарник
ls -la /opt/xray/xray
# Должно быть -rwxr-xr-x

# как вариант снести логи
sudo rm -rf /var/log/xray/*
sudo chown -R xray:xray /var/log/xray
sudo systemctl restart xray
```

