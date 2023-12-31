## Имена файлов и пути

Путь является неотъемлемой частью имени файла. Абсолютным (полным) именем файла называется путь от корневой директории, относительным — путь от текущей (рабочей) директории. В одной директории не может быть файлов с одинаковым именем.

Относительное имя файла удобно использовать. Можно поместить нужные какой-то программе или проекту файлы в одну директорию, можно использовать структуру поддиректорий для удобства организации и использования дискового пространства. При переносе всей директории на другой носитель или компьютер, проект останется в рабочем состоянии. Относительные пути, как правило, практически не зависят от операционной системы и конкретного компьютера, если вы работаете внутри какой-то директории. Но надо помнить, что относительное имя файла всегда преобразуется в абсолютное при обращении в нему.

В зависимости от операционной системы и файловой системы именование файла обладает рядом особенностей.

### Браузер и имена файлов в Интернете

Абсолютное имя может включать в себя ряд параметров:

- протокол или способ доступа (`https`, `ftp`, `file` и др.);
- имя или адрес компьютера, узла сети (`wikipedia.org`, `192.168.0.1`, `\\MYCOMPUTER`, `SYS:` и др.);
- устройство хранения, диск (`C:`, `/`, `SYSLIB` и др.);
- путь к директории (`/usr/bin`, `\TEMP`, `[USR.LIB.SRC]` и др.);
- собственно имя файла, которое может содержать его расширение (`.txt`, `.exe`, `.COM` и др.).

В строке адреса мы всегда указываем путь к конкретному файлу, ничего более. В Интернете есть части абсолютного имени, которые подставляются по умолчанию. Если вы введёте в строку адреса браузера сайт `example.com`, браузер скорее всего сначала автоматически подставит протокол по умолчанию `https`. Окончание абсолютного имени файла в адресной строке браузера зависит от технологии, которая используется для отображения контента страницы. Если страницу полностью формирует сервер (рендеринг на стороне сервера), то при запросе он может вернуть значение, например, `index.html` для абсолютного пути. В браузере по умолчанию часто не показывается конечный файл, поэтому вы можете и не увидеть, что это `index.html`. Если рендеринг происходит на стороне клиента (в браузере), то адрес может быть сформирован динамически и не всегда имеет конечный файл. Это происходит из-за специального [API](/tools/api/) браузера — History API. В этом режиме адресная строка используется для отображения виртуального файла. По сути, запуская такое веб-приложение, вы как будто загружаете файл в оперативную память.

### Операционная система Windows

Абсолютное имя файла включает в себя букву логического диска, после которой обязательно идёт двоеточие и обратная косая черта (back slash) `:\`. Затем через символ `\` перечисляются все поддиректории. В конце указывается имя файла. Чтобы указать путь с пробелами необходимо пользоваться кавычками. Например, скопировать файл можно так:

```bash
copy "c:\directory\my file name" "d:\another directory\my new file name"
```

В именах каталогов и файлов в Windows сохраняется регистр строк, используемый в момент их создания. Но, например, при поиске файла или копировании регистр не будет иметь значения, поскольку в файловой системе Windows регистр букв по умолчанию не учитывается. Есть [способ](https://github.com/vandread666/GhacksFiles/blob/master/Kelly/dontprettypath.reg) обойти это ограничение для некоторых версий Windows.

При проектировании работы веб-приложения необходимо учитывать переносимость — ваше приложение в идеале должно работать на большинстве операционных систем. Формировать имя файла нужно очень осторожно: в некоторых операционных системах используются файловые системы, в которых для имён файлов запрещены некоторые символы. Например, для Windows следующие символы запрещены:

- `\` — разделитель подкаталогов;
- `/` — разделитель ключей командного интерпретатора;
- `:` — отделяет букву диска или имя альтернативного потока данных;
- `*` — заменяющий символ (маска «любое количество любых символов»);
- `?` — заменяющий символ (маска «один любой символ»);
- `"` — используется для указания путей, содержащих пробелы;
- `<` — перенаправление ввода;
- `>` — перенаправление вывода;
- `|` — обозначает конвейер;
- `+` — конкатенация.

В Windows есть ограничение на длину абсолютного имени файла, которая не может больше 260 символов. При этом первые три символа используются для буквы диска и служебного разделителя `:\`, а последний символ имеет значение `<NUL>`. Оставшиеся 256 символов используются непосредственно для имени. Начиная с Windows 10, ограничение [было снято](https://docs.microsoft.com/ru-ru/windows/win32/fileio/maximum-file-path-limitation?tabs=cmd#enable-long-paths-in-windows-10-version-1607-and-later), но всегда необходимо помнить о пользователях более ранних версий этой операционной системы.

### Unix-подобные операционные системы

Абсолютное имя файла в Unix-подобных операционных системах всегда начинается со специального символа корневой директории `/` (slash), после которого перечисляются через этот же символ все поддиректории. Если путь начинается не с косой черты, то путь становится относительным. Однако существуют специальные последовательности символов, которые позволяют использовать относительные пути эффективно. Например, символ `.` используется для доступа к текущей директории, а `..` к директории, которая стоит на уровень выше. Чтобы перейти на два уровня вверх, можно использовать такую последовательность: `../../`. Символ `~` в начале относительного имени будет указывать на домашнюю директорию пользователя, которая обычно расположена в директории `/home/username`. Например, можно по-разному указать путь для домашней директории пользователя с именем `username`:

```bash
# Абсолютный путь
/home/username

# Относительный путь из папки /tmp
../home/username

# Если вы работаете от имени пользователя username
~

# Эквивалент
~/../../home/username
```

В большинстве Unix-подобных операционных систем, имена файлов и директорий зависят от регистра букв. Например, файлы с именами `File1` и `file1` — это разные файлы. Если необходимо указать пробел в имени файла или директории, можно использовать кавычки или символ `\` перед пробелом. Например, следующие пути эквивалентны:

```bash
'~/super project/script.sh'
"~/super project/script.sh"
~/super\ project/script.sh
```

В именах файлов UNIX-подобных операционных систем запрещён символ `/` и символ конца строки `\0`.

### Расширение имени файла

Расширение имени файла часто используется для идентификации формата файла. Это нужно в основном для пользователя и простой фильтрации, сортировки или группировки имён файлов. Например, файл `image.png` является картинкой, `movie.avi` — видеофайлом, а файл `readme.txt` — текстовым документом. И мы можем это узнать, не просматривая атрибуты файла. Сам тип файла при этом задаётся в атрибутах файла, расширение имени файла — это лишь инструмент для быстрого (визуального) определения типа файла. Расширение файла помогает не только нам, но и менеджеру запуска приложений. Он может автоматически определить целевую программу, для которой предназначен тот или иной файл.

Есть и специализированные расширения. Например, файлы с расширениями `.com` и `.exe` в Windows являются исполняемыми файлами (программами), `.ini` — описанием конфигурации приложения, `.bat` — скриптом для терминала (набором команд, выполняемых последовательно), `.dll` — является динамической библиотекой и содержит функции, которые могут вызывать программы «на лету». В Unix-подобных системах `.sh` используется для скриптов в терминале, `.conf` — для конфигурации приложения, а исполняемые файлы (программы), как правило, не имеют расширения.

## Структура директорий в Linux

Во многих Linux-системах можно встретить каталоги `/etc`, `/home`, `/usr/bin` и прочие. В конце января 2004 года был принят [стандарт Filesystem Hierarchy Standard (FHS)](https://wiki.linuxfoundation.org/lsb/fhs), согласно которому в корневой директории Linux-системы должны находиться поддиректории со стандартными именами. Более того, тип данных (файлов), которые могут находится в той или иной директории регламентирован. Стандарт определяет следующие директории в корневой директории для следующих задач:

| Директория  | Символ                                                                         |
|:------------|:-------------------------------------------------------------------------------|
| `/bin`      | Файлы основных команд (утилит)                                                 |
| `/boot`     | Неизменяемые файлы, необходимые для загрузки системы                           |
| `/dev`      | Файлы устройств                                                                |
| `/proc`     | Системные файлы                                                                |
| `/sys`      | Подсистема диагностики и управления операционной системы (аналог `/proc`)      |
| `/etc`      | Файлы конфигурации системы на данном компьютере                                |
| `/home`     | Домашние директории пользователей                                              |
| `/lib`      | Основные разделяемые библиотеки и модули ядра                                  |
| `/lib<alt>` | Основные разделяемые библиотеки для альтернативных форматов исполняемых файлов |
| `/mnt`      | Точка монтирования для временно подключаемых файловых систем                   |
| `/root`     | Домашний каталог суперпользователя root                                        |
| `/opt`      | Дополнительные пакеты программного обеспечения                                 |
| `/sbin`     | Основные системные исполняемые файлы                                           |
| `/tmp`      | Временные файлы                                                                |
| `/usr`      | Иерархия второго уровня                                                        |
| `/var`      | Переменные данные                                                              |

Если в операционной системе файлы размещены по стандарту, это позволяет предсказать поведение операционной системы. Плюсом является то, что при переходе от одной операционной системы на базе Linux к другой пользователю легко ориентироваться в подобной файловой структуре. Для программиста стандартное расположение файлов позволяет организовать автоматическое взаимодействие между разными компонентами системы.

Однако практически ни один из дистрибутивов Linux не следует стандарту полностью. И сам стандарт продолжает развиваться. Разработчики операционных системы из семейства Unix игнорируют данный стандарт в пользу поддержки собственных.
