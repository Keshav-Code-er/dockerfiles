### Dockerfile

Dockerfile is the declarative way of creating images.

We can build the images and we can push to any docker repositiry.


### How to build the docker image
```
docker build -t image-name:version . 
```


containers
----------
inside VM we can multiple containers, so that we can even improve resource utilisation

a single VM
cart --> container
catalogue --> container


DOCKER
-------
install docker in centos8

After installing the docker from cmd next step
run cmd: sudo usermod -aG docker centos
logout by exit cmd
login again then run cmd "docker ps"

image =VM
Image:Image is combination of OS + application run-time(nodejs/java/python) + some packeges/libraries required by application + application 

image is like complete setup

docker cmd:
docker images=>list down the images in the server
docker pull image-name:version => download the image from docker hub
docker ps --> list down running containers
docker ps -a --> list down all the containers including running/stopped/exited/created
docker start container-id --> to start the containers
docker images -a -q --> shows image id only

docker rm `docker ps -a -q` --> removing all containers
docker rmi `docker images -a -q` --> removing all images
docker rmi <image-id> --> remove particular image


DOCKER HUB: Location where all the images are available

Every server have 0-65535 PORTS avaialble
Every container 0-65535 ports

pull image + created container + started container ==
docker run = pull + create + start

docker exec -it <6f7c1d171c35> bash/sh --> login inside container

docker run -p <host-port>:<container-port> image
docker run -d -p 80:80 nginx --> port mapping
 
docker run -d --> detach the screen and run in background
 
docker run -d --name mynginx -p 8080:80 nginx --> for changing the name of container
 
docker logs <container-id>

How to  create images?
----------------------
Dockerfile --> declarative way of creating images

base Os

docker/containers --> runs on linux server not window

FROM --> to select base OS
RUN --> to install the packages or to configure the image inside the base os , it will run at image creation
CMD --> it is use to run the container, it will only run at container creation 

systemctl start nginx --> systemctl will not work

nginx -g daemonoff 

install catalogue --> systemctl start catalogue

wjile running container, your CMD command should keep your container running for infinte time

as we enter the command to start the server(systemctl start nginx)same as we use CMD [ "nginx", "-g", "daemon off" ] to up n running the containers.

docker images --filter label=COURSE=DevOps --> filter the images with key-value pairs

docker inspect <image-id> --> details of the image using which port

EXPOSE: EXPOSE is not adding any functionality, this is just for information OF PORTS

Dockerfile -> create image using docker build --> run it as container


[ centos@ip-172-31-23-214 ~/dockerfiles/ENV ]$ docker run fb9eafbf59e3 env
															(image-id)
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=4f6ba929de52
NAME=KESHAV
AGE=26
HOME=/root

docker run <container-ID> command

command --> env --> it will display the environment variables

CMD [ "nginx", "-g", "daemon off;" ] --> running for infinte time untill you kill

COPY --> Use to copy file from current directory

When you want to push the docker image to docker hub

docker push <URL>/<username>/<image-name>:<version>

 docker tag copy:v1 docker.io/keshavkumar7/index.html:v1
 
 docker tag copy:v1 docker.io/keshavkumar7/index.html:v2 ==>for taging the image to other tag or name
 
docker push keshavkumar7/index.html:v2 ==>for pushing the images to docker hub

docker rm -f `docker ps -a -q`===>for deleting all the containers

docker rmi `docker images -a -q` ===> for deleting all the Images

docker rmi -f 0638546d4b7d

Build( docker build -t add_intrn:v1 .)

==================================================================================================================================
ADD --> It can directly get the content from internet and copy.

Generally we do: 
docker run -d <image-ID> sleep 60
docker exec -it <container-ID> bash/sh

Now we do: 
docker run -it <image-ID> bash 



