---
@title[Docker Hub]
## Docker Hub

Es el repositorio por defecto de imágenes para contenedores Docker https://hub.docker.com
Se pueden encontrar imágenes tanto oficiales como no oficiales y a través de un registro gratuito podemos aportar a la comunidad.

---
@title[Buscar imágenes]
## ¿Cómo buscar imágenes?

Mediante línea de comando se ejecuta lo siguiente:

```
$ docker search nginx
NAME                      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
nginx                     Official build of Nginx.                        8341      [OK]
jwilder/nginx-proxy       Automated Nginx reverse proxy for docker c...   1314                 [OK]
richarvey/nginx-php-fpm   Container running Nginx + PHP-FPM capable ...   544                  [OK]
```


---
@title[Descargar imagen]
## Descargar una imagen

Para descargar una imagen ejecutamos lo siguiente:

```
$ docker pull httpd
Using default tag: latest
Trying to pull repository docker.io/library/httpd ...
latest: Pulling from docker.io/library/httpd
f2b6b4884fc8: Pull complete
Digest: sha256:b54c05d62f0af6759c0a9b53a9f124ea2ca7a631dd7b5730bca96a2245a34f9d
Status: Downloaded newer image for docker.io/httpd:latest
```
>**Nota:** Si no se especifica la versión de la imagen, se descargará la última versión (latest).

---
@title[Iniciar contenedor]
## Iniciar un contendor

Para iniciar un contendor y mantenerlo en ejecución ejecutamos lo siguiente:

```
$ docker run -d httpd
87595b724f012b29857a55283383c4214e07188dfe6a06553cc329282c336f0e
```

