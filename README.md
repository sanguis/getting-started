# Minikube Getting Started Tutorial

This tutorial has been written with the intent of helping folks get up and running
with containers and is designed to work with Docker Desktop. While not going too much
into depth, it covers the following topics:

- running your first minikube cluster
- adding AWS registries
- adding ingress addon
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

### Running your first container


### Building containers
### Learning what containers are running and removing them
### Using volumes to persist data
### Using bind mounts to support development
### Using container networking to support multi-container applications
### Converting from Docker Compose with `kompose`
### Using image layer caching to speed up builds and reduce push/pull size
### Using multi-stage builds to separate build-time and runtime dependencies

## Development

This project has a `docker-compose.yml` file, which will start the mkdocs application on your
local machine and help you see changes instantly.

```bash
docker-compose up
```

## Contributing

If you find typos or other issues with the tutorial, feel free to create a PR and suggest fixes!

If you have ideas on how to make the tutorial better or new content, please open an issue first before working on your idea. While we love input, we want to keep the tutorial  scoped to newcomers.
As such, we may reject ideas for more advanced requests and don't want you to lose any work you might
have done. So, ask first and we'll gladly hear your thoughts!
