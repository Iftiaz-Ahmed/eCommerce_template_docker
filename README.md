# Ecommerce Template with Docker
-------------------------------

[](#ecommerce-template-with-docker)

### Create a network for the docker containers

[](#create-a-network-for-the-docker-containers)

`docker network create ecommerce`

### Build the clients

[](#build-the-client)

```
cd frontend
docker build -t ecommerce-frontend .
```

```
cd admin
docker build -t ecommerce-admin .
```


### Run the clients

[](#run-the-client)

`docker run --name=frontend --network=ecommerce -d -p 5173:5173 ecommerce-frontend`

`docker run --name=admin --network=ecommerce -d -p 5174:5174 ecommerce-admin`

### Verify the client is running

[](#verify-the-client-is-running)

Open your browser and type `http://localhost:5173`

Open your browser and type `http://localhost:5174`

### Run the mongodb container

[](#run-the-mongodb-container)

`docker run --network=ecommerce --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongodb:latest`

### Build the server

[](#build-the-server)

```
cd backend
docker build -t ecommerce-backend .
```


### Run the server

[](#run-the-server)

`docker run --name=backend --network=ecommerce -d -p 4000:4000 ecommerce-backend`

Using Docker Compose
--------------------

[](#using-docker-compose)

`docker compose up -d`
