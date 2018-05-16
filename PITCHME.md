---?image=images/kubernetes.png&size=auto 40%
@title[Inicio]

---
@title[Deployment]

## Despliegue de aplicaciones

Los despliegues (deployment) se crean en un archivo formato `yaml` y se ejecutan:
<br>

```
kubectl create -f archivo.yaml
```
+++
@title[Ejemplo]

<p align="center"><img src="https://raw.githubusercontent.com/coneking/charla_kube/dia7/images/deploy1.jpg" width="600" /></p>


+++
@title[Ejemplo2]

<p align="center"><img src="https://raw.githubusercontent.com/coneking/charla_kube/dia7/images/deploy2.png" width="600" /></p>

---
@title[Ejemplo_Deployment]

## Ejemplo Deployment

```yaml
apiVersion: extensions/v1beta1 
kind: Deployment ----> Tipo de objeto o recurso 
metadata:   
  name: nginx-deployment ----> Nombre del despliegue   
  labels:     
    app: nginx
spec:   
  replicas: 1 ----> Cantidad de replicas   
  selector:     
    matchLabels:       
      app: nginx   
    template:     
      metadata:       
        labels:         
	  app: nginx     
      spec:       
        containers: ----> El/los contenedores del pod       
	- name: nginx ----> Nombre del contenedor         
	  image: nginx:1.10.2 ----> Imagen del contenedor         
	  ports:         
	  - containerPort: 80 ----> Puerto del contenedor
```

---
@title[Deployment2]

Otra forma de crear un "deployment" es a través de línea de comando:

```
kubectl -n "Nombre_Namespace" run "Nombre_Deploy" --image="Nombre_de_Imagen"
```
<br>
Si no se indica la cantidad de replicas, creará un Pod por deploy.

---
@title[Service]

## Creación de Service

Los recursos Service se crean en un archivo formato `yaml` y se ejecutan:
<br>

```
kubectl create -f archivo.yaml
```


---
@title[Ejemplo_Service]

## Ejemplo Service

```yaml
apiVersion: v1
kind: Service ----> Tipo de objeto o recurso
metadata:
  name: my-service ----> Nombre del servicio
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP ----> Protocolo a usar
    port: 80 ----> Puerto a exponer
    targetPort: 80 ----> Puerto del pod
```
---
@title[Service2]

Otra forma de crear un recurso "service" es a través de línea de comando:

```
kubectl -n "Nombre_Namespace" create service "Tipo_servicio" "Nombre_service" --tcp=[port]:[target]
```
<br>
Posteriormente se debe editar para hacer coincidir con los pods que necesita balancear.

---
@title[Replicasets]


---
@title[Información]

Ayudas de comando kubectl [Kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

---
@title[Práctica1]

## Práctica 1

- Crear un archivo tipo Deploy para nginx. |
  - labels: |
    - app: nginx |
    - clase: dia-7 |
  - Replicas: 2 |
  - Contenedor: nginx:1.7.9 |
  - containerPort: 80 |
- Generar deploy con el archivo previamente creado. |

+++
@title[Práctica2]

## Práctica 2

- Playbook (deshabilitar swap, reconfigura grub, elimina lv).

+++
@title[Práctica3]

## Práctica 3

- Playbook (reconfigurar hostname, /etc/resolv.conf).

---
@title[Gracias]

# GRACIAS
