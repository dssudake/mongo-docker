## Basic usage of MongoDB as a Docker Container

### Run mongoDB using docker commands

```bash
# Pull official MongoDB and mongo-express image from docker hub
docker pull mongo
docker pull mongo-express

# Create a docker network
docker network create mongo-network

# Run mongoDB container in detached mode
docker run -d \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=root \
  -e MONGO_INITDB_ROOT_PASSWORD=example \
  --net mongo-network \
  --name mongodb \
  mongo

# Run mongo-express container in detached mode
docker run -d \
  -p 8081:8081 \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=root \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=example \
  -e ME_CONFIG_MONGODB_SERVER=mongodb \
  --net mongo-network \
  --name mongo-express \
  mongo-express
```

Then you can hit http://localhost:8081 or http://host-ip:8081 in your browser to view MongoDB admin interface.
