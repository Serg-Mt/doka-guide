---
title: "`::selection`"
description: "Управляем стилями выделенного элемента."
authors:
  - rusakov
editors:
  - tachisis
keywords:
  - ::selection
  - псевдоэлемент
related:
  - css/pseudoelements
  - css/text-shadow
  - css/background-color
tags:
  - doka
---

## Кратко

[Псевдоэлемент](/css/pseudoelements/) `::selection` позволяет применить стили к пользовательскому выделению (например, к выделенному с помощью мыши тексту) и изменить его вид. Это полезно, если вы хотите оформить выделение текста в соответствии с вашим дизайном.

<aside>
⚠️ Этот псевдоэлемент не поддерживается в Safari на iOS.
</aside>

## Пример

Чтобы увидеть `::selection` в действии, выделите текст в демке при помощи курсора мыши или клавиш <kbd>Ctrl A</kbd>.

<iframe title="Пример базовой работы ::selection" src="demos/variants/" height="400"></iframe>

## Как пишется

```css
::selection {
  /* Стили */
}
```

Обратите внимание, что этому псевдоэлементу необходимо двойное двоеточие.

Для Mozilla Firefox версии 61 и ниже нужно использовать [вендорный префикс](/css/vendor-prefixes/):

```css
::-moz-selection {
  /* Стили */
}
```

Можно оформлять отдельные элементы на странице, задав им псевдоэлемент, или можно оформить всю страницу целиком — оставив `::selection` без селектора слева, как показано в примере выше.

Список свойств, которые можно изменять с помощью `::selection`, ограничен:

- [`color`](/css/color/);
- [`background-color`](/css/background-color/);
- шорткат [`text-decoration`](/css/text-decoration/) и отдельные свойства оформления текста;
- `text-emphasis-color`;
- [`text-shadow`](/css/text-shadow/);
- `stroke-color`, `fill-color` и `stroke-width` для SVG.

Все прочие CSS-свойства, написанные внутри правила, будут проигнорированы.
