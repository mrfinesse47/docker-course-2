networks

//step 1 create a network

docker network create favorites-net

// step 2 run a container on that network.

docker run -d --name mongodb --network favorites-net mongo // note we don’t need a -p flag here because we don’t connect from host to this container.

// use the name of one container in another to talk on the network.

mongodb://mongodb:27017/swfavorites' // using the name of the mongoldb container

// step 4 run another on the network

docker run --name favorites --rm -p 3000:3000 --network favorites-net favorites-node
