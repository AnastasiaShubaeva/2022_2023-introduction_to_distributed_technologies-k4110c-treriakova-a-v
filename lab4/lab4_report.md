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

Second, it was necessary to create calicoctl pod to use it. Manifest used in the command was received from official website of calico.

![image](https://user-images.githubusercontent.com/44613206/205988420-b93e338c-751a-42d9-b318-a161ae6492f5.png)


# 2. Creating IP-Pools and replica set
First, it was necessary to create ip-pools.

```
apiVersion: projectcalico.org/v3
kind: IPPool
metadata:
  name: zone-west-ippool
spec:
  cidr: 192.168.0.0/24
  ipipMode: Always
  natOutgoing: true
  nodeSelector: zone == "west"
---
apiVersion: projectcalico.org/v3
kind: IPPool
metadata:
  name: zone-east-ippool
spec:
  cidr: 192.168.1.0/24
  ipipMode: Always
  natOutgoing: true
  nodeSelector: zone == "east"
```

This example also was taken from official website. To apply the manifest the following command was executed:

```
kubectl exec -i -n kube-system calicoctl -- /calicoctl create -f - < ip_pool.yaml
```

![image](https://user-images.githubusercontent.com/44613206/205989030-e4e0b6d2-deda-4233-8769-4d73b4e4aae8.png)

However, there was a default ip-pool:

![image](https://user-images.githubusercontent.com/44613206/205989268-06a3fa7e-b613-4537-bde1-cc6eb0d6eb65.png)

So that it was decided to remove it:

![image](https://user-images.githubusercontent.com/44613206/205989569-177391e7-07df-41bc-9df3-5246d3cff9e1.png)

At the end, manifest with configmap, replica set and service was applied:

![image](https://user-images.githubusercontent.com/44613206/206000120-ca9633c1-9c73-45ec-8f5a-8c5d8aab9039.png)

At the stage of starting the service, the computer freezes. It was decided to deploy the application on another device.

![image](https://user-images.githubusercontent.com/44613206/206715000-a241ee89-ece7-4824-8bac-fd69bf83fb90.png)

![image](https://user-images.githubusercontent.com/44613206/206717926-361bfbe1-36d9-48ba-b5e8-7f1b2e4ea681.png)

# 3. Accessing the application
First, it was necessary to execute the following command to expose service:

```
minikube service frontend-rs-service
```

![image](https://user-images.githubusercontent.com/44613206/206715105-5b3732f9-8f20-40f0-9940-e69123cb480e.png)


After that in the browser new page was opened:

![image](https://user-images.githubusercontent.com/44613206/206715133-a281d498-fb16-4adb-9fc8-2e81aacc31c0.png)

# 4. Ping containers
At the end it was checked, that pods can ping each other:

![image](https://user-images.githubusercontent.com/44613206/206715309-cbd6a653-3aee-4f50-8a6d-917374301f0f.png)

# 5. Overall architecture
The picture below describes entities, which are used in the current lab work.

![image](https://user-images.githubusercontent.com/44613206/206717631-e22edead-19fa-4dbb-abba-e2fb127948e3.png)

