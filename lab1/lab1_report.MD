University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4110c\
Author: Ageev Andrey Evgenevich\
Lab: Lab 1\
Date of create: 10.09.2023\
Date of finished: 22.09.2023
## Лабораторная работа №1 "Установка Docker и Minikube, мой первый манифест."

Для разворачивания сервиса Vault был создан namespace ```my-vault```:

```bash 
kubectl apply -f my-namespace.yaml
```

Далее был создан service для Vault с единственным портом ```8200```:

```bash 
kubectl apply -f services.yaml
```

Далее был создан service-account для service:

```bash 
kubectl apply -f sa.yaml
```

После чего был создан файл для разворачивания пода, на котором будет находиться контейнер с Vault:

```bash 
kubectl apply -f deployment.yaml
```

Дальнейшее наблюдение можно делать через следующие команды:

```bash 
kubectl get po # Покажет все доступные поды в namespace
```

```bash 
minikube dashboard # Откроет дашборд в виде UI со всей актуальной информации по каждому namespace
```

```bash 
kubectl logs <pod-name> # Покажет все логи внутри указанного пода
```

Через логи был получен токен для авторизации в поднятом Vault:

![Токен авторизации](res/token.png)

Схема организации namespace:

![Диаграмма](res/lab1.png)