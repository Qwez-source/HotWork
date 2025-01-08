### Шанс вопроса: 6%

В GitLab CI/CD можно использовать различные раннеры для запуска пайплайнов. Основными типами раннеров, которые обычно используются, являются:

1. **GitLab-provided runners**: Это встроенные runner'ы, предоставляемые GitLab. Они могут быть установлены на сервере GitLab или в облаке.
2. **Shared runners**: Это общие runner'ы, доступные для всех проектов в GitLab.
3. **Specific runners**: Эти runner'ы предназначены для конкретных проектов и могут быть созданы администратором GitLab.
4. **Custom runners**: Это пользовательские runner'ы, которые можно настроить в соответствии с требованиями проекта.

Для запуска пайплайна обычно используется GitLab-provided runner или shared runner. В файле `.gitlab-ci.yml` можно указать тип runner'а, который будет использоваться для выполнения задач. Например:

```yaml
image: docker:latest  # Использование Docker образа для запуска задачи

stages:
  - build
  - test
  - deploy

build_job:
  stage: build
  script:
    - echo "Building the project..."
    - docker run --rm -v $PWD:/app -w /app my-custom-image sh -c "make build"

test_job:
  stage: test
  script:
    - echo "Running tests..."
    - docker run --rm -v $PWD:/app -w /app my-test-image sh -c "make test"

deploy_job:
  stage: deploy
  script:
    - echo "Deploying to production..."
    - ssh user@remote_host "mkdir -p /path/to/deployment && tar xzf deployment.tar.gz -C /path/to/deployment"
```

В этом примере используется Docker образ для выполнения задач, что является распространённой практикой в DevOps.