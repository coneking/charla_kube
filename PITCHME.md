---?image=images/kubernetes.png&size=auto 40%
@title[Inicio]

---?image=images/kismatic.png&size=auto 40%
@title[Kismatic]

---
@title[Descripción_Nodos]

## Descripción de nodos

- etcd
  - Proporcionan almacenamiento de datos para los nodos Master. |
- master
  - Proporcionan API Endpoints y administran los Pods de los nodos Workers. |
- worker
  - Nodos que almacenan el despliegue de Pods. |


---
@title[Hardware]

### Requerimientos mínimos de hardware

Nodo   | CPU     | Ram  | Disk (dev) | Disk (prod)
---    | ---     | ---  | ---        | ---
etcd   | 1, 2GHz | 1 GB | 8 GB       | 50 GB
master | 1, 2GHz | 2 GB | 8 GB       | 50 GB
worker | 1, 2GHz | 1 GB | 8 GB       | 200 GB


---
@title[Plan_etcd]

### Plan para nodos etcd


Nº Nodos | Descripción
---          | ---
1        | Inseguro. Entornos de desarrollo
3        | Soporta fallas en cualquier nodo
5        | Soporta fallas en dos nodos
7        | Soporta fallas en tres nodos

---
@title[Plan_master]

### Plan para nodos master

Nº Nodos | Descripción
---      | --- 
1        | Inseguro. Entornos de desarrollo
2        | Soporta fallas en cualquier nodo

---
@title[Info_Planning]

Más información sobre plan de instalación [Cluster Kubernetes](https://github.com/apprenda/kismatic/blob/master/docs/plan.md)

---
@title[Prerequisitos]

## Prerequisitos (nodos)

- Crear usuario con permisos de sudo. |
- Crear y copiar llave de privacidad ssh. |
- Deben tener salida a internet. |
- Hostname debe ser el mismo que en la configuración de kismatic. |
- No deben tener swap. |
- Debe tener VG para /var/lib/docker (recomendado). |
- En /etc/resolv.conf debe tener la línea search.  |

+++
@title[Práctica]
## Práctica

Creación de Playbooks (Ansible)

---
@title[Info Kismatic]

Más información sobre [Kismatic](https://github.com/apprenda/kismatic)

---
@title[Gracias]

# GRACIAS