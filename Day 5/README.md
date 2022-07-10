# Working With Containers

| Command | Description |
| --- | --- |
| ***docker run -d [IMAGE]*** | It will start a container in detach mode. Which means it will run in background |
| ***docker run -d --name [NAME] [IMAGE]*** | It will start a container in detach mode with a custom name. |
| ***docker run -d --name web -p 5000:80 [IMAGE]*** | Run a container from the Alpine version 3.9 image, name the running container “web” and expose port 5000 externally,mapped to port 80 inside the container. |
| ***docker exec [CONTAINER] [COMMAND]*** | Execute a command in a running container |
| ***docker exec -it [CONTAINER] sh*** | Start a shell session in running container in interactive mode |
| ***docker stop [CONTAINER]*** | Stop a container |
| ***docker start [CONTAINER]*** | Resume a container |
| ***docker rm -f [CONTAINER]*** | Remove a running container |

### What is Volume?
---
The purpose of using Docker volumes is to persist data outside the container so it can be backed up or shared.

Docker volumes are dependent on Docker’s file system and are the preferred method of persisting data for Docker containers and services. When a container is started, Docker loads the read-only image layer, adds a read-write layer on top of the image stack, and mounts volumes onto the container filesystem.

| Command | Description |
| --- | --- |
| ***docker volume create [VOLUME_NAME]*** | It creates a new volume in docker |
| ***docker volume ls*** | List all the volumes |
| ***docker volume create [VOLUME_NAME]*** | It creates a new volume in docker |
| ***docker volume inspect [VOLUME_NAME]*** | It displays detailed information of one or more volumes. |
| ***docker volume rm [VOLUME_NAME]*** | Removes one or many volumes. |
| ***docker volume prune*** | Remove all the unused volumes. |
| ***docker run -d -p 5000:3000 -v [VOLUME_NAME]:[PATH] [IMAGE]*** | Start a container with a volume binded to it. |
| ***docker cp [CONTAINER]:[SRC_PATH] [DEST_PATH]*** | Copy file from container to host machine. |
| ***docker cp [SRC_PATH] [CONTAINER]:[DEST_PATH]*** | Copy file from host machine to container. |
| ***docker run -d -p 5001:3000 -v $(pwd):[DEST_PATH] [IMAGE]*** | Share source code with the container |
