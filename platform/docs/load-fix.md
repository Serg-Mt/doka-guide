# Если сайт Доки медленно загружается или не работает совсем

## Коротко

1. Запросите список IP-адресов серверов, на которых крутится зеркало сайта через `nslookup doka.guide`.
2. Проверьте скорость и доступность IP-адресов из пункта 1 — `ping ip-адрес`.
3. Откройте специальный файл с правами администратора — **c:\windows\system32\drivers\etc\hosts** или **/etc/hosts**.
4. Добавьте самый быстрый из IP-адресов в конец файла — `ip-адрес doka.guide www.doka.guide`.
5. Сохраните файл.

## Подробнее

Сайт Доки работает на нескольких серверах. Это сделано, чтобы обеспечить максимальную скорость и распределить нагрузку.

### Запрос списка IP-адресов серверов

Список всех серверов можно получить с помощью команды:

```bash
nslookup doka.guide
```

Это команда запрашивает у ближайшего DNS-сервера список IP-адресов, на которых расположен сайт. DNS-сервер выдаёт список, элементы которого при каждом запросе циклично смещаются на один шаг. На практике это означает, что браузер загружает сайт с разных серверов.

Очередной сервер может быть расположен далеко и близко к пользователю. Работу сайта можно ускорить, используя ближайший сервер. Это можно сделать, прописав у себя на компьютере «связку» между доменным именем и IP-адресом. Это поможет и в том случае, если один из IP-адресов попал в чёрный список интернет-провайдера пользователя.

### Проверить скорость и доступность сервера

Для выбора сервера нужно проверить список IP-адресов и скорость доступа командой:

```bash
ping 123.123.123.123
```

Вместо `123.123.123.123` подставляйте IP-адреса из списка. Сервер с наименьшем временем ответа, скорее всего, и будет лучшим решением. Не забывайте также время от времени проверять список IP-адресов.

### Открыть нужный файл

Список таких «связок» прописывается в специальном файле. Местоположение для разных операционных систем отличается:

- Windows NT, 2000, XP, 2003, Vista, 7, 8, 10, 11 — **c:\windows\system32\drivers\etc\hosts**;
- Linux, Unix, BSD — **/etc/hosts**;
- macOS — **/private/etc/hosts** или **/etc/hosts**

Для изменения необходимо открыть файл от имени администратора (или `sudo`).

### Прописать связку

Дообавьте в конец файла следующую строчку:

```bash
123.123.123.123 doka.guide www.doka.guide
```

Вместо `123.123.123.123` подставьте самый близкий из доступных серверов.

