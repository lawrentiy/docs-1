# Копирование и заполнение таблицы с локальной машины

Вы можете как [скопировать](#copy) данные из таблицы в локальный файл, так и [заполнить](#write) таблицу данными из локального файла с помощью интерактивного терминала [psql]({{ pg-docs }}/app-psql.html).

## Перед началом работы {#before-you-begin}

1. [Получите SSL-сертификат](../../managed-postgresql/operations/connect.md#get-ssl-cert).
1. Установите зависимости:

    ```bash
    sudo apt update && sudo apt install --yes postgresql-client
    ```

## Скопировать данные из таблицы {#copy}

Чтобы скопировать данные из таблицы в файл, выполните команду:

```bash
psql "host=c-<идентификатор кластера>.rw.{{ dns-zone }} \
    port={{ port-mgp }} \
    sslmode=verify-full \
    dbname=<имя БД> \
    user=<имя пользователя> \
    target_session_attrs=read-write" \
    -c "\copy (SELECT * FROM <имя таблицы>) to stdout (DELIMITER '<символ_разделителя>')" \
    >> <имя локального файла>
```

## Заполнить таблицу данными {#write}

{% note info %}

Таблица для заполнения должна быть создана заранее. Количество столбцов и типы данных в локальном файле должны совпадать с параметрами таблицы {{ mpg-name }}.

{% endnote %}

Чтобы заполнить таблицу данными из локального файла, выполните команду:

```bash
cat <имя локального файла> | \
psql "host=c-<идентификатор кластера>.rw.{{ dns-zone }} \
    port={{ port-mgp }} \
    sslmode=verify-full \
    dbname=<имя БД> \
    user=<имя пользователя> \
    target_session_attrs=read-write" \
    -c "COPY <имя таблицы> FROM stdin (DELIMITER '<символ_разделителя>')"
```
