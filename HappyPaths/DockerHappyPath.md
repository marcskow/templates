### Docker Happy Path

**1. Initialize Linux**

**2. Create Docker Image**  

https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
```
docker image build --tag <REPOSITORY>:<TAG> <PATH>
docker image build --tag marcskow/example:latest .
```
Alternatively:
```
docker [image] build .
docker inspect dd6bab74076f
docker tag dd6bab74076f marcskow/example:latest
```

**3. Push Docker Image to DockerHub**
```
docker login --username=yourhubusername
docker push <REPOSITORY>
docker push marcskow/example
```

**4. Saving / loading local backups**
```
docker save marcskow/example > marcskow_example.tar
docker load --input marcskow_example.tar
```

**5. Inspecting**  
In documentation we can find out a lot of useful format options to retrieve more specific information:
https://docs.docker.com/engine/reference/commandline/inspect/
```
docker image inspect dd6bab74076f
docker image history dd6bab74076f
```

**6. Cleaning**  
Removing all dangling images:
```
docker image prune
```
Removing all images not referred by any container:
```
docker image prune --all
```

**7. Run pushed image**
```
docker run \
--network=<NETWORK> \
-e <KEY>=<VALUE> \
-d -p 8080:8080 \
--name <NAME> \
<REPOSITORY>:<TAG>
```
