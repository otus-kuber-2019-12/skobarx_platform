## Kubernetes Controller
Содержит манифесты для развертывания frontend и payment сервис из проекта [Hipster shop](https://github.com/GoogleCloudPlatform/microservices-demo). Включает скрипт настройки мониторинга нод кубернетеста (node-exporter). 

## Как запустить Frontend Pod
1. Деплой с помощью ReplicaSet:
`$ kubectl apply -f frontend-replicaset.yaml`
2. Деплой с помощью Deployment:
`$ kubectl apply -f frontend-deployment.yaml`
## Как запустить PaymentService Pod
1. Деплой с помощью ReplicaSet:
`$ kubectl apply -f paymentservice-replicaset.yaml`
2. Деплой с помощью Deployment:
`$ kubectl apply -f paymentservice-deployment.yaml`
3. Деплой с помощью Deployment испоьзуя `Blue/Green` стратегию:
`$ kubectl apply -f paymentservice-deployment-bg.yaml`
4. Деплой с помощью Deployment испоьзуя `Reverse Update Rollout` стратегию:
`$ kubectl apply -f paymentservice-deployment-reverse.yaml`
## Как настроить мониторинг NodeExporter
1. Создать DaemonSet:
`$ kubectl apply -f node-exporter-daemonset.yaml`
## Как проверить работоспособность:
### Frontend
1. Сделать port forwarding для одного из `frontend` подов `8080 -> 8080` (можно использовать [Kube Forwarder](https://kube-forwarder.pixelpoint.io))
2. Перейти по ссылке http://localhost:8080. Сервис отрисовывает шапку, но далее отображает ошибку.

### PaymentService
1. Сделать port forwarding для одного из `paymentservice` подов `50051 -> 50051` (можно использовать [Kube Forwarder](https://kube-forwarder.pixelpoint.io))
2. Выполнить `$ curl http://localhost:50051`

### Мониторинг
1. Сделать port forwarding для одного из `node exporter` подов `9100 -> 9100` (можно использовать [Kube Forwarder](https://kube-forwarder.pixelpoint.io))
2. Выполнить `$ curl http://localhost:9100`