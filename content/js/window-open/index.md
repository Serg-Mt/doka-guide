---
title: "window.open()"
description: "Открывает ссылку в новом окне, в новой вкладке или в iframe."
authors:
  - tanugladkih
related:
  - html/a
  - tools/url
  - html/iframe
tags:
  - doka
  - placeholder
---

## Кратко

Метод `open()` объекта `window` позволяет открывать ссылки в новом окне, в новой вкладке или в iframe.

## Простой пример

```js
window.open('https://practicum.yandex.ru/');
```

## Как пишется

Метод `open()` имеет три опциональных параметра:

```js
window.open(url, target, windowFeatures);
```

`url` – строка, которая содержит относительный или абсолютный [URL](/tools/url/).

`target` – строка, которая указывает где откроется новое окно. Он может принимать те же значения, что и [атрибут target тега `<a>`](/html/a/): имя окна или одно из ключевых слов `_self`, `_blank`, `_parent`, `_top`.

`windowFeatures` – строка, которая позволяет детально описать, как будет выглядеть новое окно. Опции в строке указываются через запятую в формате `name=value`, для булевых типов значение можно опустить.

Вызвать метод без параметров тоже можно, по умолчанию будет открыта чистая вкладка `about:blank`.

### Значения:

**Числовые:**

_`width` or `innerWidth` / `height` or `innerHeight`_ - определит ширину и высоту содержимого окна включая полосы прокрутки. Минимальное возможное значения - 100px.

_`left` or `screenX` / `top` or `screenY`_ - здесь можно указать расстояние от левой верхней части (или рабочей области) экрана пользователя, на котором откроется окно.

**Булевые:**

_`popup`_ - открывает ссылку в новом окне

_`menubar`_ - отвечает за отображение строки меню

_`toolbar`_ - управляет показом кнопок панели инструментов и панели закладок

_`location`_ - отвечает за показ адресной строки

_`resizable`_ - позволяет включить/выключить возможность пользователям изменять размеры окна

_`scrollbars`_ - отображение полос прокрутки

_`status`_ - отображение строки состояния

_`noopener`_ - помогает повысить безопасность сайта, так как предотвращает доступ открываемого ресурса к текущей странице (через сеанс браузера).
При использовании `noopener` значения второго параметра метода `open()` (кроме `_top`, `_self`, `_parent`), будут обработаны как `_blank`

_`noreferrer`_ - предотвращает передачу информации об исходном ресурсе на целевой. При установке этого значения как `true` `noopener` также становится `true`.

## Примеры использования

```js
window.open("https://ya.ru/", "_self"); // ссылка откроется в текущем окне

window.open("https://ya.ru/", "yandex", "popup"); // ссылка откроется в новом окне, которое примет имя "yandex"

window.open("https://ya.ru/", "_blank", "top=100, left=100, width=400, height=500"); // ссылка откроется в новом окне, величина отступов и размеры окна будут соответствовать указанным
```

## Возможности

Использование метода `open()` позволяет получить ссылку на новое окно и взаимодействовать с ним, например:

```js
const newWindow = window.open("", "new window", "popup");
newWindow.document.write("<p>Hello, World!</p>");
// откроется новое окно с текстом "Hello, World!"
```

## Особенности применения

Авторы MDN рекомендуют использовать метод `open()` в крайних случаях и (никогда!) не прибегать к встроенному (inline) использованию `window.open()`.

```html
<a href='#' onclick='window.open(`any url`)'>  <!-- когда делаете так, где-то плачет котик. Не делайте так -->
```

У метода `open()` есть несколько _недостатков_:

1. многие браузеры блокируют попапы.
1. `open()` решает за пользователя, как именно открыть ссылку. Улучшится ли пользовательский опыт, если чтению контента будут мешать неожиданно всплывающие окна или переходы на новую вкладку (вместо открытия их в фоновом режиме)? Вряд ли.
1. инлайновые значения вызывают неожиданное поведение ссылки при взаимодействии с ней (и не только). Важно и то, что они также передают неправильную семантику скринридерам.

Узнать подробнее можно [ на сайте MDN ](https://developer.mozilla.org/en-US/docs/Web/API/Window/open#accessibility)









