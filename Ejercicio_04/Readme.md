# Taller Docker & Kubernetes 2020103 - Ejercicio 04
Docker file utilizado para generar la imagen que corra la aplicación PasswordApi contenida en la carpeta deploymentes.

## Imagen generada

[Ejercicio_04 en DockerHub](https://hub.docker.com/repository/docker/anacuenca/ejercicio_04/tags?page=1&ordering=last_updated)

```
 docker pull anacuenca/ejercicio_04:latest 
```

## Comandos para crear la imagen y publicarla

```
 docker build -t ej_04 . --build-arg JAR_FILE=./deployments/passwordapi.jar
 docker run -p 8080:8080 ej_04
 docker tag ej-04 anacuenca/ejercicio_04
 docker push anacuenca/ejercicio_04

```
