---
title: "Как настроить доступ по SSH на GitHub"
description: "Настройте безопасный доступ для работы с репозиториями на GitHub."
authors:
  - igsekor
related:
  - tools/version-control
  - tools/git-cli
  - tools/github-actions
tags:
  - article
---

## Задача

Настроить доступ по протоколу SSH для работы с репозиториями.

## Готовое решение

GitHub позволяет получить доступ к репозиториям по [протоколу SSH](/tools/ssh/) (Secure Socket Shell). Это безопасный способ передачи данных по сети. Для того чтобы настроить доступ, добавьте свой публичный ключ на GitHub. Это делается в несколько шагов.

Сначала нажмите кнопку с иконкой вашего профиля «Open user account menu» в главном меню GitHub. Это последний пункт меню.

![Главное меню GitHub на странице пользователя.](images/top-navigation.png)

В выпадающем меню, которое открывает кнопка, выберите пункт «Settings». Он находится рядом с пунктами «Feature preview» и «GitHub Docs».

![Выпадающее меню с настройками профиля пользователя.](images/choose-settings-in-profile-menu.png)

Откроется новая страница с настройками. В меню со складками выберите «SSH and GPG keys» в разделе «Access».

![Боковая панель с вкладками в профиле пользователя.](images/settings-ssh.png)

В содержимом вкладки найдите и нажмите на ссылку «New SSH key». Она находится рядом с заголовком «SSH keys».

![Содержимое вкладки с информацией о добавлении нового ключа.](images/put-public-key.png)

На открывшейся странице введите название ключа в поле «Title» (на практике можете работать с GitHub с разных компьютеров), сам ключ в поле «Key» и выберите «Authentication Key» (значение по умолчанию) в поле «Key type».

После нажмите на кнопку «Add SSH key», которая находится под формой. Ключ теперь добавлен на GiHub, и вы можете работать с репозиториями по защищённому протоколу.

