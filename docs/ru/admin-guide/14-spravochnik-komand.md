---
title: "Справочник команд"
description: "Команды выполняются в каталоге установки. Служебные — через сервис migrate (docker compose run --rm migrate <команда>)."
version: "v0.8.0"
lang: "ru"
order: 14
---

Команды выполняются в каталоге установки. Служебные — через сервис `migrate` (`docker compose run --rm migrate <команда>`). Команды копий, хранилища и аудита — на узле фоновых задач (`docker compose exec xtab-worker xtab <команда>`).

| Команда | Что делает |
|---|---|
| `doctor` | Диагностика окружения |
| `config check` / `config show` | Проверить конфигурацию / показать итоговые значения без секретов |
| `settings get` / `set` / `unset` | Настройки инстанса на всех узлах без перезапуска |
| `user access-link` / `reset-2fa` / `block` / `unblock` / `unlock` / `anonymize` / `instance-admin` | Учётные записи, когда панели недостаточно |
| `license show` / `install <файл>` | Лицензия |
| `backup now` / `status` / `checked` | Полная копия вне расписания, состояние копий, отметка о проверке восстановления |
| `restore` | Восстановление — через сценарий `restore.sh` установки |
| `storage migrate` | Перенос файлов в другое S3 |
| `keys rotate-org` / `rotate-master` | Смена ключей организаций и главного ключа |
| `audit verify` / `export` | Проверка и выгрузка журнала аудита |
| `db bootstrap-sql` | Скрипт начальной настройки для администратора внешней СУБД |
| `debug realtime on` / `off` | Отладочный формат realtime на 24 часа |

Ключи установщика `install.sh`: `--check`, `--answers <файл>`, `--yes`, `--reconfigure`, `--rollback`, `--restore`, `--drop-failed`, `--rotate-secrets`, `--uninstall`, `--purge`, `--dir`, `--lang`.
