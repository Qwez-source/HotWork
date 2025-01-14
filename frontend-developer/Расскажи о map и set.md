### Шанс вопроса: 10%

Map и Set являются важными структурами данных в JavaScript, каждая из которых имеет свои уникальные характеристики и области применения.

**Map:**
- **Описание**: `Map` — это коллекция ключ/значение, где любое значение (как объекты, так и примитивы) может быть использовано в качестве ключа. В отличие от объектов, где ключи всегда строки или символы, в Map могут быть использованы любые типы данных.
- **Пример**:
  ```javascript
  const map = new Map();
  map.set('key1', 'value1');
  map.set(2, 'value2');
  console.log(map.get('key1')); // Выведет: value1
  console.log(map.has('key1')); // true
  ```
- **Преимущества**: Гибкость ключей, удобное добавление и удаление элементов, легкая интеграция с другими структурами данных.

**Set:**
- **Описание**: `Set` — это коллекция уникальных значений, где каждое значение может встречаться только один раз. Это позволяет использовать его для удаления дубликатов из массивов или проверки наличия элемента.
- **Пример**:
  ```javascript
  const set = new Set();
  set.add('value1');
  set.add(2);
  console.log(set.has(2)); // true
  set.delete(2);
  console.log(set.has(2)); // false
  ```
- **Преимущества**: Высокая производительность при проверке наличия элемента, удобство добавления и удаления элементов, возможность использования для уникальных значений.

**Сравнение:**
- **Map**: 
  - Ключи могут быть любого типа данных.
  - Поддерживает произвольные типы ключей, включая объекты и примитивы.
  - Методы: `set`, `get`, `has`, `delete`, `size`.
- **Set**:
  - Содержит только уникальные значения.
  - Поддерживает операции добавления (`add`), проверки на наличие (`has`) и удаление (`delete`).
  - Методы: `add`, `has`, `delete`, `size`.

**Пример использования:**
- **Map**: Для хранения данных, где ключи имеют значение (например, словари с языками и их столицами).
  ```javascript
  const capitals = new Map([
    ['France', 'Paris'],
    ['Germany', 'Berlin']
  ]);
  console.log(capitals.get('France')); // Выведет: Paris
  ```
- **Set**: Для уникального списка значений (например, фильтрация массива от дубликатов).
  ```javascript
  const uniqueValues = new Set([1, 2, 3, 4, 5, 1, 2]);
  console.log(uniqueValues); // Выведет: Set { 1, 2, 3, 4, 5 }
  ```

Использование Map и Set делает код более гибким и эффективным, обеспечивая быстрый доступ к данным и легкую обработку уникальных значений.