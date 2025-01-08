### Шанс вопроса: 6%

Операторы в Kubernetes (k8s) — это инструменты, которые упрощают управление кластером. Они позволяют автоматизировать задачи управления, такие как развертывание приложений, масштабирование и обновление. Основные операторы включают:

1. **Deployment**: Это оператор для управления pod'ами. Он позволяет создавать декларативным способом развертывание приложений с возможностью масштабирования и обновлений.
   Пример:
   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: my-app
   spec:
     replicas: 3
     selector:
       matchLabels:
         app: my-app
     template:
       metadata:
         labels:
           app: my-app
       spec:
         containers:
         - name: my-app-container
           image: my-app-image:latest
           ports:
           - containerPort: 80
   ```

2. **StatefulSet**: Используется для управления pod'ами с состоянием, такими как базы данных. Он гарантирует порядок запуска и остановки pod'ов и сохраняет идентификаторы.
   Пример:
   ```yaml
   apiVersion: apps/v1
   kind: StatefulSet
   metadata:
     name: my-database
   spec:
     serviceName: "my-service"
     replicas: 3
     template:
       metadata:
         labels:
           app: my-app
       spec:
         containers:
         - name: mysql
           image: mysql:5.7
           ports:
           - containerPort: 3306
           env:
           - name: MYSQL_ROOT_PASSWORD
             value: password
   ```

3. **DaemonSet**: Используется для развертывания по одному экземпляру pod'а на каждой ноде кластера. Удобно для мониторинга, логирования и других системных служб.
   Пример:
   ```yaml
   apiVersion: apps/v1
   kind: DaemonSet
   metadata:
     name: fluentd-elasticsearch
   spec:
     selector:
       matchLabels:
         name: fluentd-elasticsearch
     template:
       metadata:
         labels:
           name: fluentd-elasticsearch
       spec:
         containers:
         - name: fluentd-elasticsearch
           image: fluent/fluentd:latest
           volumeMounts:
           - mountPath: /fluentd/log
             name: log-volume
   ```

4. **Job** и **CronJob**: Используются для выполнения фоновых задач с однократным или периодическим запуском.
   Пример Job:
   ```yaml
   apiVersion: batch/v1
   kind: Job
   metadata:
     name: pi-calculation
   spec:
     completions: 5
     parallelism: 2
     template:
       metadata:
         labels:
           app: pi-calculation
       spec:
         containers:
         - name: pi-calculation
           image: perl
           args: ["perl", "-Mbignum=bpi", "-wle", "print bpi(2000)"]
         restartPolicy: Never
   ```

5. **Service**: Обеспечивает постоянный IP-адрес для pod'ов, группируя их в набор. Используется для межpod-коммуникации.
   Пример:
   ```yaml
   apiVersion: v1
   kind: Service
   metadata:
     name: my-service
   spec:
     selector:
       app: my-app
     ports:
       - protocol: TCP
         port: 80
         targetPort: 80
   ```

Эти операторы позволяют управлять жизненным циклом приложений и сервисов в k8s, обеспечивая высокую доступность, масштабируемость и управляемость.