### University: [ITMO University](https://itmo.ru/ru/)
### Faculty: [FICT](https://fict.itmo.ru)
### Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
### Year: 2022/2023
### Group: K4110c
### Author: Tretiakova Anastasia Vladimirovna
### Lab: Lab1
### Date of create: 16.11.2022
### Date of finished: 

# Progress

## 1.Minikube installation
First, it was necessary to install minikube on the machine. The following instruction was used to do that: https://minikube.sigs.k8s.io/docs/start/

As a result it was possible to execute minikube command in CMD:

![image](https://user-images.githubusercontent.com/44613206/203626629-2d08c8d0-f5fd-4089-ba17-c681fc48ec3b.png)

## 2. Creation of a k8s cluster
After installation of minikube it was necessary to create k8s cluster. It can be made simply using command minikube start:

![image](https://user-images.githubusercontent.com/44613206/203626918-6373c663-4158-4137-bbe6-527ae4410dbf.png)

Then it was checked, that kubectl is installed on the machine, so there is no need to use minikube kubectl command.

## 3. Preparing a k8s manifest for vault
As required in the lab, vault should be deployed on the k8s cluster. It is also said, that only pod manifest should be written, so the following code block presents it:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: vault
  labels:
    app: vault
spec:
  containers:
    - name: vault
      image: vault:latest
      ports:
        - name: web
          containerPort: 8200
          protocol: TCP
```

## 4. Creating a k8s pod, service and usage of port-forward
When manifest is written, it can be applied for the cluster using command kubectl apply -f . Then information about created resources can be found (e.g. kubectl get pods). After that, service was created in order to user port-forward to get inside of the vault:

![image](https://user-images.githubusercontent.com/44613206/203627764-ce78e472-4c7d-4cb2-8ba8-121a599ac094.png)

![image](https://user-images.githubusercontent.com/44613206/203627811-cc6b4e04-cd9f-420b-8a89-569311d68c28.png)

Accessing vault:

![image](https://user-images.githubusercontent.com/44613206/203627875-9a2d133c-d3ee-4fda-be48-836f37a98b58.png)

To get a token it is necessary to research logs of the vault container:

![image](https://user-images.githubusercontent.com/44613206/203628022-eb67ecd9-566a-4b9f-a76c-b88ce67cca27.png)
![image](https://user-images.githubusercontent.com/44613206/203628045-9d9ea28c-12f9-42c6-87d4-69b2165d2b86.png)

At the bottom of the log Root Token can be found. This token will be used to access vault in the future:

![image](https://user-images.githubusercontent.com/44613206/203628111-9b55dd70-610b-4af8-bf17-1079123164f3.png)

## 5. Overall architecture
The picture below describes entities, which are used in the current lab work.

![image](https://user-images.githubusercontent.com/44613206/203629582-09545afe-06b8-4ccc-9ba0-e1560fd372d5.png)
