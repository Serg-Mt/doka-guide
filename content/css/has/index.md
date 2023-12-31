---
title: "`:has()`"
description: "Уникальный селектор, позволяющий стилизовать родителя при наличии конкретного ребёнка."
authors:
  - realetive
contributors:
  - wonder-sma
editors:
  - tachisis
keywords:
  - псевдокласс
related:
  - css/pseudoclasses
  - css/specificity
  - css/combined-selectors
tags:
  - doka
---

## Кратко

Функция-псевдокласс `:has()`позволяет уточнить основной селектор дополнительным. Это единственный способ выбрать элемент на основе дочернего или соседнего элемента посредством CSS.

<aside>

⚠️ Этот псевдокласс только в 2022 году начал получать поддержку современных браузеров. Пока он поддерживается не всеми браузерами. [Следим за обновлениями](https://caniuse.com/css-has).

</aside>

## Пример

Применяем стили ко всем ссылкам, которые содержат изображения:

```css
a:has(img) {
  /* Стили */
}
```

Стили применятся только к такому `<dt>`, за которым сразу следует элемент `<dd>`:

```css
dt:has(+ dd) {
  /* Стили */
}
```

## Как пишется

`selector1` — необязательный селектор (если не указан — правило применится ко всем подходящим элементам). Аргумент `selector2` в `:has()` описывает селектор относительно своей точки отсчёта — `selector1`:

```css
selector1:has(selector2) {
  /* Стили */
}
```

Если `.class` — валидный селектор, а `#top` — нет, то `selector` будет уточнён за счёт `.class`:

```css
selector:has(.class, #top) {
  /* Стили */
}
```

## Как понять

Функция-псевдокласс `:has()` принимает один или несколько селекторов любой сложности в качестве аргумента. В отличие от `:is()` и `:where()` правило применится только к тому селектору, который был описан **до** `:has()`

## Подсказки

💡 Использование псевдокласса `:has()` влияет на [специфичность](/css/specificity/) целевого селектора, т. е. при расчёте [веса](/css/specificity/) целевого селектора учитывается селектор, переданный в аргументах.

💡 Переданные через запятую селекторы `selector1:has(selector2, selector3)` браузер проверяет аналогично: `selector2` **или** `selector3`. Допустим, что в примере ниже оба переданных в `:has()` селектора являются действительными. Тогда `selector` будет уточнён за счёт `#link`, так как [вес](/css/specificity/) `#link` больше веса `.content`:

```css
selector:has(.content, #link) {
  /* Стили */
}
```

💡 Есть возможность соединять селекторы. Такую запись браузер интерпретирует аналогично: `selector2` **и** `selector3`. В случае валидности селекторов `selector2` и `selector3`, браузер применит стили к `selector1`:

```css
selector1:has(selector2):has(selector3) {
  /* Стили */
}
```

💡 Псевдокласс `:has()` не может быть вложен в другой `:has()`, так как это может привести к циклическим запросам при выполнении поиска селектора.

💡 Нельзя использовать псевдоэлементы в качестве аргументов в `:has()`, а также в качестве целевого селектора.
