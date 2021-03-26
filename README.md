This is a demo app for a docker workshop.

The only prerequisite for this demo app is to have Docker 18.0.6+ installed on your machine.

The app consists of 
* React frontend
* Express backend
* Postgres database

You can build the backend and frontend docker images

```
docker build -f todo-backend/Dockerfile -t docker-ws-backend:1.0 todo-backend/
docker build -f todo-frontend/Dockerfile -t docker-ws-frontend:1.0 todo-frontend/
```
and see the created docker images using
```
docker images
```

You can build the images directly using docker-compose as well using 
```
docker-compose build
```
and start them using
```
docker-compose up -d
```
or stop them using
```
docker-compose stop
```
and remove the containers using
```
docker-compose down
```

In order to see what containers are running on your system you can run
```
docker ps
```
and you can stop or force kill individual containers using 
```
docker stop <container_name> # will gracefully stop the container
docker kill <container_name> # will kill the process forcefully if it's not responding
```

You can publish the docker images to a docker registry (public or private) in order to reuse them on a different machine or share them with somebody.

To do this, you need to login in to the docker registry
```
docker login <docker_registry>
```
and push the docker image tags using a special tag name constructed as following:
`<docker_registry>/<username>/<image_name>:<tag_name>`

For example:
```
docker tag docker-ws-backend:1.0 docker.io/adinaclaudiatoma/docker-ws-backend:latest
docker push docker.io/adinaclaudiatoma/docker-ws-backend:latest

docker tag docker-ws-frontend:1.0 docker.io/adinaclaudiatoma/docker-ws-frontend:latest
docker push docker.io/adinaclaudiatoma/docker-ws-frontend:latest
```

Afterwards you can see your images in the docker registry and pull them on a different machine

```
docker pull docker.io/adinaclaudiatoma/docker-ws-backend:latest
```

https://hub.docker.com/repository/docker/adinaclaudiatoma/docker-ws-frontend
https://hub.docker.com/repository/docker/adinaclaudiatoma/docker-ws-backend

