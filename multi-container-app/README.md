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
