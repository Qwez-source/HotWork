### Шанс вопроса: 3%

Чтобы указать HTTP-заголовок с помощью мета-тега в HTML, вы можете использовать элемент `<meta>` с атрибутами `http-equiv` и `content`. Эти атрибуты позволяют вам установить различные HTTP-заголовки. Вот пример:

```html
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
</head>
```

В этом примере:
1. `<meta http-equiv="Content-Type" content="text/html; charset=utf-8">` устанавливает заголовок `Content-Type`, указывающий кодировку документа как UTF-8.
2. `<meta http-equiv="X-UA-Compatible" content="IE=edge">` задаёт заголовок `X-UA-Compatible`, чтобы обеспечить совместимость с Internet Explorer в режиме "наивысшей доступной версии".

Эти мета-теги помогают браузеру и серверу понять, как обрабатывать документ.