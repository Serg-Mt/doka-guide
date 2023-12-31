---
title: "`aria-braillelabel`"
description: "Атрибут для имени элемента, которое преобразуется в шрифт Брайля."
authors:
  - doka-dog
related:
  - a11y/aria-label
  - a11y/aria-labelledby
  - a11y/aria-attrs
tags:
  - doka
  - placeholder
---

## Кратко

[Глобальное свойство](/a11y/aria-attrs/#globalnye-atributy) из [WAI-ARIA](/a11y/aria-intro/#specifikaciya). Оно добавляет доступное имя для элемента, которое преобразуется в шрифт Брайля.

На это свойство похоже [`aria-label`](/a11y/aria-label/). Главная разница в том, что `aria-label` нужно для скринридеров, а `aria-braillelabel` — для [дисплеев Брайля](https://ru.wikipedia.org/wiki/%D0%91%D1%80%D0%B0%D0%B9%D0%BB%D0%B5%D0%B2%D1%81%D0%BA%D0%B8%D0%B9_%D0%B4%D0%B8%D1%81%D0%BF%D0%BB%D0%B5%D0%B9).

<aside>

👶 Это атрибут из [черновика ARIA 1.3](https://w3c.github.io/aria/). Он пока плохо поддерживается, так что сейчас его лучше не использовать.

</aside>

## Как пишется

Добавьте к любому тегу `aria-braillelabel` со значением в виде [символов из Брайля](https://en.wikipedia.org/wiki/Braille_Patterns) или других символов. Обратите внимание, что их нельзя смешивать. Также значение атрибута не должно совпадать с доступным именем элемента. К примеру, со значением `aria-label` или текста внутри тега.

Используйте `aria-braillelabel` только тогда, когда доступное имя плохо описывает элемент для пользователей дисплеев Брайля. Этот атрибут помогает правильно локализовать текст в некоторых ситуациях.

## Как понять

_Доступное имя_ или просто _имя элемента_ — это краткое название элемента, которое выводит дисплей Брайля при взаимодействии пользователя с интерфейсом.
