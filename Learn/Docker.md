### **3 reasons to choose to choose Docker:**

**Standardized Application packaging**

> Same package for all type of applications - java or python or is we just build a docker image for all in same way

**Multi-platform Support**

> Local machine, Data center, and cloud - AWS , azure and gcp

**Light weight and Isolation**

> Containers are light weight compared to VMs - isolated from one another

### Docker Images Commands

	docker images

	docker pull imagename

	docker run imagename

	docker search imagename or id

	docker image history imagename

	docker image history imgid

	docker image inspect imgid

	docker run -name _namewhatwelike

	docker image rm imagename

	docker image rm imageid

### Docker Container commands

	docker container rm contid

	docker run -p __ : __  imgname this is short for container run 

	docker container ls -a

	docker container ls 

	docker container pause contid 
to pause the container

	docker container unpause contID 
to un pause the container in pause stage

	docker container kill id

	docker container stop id

	docker run -d

	docker logs -f

	docker container inspect

	docker container prune

	docker run -i

	docker run -t 

> if we stop the container it will be given a time of 10 secs to shutdown so we can able to see the logs 

> But if we give command kill we can't see any logs as it don't give any time to shutdown

	docker system 
> shows the cmds we can use with it 

	docker system df

	docker system events

	docker system prune -a 

	docker stats contid

	-m _size 
> eg : docker run -m 512m imgid 

	— - cpu-quota= size imgid 
>eg: docker run - - cpu-quota= 50000 imgname 
> here 100 % is 100k - 100000
> So 50% is 50k - 50000

	docker system info

	docker container top

	**docker build -t imagenamewewant:tagsifneed .** 
last dot is important then will show error because thats where it can find dockerfile to build image

	**docker push hubId/imagename:tags**
eg: docker push -t dinesh1866/hello-world 

	docker network ls 
to see the network name , driver and scope

	docker network inspect bridge 
now we can see all the info about the ntwk

	docker network create networkname
can able to create our own network

	- - network= networkname 
to add container to the network 

### Basic template for docker file

##### Python
```dockerfile
FROM imagename: tag

WORKDIR /app

COPY . /app

RUN pip install -r requirements.txt

EXPOSE 5000

CMD python ./launch.py
```

##### NodeJS

>just like [launch.py](http://launch.py) we specify the code in index.js file and instead requirements.txt we have package.json just like we use flask in python we use express here and pip there here npm

```Dockerfile
FROM node:8.16.1-alpine

WORKDIR /app

COPY . /app

RUN npm install

EXPOSE 5000

CMD node index.js
```

##### Java
> in java we have to make a two stage build

> note: we cannot just build the java file what we do is we first we will build the jar file and will convert it into image.
> because everytime the java application gets compiled into jar file and then only executed.
> we have src instead of index or launch and pom.xml instead of requirements.txt or packages.json 
> Instead of pip and nvm we use mvn
> template Build a JAR file

```Dockerfile
FROM maven:3.6.3-jdk-8-slim AS build

WORKDIR /home/app

COPY .  /home/app/

RUN mvn -f /home/app/pom.xml clean package

#create an Image

FROM openjdk:8-jdk-alphine

EXPOSE 5000 

COPY —from=build /home/app/target/hello-world-java.jar  hello-world-java.jar

ENTRYPOINT  [”sh”, “-c”, “java -jar /hello-world-java.jar”]
```

important thing in the image is the copy cmd where we are giving the from location name, where we also given name to the build

instead build we can also give it as stage1 and give the from=stage

