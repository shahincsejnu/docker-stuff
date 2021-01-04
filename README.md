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


## upload the docker image to [Docker Hub](https://hub.docker.com/)

### First way

- `docker login --username=<docker_hub_username>`
- `docker tag <id_of_the_created_image> <docker_hub_username>/<name_of_the_image>:<tag>`
- `docker push <docker_hub_username>/<name_of_the_image>:<tag>`

### Second way

#### During docker image build use this

- `docker build -t <docker_hub_username>/<image_name>:<tag> .`

#### then for uploading in docker hub

- `docker login --username=<docker_hub_username>`
- `docker push <image_repository_name>:<tag>`


## docker essential commands

|Commands|Uses|
|----|----|
|`ps aux` | To see which processes are currently running in your machine|
|`ip addr show` | To see the ethernet card in your machine including virtual ethernet card|
|`users`  or `sudo users` | To see the users, user id of the root user is 0|
|`id -u` | To get user id|
|`id -g` | To get group id|
|`docker ps`| To see all the containers running in your machine |
|`docker ps -a` | To see the all available docker container in your machine(running and not running) with their details|
|`docker images`| To see the all the images available in your machine|
|`docker stop container_id`| To stop running container |
|`docker stop $(docker ps -a -q)`| To stop all running containers|
|`docker rm container_id` | To remove/delete a docker container(only if stopped) |
|`docker rm $(docker ps -a -q)`| To delete all containers (only if stopped)|
|`docker logs container_id`| To display logs of a container|
|`docker inspect container_id` | To see full information about the container, will return json file|
|`docker exec -it container_id sh`| To enter a container whose id is container_id in shell|
|`docker exec -it container_id bash`| To enter a container whose id is container_id in bash|
|`exit` | To exit from a docker container|
|`ps` | To see the processes that are running inside a docker container|
|`ls -l`| |
|`hostname`| To see the hostname/container_id|
|`route -n`| Can see the routing table of the container|
|`docker build -t <give_an_image_name> .`| To build the docker image from the Dockerfile, by doing this the tag will be latest of the image|
|`docker image ls`| To see the list of all the available images with their tag, image id, creation time and size|
|`docker run -d -p 8080:8080 image_name`| To run the docker image with the port mapping and in detached mode|
|`docker run -p 8080:8080 image_name`| |
|`docker run -p 8081:8088 <image_name> start -p "8088"`| To set container port at 8088 and map pc port 8081 to container port 8088 |
|`delete rm container_id`| To delete a specific container with id container_id|
|`delete rmi image_id`| To delete a specific image|
|`delete rmi -f image_id`| To delete a docker image forcefully|
|`docker rm -f (docker ps -a `&#124;` awk '{print$1}')` | To delete all the docker container available in your machine|
|`docker rmi -f (docker images `&#124;` grep none `&#124;` awk '{print $3}')` | To delete all the docker images named none available in your machine|
|`docker build -t docker_hub_username/image_name:tag_name .` | Tell the docker daemon to fetch the docker file present in the current directory(that's what the . does), then to build the image and give it a specified tag, by doing this don't need to tag before pushing docker hub|
|`docker tag source_image[:tag] target_image[:tag]` | This command just creates an alias (a reference) by the name of the TARGET_IMAGE that refers to the SOURCE_IMAGE. That’s all it does. It’s like assigning an existing image another name to refer to it. Notice how the tag is specified as optional here as well, by the [:TAG]|
|`docker rmi -f $(docker images -a -q)` | To delete all the images, but before this you should remove all the containers which are created from this images|
|`docker rm -vf $(docker ps -a -q)` | To delete all containers including its volumes usee|
|`docker container prune` | |
|`docker image rm <image_name>` | To delete a specific image|
|`docker run -v <absolute_host_path/.env>:<container_path/.env> -p 8088:8089 <image_name> start -p 8089`| To run the docker image where did not provide the .env file using docker mounting volumes on host|


