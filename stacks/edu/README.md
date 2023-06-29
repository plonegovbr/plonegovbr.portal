<div align="center"><img alt="logo" src="https://raw.githubusercontent.com/plonegovbr/plonegovbr.portal/main/docs/portalbrasil-edu.png" width="100" /></div>

<h1 align="center">PortalBrasil.edu</h1>

## Imagens

* Frontend: ghcr.io/plonegovbr/portal:latest
* Backend: ghcr.io/plonegovbr/portal_edu:latest

## Stacks

### Docker Compose

Faça o download do arquivo [docker-compose.yml](docker-compose.yml) e rode:

```bash
docker compose up -d
```

Após os serviços estarem iniciados:

* Acesse http://localhost:8080
* Crie um novo site
* Acesse http://universidade.localhost

### Helm Chart

Para instalar no Kubernetes (sem Ingress): 

```
helm repo add plone https://plone.github.io/charts
kubectl create namespace portalbrasil
helm install -n portalbrasil portalbrasil plone/plone --set "ingress.enabled=false,frontend.image.repository=ghcr.io/plonegovbr/portal,frontend.image.tag=latest,backend.image.repository=ghcr.io/plonegovbr/portal_edu,backend.image.tag=latest"
kubectl port-forward -n portalbrasil service/portalbrasil-plone-frontend 3000:3000
```