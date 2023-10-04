# Simulated Agri IoT App

* Developed for testing purposes on edge clusters.
* A microservices based architecture is used and the recommendation system is an optional service.
* All services are containerized.

## Setup Guide

### Prerequisites

- Need to install the following.
    - Python3
    - Docker
    - Kuberentes 

### Setup - Armv7 Architecture

1. [Optional] Build docker images for each of the microservice using the following ReadMe files.
    - [Master Service](https://github.com/dhaura/simulated-agri-iot-app/blob/main/master-service/README.md)
    - [Recommendation Service](https://github.com/dhaura/simulated-agri-iot-app/blob/main/recommendation-system/README.md)
    - [Temperature Reader](https://github.com/dhaura/simulated-agri-iot-app/blob/main/temp-reader/README.md)
    - [Humidty Reader](https://github.com/dhaura/simulated-agri-iot-app/blob/main/humidity-reader/README.md)
    - [User App Service](https://github.com/dhaura/simulated-agri-iot-app/blob/main/ht-user-app/README.md)
2. If you did step 1, change the docker image path in `*_deployment.yaml` of every microservice with your docker image path.
3. Start you kuberenets server.
4. Navigate into `deployment-manifests`>`armv7`.
```shell
cd deployment-manifests/armv7
```  
6. Deploy the application inside the cluster using the following command.
```shell
kubectl apply -f  .
```

### Setup - x64 Architecture

1. [Optional] Build docker images for each of the microservice using the following ReadMe files. 
    - Important:
        - When building docker images, don't use tag `--platform=linux/arm/v7`.
        - For `Recommendation Service`, instead of `Dockerfile` use `DockerfileWindows`.
    - [Master Service](https://github.com/dhaura/simulated-agri-iot-app/blob/main/master-service/README.md)
    - [Recommendation Service](https://github.com/dhaura/simulated-agri-iot-app/blob/main/recommendation-system/README.md)
    - [Temperature Reader](https://github.com/dhaura/simulated-agri-iot-app/blob/main/temp-reader/README.md)
    - [Humidty Reader](https://github.com/dhaura/simulated-agri-iot-app/blob/main/humidity-reader/README.md)
    - [User App Service](https://github.com/dhaura/simulated-agri-iot-app/blob/main/ht-user-app/README.md)
2. If you did step 1, change the docker image path in `*_deployment.yaml` of every microservice with your docker image path.
3. Start you kuberenets server.
4. Navigate into `deployment-manifests`>`x64`.
```shell
cd deployment-manifests/x64
```  
6. Deploy the application inside the cluster using the following command.
```shell
kubectl apply -f  .
```
