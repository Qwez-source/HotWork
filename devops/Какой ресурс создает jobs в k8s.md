### Шанс вопроса: 6%

В Kubernetes (K8s) ресурс `Jobs` используется для запуска задач с однократным выполнением. Он полезен при необходимости выполнения фоновых задач, таких как обработка данных, уборка мусора или любые другие задачи, которые должны быть завершены один раз.

Пример создания Job в Kubernetes:

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: example-job
spec:
  completions: 3
  parallelism: 2
  template:
    metadata:
      labels:
        app: example-job
    spec:
      containers:
      - name: example-container
        image: busybox
        command: ["/bin/sh", "-c", "echo 'Hello, Kubernetes!' && sleep 30"]
      restartPolicy: Never
```

В этом примере создается Job с именем `example-job`, который будет запускать контейнер из образа `busybox` с командой для вывода сообщения и последующего сна на 30 секунд. Параметр `completions: 3` указывает, что Job должен быть завершенным тремя экземплярами задачи, а параметр `parallelism: 2` ограничивает выполнение двух задач одновременно.