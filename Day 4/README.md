# Docker CLI Commands

| Command | Description |
| --- | --- |
| ***docker ps*** | It shows all running container |
| ***docker ps -a*** | It shows all container. (Running + Not Running) |
| ***docker logs [ID]*** | Shows all logs of a specific container |
| ***docker run -it ubuntu*** | Creates and starts a container |
| ***docker run -it [IMAGE] sh*** | Creates and starts a container with shell session |
| ***docker rename [CONTAINER_NAME] [NEW_NAME]*** | Rename an existing container |
| ***docker pull [IMAGE]*** | Pull an image from a registry |
| ***docker push [IMAGE]*** | Push an image to a registry |
| ***docker images*** | List all image that are locally stored with the docker engine |
| ***docker history [IMAGE]*** | Show the history of an image |
| ***docker container prune*** | Remove all stopped container |
| ***docker image prune*** | Remove all dangling image |
| ***docker image rm [IMAGE]*** | Remove image |
| ***docker build -t [IMAGE_NAME]:[TAG_NAME] [DOCKERFILE_PATH]*** | Build an image with tag |
| ***docker image tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]*** | Create an image with tag using existing image |
| ***docker image save -o OUTPUT_FILE.[zip/tar] SOURCE_IMAGE*** | Export an image to local storage |
| ***docker image load -i SOURCE_FILE.[zip/tar]*** | Import an image from local storage |
