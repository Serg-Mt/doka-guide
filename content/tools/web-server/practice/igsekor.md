## Простой веб-сервер

Самый простой способ запустить веб-сервер, если уже уставлена платформа [Node.js](/tools/nodejs/), использовать `http-server`. Достаточно установить этот веб-сервер глобально:

```bash
npm install --global http-server
```

Теперь, нужно зайти в любую директорию, в которой находится собранный сайт или отдельный HTML-файл, и запустить веб-сервер командой:

```bash
http-server
```

В браузере вы можете видеть свой сайт по адресу [http://localhost:8080](http://localhost:8080) или [http://127.0.0.1:8080](http://127.0.0.1:8080). Это специальный адрес локального сервера на вашем компьютере.

Ваш локальный сервер не будет видно в интернете, но вы можете открыть его на устройствах, подключённых к одной и той же локальной сети, например, по Wi-Fi. Для этого нужно воспользоваться IP-адресом, который ваш роутер выдал компьютеру, на котором запущен сервер.

```bash
Available on:
  http://127.0.0.1:8080
  http://192.168.1.56:8080
```

Первый адрес доступен только для компьютера с сервером, второй — для всех устройств сети.

## Если надо больше

`browser-sync` удобно использовать и при разработке, и при тестировании проектов, потому что это избавляет разработчиков от необходимости повторять рутинные действия вручную на нескольких экранах или устройствах. При взаимодействии пользователя с сайтом на одном из устройств все действия будут немедленно воспроизводиться и на других устройствах. Например, если вы прокрутили страницу на смартфоне, она прокрутится и на других устройствах в сети. То же случится, если вы перейдёте на другую страницу сайта или будете взаимодействовать с формами.

`browser-sync` устанавливается глобально командой:

```bash
npm install --global browser-sync
```

После установки необходимо перейти в директории, где находится сайт, и выполнить команду:

```bash
browser-sync start --server
```

Но эти веб-серверы используются для локальной разработки. Сайты и сервисы используют веб-серверы, которые способны выдерживать большие нагрузки (большое количество запросов, сессий соединения, потоков данных и так далее) и модули для обработки различных запросов. О наиболее известных написаны статьи на сайте:

- «[Веб-сервер Nginx](/tools/nginx-web-server/)»;
- «[Веб-сервер Apache](/tools/apache-web-server/)».