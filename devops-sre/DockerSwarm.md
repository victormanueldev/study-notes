# Notes

### Problematics

We have a complex app infrastructure, for example we have several microservices that be must 
containerized with docker. This is a good option, manage each container separatelly
but surge several problems related to its management and scalability.

Due that, we have the following problems:

**Scalability**
- Creation of multiple containers to improve the response time.
- Load balancers to improve the traffic on each set of containers

**Failing Containers**
- Restart the containers to keep the healty state of a service

**Nodes Fails**
- Re-distribute the containers to up other node.
- Seach a ideal place between other nodes in order to put the new containers
- Node maintenance

**Networking**
- Connect the containers to subnets and load balancers
- Complex scalability in a creation of several nodes case and the connection between them

Due that, the infrastructure manteninance is very difficult for a only person.
It's a work could take a lot of time, and also there is a high possibility of
human failure, that could affect the normal operation of the app


### Docker Swarm

- Initialize the swarm mode on Docker

```
$ docker swarm init
```

- Crear a service in docker swarm

```
$ docker service create --name web --publish 8080:80 ngnix 
```

**Service:**
It's the definition of the app that will run in a node, ie webserver, rest-api, graph-api...

**Task:**
It's a service instance, that will run inside a individual container.
One service could have many tasks, the tasks run inside a container.

- List the service tasks

```
$ docker service ps SERVICE_NAME
$ docker service ls # Lista los servicios de un nodo 
```

- Create more replicas of the service tasks

```
$ docker service update --replicas=2 SERVICE_NAME
$ docker service scale web=4
```

**Service Definition:**
It's the definition of the desired state for a service, that will recieve the swarm manager,
who ensures that this definition is maintened independently of a container state.

- Process to creation of a service
https://docs.docker.com/engine/swarm/images/service-lifecycle.png

- Stress test on a endpoint
```
$ ab -n 100 -c 4 http://localhost:3000/api/endpoint/
```

