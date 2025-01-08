### Шанс вопроса: 6%

Для доступа к внешнему IP-адресу (через LoadBalancer Service Ingress Controller) в Kubernetes, вы можете использовать стандартные маршрутизационные правила. Вот шаги для настройки и получения внешнего IP-адреса:

1. **Создание Deployment и Service:**
   Создайте Deployment для вашего приложения и Service, чтобы предоставить доступ к нему. Например:

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
           image: my-app-image
           ports:
           - containerPort: 80
   ```

   ```yaml
   apiVersion: v1
   kind: Service
   metadata:
     name: my-app-service
   spec:
     selector:
       app: my-app
     ports:
       - protocol: TCP
         port: 80
         targetPort: 80
     type: LoadBalancer
   ```

2. **Применение конфигураций:**
   Примените созданные YAML файлы с помощью команды `kubectl apply -f`:

   ```sh
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

3. **Проверка внешнего IP-адреса:**
   Используйте команду `kubectl get svc` для просмотра информации о Service, включая его внешний IP-адрес:

   ```sh
   kubectl get svc my-app-service
   ```

   Вы должны увидеть поле `EXTERNAL-IP`, которое представляет собой внешний IP-адрес, назначенный вашему LoadBalancer Service.

Этот процесс позволяет вам легко получить доступ к приложению через внешний IP-адрес, что особенно полезно для тестирования и развертывания в различных окружениях.