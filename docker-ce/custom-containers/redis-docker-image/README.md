# Redis docker image
This docker image is an installation of ubuntu with reddis installed. 

## Build the docker image
With a basic dockerfile, you can build an image with this command:
```
docker build -t redis-server . 
```

## Run the docker instance
Create a new docker container with the name "redis_instance" from our image "redis-server". Since we have the -d option enabled, the container will run as a daemon. 
```
docker run -d --name redis_instance -t redis-server

## Docker hub
```
docker login
docker search <keyword>
docker pull <user-name>/<repo-name>
docker push <user-name>/<repo-name>
```