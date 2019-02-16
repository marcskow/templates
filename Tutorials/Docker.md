### Docker Tutorial
**1. Create Linux instance**  

**2. Install docker**
```
sudo apt-get install docker
docker version
sudo systemctl start docker     // if needed
```

**3. Docker command line**
```
docker help
docker <command> --help
```

Run container:
```
docker container run hello-world
```

Download and run:
```
docker image pull nginx
docker container run -d --name nginx-test -p 8080:80 nginx
docker container stop nginx-test
docker container rm nginx-test
```

**4. Docker image**
```
FROM alpine:latest
LABEL maintainer="Marcin Skowron <marcin@skowron.io>"
LABEL description="This example Dockerfile installs NGINX."

RUN apk add --update nginx && \
 rm -rf /var/cache/apk/* && \
 mkdir -p /tmp/nginx/

COPY files/nginx.conf /etc/nginx/nginx.conf
COPY files/default.conf /etc/nginx/conf.d/default.conf

ADD files/html.tar.gz /usr/share/nginx/

EXPOSE 80/tcp

ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
```

**FROM** - from which container this container inherits. alipne:lastest is really small linux distribution
ideal for docker usage. 
Could be also: ```centos```, ```ubuntu```, ```debian```, ```fedora``` but also other images preprepared like ```java```.

**LABEL** - additional comments  
**RUN** - can be as one command or more runs like:
```
RUN apk add --update nginx
RUN rm -rf /var/cache/apl/*
RUN mkdir -p /tmp/nginx
```
But this attempt is slower because of something.

**COPY** - just copy from host to container  
**ADD** - download from url, extract zip etc.  
**EXPOSE** - do not map to host port, just show which ports are exposed   

**5. Build docker image**
```
docker image build --tag <REPOSITORY>:<TAG> <PATH>
```
**REPOSITORY** - is usually our user on DockerHub, but we can use local for training  
**TAG** - unique name  
**PATH** - usually the dot " . "