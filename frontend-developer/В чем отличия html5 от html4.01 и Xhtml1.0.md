### Шанс вопроса: 3%

HTML5 представляет собой более современную версию языка разметки гипертекста, которая включает множество новых функций и улучшений по сравнению с предыдущими версиями HTML4.01 и XHTML1.0. Вот основные отличия:

1. **Новые элементы и атрибуты**: HTML5 включает множество новых семантических элементов, таких как `<header>`, `<footer>`, `<article>`, `<section>`, `<nav>`, которые помогают структурировать содержимое веб-страницы и улучшают доступность.

2. **API**: HTML5 предоставляет множество новых API, таких как Drag and Drop, Canvas для рисования графики на веб-странице, Web Storage (localStorage и sessionStorage) для хранения данных в браузере, а также многое другое.

3. **Синтаксические изменения**: HTML5 позволяет использовать упрощенный синтаксис разметки, например, закрывающий тег `<input type="text" />` не требуется, если он единственный в своем родителе.

4. **События**: В HTML5 появились новые события, такие как `ononline`, `onoffline`, что позволяет реагировать на изменения сети.

Пример использования нового элемента `<section>` в HTML5:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML5 Example</title>
</head>
<body>
    <header>
        <h1>Welcome to My Website</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    <section>
        <h2>About Us</h2>
        <p>We are a company that provides high-quality services.</p>
    </section>
    <article>
        <h2>Our Services</h2>
        <ul>
            <li>Web Development</li>
            <li>SEO Optimization</li>
            <li>Digital Marketing</li>
        </ul>
    </article>
    <footer>
        <p>&copy; 2023 My Website. All rights reserved.</p>
    </footer>
</body>
</html>
```
В отличие от HTML4.01 и XHTML1.0, которые также являются версиями языка разметки гипертекста, они не включают все улучшения и новшества HTML5. XHTML требовал строгого соблюдения синтаксиса XML, что ограничивало свободу использования элементов вроде `<br>` без закрывающего тега. HTML4.01 допускает более гибкий синтаксис и не требует строгости XHTML.