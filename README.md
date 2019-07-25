# vsb2007_platform
vsb2007 Platform repository

## ДЗ:01
- Установил kubectl и автодополнение.
- Установил и Запустил minikube.
- Уставноил/запустил dashboard - дополнительно создал токен для авторизации.
- k9s - не подцепляет сертификаты из конфига.
- Проверил, что в кластере восстанавливаются ноды после удаления: core-dns - как ReplicaSet, остальные kube-apiserver
  скорее всего контролируются системными процессами - но это не очевидно в отличии от core-dns.
- Создал Dockerfile для http сервера - на python http.server.
- Создал манифест web-pod.yaml, согласно дз - посмотрел все стадии запуска, случано его удалил и восстановил из команды `kubectl get pod web -o yaml`.
- С помощью `kubectl port-forward --address 0.0.0.0 pod/web 8000:8000` подцепился к страничке из init контейнера.

## ДЗ:02
- task01
1. Создать Service Account bob, дать ему роль admin в рамках всего кластера
2. Создать Service Account dave без доступа к кластеру

- task02
1. Создать Namespace prometheus
2. Создать Service Account carol в этом Namespace
3. Дать всем Service Account в Namespace prometheus возможность делать get, list, watch в отношении Pods всего кластера

- task03
1. Создать Namespace dev
2. Создать Service Account jane в Namespace dev
3. Дать jane роль admin в рамках Namespace dev
4. Создать Service Account ken в Namespace dev
5. Дать ken роль view в рамках Namespace dev
