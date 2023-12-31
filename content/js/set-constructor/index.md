---
title: "Конструктор"
description: "Создаёт экземпляр коллекции `Set`."
authors:
  - nlopin
related:
  - tools/oop
  - js/arrays
  - js/map
tags:
  - doka
---

## Кратко

Вызов конструктора создаёт новую коллекцию [`Set`](/js/set/).

## Как пишется

1️⃣ Если вызывать конструктор без аргументов, тогда созданный `Set` будет пуст:

```js
const emptySet = new Set()
console.log(emptySet.size)
// 0
```

2️⃣ Если при вызове конструктора передать итерируемый объект, то все его уникальные значения будут добавлены в созданную коллекцию:

```js
const filledSet = new Set(['my', 'unique', 'values', 'are', 'unique'])
console.log(filledSet.size)
// 4
```

## Как понять

Коллекция `Set` реализована в [объектно-ориентированной парадигме программирования](/tools/oop/), для создания новой коллекции нужно воспользоваться конструктором (использовать ключевое слово `new`).

Созданные коллекции уникальны и независимы друг от друга.
