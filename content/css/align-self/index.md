---
title: "`align-self`"
description: "Если элемент не хочет жить по правилам родителя, то его можно выровнять отдельно."
baseline:
  - group: flexbox
    features:
      - css.properties.align-self.flex_context
      - css.properties.align-self.flex_context.baseline
      - css.properties.align-self.flex_context.stretch
  - group: grid
    features:
      - css.properties.align-self.grid_context
authors:
  - solarrust
editors:
  - tachisis
keywords:
  - выравнивание элемента
related:
  - css/justify-content
  - css/flexbox-guide
  - css/grid-guide
tags:
  - doka
---

## Кратко

При помощи этого свойства можно выровнять один или несколько элементов по вертикальной оси иначе, чем задано у родительского элемента.

## Пример

В этом примере у родителя задано выравнивание вложенных элементов по верхнему краю родителя. А для элемента с классом `.item` мы задаём выравнивание по нижнему краю.

```css
.container {
  display: flex;
  align-items: flex-start;
}

.item {
  align-self: flex-end;
}
```

## Как понять

Иногда требуется все флекс-элементы выровнять по вертикальной оси одним образом, но один или несколько из них выровнять иначе.

## Как пишется

Все значения этого свойства совпадают со значениями свойства [`align-items`](/css/align-items/).

## Подсказки

<aside>

📝 Полный список свойств флексбоксов можно посмотреть в [гайде по flexbox](/css/flexbox-guide/).

</aside>
