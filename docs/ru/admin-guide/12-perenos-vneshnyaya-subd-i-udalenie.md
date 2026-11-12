---
title: "Перенос, внешняя СУБД и удаление"
description: "Что сохранить при переносе: файл .env, install.toml и папку secrets/. Без secrets/master_key база не откроется, без secrets/backup_key не прочитаются копии."
version: "v0.8.0"
lang: "ru"
order: 12
---

**Что сохранить при переносе:** файл `.env`, `install.toml` и папку `secrets/`. Без `secrets/master_key` база не откроется, без `secrets/backup_key` не прочитаются копии.

**На новый сервер из резервных копий** (копии должны лежать на S3 другой машины):

1. Разверните на новом сервере ту же версию: `sudo ./install.sh --answers install.toml --yes`. Положите в `/opt/xtab/secrets/` файлы со старого сервера и запустите ту же команду ещё раз.
2. Выполните `sudo /opt/xtab/restore.sh --discard-current` (или с `--to-time`): база восстановится, файлы вернутся из их копий.
3. Переключите DNS домена на новый сервер.

**Файлы в другое S3:**

```bash
docker compose exec xtab-worker xtab storage migrate --to-endpoint https://s3.example.ru --to-bucket xtab \
  --to-access-key-file /run/secrets/… --to-secret-key-file /run/secrets/…
```

Команда копирует объекты и проверяет каждый; `--dry-run` только считает. Её можно запускать при работающих узлах и повторять: второй запуск заберёт появившееся. Затем укажите новое хранилище в разделе `[storage]` ответов и запустите установщик.

**Внешняя СУБД:** PostgreSQL 16 или новее с расширениями `pg_trgm` и `btree_gist`.

1. Администратор СУБД выполняет скрипт начальной настройки из `docker compose run --rm migrate db bootstrap-sql` с паролями из `secrets/`.
2. Перенесите данные: `pg_dump -Fc` встроенной базы и `pg_restore` на внешнюю, остановив на это время узлы.
3. Положите сертификат центра сертификации сервера СУБД в `secrets/db_ca.pem`, в `.env` задайте `XTAB_DB_HOST` и `XTAB_DB_PORT`, добавьте `docker-compose.external-db.yml` в `COMPOSE_FILE` и выполните `docker compose up -d`. Соединение с базой проверяет сертификат сервера.
4. Для копий направьте `archive_command` сервера СУБД в каталог, доступный узлу фоновых задач (том `wal-spool`).

**Удаление:** `sudo ./install.sh --uninstall` убирает контейнеры и оставляет данные, настройки и секреты — следующая установка подключится к ним. `sudo ./install.sh --purge` удаляет всё безвозвратно и просит ввести домен установки.
