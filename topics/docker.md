# Docker

## What is Docker?

- Docker is a containerization platform which packages your application and all its dependencies together in the form of containers so as to ensure that your application works seamlessly in any environment be it development or test or production.
- Docker containers, wrap a piece of software in a complete filesystem that contains everything needed to run: code, runtime, system tools, system libraries etc. anything that can be installed on a server.
- This guarantees that the software will always run the same, regardless of its environment.

## What are docker images?

They are executable packages(bundled with application code & dependencies, software packages, etc.) for the purpose of creating containers. Docker images can be deployed to any docker environment and the containers can be spun up there to run the application.

## What can you tell about Docker Compose?

- It is a YAML file consisting of all the details regarding various services, networks, and volumes that are needed for setting up the Docker-based application. So, docker-compose is used for creating multiple containers, host them and establish communication between them. For the purpose of communication amongst the containers, ports are exposed by each and every container.

## Differentiate between COPY and ADD commands that are used in a Dockerfile?

- Both the commands have similar functionality, but COPY is more preferred because of its higher transparency level than that of ADD.
- COPY provides just the basic support of copying local files into the container whereas ADD provides additional features like remote URL and tar extraction support.

## Can you explain the difference between CMD and ENTRYPOINT?

- CMD command provides executable defaults for an executing container. In case the executable has to be omitted then the usage of ENTRYPOINT instruction along with the JSON array format has to be incorporated.
- ENTRYPOINT specifies that the instruction within it will always be run when the container starts.
  - This command provides an option to configure the parameters and the executables. If the DockerFile does not have this command, then it would still get inherited from the base image mentioned in the FROM instruction.
  - The most commonly used ENTRYPOINT is /bin/sh or /bin/bash for most of the base images.
- As part of good practices, every DockerFile should have at least one of these two commands

## How would you download a remote docker image to your machine

- `docker pull <image_name>`

## How do you create a docker container from an image?

- `docker run -it -d <image_name>`

## How would you connect to a running container

- `docker exec -it <container id> bash`

## How do you list all running docker images

- `docker ps`

## How would you build and deploy a custom docker image

- Open a terminal in the same folder as your Dockerfile

```sh
docker login
docker build .
docker images # get the id of the docker image
docker tag IMAGE_ID NEW_IMAGE_NAME:latest
docker push NEW_IMAGE_NAME:latest
```

## Dockerfile

- Know the components of a Dockerfile and how to make your own
- This uses the ubuntu docker image and installs python and an python app

```Dockerfile
FROM ubuntu
RUN apt-get update && apt-get install curl python
COPY main.py /app/main.py
WORKDIR /app
ENTRYPOINT ["python /app/main.py"]
```

## How do you keep docker images lightweight?

- Disable caching in commands
- Reduce the amount of layers
- Use multi-stage builds
- Run multiple commands on the same line

## What is a multi-stage docker build and whats the benefit?

- A multi-stage docker build is a technique used to keep dockerfiles small.
- An example, use a dockerfile to build the application, then copy the compiled application and place on a lightweight image like alpine to serve the compiled app.

```Dockerfile
# syntax=docker/dockerfile:1

FROM golang:1.16 AS builder
WORKDIR /go/src/github.com/alexellis/href-counter/
RUN go get -d -v golang.org/x/net/html
COPY app.go ./
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /go/src/github.com/alexellis/href-counter/app ./
CMD ["./app"]
```
