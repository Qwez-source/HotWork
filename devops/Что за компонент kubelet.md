### Шанс вопроса: 13%

Kubelet — это основной агентский компонент в Kubernetes, который обеспечивает управление pod'ами на узлах (рабочих станциях или серверах). Он взаимодействует с API-сервером Kubernetes для получения заданий по pod'ам и мониторинга их состояния.

Kubelet выполняет следующие функции:
1. **Запуск контейнеров**: Kubelet запускает указанные в конфигурации pod'ы на узле, используя соответствующий runtime-ом (например, Docker, containerd).
2. **Мониторинг состояния pod'ов**: Kubelet регулярно проверяет состояние запущенных pod'ов и отправляет информацию о них в API-сервер Kubernetes.
3. **Системы управления контейнерами**: Kubelet поддерживает различные системы управления контейнерами, такие как Docker, containerd и rkt.
4. **Настройка pod'ов**: Kubelet может автоматически настраивать pod'ы в соответствии с требованиями, указанными в подах (например, ограничения ресурсов, конфигурация сетей).
5. **Пути к файлам и каталогам**: Kubelet использует пути к файлам и каталогам для хранения информации о pod'ах, журналах и других данных.

Пример конфигурационного файла kubelet с настройками для Docker:
```yaml
apiVersion: kubelet.config.k8s.io/v1beta1
kind: KubeletConfiguration
address: "0.0.0.0"
port: 10250
authentication:
  anonymous:
    enabled: false
  webhook:
    enabled: true
authorization:
  mode: Webhook
clusterDomain: "cluster.local"
clusterDNS:
  - 10.96.0.10
containerLogMaxSize: "10Mi"
containerLogMaxFiles: 5
imagePullProgressDeadline: 1m
kubeReserved:
  cpu: "100m"
  memory: "100Mi"
systemReserved:
  cpu: "100m"
  memory: "100Mi"
evictionHard:
  memory.available: "100Mi"
runtimeRequestTimeout: "2m"
```

Этот конфигурационный файл настраивает Kubelet для работы с Docker и задаёт различные параметры, такие как адрес и порт, аутентификация, авторизация, управление ресурсами, вытеснение (eviction) и т.д.