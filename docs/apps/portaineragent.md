# Portainer Agent

Portainer Agent is used to work around a Docker API limitation. When using the Docker API to manage a Docker environment, the user interactions with specific resources (containers, networks, volumes and images) are limited to these available on the node targeted by the Docker API request.

Docker Swarm mode introduce the concept of cluster of Docker nodes. With that concept, it also introduces the services, tasks, configs and secrets which are cluster aware resources. This means that you can query for the list of service or inspect a task inside any node on the cluster as long as you're executing the Docker API request on a manager node.

Containers, networks, volumes and images are node specific resources, not cluster aware. If you want to get the list of all the volumes available on the node number 3 inside your cluster, you need to execute the request to query the volumes on that specific node.

The agent purpose aims to solve that issue and make the containers, networks and volumes resources cluster aware while keeping the Docker API request format.

- App: [[Website](https://www.portainer.io/)] [[App Source](https://github.com/portainer/agent)]
- Docker Image: [[Docker Hub](https://hub.docker.com/)] [[Image Source](https://hub.docker.com/r/portainer/agent)]

---
