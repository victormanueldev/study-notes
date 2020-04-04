# Notas

### Problematica

Tenemos para nuestra aplicacion una infraestructura compleja, por ejemplo tenemos 
varios microservicios que deben ser "containerized" con Docker. Es una buena opcion manejar cada
contenedor por serparado pero de aquí surgen varios problemas relacionados con su 
administracion y escalabilidad. 

Dado esto, tenemos la siguiente problematica:

**Capacidad de Escalado**
- Creacion de multiples contenedores para mejorar el tiempo de respuesta
- Balanceadores de carga para manejar el trafico en cada grupo de contenedores

**Fallos en contenedores**
- Reiniciar los contenedores para recuperar el estado saludable de un servicio

**Fallos en nodos**
- Redistribuir los contenedores al levantar otro nodo
- Buscar un lugar idoneo entre nodos para poner los contenedores
- Mantenimiento del nodo

**Comunicacion interna**
- Conectar los contenedores dadas las subnet y los balanceadores existente
- Escalamiento complicado en caso de creacion de varios nodos y coneccion entre ellos

Debido a esto, se torna complejo el mantenimiento de la infraestructura para 
una sola persona, es un trabajo engorroso y conlleva mucho tiempo, además de alta
probabildad de fallo humano que puede afectar el funcionamiento normal de la app.


### Docker Swarm

- Initialize the swarm mode on Docker

```
$ docker swarm init
```

- Crear un contenedor en Swarm

```
$ docker service create --name web --publish 8080:80 ngnix 
```

**Service**
Es la definicion de la aplicacion que se quiere correr, ej. webserver, api, restapi...

**Task**
Es la ejecución de un servicio, que se correrá en un contenedor individual.
Un servicio puede tener varias tareas, las tareas se corren en contenedores

Listar las tareas de un servicio

```
$ docker service ps SERVICE_NAME
$ docker service ls # Lista los servicios de un nodo 
```

- Crea mas replicas de las tareas del servicio

```
$ docker service update --replicas=2 SERVICE_NAME
$ docker service scale web=4
```

**Service Definition**
Es la definicion del funcionamiento deseado para un servicio, que recibirá el 
swarm manager, quien garantiza que esta definicion se mantenga independientemente
de lo que pueda pasar a un contenedor

- Proceso de creacion de un servicio 
https://docs.docker.com/engine/swarm/images/service-lifecycle.png

- Prueba de estres 

```
$ ab -n 100 -c 4 http://localhost:3000/api/endpoint/
```

