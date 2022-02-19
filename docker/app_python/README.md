# Instructions for downloading and compiling the Docker image

Attention:

1) The application run here was developed by Andreyev Melo and is very well documented in the links below.

* https://github.com/andreyev/prometheus_hands-on/tree/demo/demo

2) Install **Docker** .

3) Start the containers.

```sh

cd docker/app_python

docker build -f Dockerfile -t andreluys01/app-python:1.0.0 .
docker run -i -t --name myapp-python -p 81:8001 -p 82:8002 andreluys01/app-python:1.0.0
```

4) Access the app in the URL http://localhost:81 or http://localhost:82  (for HTTP).

5) Stop the containers.

```sh
docker stop myapp-python
```
