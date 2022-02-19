# Instruções para baixar e compilar a imagem Docker 

Atenção:

1) A aplicação python foi desenvolvida por Andreyev Melo e esta documentada em:
* https://github.com/andreyev/prometheus_hands-on/tree/demo/demo

2) Instale o **Docker** .

3) Compile a imagem Docker

```sh
cd docker/app_python

docker build -f Dockerfile -t andreluys01/app-python:1.0.0 .
```
4) Inicie o container:

```sh
docker run -i -t --name myapp-python -p 81:8001 -p 82:8002 andreluys01/app-python:1.0.0
```

5) Acesse a aplicação na URL http://localhost:81 ou http://localhost:82  (para HTTP).

6) Pare o container.

```sh
docker stop myapp-python
```
