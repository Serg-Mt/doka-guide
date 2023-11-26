---
title: "`.toString()`"
description: "Метод преобразует объект в строковое представление."
authors:
  - nlopin
related:
  - js/string
  - js/console-log
  - js/ref-type-vs-value-type
tags:
  - doka
---

## Кратко

Метод `toString()` преобразует объект в строковое представление. Метод автоматически вызывается JavaScript, когда объект нужно представить в текстовом виде.

Если метод не переопределён, то он возвращает строку формата `[object тип]`, где _тип_ — это строка, которая уточняет тип объекта. В подавляющем большинстве вы будете видеть вывод `[object Object]`.

## Пример

```js
const book = {
  title: 'JavaScript: the good parts',
  author: 'Douglas Crockford'
}

console.log(`Сейчас читаю ${book}`)
// Сейчас читаю [object Object]
```

## Как пишется

Метод вызывается без аргументов. Возвращает строковое представление объекта.

## Как понять

Существует соглашение, что метод `toString()` вызывается JavaScript автоматически, если объект находится в контексте, где он должен быть представлен в виде строки. Чаще всего это случаи, связанные с печатью данных на экран или в консоль браузера.

Объекты, в отличие от примитивных типов, сложно преобразовывать в строку. Объект может содержать произвольное количество полей и без программиста непонятно, какие из них важные. Поэтому стандартная реализация метода `toString()` представляет собой заглушку, печатающую `'[object Object]'`.

Многие структуры данных, базирующиеся на объекте [`Object`](/js/object/), содержат собственные реализации этого метода. Например, [`Number` преобразует число в строку в указанной системе счисления](/js/number-tostring/), а массив выводит список элементов через запятую.

### Переопределение стандартной реализации

Стандартная реализация метода `toString()` не даёт достаточно информации об объекте даже для использования в отладке программы. Программисты могут переопределить метод `toString()`, чтобы выводить необходимые данные.

Если мы работаем в ООП стиле, то классу нужно просто добавить метод `toString()`:

```js
class Book {
  title = ''
  author = ''

  constructor(title, author) {
    this.title = title
    this.author = author
  }

  toString() {
    return `«${this.title}», автор ${this.author}`
  }
}

const book = new Book('Палата №6', 'А. П. Чехов')
console.log(`Читаю ${book}`)
// Читаю «Палата №6», автор А. П. Чехов
```

Если вы предпочитаете работать в функциональном стиле, то придётся создать новый тип объекта и переопределить метод `toString()` в прототипе:

```js
function Book(title, author) {
  this.title = title
  this.author = author
}

Book.prototype.toString = function() {
  return `«${this.title}», автор ${this.author}`
}

const book = new Book('Палата №6', 'А. П. Чехов')
console.log(`Читаю ${book}`)
// Читаю «Палата №6», автор А. П. Чехов
```

Под капотом JavaScript обе реализации идентичны и отличаются только использованным синтаксисом.