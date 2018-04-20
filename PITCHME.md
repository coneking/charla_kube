---?image=images/kubernetes.png&size=auto
@title[Inicio]

---
@title[Introducción Kubernetes]
## ¿Qué es Kubernetes?

También conocido como **k8s**, es una plataforma Open-Source que permite la administración de contenedores (orquestador).
<br>
Se encarga del despliegue, la mantención y la escalabilidad de las aplicaciones.
<br>
[Kubernetes](https://kubernetes.io/docs/concepts/)

---
@title[Historia]
<p align="center"><img src="https://raw.githubusercontent.com/coneking/charla_kube/develop/images/googlelogo.png" width="500" /></p>

Desarrollado originalmente por Google en 2014 y liberado en el 2015 para la Cloud Native Computing Foundation es actualmente utilizado por grandes compañías como **Redhat**, **IBM**, **CoreOS**, **SAP** entre otras.

---
@title[Kubectl]
## Comando Kubectl

Para administrar Kubernetes utilizamos el comando **kubectl**, el cual interactúa con el cluster Kubernetes.
<br>

**Sintáxis:**
```
kubectl [command] [TYPE] [NAME] [flags]
```

+++
@title[Ejemplo Kubectl]
## Ejemplo

Listar los nodos del cluster Kubernetes:
```
$ kubectl get nodes
NAME           STATUS                     ROLES     AGE       VERSION
nodo1          Ready,SchedulingDisabled   <none>    20d       v1.8.0
nodo2          Ready                      <none>    20d       v1.8.0
nodo3          Ready                      <none>    20d       v1.8.0
```

---
@title[Instalación1]
### Instalación Kubectl Windows (chocolatey)

Ejecutar desde PowerShell o CMD:
```
choco install kubernetes-cli
```

<br>

Revisar la versión de `kubectl`:
```
kubectl version
```

([instalación chocolatey](https://chocolatey.org/install))

+++
@title[Instalación2]
### Instalación Kubectl Windows (binario)

Descargar el binario kubectl.exe
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/windows/amd64/kubectl.exe
```

---
@title[Conceptos]
## Conceptos

- Namespace |
- Pod |
- Service |
- Deployment |
- PV y PVC |
- ReplicaSets |
- Ingress |

+++
@title[Namespace]
## Namespace

Son áreas de trabajo que agrupan diferentes objetos como, deployment, services, ingress, etc.
<br>
Estas áreas de trabajo son independientes entre si.

```
$ kubectl get namespaces
NAME          STATUS    AGE
default       Active    43d
kube-public   Active    43d
kube-system   Active    43d
```

+++
@title[Pod]
## Pod

Un Pod es la unidad mas pequeña que se puede desplegar y puede ser modificada o programada desde Kubernetes.

```
$ docker container run -d httpd
87595b724f012b29857a55283383c4214e07188dfe6a06553cc329282c336f0e
```

+++
@title[Service]
## Service

Un Grupo de pod a los que se les define un concepto, con la logica de acceder a los mismos

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```
>**Nota:** Nota 

+++
@title[Deployment]
## Deployment

Es el controlador de implementaciones esta declara actualizaciones declaradas para Pods  y ReplicaSets.

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```
>**Nota:** Nota

+++
@title[PV y PVC]
## PV yPVC

**PV** Volumen Persistente , este define las asignaciones de almacenamiento, se puede divir en sub volumenes.
PVC Reivindicaciones de Volumen persisitente, un espacio de un PV que solicita ser asignado para un o mas pods.

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```
>**Nota:** Nota

+++
@title[PeplicaSets]
## PeplicaSets

Es un controldor de replicación.

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```
>**Nota:** Nota

+++
@title[Ingress]
## Ingress

Es el objeto API que gestiona es acceso externo a los servicios de un cluster.

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```
>**Nota:** Nota

---
@title[Práctica]
# Práctica

- Buscar una imagen |
- Descargar e iniciar un contenedor con parámetros |
- Verificar su estado y si es visible (web) |
- Eliminar solo el contenedor |

---
@title[Crear imagen]
## Crear una imagen

Para crear una imagen podemos hacerlo basándonos en un contenedor que hayamos iniciado, ajustándolo a nuestra necesidad.
También podemos crear una imagen en base a un archivo (Dockerfile).

+++
@title[Creando imagen1]
## Creando imagen desde contenedor

Debemos tener un contenedor iniciado y modificarlo.
Posteriormente ejecutamos lo siguiente:

```
$ docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
836d31ee29e2        httpd               "httpd-foreground"       8 minutes ago       Up 8 minutes        0.0.0.0:82->80/tcp     mi_apache

$ docker commit mi_apache mi_imagen
sha256:9f622d201933a6197310aa0995e746b3bbd736e04f186c39b1adb4b28494f316
```
---
@title[Práctica2]
# Práctica

- Iniciar un contenedor apache |
- Editar el contenedor |
- Crear una imagen |
- Iniciar un contenedor con la nueva imagen |
- Eliminar el contenedor y la imagen |
---

@title[Dockerfile]
## Dockerfile

Dockerfile define varios pasos que se requieren para la creación de una imagen.
Estos pasos se añaden a un archivo de texto, llamado de preferencia, Dockerfile.

+++
@title[Ejemplo Dockerfile]

### Ejemplo de archivo Dockerfile

```
# FROM Indica qué imagen base se usará
FROM ubuntu:16.04

# Se dejan los datos del creador de la imagen
MAINTAINER Nombre Apellido version: 1 correo@dominio.com

# Ejecuta tareas antes de crear la imagen
RUN apt-get update && apt-get install -y apache2 && apt-get clean && rm -rf /var/lib/apt/lists/*

# Asignación de variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

# Puerto o rango de puertos que se expondrán en la imágen
EXPOSE 80

# Comandos que se ejecutarán una vez se creé el contenedor
CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
```

+++
@title[Creando imagen2]

## Crear imagen desde Dockerfile

Se deben definir los pasos para la imagen en un archivo llamado `Dockerfile`. Posteriormente se crea la imagen de la siguiente manera:

```
$ docker build -t nombre_de_la_imagen:version .
```

---
@title[Práctica3]
# Práctica Dockerfile

- Crear un archivo Dockerfile con sus pasos |
- Crear una imagen (Dockerfile) |
- Iniciar un contenedor con la nueva imagen |
- Eliminar el contenedor y la imagen |

---
@title[Gracias]

# GRACIAS