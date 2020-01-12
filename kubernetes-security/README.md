## Kubernetes Security
Содержит настройки безопасности для кластера и prometheus, dev namespaces

## Как применить настройки безопасности для кластера
1. Чтобы дать админские права service account `bob` необходимо выполнить:
`$ kubectl apply -f task01/bob-admin.yaml`
2. Чтобы создать service account `dave` необходимо выполнить:
`$ kubectl apply -f task01/dave-user.yaml`
## Как применить настройки безопасности к `prometheus` namespace
1. Выполнить:
`$ kubectl apply -f task02/01-namespace.yaml`
## Как применить настройки безопасности к `dev` namespace
1. Выполнить:
`$ kubectl apply -f task03/01-dev-namespace.yaml`
