---?image=images/kubernetes.png&size=auto
@title[Inicio]

---
@title[Introducción Kubernetes]
## ¿Qué es Kubernetes?

También conocido como **k8s**, es una plataforma Open-Source que permite la administración de contenedores (orquestador).
<br>
Se encarga del despliegue, la mantención y la escalabilidad de las aplicaciones.

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
@title[Win-Instalación1]
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
@title[Win-Instalación2]
### Instalación Kubectl Windows (binario)

Descargar el binario kubectl.exe
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/windows/amd64/kubectl.exe
```

---
@title[Linux-Instalación1]
### Instalación Kubectl Linux (yum)

Crear repositorio
```
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

yum install -y kubectl
```

<br>

Revisar la versión de `kubectl`:
```
kubectl version
```

+++
@title[Linux-Instalación2]
### Instalación Kubectl Linux (binario)

Descargar el binario kubectl
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl
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

Un Pod es la unidad más pequeña que se despliega y puede ser modificada o programada desde Kubernetes.
Puede estar compuesta de uno o más contenedores.
```
$ docker container run -d httpd
87595b724f012b29857a55283383c4214e07188dfe6a06553cc329282c336f0e
```

+++
@title[Service]
## Service

Un grupo de pod a los que se les define un concepto, con la logica de acceder a los mismos.

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```

+++
@title[Deployment]
## Deployment

Es el controlador de implementaciones, esta declara actualizaciones para Pods  y ReplicaSets.

```
$ docker container stop 87595b7
87595b7

$ docker container rm 87595b7
87595b7
```

+++
@title[PV y PVC]
## PV y PVC

**PV** Volumen Persistente , este define las asignaciones de almacenamiento, se puede divir en sub volumenes.
**PVC** Reivindicaciones de Volumen persisitente, un espacio de un PV que solicita ser asignado para un o mas pods.

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

+++
@title[Info]

Más información sobre [Conceptos Kubernetes](https://kubernetes.io/docs/concepts/)

---
@title[Gracias]

# GRACIAS