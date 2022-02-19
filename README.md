# Case SRE Descomplica

Desafio SRE Descomplica.

# Criando um cluster kubernetes com o kind

Execute os seguintes comandos para instalar o kind (Kubernetes in Docker), indicado apenas para ambiente de desenvolvimento e estudo.
Esses comandos também vão criar um cluster Kubernetes com três nós (1 master e 2 workers).
Não precisa ser root (tem o comando sudo quando for necessário de mais permissão).

```bash 

#----------------------------
# kind
#----------------------------
cd $HOME
VERSION=v0.11.1
cd /tmp
curl -Lo ./kind https://kind.sigs.k8s.io/dl/$VERSION/kind-$(uname)-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

cat << EOF > $HOME/kind-3nodes.yaml
# References:
# Kind release image: https://github.com/kubernetes-sigs/kind/releases
# Configuration: https://kind.sigs.k8s.io/docs/user/configuration/
# Metal LB in Kind: https://kind.sigs.k8s.io/docs/user/loadbalancer
# Ingress in Kind: https://kind.sigs.k8s.io/docs/user/ingress

# Config compatible with kind v0.11.1
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
    image: kindest/node:v1.22.0@sha256:b8bda84bb3a190e6e028b1760d277454a72267a5454b57db34437c34a588d047
  - role: worker
    image: kindest/node:v1.22.0@sha256:b8bda84bb3a190e6e028b1760d277454a72267a5454b57db34437c34a588d047
  - role: worker
    image: kindest/node:v1.22.0@sha256:b8bda84bb3a190e6e028b1760d277454a72267a5454b57db34437c34a588d047
EOF

kind create cluster --name mykube --config $HOME/kind-3nodes.yaml
kubectl cluster-info --context kind-mykube
kubectl get nodes
kubectl get pods
```

# Instalando a aplicação python com o helm 

Siga as instruções do arquivo [kubernetes/helm/app-python/README.md](kubernetes/helm/app-python/README.md).

A imagem Docker desta aplicação foi construida a partir do Dockerfile que esta em: [docker/app_python/README.md](docker/app_python/README.md).
