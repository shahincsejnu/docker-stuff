# docker-stuff

## Uninstall Old versions from your machine

`sudo apt-get remove docker docker-engine docker.io containerd runc`

## Install Using Repository

### SET UP THE REPOSITORY

- `sudo apt-get update`
- `sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common`
    
- `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
- `sudo apt-key fingerprint 0EBFCD88`
- `sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"`
   
### INSTALL DOCKER ENGINE

- `sudo apt-get update`
- `sudo apt-get install docker-ce docker-ce-cli containerd.io`


## Manage Docker as a non-root user (use docker without sudo)

- `sudo groupadd docker`
- `sudo usermod -aG docker $USER`
- log out and log back
- `newgrp docker`


## docker essential commands

|Commands|Uses|
|----|----|
|`ps aux` | To see which processes are currently running in your machine|
|`ip addr show` | To see the ethernet card in your machine including virtual ethernet card|
|`users`  or `sudo users` | To see the users, user id of the root user is 0|
|`id -u` | To get user id|
|`id -g` | To get group id|
|`docker ps`| To see all the containers running in your machine |
|`docker ps -a` | To see the all available docker container in your machine with their details|
|`docker images`| |
|`docker stop container_id`| To stop running container |
|`docker rm container_id` | To remove a docker container |
|`docker inspect container_id` | To see full information about the container, will return json file|
|`docker exec -it container_id sh`| To enter a container whose id is container_id in shell|
|`docker exec -it container_id bash`| To enter a container whose id is container_id in bash|
|`exit` | To exit from a docker container|
|`ls -l`| |
|`hostname`| To see the hostname/container_id|
|`route -n`| Can see the routing table of the container|
|`docker build -t image_name_in_small_case .`| To build the docker image from the Dockerfile|
|`docker image ls`| To see the list of all the available images with their tag, image id, creation time and size|
|`docker run -d -p 8080:8080 image_name`| To run the docker image with the port mapping and in detached mode|
|`docker run -p 8080:8080 image_name`| |
|`docker run -p 8081:8088 <image_name> start -p "8088"`| To set container port at 8088 and map pc port 8081 to container port 8088 |


