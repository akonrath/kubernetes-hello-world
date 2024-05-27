## Summary
This repo deploys a Hello World application to a Kubernetes cluster and can be tested locally.

## Prerequisites
The following must be installed:
- docker
- helm
- kubectl

## Installation and Configuration
### Docker
A local Kubernetes cluster can be created using Docker Desktop and the installation instructions can be found [here](https://docs.docker.com/desktop/kubernetes/).

### Traefik
The following will install the Traefik ingress controller using the Traefik [Helm chart](https://github.com/traefik/traefik-helm-chart):
```
helm repo add traefik https://traefik.github.io/charts
helm repo update
helm install traefik traefik/traefik
```

### Web server
The following will deploy the Hello World web server:
```
kubectl apply -f deployment.yaml -f service.yaml -f ingress.yaml
```

## Testing
The application will be reachable on localhost:
```
curl http://localhost/
```

## Removal
The web server can be removed with:
```
kubectl delete -f deployment.yaml -f service.yaml -f ingress.yaml
```

Traefik can be removed with:
```
helm uninstall traefik
helm repo remove traefik
```
