## Basic of Docker
To use docker for your project you will need to know few things:
1. Pull Docker image: Its an Operating system image placed on Docker repository which you can pull into your machine.
2. Create Contianer: Its a process of using the image you have downloaded and making it a runnable virtual machine.
3. Run Contianer: To run an instance of the container OS.
4. Expose Contianer: It allows you to access running contianer elements like ports/volume/terminal from host machine.

### Create a docker container (Full Command way)
#### Pull Docker image:
```
docker pull image_repo_name:tag
```
You can go here ```https://hub.docker.com/search/?type=image``` to grab an image of OS required for your poject.
Lets say I want to run a webserver, in that case I can use apache image as ```docker pull httpd:latest``` where httpd is the repo name and latest is the tag or version.

#### Create a Contianer
```
docker --create --name containerName image_repo_name:tag
```
For example if I like to create a container with apache then ```docker --create --name mywebserver apache:latest```

#### Run Container
```
docker run -it --name containerName
```

#### Expose Contianer
```
docker run -it --name containerName -p 80:80 -v ./myfolder:/var/www/html
```
Where p means publish but you can think it as a host vs guest port mapping. Here I am mapping host port 80 wuth guest/container port 80
-v denotes volume and we map host and container volumes.

### Other useful commands

#### List
To start an existing container ```docker start containerID```
To stop an existing container ```docker stop containerID```
To list all running images ```docker image```
To list all running and dormant images: ```docker image -a```
To list all running contianers ```docker ps ```
To remove image ```docker rmi imageID```
To remove container ```docker rm containerID``` (remember to stop the container before removing it)
To Execute a command or access container terminally ```docker exec -it contianerID /bin/bash```

### Create a docker container (DockerFile way)
You can pull image, configure the container and expose ports and volume all from one place using DockerFile.
