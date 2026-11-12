---
title: "Безопасность"
description: "Журнал аудита только дополняется. Записи связаны цепочкой хешей, контрольные точки подписываются ключом secrets/audit_signing_key, которого нет в базе."
version: "v0.8.0"
lang: "ru"
order: 11
---

## Журнал аудита

Журнал аудита только дополняется. Записи связаны цепочкой хешей, контрольные точки подписываются ключом `secrets/audit_signing_key`, которого нет в базе. Ежемесячный архив шифруется ключом `audit_archive_key`, узлы получают только его открытую часть.

```bash
docker compose exec xtab-worker xtab audit verify            # целостность цепочки и подписей
docker compose exec xtab-worker xtab audit export > audit.jsonl
age -d -i secrets/audit_archive_key <месяц>.jsonl.age        # чтение архива утилитой age
```

Выгрузка в SIEM (syslog по TLS) настраивается администратором организации на странице «Журнал аудита».

## Смена ключей

Команды выполняются в каталоге установки.

**Ключ организации** — им запечатаны её секреты: ключи автоматизаций, приложений-аутентификаторов, клиентов SSO. Смена — без остановки:

```bash
docker compose run --rm migrate keys rotate-org
```

Без `--org N` меняются ключи всех организаций.

**Главный ключ** (`secrets/master_key`) — им обёрнуты ключи установки и организаций. Узлы держат его в памяти, поэтому на время смены они останавливаются:

```bash
od -An -tx1 -N32 /dev/urandom | tr -d ' \n' >secrets/master_key.new
docker compose stop xtab xtab-worker
docker compose run --rm -v "$PWD/secrets/master_key.new:/run/secrets/master_key_new:ro" migrate keys rotate-master --new-key-file /run/secrets/master_key_new
cp secrets/master_key secrets/master_key.old
cat secrets/master_key.new >secrets/master_key && rm secrets/master_key.new
docker compose up -d
```

Ключи переворачиваются одной транзакцией: при ошибке ничего не меняется, узлы запускаются со старым ключом. Резервные копии, снятые до смены, открываются только старым ключом — храните `master_key.old` отдельно от них, пока копии нужны.

## Рекомендации

- Ограничьте вход на сервер и доступ к каталогу установки: у кого есть `secrets/` и консоль, у того полные права на установку.
- Включите второй фактор для всех пользователей политикой организации, а не только для администраторов.
- Храните `secrets/master_key`, `backup_key` и ключи аудита вне сервера и вне копий: в сейфе или хранилище секретов организации.
- Держите копии на S3 другой машины и проверяйте восстановление раз в квартал.
- Подключите алерты из `monitoring/` и выгрузку аудита в SIEM.
