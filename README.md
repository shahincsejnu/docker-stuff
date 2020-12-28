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
