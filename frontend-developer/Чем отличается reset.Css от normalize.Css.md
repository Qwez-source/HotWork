### Шанс вопроса: 3%

Reset CSS и Normalize CSS — это два подхода к сбросу стилей, которые используются для нормализации внешнего вида веб-страниц. Однако они имеют различия в том, как обрабатывают стили и какие браузерные дефолты удаляют или изменяют.

**Reset CSS:**
- **Основной принцип:** Удаляет все браузерные дефолты.
- **Пример кода:** 
  ```css
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  ```
- **Преимущества:** Простота и предсказуемость, так как все элементы начинаются с чистого листа.
- **Недостатки:** Может быть излишне разрушительным для некоторых элементов, особенно если нужно установить базовые стили.

**Normalize CSS:**
- **Основной принцип:** Сохраняет полезные браузерные дефолты и делает изменения по необходимости.
- **Пример кода:** 
  ```css
  /* Устанавливаем базовые стили */
  body {
    font-family: Arial, sans-serif;
  }

  /* Нормализуем некоторые элементы */
  h1 {
    margin: 0;
  }
  ```
- **Преимущества:** Сохраняет функциональность браузера, избегая крайних значений. Удобно для создания адаптивного дизайна и поддержания стилистической согласованности между различными элементами.
- **Недостатки:** Может быть менее предсказуемым, так как некоторые дефолтные стили остаются неизменными.

**В целом:**
- Использование Reset CSS предпочтительно для создания чистых проектов или приложений, где нужно абсолютно точно контролировать все стили.
- Нормализация (Normalize CSS) более гибкая и рекомендуется для веб-проектов, требующих современного и адаптируемого дизайна.