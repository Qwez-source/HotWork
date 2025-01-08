### Шанс вопроса: 6%

В GitLab CI можно создавать повторяющиеся задачи, чтобы упростить управление и повторное использование конфигураций. Это делается с помощью переменных и include директив в файле `.gitlab-ci.yml`.

Пример:
```yaml
stages:
  - build
  - test
  - deploy

build_job:
  stage: build
  script:
    - echo "Building the project"

test_job:
  stage: test
  script:
    - echo "Running tests"

deploy_job:
  stage: deploy
  script:
    - echo "Deploying to production"
```

Если у вас есть несколько задач, которые выполняют похожие действия, вы можете создать общий файл с задачами и затем включать его в основную конфигурацию:
```yaml
include:
  - local: 'common_tasks.yml'
```

В `common_tasks.yml`:
```yaml
build_and_test:
  stage: build
  script:
    - echo "Building the project"
    - echo "Running tests"

deploy_to_staging:
  stage: deploy
  script:
    - echo "Deploying to staging"
```

Теперь вы можете включать этот файл в ваш основной `.gitlab-ci.yml`:
```yaml
include:
  - local: 'common_tasks.yml'
```

Таким образом, все задачи, определенные в `common_tasks.yml`, будут доступны во всех этапах вашего CI/CD процесса.