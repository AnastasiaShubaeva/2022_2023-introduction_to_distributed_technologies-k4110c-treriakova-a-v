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
![image](https://user-images.githubusercontent.com/44613206/204882367-42bac073-63c4-424b-b039-6367bec3ceed.png)
