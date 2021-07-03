# Docker tutorial

## Concepts

### Basic concepts

image: an environment composed of a list of installed programs and dependencies

container: a program that execute from the environement defined in an image

repository: the same way that we can have "git repositories" docker has the concept of "docker repository"
A docker repository is a storage place where the software teams/distributors can share their docker images.

The registry by default is [docker hub](https://hub.docker.com/).

When you want to download an image from the repository you can use the `docker pull` command.

Example: `docker pull hello-world`

Remark when you try to use `docker run` on an image that you don't have already dowloaded, it will try to download it from docker hub.

### Intermediate concepts

#### Create a custom docker image

We can also create our own docker images. To do so we need to create a `Dockerfile`.

#### docker volumes

Before we understand docker volumes let's start from an example.

Let's say we are running a database in a docker container.

Docker creates an "isolated bubble" for every container. This "bubble" is comprised a running program and a memory and even a hard disk memory.

This "bubble" is completely erased when the container is erased.

If in our example we are running a database inside our container, this means that all our data gets erased when the container is terminated.

In order to avoid that: docker has invented the concept of "docker volumes".

A "docker volume" is a repertory/directory that is shared between the "host machine" (the host machine means: "the computer running docker") and the container.

Which means every read or write on that directory, no matter if it is performed from the host or the container, will be seen by both of them.

## Cheatsheet

`docker images`: list the images that you already have downloaded with their version.

`docker ps`: list running containers

`docker ps -a`: list running and stopped containers

`docker run $IMAGE_NAME`: start a container from the image `$IMAGE_NAME`

Example: 

`docker run hello-world`


## Cleaning your containers

You can first list the stopped containers using `docker ps -a`

Then copy paste the image id (`$IMAGE_ID`):


`docker rm $IMAGE_ID`


Example:


```sh
sonia@brick:~/ark$ docker ps -a 
CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS                     PORTS     NAMES
2c84d6f68322   hello-world   "/hello"   4 seconds ago   Exited (0) 2 seconds ago             optimistic_rosalind
```

We have a stopped image with the id: 2c84d6f68322

We can stop it using the following command.

`docker rm 2c84d6f68322`

Remark: 

It also works with the image name:

`docker rm optimistic_rosalind`
