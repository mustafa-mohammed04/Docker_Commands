
1. how to search a docker image in hub.docker.com
```sh
docker search <imageName>
```
2. Download a docker image from hub.docker.com
```sh
docker image pull <image_name>:<image_version/tag>
```

3. Show all docker images on your local system
```sh
docker images
docker image ls
docker image ls -a
```

4. Build docker image from Dockerfile
```sh
docker build -t <image_name> . #the dot in the end specify the current directory where the Dockerfile is located 
```

5. Create a docker container from image
```sh
docker run --name <container_Name> <image_name>:<image_version/tag>

docker - run your container in back ground (detached)
 
docker run -d --name <container_Name> <image_name>:<image_version/tag>
```

6. Expose your application to host server
```sh
docker run -d --name <container_Name> -p <host_port>:<container_port> <image_name>:<Image_version/tag>

docker run -d --name httpd_container -p 8080:80 httpd:latest
```

7. Show all running containers
```sh
docker ps
docker container ls
```

8. Show all docker container (running, stpooed, terminated, etc...)
```sh
docker ps -a
docker container ls -a
```

9. Get inside a container

```sh
docker exec -it <container_Name> bash
```

10. Stop a container 
```sh
docker stop <container_id>
```

11. Start a container which is stopped 

```sh
docker start <container_id>
```
12. Remove a container

```sh
docker rm <container_id>
```

13. Remove docker image
```sh
docker rmi <image_id>
```
14. 2. Upload a docker image to hub.docker.com
``` sh
 docker push <username>/<imageName>
```
``` sh

## Arguments of Docker Commands ?
``` sh
   -it "Interactive Terminal"
```
``` sh
   -v "Volume Mapping"
```
``` sh
   -p "Port Mapping"
``` 
``` sh
   -e  "Environment Varibale"
```    
``` sh   
   -f "force kill or remove"
```    
``` sh      
   -a "all"
```    
   
``` sh   
   -d "detached " in Background
```    
   
``` sh   
   -a "attach in Foreground" >> "default" 
``` 
``` sh   
   -w "working directory in the container" >> $ docker run -w /app some-image
```    
``` sh   
   --name  container-name
```    

``` sh      
   --network  network-name
```   

## Setting resource limits ?
```sh
   $ docker run --cpus=2 --memory=4g some-image
```
## Setting container restart policy ?
``` sh   
   $ docker run --restart=always some-image
```

## Dockerfile
``` sh
   FROM : YOUR Base Image
   CMD : Specifies the command to run when a container is started from the Docker image that (change behvior)
   ENTRYPOINT : Specifies the command to run when a container is started from the Docker image ( but not change behvior )
   ADD : SRC- DEST (TAR AND URL)
   COPY : SRC-DEST
   ENV : Environment Variables
   ARG : Arguments
   REFRENCES : FROM URL(ONLINE-REPO)
   RUN : Execute command
   EXPOSE : port of Container (METADATA)
   MAINTAINER : Set Author field of that generated Image (METADATA)
   USER : User that contact with container
   VOLUME : Volume
   WORKDIR : mkdir + cd your dir
   LABEL : Info of Image (METADATA)
```




## Example of Dockerfile
``` sh

FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "app.py"]

```


## Docker-Compose
``` sh
  version: '3'
services:
  service-1:
    image: your-image-1
    # service-1 configuration
  service-2:
    image: your-image-2
    # service-2 configuration
    depends_on:
      - service-1
  service-3:
    image: your-image-3
    # service-3 configuration
    depends_on:
      - service-2
```

## Example of Docker-Compose
``` sh
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
    environment:
      FLASK_ENV: development
  db:
    image: postgres
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      POSTGRES_DB: mydb

```
## To Verify Docker-Compose
``` sh
docker-compose up -d   >> -d in Background
```
