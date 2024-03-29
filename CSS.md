# Вопросы:

1. [В чём специфика CSS селекторов, и как она работает?](#1-в-чём-специфика-css-селекторов-и-как-она-работает)
2. [В чём разница между сбросом и нормализацией CSS (`reset.css` и `normalize.css`)?](#2-в-чём-разница-между-сбросом-и-нормализацией-css-resetcss-и-normalizecss)
3. [Что такое `float`?](#3-что-такое-float)
4. [Опишите, что такое `z-index`?](#4-опишите-что-такое-z-index)
5. [Что такое Block Formatting Context (BFC), и как он работает?](#5-что-такое-block-formatting-context-bfc-и-как-он-работает)
6. [Какие есть техники по clearfix?](#6-какие-есть-техники-по-clearfix)
7. [Объясните, как работают CSS спрайты, и как их можно внедрить.](#7-объясните-как-работают-css-спрайты-и-как-их-можно-внедрить)
8. [Как можно исправить проблемное отображение элементов, связанное с разницей в браузерах?](#8-как-можно-исправить-проблемное-отображение-элементов-связанное-с-разницей-в-браузерах)
9. [Какие можно использовать методы для использования страниц с ограниченными возможностями?](#9-какие-можно-использовать-методы-для-использования-страниц-с-ограниченными-возможностями)
10. [Какие есть способы спрятать контент визуально, но при этом оставить его доступным для скринридеров?](#10-какие-есть-способы-спрятать-контент-визуально-но-при-этом-оставить-его-доступным-для-скринридеров)
11. [Какие есть системы разметки в CSS?](#11-какие-есть-системы-разметки-в-css)
12. [Использовали ли вы медиа-запросы для различающегося отображения страницы на разных устройствах?](#12-использовали-ли-вы-медиа-запросы-для-различающегося-отображения-страницы-на-разных-устройствах)
13. [Вы знакомы со стилизацией SVG?](#13-вы-знакомы-со-стилизацией-svg)
14. [К каким другим устройствам можно обратиться в медиа-запросе помимо screen?](#14-к-каким-другим-устройствам-можно-обратиться-в-медиа-запросе-помимо-screen)
15. [Что нужно учитывать для описания эффективного CSS?](#15-что-нужно-учитывать-для-описания-эффективного-css)
16. [В чём преимущества и недостатки CSS препроцессоров?](#16-в-чём-преимущества-и-недостатки-css-препроцессоров)
17. [Опишите, что больше нравится и не нравится в CSS препроцессорах.](#17-опишите-что-больше-нравится-и-не-нравится-в-css-препроцессорах)
18. [Как можно подключить нестандартные шрифты?](#18-как-можно-подключить-нестандартные-шрифты)
19. [Опишите, как браузер находит подходящие элементы для CSS селектора](#19-опишите-как-браузер-находит-подходящие-элементы-для-css-селектора)
20. [Опишите, для чего существуют псевдо-элементы.](#20-опишите-для-чего-существуют-псевдо-элементы)
21. [Опишите box model в CSS, и что учитывается в этом понятии для рендера.](#21-опишите-box-model-в-css-и-что-учитывается-в-этом-понятии-для-рендера)
22. [Опишите `box-sizing` и его возможные значения](#22-опишите-box-sizing-и-его-возможные-значения)
23. [Опишите возможные значения свойства `display` с примерами использования.](#23-опишите-возможные-значения-свойства-display-с-примерами-использования)
24. [Опишите разницу между `inline` и `inline-block`](#24-опишите-разницу-между-inline-и-inline-block)
25. [В чём разница между возможными значениями свойства `position`?](#25-в-чём-разница-между-возможными-значениями-свойства-position)
26. [Какие CSS-библиотеки использовали?](#26-какие-css-библиотеки-использовали)
27. [Пользовались ли флексами или CSS Grid?](#27-пользовались-ли-флексами-или-css-grid)
28. [Можете ли объяснить разницу между разработкой адаптивного сайта и mobile-first сайта?](#28-можете-ли-объяснить-разницу-между-разработкой-адаптивного-сайта-и-mobile-first-сайта)
29. [В чём разница между отзывчивостью и адаптивностью?](#29-в-чём-разница-между-отзывчивостью-и-адаптивностью)
30. [Какие есть техники для работы с экранами с высокой плотностью пикселей?](#30-какие-есть-техники-для-работы-с-экранами-с-высокой-плотностью-пикселей)

## 1. В чём специфика CSS селекторов, и как она работает?

Браузер определяет, какие стили применять к элементу, в зависимости от специфики правил CSS. Предположим, браузер уже определил правила, соответствующие конкретному элементу. Среди всех правил приоритетными выявляются правила по четырём значениям (a, b, c, d):
- a - используются ли встроенные стили. Если элемент имеет встроенные стили (атрибут у тега `style`), то a = 1, иначе 0;
- b - количество селекторов ID;
- c - количество классов, атрибутов и селекторов псевдоклассов;
- d - количество тегов и селекторов псевдоэлементов.

Полученные значения нужно не суммировать, а рассматривать как массив, последовательно, слева направо. При этом можно учитывать не количество баллов, а просто их наличие. То есть 0,1,0,0 будет приоритетнее 0,0,10,0 или 0,0,10,10.

Если правило обладают равной специфичностью (к примеру, оба селектора имеют 0,1,0,0), то применяться будет то правило, которое было объявлено в CSS последним.

В проектах необходимо стараться писать все CSS объявления на одном уровне специфичности. Это можно добиться с помощью методологий (К примеру, БЭМ) или инструментов (CSS модули или styled components). При этом одну методологию и/или инструмент стоит использовать в проекте повсеместно, без премешиваний.

[Источник 1](https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/), [Источник 2](https://www.sitepoint.com/web-foundations/specificity/)

## 2. В чём разница между сбросом и нормализацией CSS (`reset.css` и `normalize.css`)?

Сброс полностью обнуляет все стили. После сброса нужно определять все необходимые стили заново.

Нормализация же приводит все стили в разных браузеров к одному виду, чтобы стандартные элементы выглядели в разных браузерах одинаково.

Пример: сброс сделает все заголовки (`<h1>`, `<h2>`, `<h3>` и т.д.) в одном стиле. Нормализация же оставит примерный вид заголовков, но при этом они будут выглядеть в разных браузерах одинаково.

Сброс стоит применять в проектах с весьма необычным дизайном, который трудно определить под базовые стайлгайды. Нормализацию же необходимо использовать во всех остальных проектах.

## 3. Что такое `float`?

https://www.frontendinterviewhandbook.com/ru/css-questions/#describe-floats-and-how-they-work

## 4. Опишите, что такое `z-index`?

https://www.frontendinterviewhandbook.com/ru/css-questions/#describe-z-index-and-how-stacking-context-is-formed

## 5. Что такое Block Formatting Context (BFC), и как он работает?

https://www.frontendinterviewhandbook.com/ru/css-questions/#describe-block-formatting-context-bfc-and-how-it-works

## 6. Какие есть техники по clearfix?

https://www.frontendinterviewhandbook.com/ru/css-questions/#what-are-the-various-clearing-techniques-and-which-is-appropriate-for-what-context

## 7. Объясните, как работают CSS спрайты, и как их можно внедрить.

https://www.frontendinterviewhandbook.com/ru/css-questions/#explain-css-sprites-and-how-you-would-implement-them-on-a-page-or-site

## 8. Как можно исправить проблемное отображение элементов, связанное с разницей в браузерах?

- Можно загружать отдельную библиотеку CSS-стилей в зависимости от используемого браузера. Для этого можно использовать `User-Agent`, бэкенд или логику на фронтенде для загрузки определённого .css файла в зависимости от браузера.
- Используйте CSS-библиотеки типа Bootstrap, в которых подобные проблемы уже решены.
- Используйте `reset.css` или `normalize.css`.
- Используйте autoprefixer.
- Используйте postcss для транспиляции современного синтаксиса в более безопасный код.
- Используется `@supports`.

## 9. Какие можно использовать методы для использования страниц с ограниченными возможностями?

- Graceful degradation - практика создания приложения для современных браузеров с обеспечением его работы в старых браузерах (использование полифиллов).
- Прогрессивное улучшение - практика создания приложения с базовой функциональностью и добавлением функциональных улучшений, когда эти улучшения поддерживаются браузером.
- Можно использоватиь caniuse.com, чтобы убедиться в поддержке функций всеми популярными браузерами.
- Autoprefixer можно использовать для автоматической вставки префиксов для свойств для разных браузеров.
- Обнаружение работы функций с помощью modernizr.
- Использование `@supports`.

## 10. Какие есть способы спрятать контент визуально, но при этом оставить его доступным для скринридеров?

- `width: 0;` и `height: 0;`;
- `position: absolute` и `left: -99999px;`;
- `text-indent: -9999px` (работает только для текста).

## 11. Какие есть системы разметки в CSS?

- Табличная вёрстка;
- вёрстка на флоатах (`float: left`);
- флексбоксы;
- вёрстка на `display: inline-block` элементах;
- CSS Grid.

## 12. Использовали ли вы медиа-запросы для различающегося отображения страницы на разных устройствах?

https://www.frontendinterviewhandbook.com/ru/css-questions/#have-you-used-or-implemented-media-queries-or-mobile-specific-layoutscss

## 13. Вы знакомы со стилизацией SVG?

Да, существует несколько способов окрашивания фигур (включая указание атрибутов объекта) с помощью встроенного CSS, встроенного раздела CSS или внешнего файла CSS. Большинство SVG, которые вы найдете в Интернете, используют встроенный CSS, но у каждого типа есть свои преимущества и недостатки.

Свойства стилизации:
- `x` - позиция по X;
- `y` - позиция по Y;
- `width` - ширина;
- `height` - высота;
- `stroke` - цвет обводки;
- `fill` - цвет заливки;
- `fill-opacity` - уровень непрозрачности заливки;
- `stroke-opacity` - уровень непрозрачности обводки.

## 14. К каким другим устройствам можно обратиться в медиа-запросе помимо screen?

- `all` - все устройства, которые работают со страницей;
- `print` - принтеры;
- `speech` - скринридеры, озвучивающие текст;
- `screen` - компьютеры, телефоны, планшеты и т.д.

## 15. Что нужно учитывать для описания эффективного CSS?

- Не использовать селекторы разного веса, максимально уменьшать сложность селекторов (для этого можно использовать методологии типа БЭМ или инструменты типа CSS модулей).
- Нужно по максимуму избегать изменения значений тех свойств, которые могут вызвать перерисовку.

## 16. В чём преимущества и недостатки CSS препроцессоров?

### Преимущества:
- Код становится более поддерживаемым.
- Легче писать вложенные селекторы.
- Переменные для темизации. Они могут быть вынесены в отдельный файл для использования между проектами.
- Миксины.
- SCSS фичи типа циклов, списков, карт могут упростить жизнь.
- Разделение кода на отдельные файлы.

### Недостатки:
- Необходим инструментарий для компиляции.
- На компиляцию нужно время.
- CSS на выхлопе может быть не совсем поддерживаемым.

## 17. Опишите, что больше нравится и не нравится в CSS препроцессорах.

https://www.frontendinterviewhandbook.com/ru/css-questions/#describe-what-you-like-and-dislike-about-the-css-preprocessors-you-have-used

## 18. Как можно подключить нестандартные шрифты?

https://www.frontendinterviewhandbook.com/ru/css-questions/#how-would-you-implement-a-web-design-comp-that-uses-non-standard-fonts

## 19. Опишите, как браузер находит подходящие элементы для CSS селектора

Сначала браузер находит то, что справа селектора, а затем проходит по уточнениям налево.

Пример с селектором `p span`: сначала браузер находит все `span`, затем проверяет всех его родителей, кто из них является `p`. 

Нужно всегда стараться уменьшить количество вложенностей в селекторах (идеал - 1), чтобы ускорить этот проецсс.

## 20. Опишите, для чего существуют псевдо-элементы.

https://www.frontendinterviewhandbook.com/ru/css-questions/#describe-pseudo-elements-and-discuss-what-they-are-used-for

## 21. Опишите box model в CSS, и что учитывается в этом понятии для рендера.

https://www.frontendinterviewhandbook.com/ru/css-questions/#explain-your-understanding-of-the-box-model-and-how-you-would-tell-the-browser-in-css-to-render-your-layout-in-different-box-models

## 22. Опишите `box-sizing` и его возможные значения

Возможные значения:
- `content-box`: по умолчанию в браузерах, ширина и высота считаются только для области контента.
- `border-box`: ширина и высота включает в себя всё, вплоть до обводки.

## 23. Опишите возможные значения свойства `display` с примерами использования.

- `none`: элемент полностью скрывается, будто его нет в DOM.
- `block`: блочный элемент, автоматически переносится на новую строку, элементы после него тоже переносятся на новую строку.
- `inline`: строчный элемент, ведёт себя как теги типа `b`, `em` и т.д. Подходит для изменения внешнего вида текста, и всё.
- `inline-block`: блочный элемент, но при этом не будет переноситься на новую строку и оставлять после себя новую.
- `table`: поведение таблицы.
- `table-row`, `table-cell`: поведение строки и ячейки таблицы соответственно.
- `list-item`: поведение элемента `li`.
- `flex`: блочный элемент + внутри флексы.
- `inline-flex`: `inline-block` + внутри флексы.
- `grid`: CSS Grid внутри.
- `contents`: делает вид, что этого элемента нет в DOM, но при этом его контент отображается как ни бывало, то есть удаление только одного узла DOM.

## 24. Опишите разницу между `inline` и `inline-block`

https://www.frontendinterviewhandbook.com/ru/css-questions/#whats-the-difference-between-inline-and-inline-block

## 25. В чём разница между возможными значениями свойства `position`?

https://www.frontendinterviewhandbook.com/ru/css-questions/#whats-the-difference-between-a-relative-fixed-absolute-and-statically-positioned-element

## 26. Какие CSS-библиотеки использовали?

https://www.frontendinterviewhandbook.com/ru/css-questions/#what-existing-css-frameworks-have-you-used-locally-or-in-production-how-would-you-changeimprove-them

## 27. Пользовались ли флексами или CSS Grid?

https://www.frontendinterviewhandbook.com/ru/css-questions/#have-you-played-around-with-the-new-css-flexbox-or-grid-specs

## 28. Можете ли объяснить разницу между разработкой адаптивного сайта и mobile-first сайта?

https://www.frontendinterviewhandbook.com/ru/css-questions/#can-you-explain-the-difference-between-coding-a-website-to-be-responsive-versus-using-a-mobile-first-strategy

## 29. В чём разница между отзывчивостью и адаптивностью?

Отзывчивость - сайт корректно отображается абсолютно на любом разрешении (с адекватными минимумами и максимумами).

Адаптивность - сайт корректно отображается на устройствах с типичными разрешениями экрана.

## 30. Какие есть техники для работы с экранами с высокой плотностью пикселей?

- `<img>` с `sizes` и `srcset`;
- `@media` с `min-resolution`, `max-resolution` и `device-pixel-ratio`.
## Источники

- [Frontend Interview Handbook](https://www.frontendinterviewhandbook.com/ru/css-questions/)