---
title: "`inset`"
description: "Указываем место позиционированному элементу."
authors:
  - doka-dog
contributors:
  - bellabzhu
keywords:
  - отступы со всех сторон
  - отступы позиционированного элемента
  - направление письма
related:
  - css/position
  - css/writing-mode
  - css/position-sticky
tags:
  - doka
  - placeholder
---

## Кратко

Свойство `inset` заменяет собой сразу четыре свойства: `top`, `right`, `bottom` и `left`. Позволяет указать смещение [позиционированного элемента](/css/position/) сразу со всех четырёх сторон.

`inset` является шорткатом для свойств:

- `inset-block-start`
- `inset-block-end`
- `inset-inline-start`
- `inset-inline-end`

## Пример

```css
div {
  position: absolute;
  inset: 10px 15px 20px;
}
```

## Как пишется

Можно указать от одного до четырёх значений через пробел. Значения применяются к четырём сторонам соответственно, по часовой стрелке, начиная с верхнего края. Они могут быть в px, em, rem и %. Если указывать `left` и `right` в процентах, то они считаются от ширины элемента, если `top` и `bottom`, то от высоты.

Часто бывает, что нужно задать позиционированному элементу 0 в качестве значения для свойств `top`, `right`, `bottom` и `left`. Можно написать на старый лад:

```css
div {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
```

Свойство `inset` позволяет сэкономить три строчки кода:

```css
div {
  position: absolute;
  inset: 0;
}
```

### Особенности

Логическое свойство означает, что позиционирование опирается не на стороны окна браузера, а на [направление письма](/css/writing-mode/) и будет меняться вместе с ним.

Свойство `inset` входит в спецификацию [CSS Logical Properties and Values](https://drafts.csswg.org/css-logical/), но смещение происходит физически и поэтому оно **не является** логическим свойством.

Но этой особенностью обладают его собратья:

- `inset-block-start`
- `inset-block-end`
- `inset-inline-start`
- `inset-inline-end`

На практике логические свойства дают нам удобный способ работы с отступами. Представим, что мы работаем над международным сайтом, в котором интерфейс может переключаться между русским и арабским языками. В них различается направление письма, поэтому при вёрстке мы прописали поведение отступов для каждого элемента:

```css
.text {
  margin-right: 20px;
}

.text:dir(rtl) {
  margin-right: 0;
  margin-left: 20px;
}
```

Такой подход сильно перегрузит код, поэтому лучше использовать логические свойства:

```css
.text {
  inset-inline: 0 20px;
}
```
