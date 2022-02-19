# Original on:
# https://github.com/andreyev/prometheus_hands-on/blob/demo/demo/Dockerfile
# Thanks Andreyev ;-)

FROM python:3.10-bullseye
# Base image

# Image Information
LABEL maintener="Mags Ti" \
      author="Mags Solution TI André Luís " \
      mail="andre@magsti.com" \
      create="2022/01/09" \
      version="1.0.0" \
      description="Especify the image Docker of app" \
      license="v1.0.0"

# Getting the app
WORKDIR /usr/src/app
COPY demo.py .
RUN pip install prometheus_client

# Expose the app port
EXPOSE 8001
EXPOSE 8002

# Starting the service when starting the container
CMD [ "python", "./demo.py" ]