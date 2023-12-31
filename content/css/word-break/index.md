---
title: "`word-break`"
description: "Что делать, если слово слишком длинное и не помещается в блок целиком?"
authors:
  - goingtogogo
keywords:
  - разрыв строки
  - перенос текста
  - перенос строки
related:
  - css/overflow-wrap
  - css/hyphens
  - css/white-space
tags:
  - doka
---

## Кратко

Свойство `word-break` определяет, как будет переноситься на новую строку текст при достижении края родительского контейнера.

## Пример

```css
p {
  word-break: normal;
}
```

<iframe title="Очень длинный термин" src="demos/default/" height="300"></iframe>

## Как пишется

- `normal` — значение по умолчанию, длинные слова или строки с неразрывным пробелом не переносятся, даже если выходят за границы родительского блока.
- `break-all` — при достижении границы родительского блока перенос строки будет вставлен между любыми двумя символами.
- `keep-all` — перевод строки не будет использован в тексте на китайском, японском или корейском языках. Для текста на других языках будет применено `normal`.
- `break-word` (устаревшее) — разобьёт текст в любом месте, в том числе внутри слова, при достижении границы контейнера даже если доступен перенос по словам.

<iframe title="Разные значения" src="demos/every/" height="1000"></iframe>

Свойство `word-break` можно глобально задать для всей страницы, добавив его в стили для селектора `body`.

### Особенности переноса текста

Перенос текста в CSS происходит по определённым правилам, которые могут зависеть от языка и заданных CSS стилей (включает свойства `word-break`, `line-break`, [`white-space`](/css/white-space/), [`text-align`](/css/text-align/), [`text-justify`](/css/text-justify/) и [`hyphens`](/css/hyphens/)). Вот некоторые правила из спецификации:

- **Обязательные переносы:** текст обязательно переносится на новую строку, если есть символы перевода строки (например, `\n`).
- **Мягкие переносы:** это такие места, где текст переносится на новую строку, если он не умещается в текущей строке. Сюда относятся пробелы и другие символы-разделители. В некоторых языках между символами могут быть и другие мягкие переносы, которые зависят от языковых правил.
- **Дефисы и слоги:** в алфавитных языках, таких как английский и русский, слова могут быть разбиты на слоги и перенесены с использованием дефиса и языковых правил (кстати, язык определяется по HTML-атрибуту `lang`). Автоматическим переносом слов с использованием дефиса управляет свойство `hyphens`.
- **Особенности языка:** некоторые языки имеют специфические правила переноса текста. В идеографических языках, таких как китайский, и слоговых языках, таких как корейский, перенос слов и разрыв строк происходит в других местах (например, между корейскими иероглифами может быть разрыв, даже если между ними нет пробела).

Когда определены возможные места переноса, подбирается подходящее место, учитывающее заданные стили. В случае с длинными словами, ссылками или другой последовательностью символов, которые не умещаются в одной строке, мы можем указать браузеру, как следует переносить текст, используя свойства `overflow-wrap` и `word-break`.

Также свойство `word-break` играет важную роль в CJK языках (китайский, японский и корейский): значение `word-break: keep-all` запрещает разрывать слова внутри CJK текста, где разрывы строк могут быть нежелательными между определёнными иероглифами.

## На практике

Свойство `word-break: break-all` очень похоже на [`overflow-wrap: break-word`](/css/overflow-wrap/) по своей сути. Однако, есть некоторые различия в их работе.

Свойство `word-break: break-all` позволяет разрывать слова в любом месте, в том числе и в середине слова, чтобы уместить их в контейнере. С одной стороны, это можно привести к трудно читаемому тексту, с другой, такой перенос хорошо подходит для переноса длинных ссылок или, например, строк кода.

Свойство `overflow-wrap: break-word` пришло на смену `word-wrap: break-word`. Оно позволяет переносить длинные слова в любом месте, а не только посередине слова. Это означает, что браузер может добавить перенос слова в любом месте, если это позволяет уместить слово внутри контейнера. Это свойство также сохраняет целостность слов, если они могут поместиться внутри контейнера.

<iframe title="Сравнение word-break и overflow-wrap" src="demos/overflow-wrap/" height="680"></iframe>
