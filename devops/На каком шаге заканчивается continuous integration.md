### Шанс вопроса: 6%

Continuous Integration обычно завершается на этапе сборки и тестирования кода. Вот основные моменты, которые можно рассмотреть в рамках этого процесса:

1. **Сборка проекта**: Когда разработчик коммитит изменения в репозиторий, CI сервер запускает сборку проекта. Это включает в себя установку всех необходимых зависимостей и инструментов, а также компиляцию кода.

2. **Запуск тестов**: После успешной сборки, CI сервер выполняет набор автоматизированных тестов для проверки правильности внесенных изменений. Эти тесты могут включать юнит-тесты, интеграционные тесты и другие виды тестирования в зависимости от специфики проекта.

3. **Анализ кода**: Некоторые CI системы также выполняют анализ статического кода для обнаружения потенциальных проблем, таких как синтаксические ошибки, неправильное форматирование или другие кодгайды.

4. **Репорт о статусе**: После завершения всех этапов CI сервер обновляет статус проекта в репозитории (например, GitHub, GitLab) и уведомляет участников команды о результатах сборки и тестирования.

Пример конфигурационного файла для Jenkins, который настроен на непрерывную интеграцию:
```yaml
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'make'
            }
        }
        stage('Test') {
            steps {
                sh 'make test'
            }
        }
    }
}
```
В этом примере показано, как настроить пайплайн в Jenkins для выполнения сборки и тестирования проекта.