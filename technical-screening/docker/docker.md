# Docker

This section covers some scenarios for working with Docker

## What are the main parts of a Dockerfile

1. The `FROM` section determines what docker image to use as a base

## Walk through how you would build and push a Docker Image

1. Open a terminal in the directory that has the Dockerfile
1. Run `docker build .` to build the Dockerfile in the current directory
1. After the docker image has been built successfully, you need to tag it
1. Run `docker ps` to get the image name of the docker image that was just build
1. Run `docker tag IMAGE_ID DOCKER_REGISTRY.COM/IMAGE_NAME_YOU_WANT`
1. Then run `docker push IMAGE_NAME_YOU_WANT` to push the docker image to the registry

https://stackoverflow.com/questions/28349392/how-to-push-a-docker-image-to-a-private-repository

## Describe how you would try to make the image size smaller

1. Docker images are typically large because they are comprised of multiple layers
1. You can try to chain commands together to reduce the number of layers

    ```Dockerfile
    RUN apt update
    RUN apt -y install curl
    RUN apt -y install python3
    RUN apt -y install vim
    ```

    = 4 layers
    vs
    `RUN apt update && apt -y install curl python3 vim`
    = 1 layer

1. Another option is to use multi-stage builds

## Can you describe how multi-stage builds work and how to implement it?

1. Multi-stage builds work by having a "builder" docker image that downloads all the dependencies for an app, then builds the binary for the application. Then the binary can be copied to a more lightweight image without the build dependencies and can serve the application, resulting in a smaller image

1. You would setup a Dockerfile as normal to compile the application. You would define the `FROM` section as `FROM IMAGE AS builder` to notate its the builder image. Further down you would define the image to serve the binary and add a step to `COPY APP_NAME --from=builder` to show to copy that file to the new image.

See example Dockerfiles in this repo for more
