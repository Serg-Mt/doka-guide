---
title: "Универсальный селектор"
description: "Как выбрать все элементы на странице? И при чём тут лоботомированная сова?"
authors:
  - solarrust
editors:
  - tachisis
keywords:
  - звёздочка
  - лоботомированная сова
related:
  - css/class-selector
  - css/specificity
  - css/selector-list
tags:
  - doka
---

## Кратко

Универсальный селектор `*` соответствует абсолютно **любому** тегу, но не включает псевдоэлементы, вроде `::before` и `::after`.

## Пример

Такое CSS-правило, объявленное в начале файла со стилями, установит размер шрифта для **всех элементов** на странице:

```css
* {
  font-size: 2rem;
}
```

## Как пишется

Универсальный селектор очень удобен, если какие-то свойства нужно применить ко всем элементам на сайте.

Некоторые используют универсальный селектор для изменения алгоритма расчёта размеров элементов перед началом вёрстки:

```css
* {
  box-sizing: border-box;
}
```

Учитывайте, что это CSS-правило не будет иметь влияния на псевдоэлементы. Алгоритм расчёта нужно будет менять точечно. Или дополнить селектор, упомянув в нём [`::before`](/css/before/) и [`::after`](/css/after/):

```css
*,
::before,
::after {
  box-sizing: border-box;
}
```

### Комбинированные селекторы

Универсальный селектор можно использовать в комбинированных селекторах, ограничивая его область действия.

Такое CSS-правило применит цвет текста ко всем элементам, вложенным в блок с классом `.preview`:

```css
.preview * {
  color: green;
}
```

Изменим селектор на вложенный, и цвет изменится у всех прямых потомков блока с классом `.preview`:

```css
.preview > * {
  color: green;
}
```

### «Лоботомированная сова»

Можно использовать `*` в [смежном селекторе](/css/combined-selectors/#smezhnye-.element1-.element2), чтобы правило применялось только в случае, если рядом с элементом есть сосед. Например, такое CSS-правило задаст нижний отступ всем элементам при условии, что они не являются единственными детьми своего родителя:

```css
* + * {
  margin-bottom: 15em;
}
```

Такой приём в шутку называют «лоботомированная сова». Можно подробнее почитать о способах его использования в статье «[Аксиоматический CSS и лоботомированные совы](https://frontender.info/axiomatic-css-and-lobotomized-owls/)».

## Подсказки

💡 Не стоит злоупотреблять универсальным селектором. Есть вероятность столкнуться с необходимостью постоянно переопределять заданные с его помощью свойства.