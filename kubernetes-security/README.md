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
### Как проверить настройки безопасности
## Настройки кластера
Выполнить команду проверки прав
 - `$ kubectl auth can-i get deployments --as system:serviceaccount:default:bob` должен вернуть `YES` так как Боб имеет права админа на весь кластер.
 - `$ kubectl auth can-i get pods --as system:serviceaccount:default:dave` должен вернуть `NO` так как Дэйв не имеет права для работы с кластером.
## Настройки безопасности `prometheus` namespace
Выполнить команду проверки прав:
 - `$ kubectl auth can-i get deployments --as system:serviceaccount:prometheus:carol` должен вернуть `NO` так как Кэрол не имеет прав доступа к объектам `deployments`
 - `$ kubectl auth can-i list pods --as system:serviceaccount:prometheus:carol -n prometheus` должно вернуть `YES` так как Кэрол имеет права `get, list, watch` на `Pod` объекты
## Настройки безопасности `dev` namespace
Выполнить команду проверки прав:
 - `$ kubectl auth can-i create pods --as system:serviceaccount:dev:ken` должен вернуть `NO` так как Кен не имеет прав на создание объектов `pod`
 - `$ kubectl auth can-i watch pods --as system:serviceaccount:dev:ken` должен вернуть `YES` так как Кен имеет права на просмотр любых объектов.
 - `$ kubectl auth can-i create pods --as system:serviceaccount:dev:jane` должен вернуть `YES` так как Джейн имеет права админа.
