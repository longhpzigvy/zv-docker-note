# Zigvy Docker Note

## Content
TBA

## Setup
Head to [Docker installation guide](https://docs.docker.com/install/overview/) for more deail

## Basic commands

### Images
- List current active images
```
docker image ls
# or
docker images
```
- List all images
```
docker image ls -a
# or
docker images -a
```
- Remove an image
```
docker image rm image_name/image_id    # require all containers must be stopped
docker image rm image_name/image_id -f # force delete, all container will be removed

# or
docker rmi image_name/image_id

# example
# docker image rm 59ab3f4
```
- Build/Rebuild an image from Dockerfile
```
docker build [OPTION] path_to_Dockerfile

# Useful option
-t image_name - associate a meaningful tag (name) for an image

# example
# docker build -t test .
# docker build -t test ~/Zigvy/docker-tutorial
```
### Containers
- List current active containers
```
docker container ls
```
- List all containers
```
docker container ls -a
```
- Remove a container
```
docker container rm container_name/container_id # you may want to stop the container first

# or
docker rm container_name/container_id

# example
# docker container rm 59ab3f4
```
- Create and run a container from an image
```
docker [OPTION] run image_id/image_name

# Useful option
--name name: Create a container with given name
-d: Run in daemon mode
-t: Connect stdout to current tty (terminal)
-i: Allow user to interact with docker shell
--add-host k:v: Add host with name = k and ip = v to /etc/hosts file
--rm: Clean up, automatically remove the container once existed

# example
# docker run --name docker-tut-con docker-tut -it -d
```
- Stop a container without removing it
```
docker stop [OPTION] container_name/container_id
```

### Docker compose
- Run all services defined within the docker-compose.yml
```
docker-compose [OPTION] up

# Useful option
-d: detach
--build: always build an image before start
```

### More information
- [docker image](https://docs.docker.com/engine/reference/commandline/image/)
- [docker images](https://docs.docker.com/engine/reference/commandline/images/)
- [docker container](https://docs.docker.com/engine/reference/commandline/container/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker-compose](https://docs.docker.com/compose/reference/)
- [More commands](https://docs.docker.com/engine/reference/commandline/)

## Dockerfile
```Dockerfile
FROM alpine:latest # Select base image, always required
WORKDIR /app # Create new working directory
COPY . /app # Copy current directory to working directory
RUN apk add py-pip # Run a command
RUN make /app
CMD python /app/app.py # Define a startup command
```

Reference: [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)

## Docker compose file
```yml
version: "3.7" # Docker compose version for this file
services: # Service defination
  db: # service name
    image: postgres:9.4 #service image, building service from direct image
    volumes: # define volumn for this service
      - db-data:/var/lib/postgresql/data

  vote:
    build: ./ # similar to image tag
    ports: # map port to the host
      - "5000:80"
    depends_on: # tell compose that this service should be wait for db to be started
      - db
```
Referece: [Compose file](https://docs.docker.com/compose/compose-file/)
