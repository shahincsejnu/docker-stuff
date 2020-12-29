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
|`docker exec -it container_id sh`| To enter a container whose id is container_id|
|`exit` | To exit from a docker container|
|`ls -l`| |
|`hostname`| To see the hostname/container_id|
|`route -n`| Can see the routing table of the container|
