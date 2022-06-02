# Kubernetes Super Mario
Infinite Mario in HTML5 JavaScript - using Canvas and Audio elements


This a fork: [PengBAI/mariohtml5](https://github.com/PengBAI/mariohtml5)



[![Docker Hub](https://img.shields.io/badge/docker-ready-blue.svg)](https://hub.docker.com/r/pengbai/docker-supermario/)


<img src="img/kubectl.gif" width="900" height="300" />


Image on docker hub: [https://hub.docker.com/r/pengbai/docker-supermario/](https://hub.docker.com/r/pengbai/docker-supermario/)

## Run Deployment


```
kubectl apply -f manifest

```

```
kubectl port-forward deployment/supermario-deployment 8600:8080

```

<img src="img/supermario.gif" width="800" height="600" />

