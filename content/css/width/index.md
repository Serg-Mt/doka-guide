---
title: "`width`"
description: "Управляем шириной элементов."
authors:
  - solarrust
contributors:
  - skorobaeus
keywords:
  - ширина
  - размер
  - inline-size
related:
  - css/height
  - css/box-model
  - css/box-sizing
tags:
  - doka
---

## Кратко

Свойство `width` отвечает за ширину элемента. С его помощью мы можем увеличивать или уменьшать ширину строчно-блочных (`inline-block`) и блочных (`block`) элементов. На строчные элементы это свойство не будет иметь никакого влияния.

Строчно-блочные (`inline-block`) элементы по умолчанию подстраиваются под ширину контента, лежащего у них внутри.

Блочные (`block`) элементы по умолчанию имеют ширину 100%. Если представить сайт как документ с текстом, то блочный элемент займёт всю строку, на которой стоит.

Кроме фиксированной ширины можно задавать элементу минимальную ширину `min-width` или максимальную ширину `max-width`.

В современном CSS есть логический аналог этого свойства — `inline-size`.

## Пример

```html
<div class="block">Я — блочный элемент!</div>

<div class="inline-block">Я</div>
<div class="inline-block">строчно-блочный</div>
<div class="inline-block">элемент!</div>
```

Не меняем `display` для `.block`, поскольку [`<div>`](/html/div/) уже является блочным:

```css
.block {
  background-color: #2E9AFF;
}

.inline-block {
  display: inline-block;
  background-color: #F498AD;
}
```

<iframe title="Ширина блочного и строчно-блочного элемента" src="demos/default/" height="190"></iframe>

Благодаря фонам можно увидеть, какую ширину имеет каждый из элементов. Элемент с классом `.block` занял всю строку, его ширина равна 100% от ширины родителя. Элементы с классом `.inline-block` подстроились по ширине под контент и встали в одну строку.

Напишем свойство `width` и изменим это стандартное поведение. Ограничим ширину `.block` до половины окна, а каждый элемент `.inline-block` сделаем на всю ширину окна:

```css
.block {
  width: 50%;
  background-color: #2E9AFF;
}

.inline-block {
  width: 100%;
  display: inline-block;
  background-color: #F498AD;
}
```

<iframe title="Ширина строчно-блочного элемента 100%" src="demos/full/" height="280"></iframe>

## Как понять

Свойство `width` позволяет управлять шириной элемента.

## Как пишется

Для фиксированной ширины пишем свойство `width`. Для минимальной ширины — `min-width`. Для максимальной ширины — `max-width`. Эти три свойства можно указывать по отдельности, а также комбинировать для достижения нужного результата.

В качестве значения указываем число и сразу после него без пробела пишем единицу измерения. Ширину можно указывать как в относительных единицах — процентах (`%`), `vw`, `vmin` и так далее, так и в абсолютных единицах — пикселях (`px`), `rem`, `em` и любых других единицах измерения, доступных в вебе.

В данном коде все значения будут рабочими:

```css
selector {
  width: 70%;
  min-width: 320px;
  max-width: 76rem;
}
```

## Подсказки

💡 По умолчанию у блочных (`block`) элементов ширина равна 100%. У строчно-блочных (`inline-block`) элементов ширина равна ширине вложенного контента.

💡 Ширина в процентах рассчитывается от ширины родительского элемента. Если родительский элемент ограничен по ширине, к примеру, 450 пикселями, то у вложенного элемента ширина в 100% будет равна 450 пикселям. То есть 100% от родительского элемента. Если при этом у родителя будут также указаны внутренние отступы ([`padding`](/css/padding/)), то 100% ширины для ребёнка будут равны 450px минус боковые отступы.

💡 Блочный (`block`) элемент занимает всю строку вне зависимости от своей ширины. Оставшееся пространство займёт внешний отступ. Поэтому, ограничивая ширину блочному элементу, не ожидай, что элементы, следующие за ним, встанут с ним в одну строку. Если нужно, чтобы все элементы встали в строку, то нужно менять их с блочных (`block`) на строчно-блочные (`inline-block`).

💡 Ограничив ширину блочного элемента, можно очень просто выровнять его по центру экрана. Для этого пропишем внешний отступ ([`margin`](/css/margin/)) со значениями `0 auto`, где 0 отвечает за отступы сверху и снизу, а ключевое слово `auto` — за боковые отступы.

<iframe title="Выравнивание по центру" src="demos/auto-margin/" height="150"></iframe>

Именно таким образом принято выравнивать контент сайта по центру окна браузера.