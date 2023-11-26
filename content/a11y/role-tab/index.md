---
title: "`tab`"
description: "Как правильно и доступно наверстать вкладки?"
authors:
  - tatianafokina
contributors:
  - skorobaeus
related:
  - a11y/aria-roles
  - a11y/role-tablist
  - a11y/role-tabpanel
tags:
  - doka
---

## Кратко

[Самостоятельная роль виджета](/a11y/aria-roles/#roli-vidzhetov) из [WAI-ARIA](/a11y/aria-intro/#specifikaciya), которая означает вкладку.

В HTML нет эквивалента для роли `tab`.

## Пример

```html
<button
  role="tab"
  aria-controls="tabpanel-1"
  aria-selected="true">
  Тапиры
</button>
```

<iframe title="button с ролью tab" src="demos/tabs/" height="350"></iframe>

При фокусе на вкладке [скринридер](/a11y/screenreaders/) прочтёт её примерно так: «Тапиры, выбранная вкладка, одна из двух». Некоторые скринридеры не объявляют количество вкладок.

## Как пишется

Элемент с ролью `tab` обязательно должен находится внутри другого с [ролью `tablist`](/a11y/role-tablist/).

Роль `tab` можно задать любому тегу, но лучше всего подходят [`<button>`](/html/button/), [`<div>`](/html/div/) или [`<span>`](/html/span/). `<button>` — интерактивный элемент, который по умолчанию поддерживает навигацию с клавиатуры. На кнопке можно сделать фокус с помощью <kbd>Tab</kbd> и нажать на неё пробелом или <kbd>Enter</kbd>. Эти клавиши должны поддерживать и вкладки.

Если решили использовать для вкладок `<button>`, нужно немного поколдовать над фокусом. Перемещаться между вкладками принято с помощью стрелок, так что для `<button role="tab">` пригодится приём с отрицательным и положительным значениями [`tabindex`](/html/global-attrs/#tabindex). Для активной вкладки добавьте `tabindex="0"`, а для неактивной `tabindex="-1"`. Так при нажатии <kbd>Tab</kbd> попадём на первую или ранее выбранную вкладку, а к другим вкладкам так уже переместиться не сможем. Не забудьте отслеживать события и переключать значение `tabindex` с помощью JavaScript.

`tab` обязательно должна быть связана с содержимым из [`tabpanel`](/a11y/role-tabpanel/). Для этого задайте атрибут [`aria-controls`](/a11y/aria-controls/) для `tab` и добавьте `id` с таким же значением к `tabpanel`.

```html
<button
  role="tab"
  aria-controls="tabpanel-1"
>
  Тапиры
</button>
<div
  role="tabpanel"
  id="tabpanel-1"
>
  <p>Травоядные животные с коротким хоботом, которые живут в лесу.</p>
</div>
```

Также у элемента с ролью `tab` обязательно должен быть атрибут [`aria-selected`](/a11y/aria-selected/). Он указывает на то, выбрана вкладка или нет. У выбранной вкладки должен быть `aria-selected="true"`, у неактивной вкладки или без явно указанного атрибута — `aria-selected="false"`. Так что, тут опять не обойтись без JavaScript.

```html
<!-- Выбранная вкладка -->
<button
  role="tab"
  aria-selected="true"
>
  Тапиры
</button>

<!-- Невыбранная, неактивная вкладка -->
<button
  role="tab"
  aria-selected="false"
  tabindex="-1"
>
  Ламантины
</button>
```

Когда можно одновременно выбрать несколько вкладок и у `tablist` есть [`aria-multiselectable`](/a11y/aria-multiselectable/), задайте `tab` атрибут [`aria-expanded`](/a11y/aria-expanded/), когда её содержимое видно. Если вкладка неактивна, у неё должно стоять противоположное значение `aria-expanded="false"`.

Кроме обязательных атрибутов, элементам с ролью `tab` можно задавать все [глобальные ARIA-атрибуты](/a11y/aria-attrs/#globalnye-atributy) и некоторые [атрибуты виджетов](/a11y/aria-attrs/#atributy-vidzhetov):

- [`aria-disabled`](/a11y/aria-disabled/);
- [`aria-haspopup`](/a11y/aria-haspopup/);
- [`aria-posinset`](/a11y/aria-posinset/);
- [`aria-setsize`](/a11y/aria-setsize/).

Внутри `tab` лучше всего размещать текст. Если в названии вкладки иконка, не забудьте её подписать с помощью [`aria-label`](/a11y/aria-label/) или добавить скрытую подпись с классом [`.visually-hidden`](/a11y/content-hidden/#klassy-.visually-hidden-.sr-only-.off-screen).

Если вложите внутрь `tab` другой тег, например, [`<р>`](/html/p/), у параграфа сбросится его встроенная роль и заменится на [`presentation`](/a11y/role-presentation-none/). Поэтому скринридер прочтёт только текстовое содержимое. Так увидите код вы:

```html
<div role="tab">
  <p>Я вкладка</p>
</div>
```

А так скринридер:

```html
<div role="tab">Я вкладка</div>
```

### Поддержка клавиатуры

Когда пользователь перешёл к `tablist` с помощью <kbd>Tab</kbd>, в фокусе должна оказаться первая активная вкладка с ролью `tab`.

Между горизонтальными вкладками перемещаемся стрелками влево и вправо, а вертикальными — вверх и вниз. Когда на вкладке сделан фокус, она может раскрываться либо автоматически, либо после нажатия на <kbd>Enter</kbd> или пробел.

Если со вкладкой связано выпадающее меню, то рекомендуют поддерживать для его открытия сочетание клавиш <kbd>Shift + F10</kbd>.

Дополнительно, но не обязательно, можно добавить поддержку <kbd>Home</kbd> для возврата к первой вкладке, <kbd>End</kbd> для перехода к последней вкладке, <kbd>Delete</kbd> для закрытия текущей вкладки и перехода к следующей или предыдущей в зависимости от количества вкладок.

## Как понять

Обычно визуально вкладки располагаются либо над их содержимым, либо сбоку от него.

При клике или фокусе на вкладке появляется связанное с ней содержимое.