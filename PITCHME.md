---?image=images/kubernetes.png&size=auto 40%
@title[Inicio]

---?image=images/kismatic.png&size=auto 40%
@title[Kismatic]

---
@title[Descripción_Nodos]

## Descripción de nodos

* etcd
  * Proporcionan almacenamiento de datos para los nodos Master.

* master
  * Proporcionan API Endpoints y administran los Pods de los nodos Workers.

* worker
  * Nodos que almacenan el despliegue de Pods.


---
@title[Hardware]

## Requerimientos mínimos de hardware

Nodos    | CPU               | Ram  | Disco (Prototyping) | Disco (Producción)
---      | ---               | ---  | ---                 | ---
etcd     | 1 CPU Core, 2 GHz | 1 GB | 8 GB                | 50 GB
master   | 1 CPU Core, 2 GHz | 2 GB | 8 GB                | 50 GB
worker   | 1 CPU Core, 2 GHz | 1 GB | 8 GB                | 200 GB


---
@title[Plan_etcd]

## Plan para nodos etcd


Cantidad de Nodos | Descripción
---          | ---  | ---
1        | Inseguro. Se usa para entornos pequeños de desarrollo
3        | Soporta fallas en cualquier nodo
5        | Soporta fallas en dos nodos a la vez
7        | Soporta fallas en tres nodos a la vez

---
@title[Plan_master]

## Plan para nodos master

Cantidad de Nodos | Descripción
---      | --- 
1        | Inseguro. Se usa para entornos pequeños de desarrollo
2        | Soporta fallas en cualquier nodo


---
@title[Prerequisitos]

## Prerequisitos (nodos)

* Crear usuario con permisos de sudo. |
* Crear y copiar llave de privacidad ssh. |
* Deben tener salida a internet. |
* Hostname debe ser el mismo que en la configuración de kismatic. |
* No deben tener swap. |
* Debe tener VG para /var/lib/docker (recomendado). |
* En `/etc/resolv.conf` debe tener la línea `search`. |

+++
@title[Práctica]
## Práctica

- Instalación [Kismatic](https://github.com/apprenda/kismatic/releases)

```
$ mkdir $HOME/kismatic; cd $HOME/kismatic
$ wget https://github.com/apprenda/kismatic/releases/download/v1.8.0/kismatic-v1.8.0-linux-amd64.tar.gz -O - | tar -xz
```

---
@title[Info Kismatic]

Más información sobre [Kismatic](https://github.com/apprenda/kismatic)

---
@title[Gracias]

# GRACIAS