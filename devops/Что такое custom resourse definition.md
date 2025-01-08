### Шанс вопроса: 6%

Custom Resource Definition (CRD) — это объекты Kubernetes, которые позволяют определять новые типы ресурсов в кластере. Они расширяют возможности Kubernetes, давая возможность создавать пользовательские ресурсы поверх базовых объектов Kubernetes, таких как Pods, Services и т.д.

CRD полезны для следующих сценариев:
1. **Расширение функциональности**: Если вам нужно добавить новый тип ресурса, который не является частью основных объектов Kubernetes (например, пользовательские статусы задач или проектные данные), вы можете создать CRD.
2. **API Aggregation Layer**: CRD можно использовать для создания прокси-сервера API между клиентом и сервером Kubernetes, что позволяет добавлять новые API-ресурсы без изменения базового API-сервера.
3. **Интеграция с внешними системами**: Если вы работаете с внешними системами данных или сервисами, создание CRD может упростить интеграцию и управление этими ресурсами через Kubernetes.

Пример создания простейшего CRD для приложения:
```yaml
apiVersion: apiextensions.k8s.io/v1
kind: CustomResourceDefinition
metadata:
  name: apps-app-crd.example.com
spec:
  group: example.com
  version: v1
  names:
    kind: App
    listKind: AppList
    plural: apps
    singular: app
  scope: Namespaced
  validation:
    openAPIV3Schema:
      properties:
        spec:
          properties:
            replicas:
              type: integer
            image:
              type: string
```

После создания CRD можно использовать его для создания пользовательских ресурсов, например:
```yaml
apiVersion: example.com/v1
kind: App
metadata:
  name: my-app
spec:
  replicas: 3
  image: nginx:latest
```

Этот пример демонстрирует создание простого пользовательского ресурса `App`, который включает поля `replicas` и `image`.