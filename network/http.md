# Протокол HTTP (черновик)

Протокол — это что-то вроде языка, на котором могут общаться между собой программы (не язык программирования). Протокол HTTP используется браузером для получения страниц и файлов с сервера, отправки и закачки форм на сервер. Также, он может использоваться в разных API (сервисах, на которые можно отправлять запросы из программ, например API яндекс-карт позволяет по адресу определить географиеские координаты точки, и наоборот).

Тот, кто отправляет запрос (например, браузер), называется *клиент*, тот кто принимает запрос и отвечает на него, называется *сервер*. Заметь что сервером часто еще называют компьютер, на котором запущена программа-сервер. 

Вот что делает браузер, когда ты пытаешься зайти на какую-то страницу, например http://example.com/test:

- он выделяет из URL (адреса сайта) домен example.com и устанавливает TCP-соединение с этим сервером (TCP-соединение — это что-то вроде канала по которому можно передавать данные в обоих направлениях)
- соединившись, он отправляет серверу HTTP-запрос на получение страницы с адресом /test, расположенной на домене example.com
- сервер в ответ на запрос посылает браузеру HTML-код страницы
- браузер закрывает соединение и отображает страницу на экране. Если для отображения страниц нужны другие файлы (например, картинки, CSS файлы, JS скрипты), то браузер создает новые соединения и отправляет по ним запросы на получение этих файлов.

При скачивании файла происходит примерно то же самое, только браузер не отображает содержимое полученного от сервера ответа, а сохраняет его на диск. 

Также, протокол HTTP позволяет отправлять на сервер заполненные формы (например, форму регистрации или форму добавления комментария), в том числе с приложенным к ними файлами. В этом случае при нажатии кнопки отправки браузер собирает данные из формы вместе и отправляет их в теле запроса. Сервер их обрабатывает и отдает ответ, который браузер отображает на экране.

## Методы 

В HTTP есть несколько методов, например `GET`, `HEAD`, `POST`, `PUT`, `DELETE`. Метод указывается в запросе и с его помощью клиент говорит о том, что именно он хочет сделать: получить данные, отправить данные, изменить данные на сервере. Браузер использует только методы `GET`, `POST` и (в редких случаях) `OPTIONS`, а остальные методы могут использоваться в API и в этом случае разработчик API сам определяет что значит каждый метод.

- `GET` используется когда клиент хочет получить файл (или страницу с сервера)
- `HEAD` аналогичен `GET`, но он возвращает только заголовки, без тела ответа. Он может использоваться, например, чтобы узнать размер файла по заголовкам, не скачивая его (если сервер поддерживает такую возможность) или для проверки есть ли страница по данному адресу или нет.
- `POST` используется для отправки заполненных форм на сервер
- `OPTIONS` браузер использует при кроссдоменных запросах (когда страница, загруженная с одного сервера пытается получить данные с другого сервера), чтобы узнать, разрешает ли сервер такие запросы или нет. Не бойся, их мы пока изучать не будем.

## Запрос

HTTP — это текстовый протокол, то есть данные, которые посылает клиент и сервер, человекочитаемы (если конечно человек вышел этот урок и знает протокол). И запросы и ответы в протоколе HTTP состоят из 3 частей: стартовой (первой) строки, заголовков и тела. Тело и заголовки могут отсутствовать, стартовая строка обязательна. Вот пример запроса к странице http://ya.ru:

```
GET / HTTP/1.1
Host: ya.ru
Connection: keep-alive
Cache-Control: max-age=0
User-Agent: Mozilla/5.0 (Windows NT 5.1) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.41 Safari/535.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Encoding: gzip,deflate,sdch
Accept-Language: ru-RU,ru;q=0.8,en-US;q=0.6,en;q=0.4
Accept-Charset: windows-1251,utf-8;q=0.7,*;q=0.3

```

Стартовая строка запроса (`GET / HTTP/1.1`) содержит ровно 3 значения, разделенных пробелами: метод (тип запроса, в данном случае запрос на получение страницы), адрес страницы (без домена и протокола, то есть для URL `http://exaple.com/test?a=1` указывается только `/test?a=1`) и версия протокола. Сейчас используется `HTTP/1.1`.

Обрати внимание, что расстановка и число пробелов имеет значение. Нужно использовать ровно один пробел, и нельзя добавлять лишние пробелы или переводы строк.

После стартовой строки идут *заголовки запроса*. В них браузер добавляет информацию о себе и поддерживаемых им форматах и кодировках. Обязательным является только заголовок `Host:`, в котором указывается имя домена сайта, в данном случае `ya.ru`. Заметь, что протокол перед ним (`http://`) не указывается. Заголовок `Host` является обязательным, так как на одном сервере может располагаться много сайтов и без него было бы непонятно, к какому из них обращается клиент.

Из других заголовков стоит обратить внимание на `User-Agent`. В нем браузер передает информацию о своем названии и версии (в данном примере `Chrome/13.0.782.41`). Как ты видишь, кроме настоящей версии браузера там еще куча других названий (Mozilla, Safari, KHTML, Gecko). Их браузеры передают из-за криворуких программистов, которые на сервере проверяли этот заголовок и выводили сообщение о неподдерживаемом браузере если он не соответствовал их ожиданиям. Например, раньше, когда было только 2 основных браузера — Mozilla и Internet Explorer, все, что не содержало слова Mozilla, считалось IE, не поддерживающим современные стандарты. В итоге теперь все браузеры (включая Internet Explorer) содержат слово Mozilla в этой строке.

Еще важен заголовок `Referer`. Тут его нет, он передается когда ты переходишь по ссылке с одной страницы на другую, и содержит адрес той страницы, с которой ты перешел. С его помощью сервер может узнать, откуда люди приходят на сайт. Если ты ввел адрес руками или перешел из закладок браузера, этот заголовок отстутсвует. Также, некоторые браузеры позволяют не передавать его в целях анонимности.

Значение остальных заголовков ты можешь [посмотреть в википедии](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%B7%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%BE%D0%B2_HTTP#.D0.97.D0.B0.D0.B3.D0.BE.D0.BB.D0.BE.D0.B2.D0.BA.D0.B8_.D0.B7.D0.B0.D0.BF.D1.80.D0.BE.D1.81.D0.B0), запоминать их не надо.

Заголовок имеет вид `название: значение`. Каждый заголовок идет на отдельной строке. Заголовок можно перенести на новую строку, но в этом случае в начале второй строки должен быть один пробел или таб (чтобы было понятно что это продолжение предыдущей строки):

```
Example1: value
Example2: value
    value value
Example3: value
```

Заголовок может содержать только символы из кодировки [ASCII](https://ru.wikipedia.org/wiki/ASCII), то есть русские буквы использовать нельзя, только латинницу, цифры, знаки.

Список допустимых заголовков описан в стандарте HTTP. Ты (если ты будешь разрабатывать HTTP-клиент) можешь также добавлять свои заголовки, но их название должно начинаться с символов `X-`, например `X-Example: value`.

Заголовки заканчиваются пустой строкой (потому между ними этой строки не должно быть). За ней может идти тело запроса, если оно есть. В данном случае, у нас GET запрос и тела нету. Тело было бы, если бы это был POST запрос, передающий данные заполненной формы на сервер.

## Ответ

Получив запрос, сервер обрабатывает его и возвращает ответ. Ответ состоит тоже из 3 частей: стартовая строка, заголовки и тело ответа. Тело является необязательным.

Вот пример ответа, который сервер отдает на описанный выше запрос: 

```
HTTP/1.1 200 Ok
Server: nginx
Date: Sat, 11 Jul 2015 01:54:57 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: close
Cache-Control: no-cache,no-store,max-age=0,must-revalidate
Expires: Sat, 11 Jul 2015 01:54:57 GMT
Last-Modified: Sat, 11 Jul 2015 01:54:57 GMT
P3P: policyref="/w3c/p3p.xml", CP="NON DSP ADM DEV PSD IVDo OUR IND STP PHY PRE NAV UNI"
Set-Cookie: S=; Expires=Wed, 13-Jul-2005 01:54:57 GMT; Path=/
X-Frame-Options: DENY
Content-Encoding: gzip

<!DOCTYPE html><html class="i-ua_js_no i-ua_css_standart i-ua_browser_chrome" lang="ru">
<head xmlns:og="http://ogp.me/ns#"><meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>Яндекс</title><meta http-equiv=Content-Type content="text/html;charset=UTF-8">
<link rel="apple-touch-icon" href="//yastatic.net/morda-logo/i/apple-touch-icon/ru-76x76.png" sizes="76x76">
.... остаток страницы я вырезал ....
```

В стартовой строке (`HTTP/1.1 200 Ok`) сервер сообщает нам версию протокола, по которому он работает, код состояния (status code), показывающий, успешно ли обработан запрос или произошла ошибка (в данном случае `200` — все в порядке) и текстовую расшифровку этого кода (`Ok`).

Если бы например мы попытались запросить несуществующую страницу, стартовая строка выглядела бы так: `HTTP/1.1 404 Not Found`.

Первая цифра кода статуса определяет его значение: 

- 1xx — информационный код, используется в редких слуаях и значит «все в порядке, продолжайте отправлять запрос»
- 2xx — запрос успешно обработан
- 3xx — перенаправление (редирект), запрошенная страница находится по другому адресу, адрес указан в заголовке `Location`
- 4xx — ошибка клиента, например неправильно сформирован запрос, указан неправильный адрес или доступ запрещен
— 5xx — ошибка на стороне сервера, например произошла ошибка в программе, которая обрабатывала запрос

Сам список кодов достаточно большой: [список в википедии](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP)

Тебе не надо запоминать его весь, прочитай и запомни эти коды: 

- [200](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP#200) - запрос обработан успешно, запрошенная страница идет в теле ответа
- [301](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP#301) - перенаправление, искомая страница переехала по другому адресу, который указан в заголовке `Location`
- [400](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP#400) - запрос содержит синтаксическую ошибку и не соответствует стандарту HTTP
- [403](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP#403) - доступ к странице запрещен администратором сервера
- [404](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP#404) - страница с данным адресом не найдена (эту ошибку ты наверно видел не раз)
- [500](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP#500) - произошла ошибка в программе на сервере, обрабатывавшей запрос

После стартовой строки идут заголовки. Они содержат информацию о сервере, формате и кодировке передаваемых данных. Заголовки, как и в запросе, завершаются пустой строкой, за которой может идти тело запроса. В нашем случае тело запроса содержит HTML-код запрашиваемой страницы, который браузер должен отобразить на экране. Если тело есть, то оно содержит запрошенный файл. Оно может отсутствовать, например, если файл не найден.

Заголовков ответа существует довольно много, вот, какие из них самые важные: 

`Content-Type` говорит о том, какого типа файл передается в ответе. Это обязательный заголовок. В зависимости от этого заголовка, браузер будет пытаться отобразить содержимое по-разному. Вот примеры некоторых типов: 

- `text/html` — тело ответа надо воспринимать как HTML файл
- `text/plain` — тело надо отобразить как простой текст без форматирования
- `image/jpeg` — тело содержит бинарные данные картинки в формате JPEG
- `video/mp4` — тело содержит видеофайл

Для текстовых типов добавляется параметр `charset` который говорит о том, в какой кодировке текст. Например: `Content-Type: text/plain; charset=utf-8`.

Список типов файлов (MIME-типов) официально издается организацией IANA, вот его часть в википедии: https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_MIME-%D1%82%D0%B8%D0%BF%D0%BE%D0%B2

MIME-тип состоит из 2 частей, разделенных слешем. Первая часть говорит об общем типе файла (text, image, video, audio и тд), а вторая уточняет используемый формат (например, image/jpeg или image/png).

Если браузер встречает не поддерживаемый им тип, то вместо отображения файла он предлагает сохранить его на диск. Но сервер может попросить сохранить файл явно, добавив специальный заголовок `Content-Disposition: attachment`. Это используется при скачивании файлов, если мы хотим, чтобы при клике по ссылке файл сохранялся на диск, даже если это картинка или текстовый файл.

`Server` содержит название программы-сервера, в данном случае это nginx.

`Date` содержит дату и время генерации ответа по часам сервера. Дата пишется в описанном в стандарте HTTP формате.

[Про остальные заголовки ты можешь прочесть в википедии](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%B7%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%BE%D0%B2_HTTP#.D0.97.D0.B0.D0.B3.D0.BE.D0.BB.D0.BE.D0.B2.D0.BA.D0.B8_.D0.BE.D1.82.D0.B2.D0.B5.D1.82.D0.B0), запоминать их не требуется.

Итак, давай еще раз вспомним как выглядит запрос и ответ. Запрос: 

```
Метод URL HTTP/1.1
Host: имя-домена
ДругойЗаголовок: значение
ДругойЗаголовок: значение

Тело (если есть)
```

Ответ: 

```
HTTP/1.1 Код Текстовое-описание-кода
Content-Type: тип-содержимого (если оно есть)
ДругойЗаголовок: значение

Тело-содержащее-запрошенный-файл (если есть)
```

## Структура URL

## DNS

## Процентное кодирование

## Перенаправление (редирект)

## Формы

## Куки

## Полезные команды

## Задачи

- отправка правильного запроса
- отправка неправильного HTTP запроса
- запрос к API

## HTTP и PHP

$_GET, $_POST, $_COOKIE, $_SERVER, setcookie(), header()
curl, библиотеки поверх

- HTTP клиент
- отправка запроса к API

