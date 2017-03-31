# Docker exploration

Example project showing Dockerization of a Spring boot application.

## Build example application
    git clone https://github.com/spring-guides/gs-spring-boot-docker.git
    cd gs-spring-boot-docker/complete
    mvn package
    cd target
    cp ../src/main/docker/Dokerfile .
    sudo docker build -t gs-spring-boot-docker .
    docker run -p 8080:8080 gs-spring-boot-docker 
    
You should now have created an image with the tag `gs-spring-boot-docker` verify with `sudo docker images`

Start a container based on the image with: 
    
    sudo docker run --name spring-application -p 8081:8080 -d gs-spring-boot-docker
     
Verify by doing: `curl http://localhost:8081`

The `-p` option states that port 8080 on the container will be exposed on localhost on port 8081

The `-d` option started the container in detached mode meaning that in order to access application logs we either ship
logs to a centralized server or simply:

    sudo docker logs spring-application

To access the running container:
    
    sudo docker exec -it spring-application /bin/sh

References:
- https://spring.io/guides/gs/spring-boot-docker/
- https://springframework.guru/running-spring-boot-in-a-docker-container/