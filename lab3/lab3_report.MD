University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4110c\
Author: Ageev Andrey Evgenevich\
Lab: Lab 3\
Date of create: 10.09.2023\
Date of finished: 22.09.2023
## Лабораторная работа №3 "Сертификаты и "секреты" в Minikube, безопасное хранение данных."

Для разворачивания сервиса itdt-contained-frontend был создан namespace ```second-itmo```:

```bash 
kubectl apply -f my-namespace.yaml
```

Был создан config-map:

```bash 
kubectl apply -f config-map.yaml
```

Был создан service-account:

```bash 
kubectl apply -f sa.yaml
```

Далее был создан service с типом NodePort с единственным портом ```3000```:

```bash 
kubectl apply -f services.yaml
```

После чего был создан файл для разворачивания пода, на котором будет находиться контейнер с itdt-contained-frontend:

```bash 
kubectl apply -f deployment.yaml
```

После чего был сгенерирован tls-сертификат и сделан secret:

```bash 
kubectl apply -f secret.yaml
```

После чего был сформирован ingress:

```bash 
kubectl apply -f ingress.yaml
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

После разворачивания сервиса и добавления в hosts ```my-second-itmo.com``` была получена следующая страница c подтверждающим сертификатом:

![Стартовая страница](res/cert-screen.png)

При написании ```deployment.yaml``` переменные окружения были указаны в config-map как:
* ```REACT_APP_USERNAME: STUDENT```
* ```REACT_APP_COMPANY_NAME: ITMO```

Схема организации namespace:

![Диаграмма](res/lab3_d.png)