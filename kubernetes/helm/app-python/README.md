# app-python

![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)  ![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square)

My Helm chart for install app-python

# Prerequisitos

## Kubectl

Instale o comando:  ``kubectl``

```bash
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

kubectl version --client
```

## Helm

Instale o comando: ``helm``

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3

chmod 700 get_helm.sh

./get_helm.sh

helm version
```

# Instale a aplicão app-python:

* Primeiro acesse o cluster kubernetes:

* Mude os valores de acordo com a necessidade do ambiente no arquivo ``app-python/values.yaml``.

* Crie o namespace ``app-python``.

```bash
kubectl create namespace app-python
```

* Teste a instalação com o comando:

```bash
helm upgrade --install app-python -f app-python/values.yaml app-python/ -n app-python --dry-run
```

Acesse aplicação com o seguinte comando:

```bash
kubectl port-forward svc/app-python 8080:81 -n app-python
```
* Para instalar/atualizar a aplicação use o seguinte comando:

```bash
helm upgrade --install app-python -f app-python/values.yaml app-python/ -n app-python
```

* Liste todos os recursos criados pelo helm chart:

```bash
helm list all -n 'app-python'
```

## Desinstalando a aplicação

Para desinstalar a aplicação execute o seguinte comando:

```bash
helm uninstall app-python -n app-python
```

## Parâmetros

Os seguintes parâmetros podem ser configurados no arquivo values.yaml.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"andreluys01/app-python"` |  |
| image.tag | string | `"1.0.0"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` |  |
| livenessProbe.failureThreshold | int | `3` |  |
| livenessProbe.initialDelaySeconds | int | `20` |  |
| livenessProbe.path | string | `"/"` |  |
| livenessProbe.periodSeconds | int | `10` |  |
| livenessProbe.successThreshold | int | `1` |  |
| livenessProbe.timeoutSeconds | int | `5` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| readinessProbe.failureThreshold | int | `3` |  |
| readinessProbe.initialDelaySeconds | int | `20` |  |
| readinessProbe.path | string | `"/"` |  |
| readinessProbe.periodSeconds | int | `10` |  |
| readinessProbe.successThreshold | int | `1` |  |
| readinessProbe.timeoutSeconds | int | `5` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port1 | int | `81` |  |
| service.port2 | int | `82` |  |
| service.type | string | `"ClusterIP"` |  |
| tolerations | list | `[]` |  |
