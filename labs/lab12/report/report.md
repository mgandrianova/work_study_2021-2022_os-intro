---
## Front matter
title: "Отчёт по лабораторной работе № 12"
subtitle: "*дисциплина:*Операционные системы"
author: "Андрианова Марина Георгиевна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучить основы программирования в оболочке ОС UNIX. Научиться писать более
сложные командные файлы с использованием логических управляющих конструкций
и циклов.

# Выполнение лабораторной работы

1. Создала файл s1.sh(рис.1) и написала соответствующий скрипт(рис.2): командный файл, реализующий упрощённый механизм семафоров. Командный файл должен в течение некоторого времени t1 дожидаться освобождения ресурса, выдавая об этом сообщение, а дождавшись его освобождения, использовать его в течение некоторого времени t2<>t1, также выдавая информацию о том, что ресурс используется соответствующим командным файлом (процессом). 

![Создание файла s1.sh](image/1.png){ #fig:001 width=70% }

![Пишем командный файл s1.sh](image/2.png){ #fig:002 width=70% }

Проверяем работу написанного скрипта (команда "./s1.sh 2 5"), предварительно добавив право на исполнение файла(команда "chmod +x s1.sh"). Скрипт работает корректно(рис.3).

![Проверка скрипта](image/3.png){ #fig:003 width=70% }

После этого изменяем скрипт так, чтобы его можно было выполнять в нескольких терминалах(рис.4). Проверила его работу(команда "./s1.sh 3 5 Ожидание > /dev/pts/2 &" и команда "./s1.sh 3 5 Ожидание > /dev/tty2"). При этом ни одна из команд не сработала, выводя сообщение "Отказано в доступе". При этом скрипт работает корректно(рис.5).

![Изменение командного файла s1.sh](image/4.png){ #fig:004 width=70% }

![Проверка скрипта](image/5.png){ #fig:005 width=70% }

2. Реализовала команду man с помощью командного файла. Изучила содержимое каталога /usr/share/man/man1:сначала перешла в него командой "cd /usr/share/man/man1",а затем вывела его содержимое(команда "ls")(рис.6). В нем находятся архивы текстовых файлов, содержащих справку по большинству установленных в системе программ и команд. Каждый архив можно открыть командой less сразу же просмотрев содержимое справки. Командный файл должен получать в виде аргумента командной строки название команды и в виде результата выдавать справку об этой команде или сообщение об отсутствии справки, если соответствующего файла нет в каталоге man1.

![Переход в каталог и вывод его содержимого](image/6.png){ #fig:006 width=70% }

Для данной задачи я создала файл s2.sh(рис.7) и написала соответствующий скрипт(рис.8).

![Создание файла s2.sh](image/7.png){ #fig:007 width=70% }

![Пишем командный файл s2.sh](image/8.png){ #fig:008 width=70% }

Проверяем работу написанного скрипта (команды "./s2.sh touch" и "./s2.sh rm"), предварительно добавив право на исполнение файла(команда "chmod +x s2.sh")(рис.9). Скрипт работает корректно(рис.10,рис.11).

![Предоставление права на исполнение и проверка скрипта](image/9.png){ #fig:009 width=70% }

![Результат после введения команды "./s2.sh touch"](image/10.png){ #fig:010 width=70% }

![Результат после введения команды "./s2.sh rm"](image/11.png){ #fig:011 width=70% }

3. Создала файл s3.sh(рис.12) и написала соответствующий скрипт(рис.13). Используя встроенную переменную $RANDOM, написала командный файл, генерирующий случайную последовательность букв латинского алфавита. Учтём, что $RANDOM выдаёт псевдослучайные числа в диапазоне от 0 до 32767. Добавила право на исполнение файла(команда "chmod +x s3.sh")(рис.14). Скрипт работает корректно(рис.14).

![Создание файла s3.sh](image/12.png){ #fig:012 width=70% }

![Пишем командный файл s3.sh](image/13.png){ #fig:013 width=70% }

![Проверка скрипта](image/14.png){ #fig:014 width=70% }

# Выводы

Я изучила основы программирования в оболочке ОС UNIX и научилась писать более сложные командные файлы с использованием логических управляющих конструкций и циклов.

# Контрольные вопросы:

1). while [$1 != "exit"]

В данной строчке допущены следующие ошибки:
не хватает пробелов после первой скобки (и перед второй скобкой)
выражение $1 необходимо взять в “”, потому что эта переменная может содержать пробелы.
Таким образом, правильный вариант должен выглядеть так: while [ “$1”!= "exit" ]

2). Чтобы объединить несколько строк в одну, можно воспользоваться несколькими способами:

Первый:
VAR1="Hello,"
VAR2="World"
VAR3="$VAR1$VAR2"
echo "$VAR3"
Результат: Hello, World

Второй:
VAR1="Hello, "
VAR1+=" World"
echo "$VAR1"
Результат: Hello, World

3). Команда seq в Linux используется для генерации чисел от ПЕРВОГО до ПОСЛЕДНЕГО шага INCREMENT.
Параметры:
seq LAST: если задан только один аргумент, он создает числа от 1 до LAST с шагом шага, равным 1. Если LAST меньше 1, значение is не выдает.
seq FIRST LAST: когда заданы два аргумента, он генерирует числа от FIRST до LAST с шагом 1, равным 1. Если LAST меньше FIRST, он не выдает никаких выходных данных.
seq FIRST INCREMENT LAST: когда заданы три аргумента, он генерирует числа от FIRST до LAST на шаге INCREMENT . Если LAST меньше, чем FIRST, он не производит вывод.
seq -f «FORMAT» FIRST INCREMENT LAST: эта команда используется для генерации последовательности в форматированном виде. FIRST и INCREMENT являются необязательными.
seq -s «STRING» ПЕРВЫЙ ВКЛЮЧЕНО: Эта команда используется для STRING для разделения чисел. По умолчанию это значение равно /n. FIRST и INCREMENT являются необязательными.
seq -w FIRST INCREMENT LAST:эта команда используется для выравнивания ширины путем заполнения начальными нулями. FIRST и INCREMENT являются необязательными.
4). Результатом данного выражения $((10/3))будет 3, потому что это целочисленное деление без остатка.
5). Отличия командной оболочки zsh от bash:
В zsh более быстрое автодополнение для cdс помощью Тab
В zsh существует калькулятор zcalc, способный выполнять вычисления внутри терминала
В zsh поддерживаются числа с плавающей запятой
В zsh поддерживаются структуры данных «хэш»
В zsh поддерживается раскрытие полного пути на основе неполных данных
В zsh поддерживается замена части пути
В zsh есть возможность отображать разделенный экран, такой же как разделенный экран vim

6). for((a=1; a<= LIMIT; a++)) синтаксис данной конструкции верен, потому что, используя двойные круглые скобки, можно не писать $ перед переменными ().
7). Преимущества скриптового языка bash:
Один из самых распространенных и ставится по умолчаниюв большинстве дистрибутивах Linux, MacOS
Удобное перенаправление ввода/вывода
Большое количество команд для работы с файловыми системами Linux
Можно писать собственные скрипты, упрощающие работу в Linux

Недостатки скриптового языка bash:
Дополнительные библиотеки других языков позволяют выполнить больше действий
Bash не является языком общего назначения
Утилиты, при выполнении скрипта, запускают свои процессы, которые, в свою очередь, отражаются на быстроте выполнения этого скрипта
Скрипты, написанные на bash, нельзя запустить на других операционных системах без дополнительных действий.
