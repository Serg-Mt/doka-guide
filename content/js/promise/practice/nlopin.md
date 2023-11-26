🛠 Промис становится «разрешённым» или «завершённым», когда он переходит из состояние `pending` в `fulfilled` или `rejected`. Состояние завершённого промиса нельзя поменять.

```js
const promise = new Promise(function (resolve, reject) {
  resolve() // в этот момент промис переходит в состояние fulfilled
  reject() // этот вызов игнорируется, потому что промис разрешился
})
```

🛠 Всегда завершайте использование промиса методом `catch()`. Если этого не сделать, то следующие промисы в цепочке перестанут работать, и такую ошибку получится поймать только через специальный обработчик – `unhandledrejection`.

🛠 Время от времени нужно выполнить несколько асинхронных функций и дождаться, пока все выполнятся или одна из них завершится ошибкой. Для этого существует статический метод [`Promise.all()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) (он возвращает промис).

🛠 Если нужно дождаться пока несколько асинхронных функций завершатся (без разницы, успешно или ошибкой), используйте метод [`Promise.allSettled()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled) (вернёт промис).