commands

#### a basic form of starting a mongo db image

```
    docker run --name mongodb --rm -d mongo
```

- this will pull a mongo db image from docker hub

- however we may want to publish a port since we are still running everything on the local machine at this point by:

```
    docker run --name mongodb --rm -d -p 27017:27017 mongo
```

- we can find that the mongo db image runs on port 27017 internally from looking at documentation

### build the backend image

```
    docker build -t goals-node .
```

- we gave it the tag of "goals-node"

##### now run a container based on that newly created image

```
    docker run --name goals-backend --rm -d goals-node
```

- this fails to run because the original mongo db on the backend was running on localhost.

- also it fails if I use host.docker.internal since mongodb is no longer running on the host and it is in the container

- so I decided to make a docker network

```
    docker network create mongo-net
```

- now I have to change the host.docker.internal address to the name of the mongo container. \*remember to rebuild the image since code has changed. and have to run the original mongo container with --network mongo-net flag.

```
    docker run --name mongodb --network mongo-net --rm -d mongo
```

- and run the backend with the network flag as well

```
    docker run --name goals-backend --network mongo-net --rm -d goals-node
```

- but now the front end needs the backend to publish ports since it is no longer running on the localhost.

```
    docker run --name goals-backend --network mongo-net --rm -d -p 80:80  goals-node
```

#### now we are going to dockerize the front end application

- after writing the docker file in the frontend dir

```
    docker build -t goals-react .
```

- now run the container

```
    docker run --name goals-frontend --rm -p 3000:3000 -d goals-react
```
