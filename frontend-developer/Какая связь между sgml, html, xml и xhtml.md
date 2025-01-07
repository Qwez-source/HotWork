### Шанс вопроса: 3%

SGML, HTML, XML и XHTML являются различными языками разметки, каждый из которых имеет свою специфику и назначение. Вот краткое объяснение взаимосвязи между ними:

1. **SGML (Standard Generalized Markup Language)**: SGML — это универсальный стандарт, определяющий основные принципы структурирования документов. Он является предком многих современных языков разметки, включая HTML и XML.

2. **HTML (Hypertext Markup Language)**: HTML — это конкретный диалект SGML, предназначенный для описания структуры веб-страниц. Он используется для создания веб-сайтов и приложений. HTML5, в частности, является последней версией этого языка и включает множество новых функций и улучшений.

3. **XML (Extensible Markup Language)**: XML — это более простой и легкий вариант SGML, который был разработан для того, чтобы быть менее громоздким и более удобным для машинной обработки. XML фокусируется на структуре данных и не включает правила отображения, характерные для HTML.

4. **XHTML (Extensible Hypertext Markup Language)**: XHTML — это строгое подмножество HTML, которое также является подмножеством XML. Он требует, чтобы все документы соответствовали синтаксису XML и следовали правилам HTML, но в более строгой форме. XHTML 1.0 и XHTML 1.1 — это конкретные версии этого языка.

Взаимосвязь между ними можно представить следующим образом:
- **HTML** является частным случаем **SGML**.
- **XML** и **XHTML** также являются частными случаями **SGML**, но с более строгими правилами.
- **XHTML** — это специальный подмножество HTML, который также соответствует синтаксису XML.

Пример простейшего документа на HTML:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My First Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is a simple HTML document.</p>
</body>
</html>
```

Пример простейшего документа на XML:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<hello>
    <world>Hello, World!</world>
    <message>This is a simple XML document.</message>
</hello>
```

Пример простейшего документа на XHTML:
```xhtml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>My First Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is a simple XHTML document.</p>
</body>
</html>
```

Таким образом, HTML является языком разметки веб-страниц, XML — это более общий язык для структурирования данных, а XHTML — это строго определенная версия HTML, соответствующая синтаксису XML.