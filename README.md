# I2CAT SONATA
This repository contains the modules for demonstrating the user management in Paderborn F2F, which takes place between the 7th and 9th of Marz.

## Requirements

These installations steps are valid for Ubuntu 14.04

####  Installing docker

###### Add Docker’s official GPG key:

```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

###### Add stable repository
```bash
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

###### Install docker
```bash
$ sudo apt-get update
$ sudo apt-get install docker-engine
```

###### Managing docker as regular user (non root)
```bash
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
```

###### Test the installation
```bash
$ docker run hello-world
```

#### Installing docker-compose
###### Install pip
```bash
$ sudo apt-get install python-pip
```
###### Install docker-compose using pip
```bash
$ pip install docker-compose
```
## Deployment
###### Deploy GK, adapter and keycloak with docker-compose
```bash
$ cd son-gkeeper/son-gtkusr/
$ docker-compose up --build
```
###### Wait until it's up and deploy catalogue with docker-compose
```bash
$ cd son-catalogue-repos/
$ docker-compose up --build
```
## Troubleshooting

- #### Error deploying adapter: Could not resolve keycloak address through DNS
Remove both dockers and start them again
```bash
$ docker rm -f sonata-adapter
$ docker rm -f sonata-keycloak
$ docker-compose up --build
```

## Tips
- #### Remove all containers
```bash
docker rm $(docker ps -a -q) -f
```
