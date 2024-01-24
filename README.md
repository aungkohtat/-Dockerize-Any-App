# Dockerize-Any-App

## Dockerfile Create
```bash
# select the base image to run the app. We want to run a javascript app, so we use the node runtime image from docker hub
# we can use any image from docker hub. We can also use a custom image that we have created
# node:20-alpine -> node is the image name, 20-alpine is the tag
# alpine is a lightweight version of linux
# we can see complete list of node image tags here: https://hub.docker.com/_/node
FROM node:20-alpine

# set the working directory to /app. This is the directory where the commands will be run. We can use any directory name but /app is a standard convention
WORKDIR /app

# copy everything from the current directory to the PWD (Present Working Directory) inside the container. 
# First `.` is the path to the current directory on the host machine. Second `.` is the path to the current directory inside the container i.e., source and destination
# source - current directory on the host machine
# destination - current directory inside the container (/app)
COPY . .

# commands to run the app
CMD node hello.js

# build the image
# docker build -t hello-docker .
    # -t -> tag the image with a name
    # hello-docker -> name of the image
    # . -> path to the Dockerfile
  ```


  - `docker build -t hello-docker .`

  ```bash
  gitpod /workspace/Dockerize-Any-App/hello-docker (main) $ docker build -t hello-docker .
[+] Building 4.9s (8/8) FINISHED                                                                     docker:default
 => [internal] load build definition from Dockerfile                                                           0.0s
 => => transferring dockerfile: 99B                                                                            0.0s
 => [internal] load metadata for docker.io/library/node:20-alpine                                              0.9s
 => [internal] load .dockerignore                                                                              0.0s
 => => transferring context: 2B                                                                                0.0s
 => [1/3] FROM docker.io/library/node:20-alpine@sha256:8e6a472eb9742f4f486ca9ef13321b7fc2e54f2f60814f339eeda2  3.0s
 => => resolve docker.io/library/node:20-alpine@sha256:8e6a472eb9742f4f486ca9ef13321b7fc2e54f2f60814f339eeda2  0.0s
 => => sha256:be93293fd5362dfcc94826d8bd1f36150cb06ed2ed085d21d9dba20195faded7 42.17MB / 42.17MB               0.6s
 => => sha256:376f9b7a67706b1a26941e182521e904295efb7b090d524a191417621d70d0db 2.34MB / 2.34MB                 0.2s
 => => sha256:8e6a472eb9742f4f486ca9ef13321b7fc2e54f2f60814f339eeda2aff3037573 1.43kB / 1.43kB                 0.0s
 => => sha256:201a9b31be9fb5148ca40c9e727d5e559c659ed9521b3175ba73847026257e32 1.16kB / 1.16kB                 0.0s
 => => sha256:b677a20cbee9aac399b0c35f8856bb076851a9bba3d89b2a7db6a9287bc24260 7.14kB / 7.14kB                 0.0s
 => => sha256:661ff4d9561e3fd050929ee5097067c34bafc523ee60f5294a37fd08056a73ca 3.41MB / 3.41MB                 0.2s
 => => extracting sha256:661ff4d9561e3fd050929ee5097067c34bafc523ee60f5294a37fd08056a73ca                      0.1s
 => => sha256:4e53c60b2bbe88730ffe3d177c7169bd98e824643e5f9fa3f2656e67725b35f5 450B / 450B                     0.3s
 => => extracting sha256:be93293fd5362dfcc94826d8bd1f36150cb06ed2ed085d21d9dba20195faded7                      1.7s
 => => extracting sha256:376f9b7a67706b1a26941e182521e904295efb7b090d524a191417621d70d0db                      0.1s
 => => extracting sha256:4e53c60b2bbe88730ffe3d177c7169bd98e824643e5f9fa3f2656e67725b35f5                      0.0s
 => [internal] load build context                                                                              0.0s
 => => transferring context: 173B                                                                              0.0s
 => [2/3] WORKDIR /app                                                                                         0.0s
 => [3/3] COPY . .                                                                                             0.0s
 => exporting to image                                                                                         0.9s
 => => exporting layers                                                                                        0.9s
 => => writing image sha256:705e9c0041a8467def670a4703d394c1138628a6ffc8c98ce03b8c81104dc221                   0.0s
 => => naming to docker.io/library/hello-docker                                                                0.0s
gitpod /workspace/Dockerize-Any-App/hello-docker (main) $ 
  ```

```bash
gitpod /workspace/Dockerize-Any-App/hello-docker (main) $ docker images
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
hello-docker   latest    705e9c0041a8   3 minutes ago   137MB
gitpod /workspace/Dockerize-Any-App/hello-docker (main) $ 
```

```bash
gitpod /workspace/Dockerize-Any-App/hello-docker (main) $ docker run hello-docker
Hello from Docker 🐳
gitpod /workspace/Dockerize-Any-App/hello-docker (main) $ 
```
```bash
gitpod /workspace/Dockerize-Any-App (main) $ npm create vite@latest react-docker
Need to install the following packages:
create-vite@5.1.0
Ok to proceed? (y) y
✔ Select a framework: › React
? Select a variant: › - Use arrow-keys. Return to submit.
❯   TypeScript
    TypeScript + SWC
    JavaScript
    JavaScript + SWC

```
## react-docker

- `docker build -t react-docker .`

```bash
gitpod /workspace/Dockerize-Any-App/react-docker (main) $ docker build -t react-docker .
[+] Building 13.0s (12/12) FINISHED                                                                       docker:default
 => [internal] load build definition from Dockerfile                                                                0.0s
 => => transferring dockerfile: 1.62kB                                                                              0.0s
 => [internal] load metadata for docker.io/library/node:20-alpine                                                   0.6s
 => [internal] load .dockerignore                                                                                   0.0s
 => => transferring context: 53B                                                                                    0.0s
 => CACHED [1/7] FROM docker.io/library/node:20-alpine@sha256:8e6a472eb9742f4f486ca9ef13321b7fc2e54f2f60814f339eed  0.0s
 => [internal] load build context                                                                                   0.0s
 => => transferring context: 15.07kB                                                                                0.0s
 => [2/7] RUN addgroup app && adduser -S -G app app                                                                 0.6s
 => [3/7] WORKDIR /app                                                                                              0.0s
 => [4/7] COPY package*.json ./                                                                                     0.1s
 => [5/7] RUN chown -R app:app .                                                                                    0.7s
 => [6/7] RUN npm install                                                                                           9.3s
 => [7/7] COPY . .                                                                                                  0.0s 
 => exporting to image                                                                                              1.7s 
 => => exporting layers                                                                                             1.7s 
 => => writing image sha256:9883ed39694b45a60a0dc552ced31f9a5c57e874eca50c6fb37124acb0eba3b6                        0.0s 
 => => naming to docker.io/library/react-docker                                                                     0.0s
gitpod /workspace/Dockerize-Any-App/react-docker (main) $ 
```

```bash
gitpod /workspace/Dockerize-Any-App/react-docker (main) $ docker run react-docker

> react-docker@0.0.0 dev
> vite


  VITE v5.0.12  ready in 301 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

