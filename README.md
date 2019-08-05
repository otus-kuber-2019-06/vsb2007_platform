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

## ДЗ:03 - Лекция - 06
- Добавили в описание пода readinessProbe
- Добавили в описание пода livenessProbe
- Создали web-deploy.yaml
- Добавили в манифест (web-deploy.yaml) блок strategy
- Создали web-svc-cip.yaml
- Включили ipvs - пока не понятно нужно ли это делать в кластерах всегда как бест-пркатис или это только в частном случае, дли примера
- Создали MetalLB
- Создали конфигурацию metallb-config.yaml
- Создали web-svc-lb.yaml - поменяли ClusterIP на LoadBalancer
- Добавили статический маршрут на подсеть из metallb-config.yaml, чтобы достучаться до приложения
- Создали сервис LoadBalancer, который откроет доступ к CoreDNS снаружи кластера - отдельно для TCP и UDP
- Установили ingress-nginx
- Создали nginx-lb.yaml
- Создали web-svc-headless.yaml
- Создали web-ingress.yaml - направили на сервис из web-svc-headless.yaml
- Добавили доступ к kubernetes-dashboard - dashboard-ingress.yaml - пока не понятно почему надо делать обработку пути по regex
- Создали канареечные поды (web-deploy-canary.yaml), сервис (web-svc-headless-canary.yaml) и ingress (web-ingress-canary.yaml)
