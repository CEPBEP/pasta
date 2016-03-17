# Путь HTML/CSS

Это список ссылок и заданий, которые помогут тебе изучить языки HTML/CSS на достаточном уровне. HTML и CSS используется для верстки (создания) веб-страничек — тех самых, которые ты видишь в браузере когда открываешь какой-то сайт. Задания несложные и надо решить их все.

Станешь ли ты полноценным верстальщиком, пройдя этот путь? Скорее нет, чем да. С одной стороны, ты научишься верстать веб-страницы, с другой стороны от верстальщиков в большинстве случаев требуют дополнительно знать язык программирования Javascript (и популярные библиотеки вроде jQuery, jQuery UI). Так что воспринимай это как первую (короткую) половину пути.

Время, требуемое на изучение материала и решение всех заданий зависит от тебя, ориентировочно это занимает от 2 до 8 недель. В конце тебя ждет главное задание — сверстать страницу из макета.

## Что такое HTML

HTML — язык разметки текста. Он позволяет добавить в текст специальные коды-теги (которые выглядят примерно так: `<p>`), которые разбивают его на части и позволяют вставлять дополнительные элементы вроде изображений. Вот пример HTML-кода: 

```html
<h1>Это заголовок</h1>

<p>
    Это абзац текста, в котором содержится 
    <a href="http://google.com/">ссылка на Гугл</a>. 
    После текста идет картинка:
</p>

<img src="http://lorempixel.com/200/150/cats/" alt="Красивая картинка">
```

А вот как этот код отображает браузер ([посмотреть на jsfiddle](http://jsfiddle.net/0bfpmjLu/)). Согласись, пока ничего сложного? Ссылка в теге `img` — это ссылка на картинку.

![Как выглядит пример в браузере](http://i.imgur.com/4lmOu4D.png)

## Что такое CSS

CSS — это язык правил, задающих, как отображаются элементы на странице. Каким шрифтом и цветом написан текст, какие у него поля и отступы от краев страниц и соседних абзацев, каким цветом или изображением закрашен фон. Также CSS задает размеры и расположение блоков на странице. Ты можешь располагать элементы вертикально, горизонтально друг за другом, вынести влево или вправо или поместить в указанном месте страницы. 

Вот пример CSS-правил, которые я применяю к фрагменту HTML кода выше:

```css
/* Элементы <a> (ссылки) имеют желтый фон */
a { background-color: yellow; }

/* Элемент <h1> (заголовок) написан шрифтом Arial (а если его нет в системе, 
    то стандартным шрифтом без засечек, sans-serif) лиловым цветом */
h1 { font-family: Arial, sans-serif; color: purple; }

/* Картинка заключена в черную штрихованную рамку шириной 1 пиксель  */
img { border: 1px dashed black; }
```

И вот как это выглядит в браузере ([посмотреть на jsfiddle](http://jsfiddle.net/jdpjds1d/1/)): 

![Второй пример, HTML и CSS вместе](http://i.imgur.com/UacsApq.png)

## Где можно почитать про HTML и CSS

- Самоучитель HTML4: http://htmlbook.ru/samhtml
- Самоучитель CSS: http://htmlbook.ru/samcss
- Интерактивные уроки: http://htmlacademy.ru/
- Про HTML5: http://htmlbook.ru/html5
- Тонкости позиционирования в CSS: http://softwaremaniacs.org/blog/category/primer/ (читать снизу вверх)
- Подробности про раскладку элементов внутри строки (продвинутый уровень): http://css-live.ru/css/vvedenie-v-inlajnovyj-kontekst-formatirovaniya-ikf-osnovnye-ponyatiya-1-ya-publikaciya-cikla-tajny-css2-1.html
- Картинки, которые можно нарисовать с помощью лишь одного дива: http://habrahabr.ru/company/paysto/blog/251933/ 

После того, как немного изучишь основы, можешь начинать решать задания ниже и параллельно изучать дальше.

Существует 2 версии — HTML4 (старый) и HTML5 (новый). HTML5 по сути расширяет HTML4 так что можешь начать с него.

Не ставь закрывающий слеш в конце тега: `<br />` — такое используется в XHTML и XML, но не используется в HTML. В HTML надо писать `<br>`.

## Какой редактор посоветуешь? 

Любой, кроме блокнота. Sublime Text 3, Notepad++, PhpStorm, TextMate, vim, emacs — любой подойдет. Файлы надо сохранять в кодировке utf-8 **без** BOM.

Есть 2 специальных плагина, которые помогут тебе печатать код гораздо быстрее. Это Emmet для HTML: http://emmet.io/ и Hayaku для CSS: http://hayakubundle.com/ (англ.).

## Как просмотреть и куда выкладывать примеры кода? 

Самый простой способ просмотреть страницу — сохранить код в файл с расширением `.html` и перетащить в окошко браузера. Если же ты хочешь выложить пример в интернет, чтобы все его увидели, используй удобные сервисы (некоторые  позволяют прямо в браузере редактировать код и видеть изменения): 

- http://jsbin.com/
- http://jsfiddle.net/
- http://codepen.io/
- На гитхабе можно использовать github pages: http://pages.github.com/ (англ.) если тебе надо выложить не одиночный файл, а страницу со стилями, скриптами, картинками

## У меня проблемы с кодировкой

- используй тег `<meta charset>` в своем коде
- сохраняй код в кодировке utf-8 без BOM

## Как отлаживать код

В браузеры встроен специальный инструмент для отладки страниц - инспектор. Он открывается нажатием `Ctrl + Shift + I` (в ИЕ надо жать `F12`, в Сафари надо сначала включить инструменты разработчика). Краткий обзор: http://habrahabr.ru/post/143767/

## Задания

Сверстай изображенные на картинках примеры. Если где-то ширина не указана, она должна зависеть от ширины окна браузера или содержащегося в блоке текста (а не быть жестко заданной). Если где-то не указана ширина отступа/полей, ставь 10px. Цвет блоков должен быть как на картинке (чтобы определить цвет, используй функцию «пипетка» в графическом редакторе, или отдельную программу-пипетку). Размер шрифта выбери сам. Серую рамку верстать не надо.

Никогда не используй CSS-селектор «звездочка» и CSS reset.

Перед тем, как сдать задание, проверь, все ли корректно отображается при изменении ширины окошка браузера.

### Задание 1

![1](http://i.imgur.com/Zav7asd.png)

- в этом задании нельзя использовать свойства `position`, `float` или `display` (почему? потому, что без них проще).
- подсказка: чтобы решить это задание, необходимо сначала изучить такие свойства CSS: `width`, `height`, `margin`, `padding`, `border`, `text-align`, `background-color`, `color`, `font`, `line-height`, `font-weight`, `font-style` и боксовую модель: http://htmlbook.ru/samlayout/blochnaya-verstka/blochnaya-model
- подсказка: http://softwaremaniacs.org/blog/2005/08/27/css-layout-flow/
- подсказка: полезно будет почитать про единицы измерения в CSS: http://htmlbook.ru/content/edinitsy-izmereniya

### Задание 2

![2](http://i.imgur.com/WQ0AlXl.png)

- подсказка: в этом задании нельзя использовать свойства `poistion`, `float`, `display` или `width`.
- подсказка: тебе надо изучить CSS-свойства `min-width`, `max-width`, `min-height`, `max-height`

### Задание 3

![3](http://i.imgur.com/9FMuOMt.png)

- из тегов можно использовать только `<em>`
- подсказка: вот таблица с кодами юникодных символов: http://unicode-table.com/ru/ , сердечко ищется поиском по слову «heart», стрелочка по слову «arrow».
- подсказка: символы `<`, `>`, `&` в HTML надо записывать с использованием html entity (HTML-мнемоник).
- подсказка: шрифт — Times New Roman
- подсказка: для решения этой задачи надо почитать про HTML мнемоники (html entities): http://htmlbook.ru/samhtml/tekst/spetssimvoly

### Задание 4

![4](http://i.imgur.com/XzZ1h48.png)

- ширина и высота желтых блоков определяется заключенным в них текстом (то есть не задана жестко). Мы должны иметь возможность поменять числа или добавить еще несколько строчек, не меняя css. У желтых блоков есть поля размером 10px. У синего блока поля размером 10px.
- для переноса строк можно использовать `<br>`
- здесь нельзя использовать свойство `position` и `float` (потому что блоки с `float` всегда выравниваются по верхнему краю, а позиционированные блоки не выстраиваются друг за другом)
- подсказка: изучи свойства `display` и `vertical-align` и почитай статьи http://htmlbook.ru/samlayout/blochnaya-verstka/strochnye-elementy и http://htmlbook.ru/samlayout/blochnaya-verstka/strochno-blochnye-elementy
- подсказка: свойство `vertical-align` работает только в 2 случаях: внутри ячейки таблицы и для выравнивания элементов с `display: inline` или `display: inline-block` в строке. В остальных случаях оно не действует.
- если тебе никак не удается добиться, чтобы расстояние между блоками по горизонтали было ровно 10px, прочти статью: http://css-live.ru/articles/zagadochnye-otstupy-mezhdu-inlajn-blokami.html

### Задание 5

![5](http://i.imgur.com/CDZGEMa.png)

- подсказка: не забудь добавить padding, чтобы цветная плашка была чуть больше чем текст.
- подсказка: тебе может помочь статья (учти, она сложная) http://css-live.ru/css/vvedenie-v-inlajnovyj-kontekst-formatirovaniya-ikf-osnovnye-ponyatiya-2-ya-publikaciya-cikla-tajny-css2-1.html

### Задание 6

![6](http://i.imgur.com/2MGgW1k.png)

- ни в коем случае не используй тут свойство `overflow` - оно имеет побочные эффекты
- подсказка: для верстки меню слева надо использовать теги `<ul>`, `<li>`, `<a>` и по желанию `<nav>`. Для статьи справа можно использовать `<atricle>`
- подсказка: если удалить весь текст справа или все пункты меню, верстка не должна ломаться. Если добавить несколько пунктов меню или абзацев текста, тоже.
- подсказка: шрифт — Trebuchet MS, не забудь что он пишется в кавычках в CSS
- подсказка: тебе надо изучить свойства `float` и `clear` и почитать статью http://softwaremaniacs.org/blog/2005/12/01/css-layout-float/

### Задание 7

![7](http://i.imgur.com/ioJmE2x.png)

- подсказка: разные элементы форм по-разному воспринимают свойства `width` и `height`. Для `input` и `textarea` они задают внутренние размеры, без паддинга и бордера, для `select` и кнопок — внешние. 
- не вздумай обнулять паддинг на поле ввода и кнопке — это некрасиво
- подсказка: браузер по умолчанию добавляет к `input` 2px паддинга и бордер.
- подсказка: тебе может помочь свойство `box-sizing` или задание разной высоты для 2 элементов
- подсказка: не забудь использовать тег `<form>`

### Задание 8

![8](http://i.imgur.com/pgrJeTv.png)

- текст: http://ideone.com/k9txx8
- верстка должна позволять без изменения CSS дописать или убрать любое число абзацев, списков, заголовков, картинок и примечаний
- можно использовать тег `<p>` для абзаца и `<aside>` для примечания
- не задавай поля с помощью `margin` на `<p>`. Поля задаются с помощью `padding` на родительском элементе
- маргины могут быть отрицательными (не только для флоатов), вот урок по теме: https://gist.github.com/codedokode/3f6063edf0a2227eb313

### Задание 9

![9](http://i.imgur.com/uf3FfZH.png)

- верстка должна позволять добавить или убрать любое число серых блоков
- верстка не должна ломаться, если в сером блоке убрать текст или желтый блок
- верстка не должна ломаться, если увеличить или уменьшить высоту желтого блока
- в серый блок кроме текста может быть добавлено любое число списков, заголовков, картинок и таблиц, верстка не должна сломаться
- помни, что маргины могут быть отрицательными
- в этом задании нельзя использовать свойство `overflow` и `position`
- подсказка: обрати внимание на этот код: http://nicolasgallagher.com/micro-clearfix-hack/ (англ.), перевод http://webknowledge.ru/novaya-mikro-versiya-haka-clearfix/

### Задание 10

![10](http://i.imgur.com/eRXhBC8.png)

- HTML-код добрый дядя уже написал и выложил тут: http://jsbin.com/bidezoqoja/1/ (копия: http://ideone.com/P6pPkP http://paste.ubuntu.com/8794987/ ), его менять нельзя, тебе надо лишь добавить свой CSS.
- обрати внимание, размер картинки должен определяться так: если картинка большая — она ужимается до ширины окна (с учетом полей конечно), маленькая — выводится как есть. 
- шрифт — Times New Roman
- никогда не увеличивай растровые (jpeg, png, gif) картинки, так как они мылятся. Можно только уменьшать их.
- появляется какой-то странный 3-4 пиксельный отступ под картинкой? Читай http://xiper.net/collect/html-and-css-tricks/content/img-in-the-block

### Задание 11

![11](http://i.imgur.com/CcDCDin.png)

- в HTML-коде необходимо использовать радиокнопки (`<input type="radio">`)
- должна быть возможность поменять `type="radio"` на `type="checkbox"` и все должно работать (с той разницей что можно нажать больше одной кнопки)
- код не должен использовать аттрибуты `for` и `id` (можно вложить `input` внутрь `label`)
- я смог решить задание, используя 3 тега на кнопку (`label`, `input`, `i`)
- должна быть возможность, не меняя CSS, добавить или убрать любое число кнопок
- это задание рассчитано на современные браузеры. Но если ты сделаешь, чтобы код работал и в старых (за счет яваскрипта), это будет плюсом. Или если в старых браузерах будет выводиться просто набор чекбоксов, это тоже лучше, чем ничего.
- кнопки должны реагировать на наведение (становятся серыми, а курсор меняет форму) и на нажатие. Вид нажатой кнопки и кнопки с наведением мыши должен раличаться. Например, вжатие можно обозначать тенью.
- твои CSS стили должны применяться только к элементам внутри переключателя. Недопустимо писать стили вроде `label {... }` меняющие вид всех `label` на странице.
- если кнопки будут «загораться» плавно, это будет плюсом
- чтобы определить состояние «кнопка вжата», можно использовать селектор ~~`label:active`~~ (на самом деле `input:active`)
- подсказка: чтобы нажатие на кнопку выключало другие, у них должен быть прописан аттрибут `name`
- подсказка: http://habrahabr.ru/post/154719/
- подсказка: http://habrahabr.ru/post/105267/
- дополнительный пункт: если ты посмотришь на обычные, не стилизованные радиокнопки и чекбоксы, то увидишь что по ним можно перемещать фокус с клавиатуры кнопками `Tab`, `Shift` + `Tab`, стрелками и переключать пробелом. Попробуй сделать поддержку клавиатурной навигации и в стилизованных кнопках. Подсказка: для этого надо отказаться от `display: none` на `input`, так как перемещать фокус по скрытым элементам нельзя.

### Задание 12

Сделай табы (вкладки) на CSS3, как здесь: http://cssdeck.com/labs/full/css-responsive-tabs

- если тебя тоже раздражает использованная анимация, можно заменить ее на любую другую, например плавное изменение прозрачности текста
- обрати внимание, что если сделать окно узким, вкладки перестраиваются. Это можно сделать с помощью css-правила `@media`
- подсказка: http://habrahabr.ru/post/138020/
- твои стили должны применяться только к элементам вкладок. Не пиши стили вроде `input {...}`, меняющие вид всех элементов на странице. Стили не лолжны влиять на элементы внутри содержимого вкладки, там тоже могут быть инпуты, чекбоксы, лабелы.
- протестируй что если сделать текст в заголовках вкладок длиннее или короче, верстка не ломается. Разрешается ограничивать длину заголовка разумным значением, разрешается переносить заголовки если они не умещаются в одну строку.
- протестируй что все корректно работает если текст на вкладках имеет разную высоту, содержит разные теги, в том числе формы с радиокнопками
- протестируй что выше и ниже блока вкладок можно поместить произвольные блоки текста и они не накладываются друг на друга. Блоки текста - обычные элементы вроде `h1`, `p`, `div`.
- старайся не использовать id в верстке так как с ними не получится вывести на странице несколько блоков вкладок. Разрешается использовать классы или data-атрибуты для связи вкладок и заголовков.
- сверстай блок так, чтобы блок с вкладками можно было вложить в страницу блока вкладок
- сделай, чтобы вкладки можно было переключать с клавиатуры без использования мыши (для этого не требуется яваскрипт, достаточно сделать возможность перемещать фокус клавишей `Tab` или стрелками по чекбоксам)
- это задание рассчитано на современные браузеры. Но если ты сделаешь, чтобы код работал и в старых (за счет яваскрипта), это будет плюсом. Или если в старых браузерах будет выводиться просто содержимое вкладок друг над другом, это лучше чем ничего.
- интересный способ сверстать вкладки без использования идентификаторов или номеров для связи заголовка и вкладки: http://chikuyonok.ru/2009/04/dl-tabs/ минус: не сработает если заголовки надо выводить в 2 строки или в адаптивной версии.

### Главное задание на верстку макета

Сверстай макет: http://www.mediafire.com/download/d1j980z595w6owi/pack180-webpaint-home-psd.zip (копия: http://rghost.ru/6L5kMK7q9 ~~http://rghost.ru/58855578 удалено~~ )

- старайся не использовать `id` в селекторах, так как он не должен повторяться и это сильно ограничивает его использование
- тебе скорее всего понадобится Photoshop. Бесплатный аналог - GIMP может открывать psd-файлы, но не факт что правильно.
- кнопки и ссылки должны реагировать на нажатие и наведение мыши
- в блоке All/Graphic/Illustration/Motion кнопки должны переключаться при нажатии
- тег `<img>` используется только для картинок в портфолио
- маленькие картинки надо объединить в CSS-спрайты (например, иконки соцсетей или серые иконки с фотоаппаратом и монитором). Большие картинки в портфолио — не надо.
- используй псевдоэлементы, чтобы уменьшить объем HTML, например для значка телефона внизу
- здесь используются внешние шрифты, и довольно тяжелые. Если ты можешь уменьшить их объем, это будет плюсом
- не забывай размечать заголовки с помощью тегов `<h1>` - `<h6>`
- макет должен быть читабелен и работоспособен в Internet Explorer (но вещи вроде теней или скругленных уголков, которые тот не поддерживает, можно выкинуть)
- вот мой урок про особенности Internet Explorer: https://gist.github.com/codedokode/855e3970124687b26a1c

## Что еще стоит глянуть?

Посмотри CSS-фреймворк Bootstrap 3: http://getbootstrap.com/ Он содержит огромное количество готовых компонент (иконки, меню, выпадающие элементы, группы кнопок, хитрые поля ввода) и часто используется для оформления интерфейсов. 

У Bootstrap 3 есть неприятная особенность: он ставит для всех элементов `box-sizing: border-box;` что может быть неудобно. Если это мешает, можно использовать 2 версию.

## Плохой код, который писать не стоит

Или стоит, но предварительно взвесив все за и против.

- не ставь слеш в конце одиночного тега: `<br />` — правильно будет `<br>`. Слеш использовался только в XML и XHTML.
- не используй `<a href="#"` или `<a href="javascript:void(0)"` никогда. Для этого есть кнопки или `<span>`.
- не используй CSS Reset (он сбрасывает все стили текста, списков, таблиц и прочее)
- не используй селектор `*`
- не используй код `* { box-sizing: border-box }` (он изменяет размер всех картинок, у которых есть border или padding)

## Как связаться с автором? 

codedokode@gmail.com