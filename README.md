# Minikube Getting Started Tutorial

This tutorial has been written with the intent of helping folks get up and running
with containers and is designed to work with Docker Desktop. While not going too much
into depth, it covers the following topics:

- running your first minikube cluster
- adding AWS registries
- adding ingress addon
- switching from docker desktop to minikubes docker engine
- Running your first container
- Building containers
- Learning what containers are running and removing them
- Using volumes to persist data
- Using bind mounts to support development
- Using container networking to support multi-container applications
- Converting from Docker Compose with `kompose`
- Using image layer caching to speed up builds and reduce push/pull size
- Using multi-stage builds to separate build-time and runtime dependencies

## Getting Started

### Running your first minikube cluster

```
minikube start --kubernetes-version=v1.21.4
```

### Adding registries

open `~/.aws/credentials` in an external window we will need to copy from there

```
minikube addons configure registry-creds
```
Yes to aws fill in blanks

no to the rest

```
# enamble remote registries
minikube addons enable registry-creds
# enable local docker registry
minikube addons enable registry
```

### Adding ingress addon

```
minikube addons enable ingress
```

### switching from docker desktop to minikubes docker engine

No docker desktop is needed to use mini kube however you will need tjhe docker cli.

on mac
```
brew install docker
```

swap out the env
```
eval $(minikube -p minikube docker-env)
```

### the kube dashboard

This is a local step. there have been numerous instances of this being used as an entry point for hacking into a production system but its nice for local work.

```
minikube dashboard
```

### Running your first container

This will call a remote hello world container and expose it so you can see it.

1. Create a Deployment using the following command:

    ```shell
    kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0
    ```

    Output:

    ```shell
    deployment.apps/web created
    ```

1. Expose the Deployment:

    ```shell
    kubectl expose deployment web --type=NodePort --port=8080
    ```

    Output:

    ```shell
    service/web exposed
    ```

1. Verify the Service is created and is available on a node port:

    ```shell
    kubectl get service web
    ```

    Output:

    ```shell
    NAME      TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
    web       NodePort   10.104.133.249   <none>        8080:31637/TCP   12m
    ```

1. Visit the service via NodePort:

    ```shell
    minikube service web --url
    ```

    Output:

    ```shell
    http://172.17.0.15:31637
    ```


### Building containers
```
minikube build ngnix-demo/ -t nginx-demo
```
