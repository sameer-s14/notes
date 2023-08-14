# Docker commands

## Basic commands

1. docker pull
2. docker start
3. docker stop
4. docker run = pull + start
5. docker ps
6. docker ps -a
7. docker images / docker image ls


## Difference between docker run and starts        
1. docker start just start the container if it is present whereas run command also checks if the image is present or not if not then it fetches from the docker hub. 
2. run mostly used with images to provide configuration but in start we can just start the container which is already present without even modifying the configuration.
3. we cant pass parameters like -p to start command.
4. run command can create new container.


### docker Run options

1. docker run [-d, -it] imageName
2. docker run [--name containerName] imageName
3. docker run [-p6000:6796] imageName

## Debugging containers

1. docker logs [containerId or containerName]
2. docker exec - get the terminal of running container
   ex- docker exec -it [imageName] bash
