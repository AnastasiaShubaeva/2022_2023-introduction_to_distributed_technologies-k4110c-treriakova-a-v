### University: [ITMO University](https://itmo.ru/ru/)
### Faculty: [FICT](https://fict.itmo.ru)
### Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
### Year: 2022/2023
### Group: K4110c
### Author: Tretiakova Anastasia Vladimirovna
### Lab: Lab4
### Date of create: 06.12.2022
### Date of finished: 

# Progress
# 1. Creating minikube cluster
First, minikube cluster with 2 nodes using calico:

```
minikube start --nodes 2 --cni calico --kubernetes-version=v1.24.3
```

After that it was checked, that all two nodes were successfully created and works normal:

![image](https://user-images.githubusercontent.com/44613206/205987281-64160976-7437-4498-b8b5-22047706209b.png)
![image](https://user-images.githubusercontent.com/44613206/205987534-f1846228-8cde-4eaa-aa36-511536c76a0f.png)
