# Taller Docker & Kubernetes 2020103 - Ejercicio 05



```

## HEALTHCHECK

Este comando permite verificar la salud del contenedor, retornando 0 si está ok o 1 en caso contrario. 
Puede utlizarse de dos maneras: 

**HEALTHCHECK [OPTIONS] CMD command: se ejecuta el comando recibido por parametro dentro del contenedor, puede ser un script o binario donde especifiquemos el servicio que se desea verificar el estado. 
**HEALTHCHECK NONE: desabilita las verificaciones de la imagen base

Parametros: 
** Interval: intervalo de tiempo en que deseamos se ejecuten los checks, default 30 segundos.
** Timeout: tiempo espera del check hasta considerar que fallo, default 30segundos.
** Start-period: tiempo permitido para la inicialización del contenedor a partir del cual se comenzaran a contabilizar los estados de los checks, default 0segundos.
** Retries: cantidad de verificaciones fallidas antes de considerar al contendero unhealthy, default 3.


Si se define el healthcheck al contenedor, al ejecutar ps, además de visualizar su estado tambien se informará un "estado de salud" 
que al inicio se encuentra en "starting" y luedo de cada check en "healthy".

Ejemplo de uso 

```
HEALTHCHECK --interval=30s --timeout=3s CMD curl --fail http://localhost:8091/pools || exit 1

```
## ONBUILD
Especifica comandos que se ejecutarán cuando la imagen se utilice en otro build, se utiliza 
en imagenes como base para crear otras imágenes que dependen de esta.

Es decir, se agrega una comando en los metadatos de la imagen que no se utilizará en la creación de la imagen base 
pero se disparará en los build de bases que utilicen esta. 

Ejemplo de uso
```
ONBUILD ADD . /app/src
ONBUILD RUN /usr/local/bin/python-build --dir /app/src

```

## VOLUME

Este comando se utiliza para montar un directorio, esto sirve para conservar los datos generados por los 
contenedores de docker o para acceder a archivos por ejemplo de configuración en el host.

Ejemplo de uso
```
$ docker run -d \
  --name devtest \
  -v myvol2:/app \
  nginx:latest

```
