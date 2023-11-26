---
title: "`.textContent`"
description: "Считываем и записываем текстовое содержимое элемента."
authors:
  - windrushfarer
related:
  - js/element-innerhtml
  - js/dom
  - js/element
tags:
  - doka
---

## Кратко

Свойство `textContent` позволяет считывать или задавать текстовое содержимое элемента. Обращение к свойству вернёт строку, которая будет состоять из текстового содержимого всех вложенных элементов, даже если они скрыты с помощью CSS и не видны на экране.

Аналогичной функциональностью, но с некоторыми ограничениями обладает свойство [`innerText`](/js/element-innertext/). Оно работает так же, но не включает в себя скрытые элементы.

## Пример
```html
<section>
  <h1>Заголовок</h1>

  <p>И параграф полезного текста</p>
</section>
```

Обращение к свойству `textContent` тега [`<section>`](/html/section/) весь текст внутри элемента:
```js
const section = document.querySelector('section')
console.log(section.textContent)
// ЗаголовокИ параграф полезного текста

const heading = document.querySelector('h1')
heading.textContent = 'Новый заголовок'
// В результате будет: <h1>Новый заголовок</h1>
```

<iframe title="Element.textContent — Element.textContent — Дока" src="demos/index/" height="850"></iframe>

## Как понять

Для считывания и изменения текстового содержимого браузер предоставляет свойства [`innerText`](/js/element-innertext/) и `textContent`. Запись значения работает идентично для обоих. Значение, которое возвращается при чтении свойств отличается. `textContent` возвращает строку с содержимым **всех** вложенных потомков, вне зависимости от того, скрыты они или нет. `innerText` же возвращает содержимое только видимых элементов.

Свойство может изменить только текстовое содержимое элемента, потому если присвоить строку, содержащую HTML, то она вставится как простой текст и не превратится в реальные DOM-элементы. Для того чтобы вставлять HTML c помощью строки подойдёт свойство [`innerHTML`](/js/element-innerhtml/).

## Как пишется

Обращение к свойству `textContent` вернёт текстовое содержимое элемента. Если внутри элемента находятся дочерние узлы, то результат будет являться конкатенацией вызовов `textContent` для всех этих узлов.

```html
<div>
  <h1>Заголовок</h1>
  <p>Параграф</p>
  <p>Второй параграф</p>
</div>
```

```js
const element = document.querySelector('div')

console.log(element.textContent)
// "ЗаголовокПараграфВторой параграф"
// Так как слова не содержат пробелов, то и в итоговой строке между словами их тоже не будет
```

Чтобы изменить текст в элементе нужно присвоить новое значение в свойство `textContent`.

<aside>

❗️ Установка нового текста с помощью `textContent` полностью удалит всё старое содержимое и запишет новое текстовое значение. Если внутри элемента были другие вложенные потомки, то все они удалятся.

</aside>

```html
<div>
  <h1>Заголовок</h1>
  <p>Параграф</p>
  <p>Второй параграф</p>
</div>
```

```js
const element = document.querySelector('div')
element.textContent = 'Я буду единственным текстом здесь'
```

Больше никакой иконки внутри, только новый текст:

```html
<div>
  Я буду единственным текстом здесь
</div>
```