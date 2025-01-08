### Шанс вопроса: 6%

PV (Persistent Volume) — это ресурс в Kubernetes, который представляет собой часть хранилища на уровне кластера. PV может быть жестко или программно провизионированным NFS, AWS EBS, GCP Persistent Disks и т.д. PV изолирован от конкретных Pods и доступен для использования другими компонентами кластера.

PVC (Persistent Volume Claim) — это запрос на использование хранилища, который создается в пространстве имен. PVC описывает требуемые ресурсы хранилища, такие как размер и доступные AccessModes (например, ReadWriteOnce, ReadOnlyMany,ReadWriteMany). Kubernetes автоматически подбирает подходящий PV для удовлетворения запроса PVC.

Пример создания PV:
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-example
spec:
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  awsElasticBlockStore:
    volumeID: "aws://us-west-2a/vol-123456"
```

Пример создания PVC:
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-example
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
```

Таким образом, PV предоставляет хранилище на уровне кластера, а PVC запрашивает и использует это хранилище в рамках конкретного пространства имен.