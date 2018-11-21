# DOCKER

`docker run` = `docker create` + `docker start`

**Create image**

```shell
$ docker run image-name
```

**Docker run with command**

```shell
# e.g.
$ docker run image-name command

# with command
$ docker run image-name echo hi there

# list image
$ docker run image-name ls
```


**Listening containers**

```shell
# Listening running containers
$ docker ps

# Lsitening all containers
$ docker ps --all
```

**Create Container**
```shell
$ docker create <image name>
```

**Start Container**
```shell
$ docker start <container id>
```

**Delete all Containers**
```shell
$ docker rm $(docker ps -a -q)
```

**Delete all Images**
```shell
$ docker rmi $(docker images -q)
```

**Delelte all**
```shell
$ docker system prune
```

**Logs**
```shell
$ docker logs <container id>
```

**Stop container**
```shell
$ docker stop <container id>
```

**Kill container**
```shell
$ docker kill <container id>
```

**Multi-command container**
```shell
# shell 1
$ dokcer run redis

# shell 2
$ docker exec -it <container id> redis-cli
```

**Shell of container**
```shell
$ docker exec -it <container id> sh
```

**Shell of container**
```shell
$ docker run -it <image name> sh
```

## Dockerfile

* **FROM** image hub
* **RUN** install dependencies
* **COPY** copy path folder to copy from on *your machine* relative to build content, place to copy stuff to inside the container
* **WORKDIR** any followings command will be  executed relative to this path in the container

**Build**
```shell
# Normal
$ docker build .

# with name userid/appName:version
$ docker build -t oscaroceguera/website:latest
```

**Run**
```shell
# Normal
$ docker run <ID>

# with name
$ docker run oscaroceguera/website:latest
```

**Expose the port**
```shell
$ docker run -p 5000:8080 <image id>
```

## Docker-compose

```shell
$ docker-compose up => dokcer run myImage

$ docker-compose up --build => docker build .
                            => docker run myImage

$ docker-compose down

# build specifically dockerfile
$ dokcer build -f Dockerfile.dev .
```

```shell
docker run -p 3000:3000 -v /app/node_modules -v $(pwd)/app <image id>

# -v /app/node_modules : put a book mark on the node_modules folder
# -v $(pwd)/app : Map the pwd into the '/app/' folder
```

## Test

```shell
# Run test
$ docker run <container id> npm run test

# fullscreen experence
$ docker run -it <container id> npm run test
```

## NGINX

```shell
# build
$ docker build .

# Start nginx
$ docker run -p 8080:80 <container id>
```