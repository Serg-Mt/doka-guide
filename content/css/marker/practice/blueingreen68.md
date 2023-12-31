🛠 К сожалению, из-за того, что на данный момент свойств для изменения маркерного поля достаточно мало, его не получится как-то по-особому стилизовать. Например, в первой демке в начале доки фактически не используется псевдоэлемент `::marker`. Синие маркеры в виде квадратиков сделаны в псевдоэлементе `::before` через [`position: absolute`](/css/position/) с указанием свойств [`width`](/css/width/) и [`heigth`](/css/height/) и свойства [`background-color`](/css/background-color/), данные свойства псевдоэлемент `::marker` не поддерживает.

🛠 Используя псевдоэлемент `::marker`, маркеры можно стилизовать отдельно от самой контентной части элемента `<li>`:

```css
li {
  color: #2e9aff;
}

li::marker {
  color: #f498ad;
  font-weight: bold;
}
```

Или вы можете стилизовать маркер конкретного элемента списка, например, комбинируя псевдоэлемент `::marker` с псевдоклассом [`last-of-type`](/css/nth-of-type/):

```css
li::marker {
  color: aquamarine;
}

li:last-of-type::marker {
  color: tomato;
}
```

🛠 Взаимодействовать можно не только с маркерами элементов списка `<ul>`. Также можно влиять и на элементы списка `<ol>` при помощи [счётчиков в CSS](/css/css-counters/).

