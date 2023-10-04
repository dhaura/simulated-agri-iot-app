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

## API Endpoints
You can access the Agri-IoT App using the following endpoints.
| Feature | Protocol | Method | API Endpoint | Request Body |
| -------- | -------- | -------- | -------- | -------- |
| Verify whether the app is running | HTTP | GET | / | N/A |
| View temparture logs in sector x | HTTP | GET | /read_temperature/x | N/A |
| View humidity logs in sector x | HTTP | GET | /read_humidity/x | N/A |
| Predict diseases in sector x | HTTP | POST | /predict_disease | {"sector": x} |
