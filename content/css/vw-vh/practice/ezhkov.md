🛠 В операционных системах Linux и Windows использование `100vw` может осложняться тем фактом, что вертикальный скроллбар является частью вьюпорта и уменьшает фактическую ширину страницы. Но ширина вьюпорта остаётся неизменной. Поэтому, если есть вертикальный скролл, то задание ширины блока `100vw` вызовет появление горизонтального скролла. На macOS при настройках по умолчанию этот эффект не наблюдается, потому что там скролл располагается НАД содержимым страницы, а не рядом.

Чтобы всегда видеть скролл и возможные связанные с ним проблемы у пользователей других операционных систем, измените настройки по пути «Оформление» → «Показывать полосы прокрутки».

<iframe title="Шапка и слайд на всю высоту" src="../demos/header-block/" height="600"></iframe>

В ОС Linux, Windows и Mac OS с изменёнными настройками скроллбаров в этом примере будет наблюдаться горизонтальный скролл.

🛠Относительные единицы измерения прекрасно подходят для адаптивной вёрстки, а если учесть, что на мобильных устройствах скролл находится НАД содержимым страницы, у нас вообще нет никаких проблем с этими единицами.
