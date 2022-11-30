### University: [ITMO University](https://itmo.ru/ru/)
### Faculty: [FICT](https://fict.itmo.ru)
### Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
### Year: 2022/2023
### Group: K4110c
### Author: Tretiakova Anastasia Vladimirovna
### Lab: Lab2
### Date of create: 30.11.2022
### Date of finished: 

# Progress
# 1. Preparing a deployment manifest
The requirements for creating a deployment manifest are as follows:
- контейнер - ifilyaninitmo/itdt-contained-frontend:master
- контейнерный порт - 3000
- количество реплик - 2
- должны быть установлены переменные окружения:
  - REACT_APP_USERNAME
  - REACT_APP_COMPANY_NAME

Using the requirements above the deployment manifest was created:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
  labels:
    app: frontend
spec:
  replicas: 2
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
      - name: frontend
        image: ifilyaninitmo/itdt-contained-frontend:master
        ports:
        - containerPort: 3000
        env:
        - name: REACT_APP_USERNAME
          value: Anastasiia
        - name: REACT_APP_COMPANY_NAME
          value: ITMO_University
```
 
# 2. Applying the manifest
To apply the manifest it is necessary to use the following command:

```
kubectl apply -f <file>
```

So the manifest was applied:

![image](https://user-images.githubusercontent.com/44613206/204882575-15f40a93-85d7-4b77-9374-d1ee518fd022.png)

Also, some information was printed, such as info about deployment and pods.

# 3. Exposing deployment
After applying, deployment was exposed and port-forwarding was used to reach container from the host machine:

![image](https://user-images.githubusercontent.com/44613206/204884466-f3303376-9ea1-4053-a7e3-af2c755febb1.png)

It was decided to use LoadBalancer service type. As a result, the following page was opened:

![image](https://user-images.githubusercontent.com/44613206/204884382-30a4e6c0-322f-4420-a2c7-1ce47f663436.png)

After refreshing nothing changed. It seems that there is not enough load of a pod, so load balancer decides not to forward requests to another pod.

Logs of pods are also the same:

