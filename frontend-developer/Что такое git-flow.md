### Шанс вопроса: 10%

Git-flow — это методология управления версиями, которая включает в себя основные и дополнительные ветки для разработки. Основными ветками являются:

1. **master** (или main): Основная рабочая ветка, где хранятся стабильные версии кода.
2. **develop**: Ветка для непрерывной разработки и тестирования.

Дополнительные ветки включают:
- **feature/***: Ветки для реализации новых функций.
- **release/***: Ветки для подготовки релизов.
- **hotfix/***: Ветки для исправления критических ошибок в стабильной версии.

### Основные команды:
1. **Создание новой ветки**:
   ```sh
   git branch feature/new-feature
   ```
2. **Переход к ветке**:
   ```sh
   git checkout feature/new-feature
   ```
3. **Слияние ветки в develop**:
   ```sh
   git merge feature/new-feature
   ```
4. **Создание и переход к новой release ветке**:
   ```sh
   git checkout -b release/1.0.0
   ```
5. **Слияние release ветки в master и tag для релиза**:
   ```sh
   git merge release/1.0.0
   git push origin master
   git tag 1.0.0
   git push --tags
   ```
6. **Создание и переход к новой hotfix ветке**:
   ```sh
   git checkout -b hotfix/critical-bug
   ```
7. **Слияние hotfix ветки в master и develop**:
   ```sh
   git merge hotfix/critical-bug
   git push origin master
   git checkout develop
   git merge hotfix/critical-bug
   git push origin develop
   ```

### Пример использования:
1. **Создание новой функции**:
   ```sh
   git checkout -b feature/login-page
   // Реализуем новую функциональность для логина пользователя
   git add .
   git commit -m "Add login page functionality"
   git push origin feature/login-page
   ```
2. **Готовность к релизу**:
   ```sh
   git checkout -b release/1.0.0
   // Тестируем и фиксим баги в этой ветке
   git add .
   git commit -m "Fix bugs before release"
   git push origin release/1.0.0
   ```
3. **Исправление критического бага**:
   ```sh
   git checkout -b hotfix/login-issue
   // Исправляем проблему с логином
   git add .
   git commit -m "Fix login issue"
   git push origin hotfix/login-issue
   ```

Таким образом, git-flow помогает структурировать рабочий процесс, делая его более предсказуемым и организованным.