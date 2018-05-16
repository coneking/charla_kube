---?image=images/kubernetes.png&size=auto 40%
@title[Inicio]

---
@title[Deployment]

## Despliegue de aplicaciones

Los despliegues (deployment) se crean en un archivo formato `yaml` y se ejecutan:
<br>

```
kubectl -f create archivo.yaml
```
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

Si no se indica la cantidad de replicas, creará un Pod por deploy.

---
@title[Service]

## Creación de Service

Los recursos Service se crean en un archivo formato `yaml` y se ejecutan:
<br>

```
kubectl -f create archivo.yaml
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
---
@title[Prerequisitos]

## Prerequisitos (nodos)

- Deben tener salida a internet. |
- Crear usuario con permisos de sudo. |
- Crear y copiar llave de privacidad ssh. |
- No deben tener swap. |
- Hostname debe ser el mismo que en la configuración de kismatic. |
- En /etc/resolv.conf debe tener la línea search. |
- Debe tener VG para /var/lib/docker (recomendado). |


---
@title[Práctica1]

## Práctica 1

- Crear llave ssh.
- Playbook (crear usuario, copiar llave, agregar sudo).

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
