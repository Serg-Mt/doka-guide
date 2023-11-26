---
title: "`aria-busy`"
description: "Свойство, которое просит скринридеры немного подождать. Тут, вообще-то, очередь!"
authors:
  - tatianafokina
contributors:
  - skorobaeus
keywords:
  - a11y
  - ARIA
  - live region
  - интерактивная область
  - ajax
  - новостная лента
related:
  - a11y/aria-live
  - a11y/aria-attrs
  - a11y/aria-atomic
tags:
  - doka
---

## Кратко

[Состояние изменяющихся областей](/a11y/aria-attrs/#atributy-izmenyayushchihsya-oblastey) из [WAI-ARIA](/a11y/aria-intro/#specifikaciya). Делает часть страницы изменяющейся или «живой» областью. `aria-busy` указывает на то, что элемент сейчас изменяется, поэтому вспомогательная технология должна подождать и пока ничего не рассказывать.

## Пример

```html
<h2>Пока вас не было</h2>
<section
  role="feed"
  aria-live="polite"
  aria-busy="true"
>
  <article>
    <!-- Содержание поста -->
  </article>
</section>
```

## Как пишется

Добавьте к любому тегу или [ARIA-роли](/a11y/aria-roles/) `aria-busy` с одним из двух значений:

- `false` (по умолчанию) — без изменений.
- `true` — все изменения завершились и о них можно рассказать.

`aria-busy` используют в сложных компонентах. Например, в фиде (ленте новостей) как в социальных сетях. В этом случае на время загрузки задайте фиду `aria-busy="true"`, а после окончания удалите атрибут. Так [скринридеры](/a11y/screenreaders/) расскажут об изменениях только тогда, когда пользователь нажмёт кнопку «Обновить ленту» и все элементы загрузятся. Также можно переключать значения атрибута с `true` на `false`. В обоих случаях скринридеры вас поймут.

Чтобы удалить или добавить атрибут, понадобятся методы `.setAttribute()` или `.removeAttribute()`.

В примере посты в блоке [с ролью `feed`](/a11y/role-feed/) загружаются с разными интервалами. Чтобы дождаться, пока всё загрузится, установим `aria-busy="true"` на нужный интервал времени, а потом удалим. В реальных ситуациях обычно отслеживают окончание загрузки нового содержимого страницы. Дополнительно добавим [`aria-atomic="true"`](/a11y/aria-atomic/), чтобы скринридеры точно прочитали все новые посты.

```html
<section
  role="feed"
  aria-live="polite"
  aria-atomic="true"
>
  <article>
    <a href="#user1">Дока</a>
    <p>Сегодня я съел невероятно вкусный морковный торт.</p>
  </article>
  <article>
    <a href="#user2">Стрела в колене</a>
    <p>Продам гараж, куплю машину.</p>
  </article>
  <article class="post">
    <a href="#user3">Исторический вестник</a>
    <p>Как часто вы думаете про Римскую империю?</p>
  </article>
</section>
```

<iframe title="Фид с атрибутом aria-busy" src="demos/feed/" height="540"></iframe>

<video controls width="640">
  <source src="video/aria-busy.mp4" type="video/mp4">
  <track
    label="Russian"
    kind="subtitles"
    srclang="ru"
    src="video/closed-captions.vtt"
  >
</video>

## Как понять

_Изменяющаяся область_ — это область страницы, в которой содержимое обновляется из-за внешних событий или действий пользователей. Благодаря изменяющимся областям вспомогательные технологии узнают об обновлениях на странице и автоматически рассказывают о них пользователям.