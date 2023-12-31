---
title: "`stroke`"
description: "Управляем цветом и толщиной обводки у SVG."
authors:
  - realetive
keywords:
  - svg-обводка
related:
  - html/svg
  - css/fill
  - css/hover
tags:
  - doka
---

## Кратко

Как и у одноимённого SVG-атрибута, задаёт цвет обводки SVG-элемента. При наличии указанного через CSS или атрибут на этом же SVG-теге свойства `stroke-width` — толщины обводки, которая должна быть больше `0`.

## Пример

```css
.circle {
  stroke: #123456;
}
```

## Как пишется

Свойство соответствует SVG-атрибуту `stroke` и содержит обозначение цвета.

Помимо стандартных форматов: именованного цвета (`orange`, `rebeccapurple` и др.), RGB(A), HEX и HSL(A), `stroke` поддерживает формат ссылки на SVG-элемент, который будет как паттерн заполнять площадь обводки:

```css
.circle {
  stroke: url(#pattern);
}
```

<iframe title="Заливка паттерном" src="demos/pattern/" height="166"></iframe>

## Подсказки

💡 Через CSS-свойство можно управлять цветом обводки SVG-элементов с помощью других возможностей CSS, например, при наведении курсора:

```css
.circle {
  stroke: url(#pattern);
}

.circle:hover {
  stroke: blue;
}
```
