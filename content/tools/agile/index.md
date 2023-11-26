---
title: "Методологии разработки и Agile"
description: "Что такое гибкие методологии и почему про них так много говорят? Зачем вообще нужны методологии разработки?"
authors:
  - igorkamyshev
contributors:
  - furtivite
  - matiesha
editors:
  - tachisis
related:
  - tools/code-style
  - tools/version-control
  - tools/technical-debt
tags:
  - article
---

## Кратко

Компаниям важно быстро проверять гипотезы — отбрасывать неверные и развивать валидные. Процесс разработки программ постоянно изменяется, чтобы лучше соответствовать этим требованиям. Сейчас очень популярны **гибкие (agile)** методологии. Они концентрируются на человеческом отношении, результате и быстрой доставке фич конечным пользователям. Главные ценности:

- люди и взаимодействие важнее процессов и инструментов;
- работающий продукт важнее исчерпывающей документации;
- сотрудничество с клиентом важнее согласования условий контракта;
- готовность к изменениям важнее следования изначальному плану.

## Классический подход

До распространения гибких методологий типичный процесс разработки программы всегда выглядел примерно одинаково. Заказчик составлял всеобъемлющее техническое задание для команды разработки — сотни и тысячи страниц текста — которое описывало финальный результат в мельчайших подробностях. Команда называла срок, когда все будет готово (обычно годы) и начинала работу.

<aside>

🤓 Часто этот подход называют методом _водопада_ — процесс разработки выглядит как поток, последовательно проходящий фазы анализа требований, проектирования, реализации, тестирования, интеграции и поддержки.

</aside>

Этот процесс, по сути, был калькой с процессов других областей — строительства, создания электроники, производства. Но у него было несколько серьёзных проблем:

- Сроки срывались. Чем длиннее срок, тем сложнее его соблюдать. В итоге сроки часто срывались, это вызывало конфликтные ситуации и вредило бизнесу.
- Продукт оказывался устаревшим. За годы разработки бизнес-ландшафт может сильно измениться, и финальный продукт окажется уже никому не нужным.
- Вносить правки было сложно. Из-за требования строго формализировать техническое задание, внести что-то новое в него было сложно — даже мелкая правка требовала всего процесса согласований, что может занять больше времени, чем её реализация.

![Принципиальное устройство классического подхода](images/waterfall.png)

В середине 1990-х годов в индустрии сформировалось мнение, что сфера разработки программ отличается от других инженерных областей своей динамичностью — одно дело изменить формат выгрузки документов из бухгалтерской программы, и совсем другое изменить количество опор железнодорожного моста. Значит процессы разработки программ можно упростить — не пытаться описать все варианты заранее, а двигаться к цели и вносить изменения по мере необходимости.

В феврале 2001 года 17 независимых экспертов в области управления разработкой опубликовали [«Манифест гибкой разработки программного обеспечения»](https://agilemanifesto.org/iso/ru/manifesto.html). Основные принципы, описанные в документе:

1. Наивысший приоритет — удовлетворение потребностей клиента благодаря регулярной и ранней поставке ценного программного обеспечения.
1. Изменение требований приветствуется, даже на поздних стадиях разработки.
1. Работающий продукт следует выпускать как можно чаще, с периодичностью от пары недель до пары месяцев.
1. На протяжении всего проекта разработчики и представители бизнеса должны ежедневно работать вместе.
1. Над проектом должны работать мотивированные профессионалы. Чтобы работа была сделана, создайте условия, обеспечьте поддержку и полностью доверьтесь им.
1. Непосредственное общение является наиболее практичным и эффективным способом обмена информацией как с самой командой, так и внутри команды.
1. Работающий продукт — основной показатель прогресса.
1. Инвесторы, разработчики и пользователи должны иметь возможность поддерживать постоянный ритм бесконечно.
1. Постоянное внимание к техническому совершенству и качеству проектирования повышает гибкость проекта.
1. Простота — искусство минимизации лишней работы — крайне необходима.
1. Самые лучшие требования, архитектурные и технические решения рождаются у самоорганизующихся команд.
1. Команда должна систематически анализировать, как улучшить эффективность, и соответственно корректировать стиль своей работы.

Это положило начало бурному развитию гибких методологий. Сейчас почти все IT-компании придерживаются принципов гибкой разработки программ.

## Методологии

Agile (читается «эджайл») — набор принципов и ценностей, описанных в манифесте. На основе этих принципов создано много разных фреймворков и систем, два самых популярных — SCRUM и Kanban.

### SCRUM

SCRUM (читается «скрам») — один из самых популярных гибких методов управления проектами. Впервые он был описан в 1986 году, но стал широко применяться только в начале 2000-х.

Основа метода — _спринт_ — контейнер для всех событий и составляющих элементов скрама. Спринт — это одна итерация разработки продукта с жёстко заданной длительностью (от 1 до 4 недель), результатом которой является готовая часть продукта (_инкремент_). Подразумевается, что инкремент можно отправить в релиз.

Спринт — это будто быстрый жизненный цикл проекта, включающий в себя _планирование_ (Sprint planning), всю работу над инкрементом (анализ, разработку, тестирование), короткие дейли (встречи или созвоны для синхронизации команды), демонстрацию продукта заказчику (Sprint review) и ретроспективу (Sprint retrospective) для решения проблем и улучшения работы в команде.

Задачи на создание или улучшение продукта находятся в _бэклоге_ (Product backlog) — упорядоченном списке всех возможных требований. В бэклог попадают не только бизнес-задачи, но и [технический долг](/tools/technical-debt/). _Владелец продукта_ (Product owner) постоянно обновляет, дополняет список и определяет приоритет задач. При планировании команда обсуждает и выбирает задачи на спринт, создавая бэклог спринта (Sprint backlog). Если во время спринта какую-либо задачу нужно уточнить, команда встречается с владельцем продукта для прояснения требований (Backlog refinement).

Смысл многократных обсуждений с владельцем продукта и внутри команды в том, чтобы при необходимости быстро поменять стратегию и отреагировать на изменения от заказчика. С помощью дейли команда понимает, где находится по отношению к запланированной цели. А на _демо_ (Review) команда часто и напрямую может получать фидбек от заказчика и оперативно изменить очерёдность или состав задач по горячим следам.

SCRUM — это не набор митингов и правил, а в первую очередь образец эффективного взаимодействия между людьми, нацеленный на регулярную, быструю и качественную поставку продукта. Скрам основан на ценностях (открытость, уважение, фокус, коммитмент, смелость), которые находят отражение во взаимодействии между людьми. Руководство по скраму (Scrum Guide) можно найти на официальном сайте фреймворка — [Scrum.org](https://www.scrum.org/)

Многие команды считают SCRUM излишне нагруженным и модифицируют его под свои нужды — берут одни концепции и отказываются от других. Другие наоборот следуют всем правилам и часто нанимают (или обучают) специального человека (_Scrum master_), который помогает команде научиться и наиболее эффективно взаимодействовать по скраму.

### Kanban

Канбан появился сильно раньше, чем другие гибкие методологии. Его придумали в Toyota в 1960-х годах и изначально применяли к производству автомобилей. С начала 2000-х канбан перекочевал в индустрию разработки программ и применяется многими командами.

Канбан подходит командам, в которых каждая задача должна пройти несколько людей. Например, над фичей для сайта должен сначала поработать дизайнер, потом разработчик, потом тестировщик.

![Пример канбан-доски](images/kanban.png)

При использовании канбана любой разработчик из команды может брать любые задачи из колонки «Готово к разработке» и делать их, любой дизайнер может брать любые задачи из колонки «Готово к дизайну» и делать их. Обычно накладываются ограничения на количество задач в работе для одного человека.

Использование канбана позволяет легко искать «бутылочные горлышки» в процессе разработки — если задачи скапливаются на этапе «Готово к разработке», значит, это и есть узкое место всей команды. С другой стороны, канбан обеспечивает прозрачность прогресса проекта для всей команды.

## Не серебряная пуля

Важно понимать, что Agile — это не серебряная пуля. Многим компаниям и командам не подходят гибкие методологии. Любой метод управления проектами должен отвечать потребностям бизнеса и удовлетворять команду. Иногда оказывается, что для конкретного проекта больше подходит классический способ управления — составление чёткой технической документации и разработка согласно этому документу. Для некоторых команд подходит только часть принципов гибкой разработки, и это тоже абсолютно нормально.

До сих пор классический подход очень популярен в заказной разработке — клиент платит за результат. Но, с другой стороны, многие студии заказной разработки внутри используют элементы гибких методологий. Например, называют клиенту диапазон цен и выставляют финальный счёт по факту потраченного времени.

В продуктовой разработке сегодня редко встретишь классический подход. Компании слишком заинтересованы в быстрой доставке продукта и гибкости результата.

<aside>

🤣 В последнее время, слово «Agile» стало в большей степени маркетинговым термином, чем идеологией. Сейчас сложно найти вакансию, в тексте который не было бы описано, как важны гибкие методологии для компании. Часто оказывается, что процессы внутри построены совсем не по гибким методологиям.

</aside>