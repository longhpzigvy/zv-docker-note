# Zigvy Docker Note

## Content
- [Zigvy Git Workflow](#zigvy-git-workflow)
  - [Content](#content)
  - [Setup](#setup)
  - [Straight Forward Workflow](#straight-forward-workflow)
  - [Fork & Pull Request Workflow](#fork--pull-request-workflow)
  - [Other scenario](#other-scenario)

## Setup
Head to [Docker installation guide](https://docs.docker.com/install/overview/) for more deail

## Basic commands

### Images
- List current active images
```
docker images ls
```
- List all images
```
docker images ls -a
```
- Remove an image
```
docker images rm image_name/image_id    # require all containers must be stopped
docker images rm image_name/image_id -f # force delete, all container will be removed

# example
# docker images rm 59ab3f4
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

### More information
- [docker image](https://docs.docker.com/engine/reference/commandline/container/)
- [docker container](https://docs.docker.com/engine/reference/commandline/images/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker-compose](https://docs.docker.com/compose/reference/)
