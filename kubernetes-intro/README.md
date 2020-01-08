## Introduction to Kubernetes
Содержит тестовый Pod с [веб сервером](https://hub.docker.com/repository/docker/skobarx/kubernetes-intro), а также frontend сервис из проекта [Hipster shop](https://github.com/GoogleCloudPlatform/microservices-demo)

## Как запустить Web Pod
1. Для создания пода с веб сервером необходимо выполнить:
`$ kubectl apply -f web/web-pod.yml`
2. Далее нужно настроить порты
`$ kubectl port-forward --address 0.0.0.0 pod/web 8000:8000`
## Как запустить Frontend Pod
1. Для создания пода с frontend сервисом необходимо выполнить:
`$ kubectl apply -f frontend-pod.yaml`
**Под не запустится так как манифест не содержит требуемых переменных окружения**
2. Выполните следующую команду, чтобы создать fronted под с _корректным_ манифестом:
`$ kubectl apply -f frontend-pod-healthy.yaml`
## Как проверить работоспособность:
### Web Pod
 - Перейти по ссылке http://localhost:8000. Вы должны увидеть страницу с информацией о кластере.
### Frontend Pod
 - Перейти по ссылке http://localhost:8080. Сервис отрисовывает шапку, но далее отображает ошибку.