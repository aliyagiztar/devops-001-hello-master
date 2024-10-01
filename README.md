
#  DOCKER 

============= docker login =============
```
To login to Docker with a username and password:
```
```nginx
docker login   --username aliyagiztar     --password 123456789
```
```nginx
docker login   -u         aliyagiztar     -p        123456789
```

============= nginx =============
DIŞ_PORT:İÇ_PORT
```nginx
docker run     -it     -d     -p 9991:80     --name my-nginx      nginx
```
http://localhost:9991

============= postgres =============
```nginx
docker run  --name my-postgres   -p 9999:5432  -e POSTGRES_PASSWORD=123456789  -d  postgres
```

============= mysql =============
```nginx
docker run  --name my-mysql      -p 9990:3306  -e MYSQL_ROOT_PASSWORD=123456789 -d  mysql 
```



============= Docker container adını değiştirne  =============
```nginx
docker container rename my-app5 my-app1
```



============= kendi projemizi Docker image haline çevimek =============
```nginx
docker build  --build-arg JAR_FILE=target/devops-001-hello-1.0.1.jar   --tag    aliyagiztar/devops-001-hello:v001   .
```
```nginx
docker build  --build-arg JAR_FILE=target/devops-001-hello-1.0.2.jar   --tag    aliyagiztar/devops-001-hello:v002   .
```
```nginx
docker build  --build-arg JAR_FILE=target/devops-001-hello-1.0.2.jar   --tag    aliyagiztar/devops-001-hello:latest   .
```


============= kendi projemizi Docker image'den container haline çevimek =============
```nginx
docker run     -it     -d     -p 8081:8080     --name my-app1      aliyagiztar/devops-001-hello
```
```nginx
docker run     -it     -d     -p 8082:8080     --name my-app2      aliyagiztar/devops-001-hello
```
```nginx
docker run     -it     -d     -p 8083:8080     --name my-app3      aliyagiztar/devops-001-hello:v001
```
```nginx
docker run     -it     -d     -p 8084:8080     --name my-app4      aliyagiztar/devops-001-hello:v002
```
```nginx
docker run     -it     -d     -p 8085:8080     --name my-app5      aliyagiztar/devops-001-hello:latest
```

http://localhost:8081 </br>
http://localhost:8082 </br>
http://localhost:8083 </br>
http://localhost:8084 </br>
http://localhost:8085 </br>


============= Docker Hub'dan image çekmek =============

```
docker pull aliyagiztar/devops-001-hello:v001
```
```nginx
docker pull aliyagiztar/devops-001-hello:v002
```
```nginx
docker pull aliyagiztar/devops-001-hello:latest
```
```nginx
docker pull aliyagiztar/devops-001-hello
```



### ============== network ==============
### networkleri listele

```nginx
docker network ls
```

### yeni bir network oluştur
```nginx
docker network create my-network
```

### network tipini değiştirmek istiyorsanız --driver parametresi
```nginx
docker network create --driver host
```


### network bilgisi ve onu kullanan containerlar
```nginx
docker network inspect my-network
```


### networke container ekleme
```nginx
docker network connect my-network my-app1
```
```nginx
docker network connect my-network my-app2
```
```nginx
docker network connect my-network my-app3
```
```nginx
docker network connect my-network my-app4
```

### network bilgisi ve onu kullanan containerlar
```nginx
docker network inspect my-network
```

### networke container çıkarma
```nginx
docker network disconnect my-app4
```


### network bilgisi ve onu kullanan containerlar
```nginx
docker network inspect my-network
```

### networkü silme
```nginx
docker network rm my-network
```


### ============== volume ==============
```nginx
docker volume ls
```
### Yeni bir volume oluşturmak
```nginx
docker volume create my-volume
```

```nginx
docker volume ls
```

```nginx
docker volume inspect my-volume
```

### bir volume silmek
```nginx
docker volume rm my-volume
```

### kullanılmayan tüm volumeleri silmek
```nginx
docker volume prune
```

### ============= docker-compose ===================
```nginx
docker compose -f docker-compose.yml up
```

```nginx
docker ps
```

```nginx
docker container ls
```

```nginx
docker-compose logs mongo
```
```nginx
docker-compose logs -f  mongo
```


```nginx
docker compose -f docker-compose.yml down
```



### ============ Kubernetes ===========

### Docker Hub'daki imajı, yerel makinemde Docker kullanarak çekiyor ve bir container olarak çalıştırıyorum.
```nginx
docker run     -it     -d     -p 8085:8080     --name my-app5      aliyagiztar/devops-001-hello:latest
```

### Docker Hub'dan imajı container olarak çekip Kubernetes'teki Pod içinde çalıştırıyorum.
```nginx
kubectl run my-pod1 --image=aliyagiztar/devops-001-hello:latest
```
kubectl run my-pod2 --image=aliyagiztar/devops-001-hello:v001
```nginx
kubectl run my-pod3 --image=aliyagiztar/devops-001-hello:v002
```
kubectl run my-pod4 --image=aliyagiztar/devops-001-hello:v002
```nginx
kubectl run my-pod5 --image=aliyagiztar/devops-001-hello:latest
```
```nginx
kubectl run my-pod6 --image=aliyagiztar/devops-001-hello:latest
```
```nginx
kubectl run my-pod7 --image=aliyagiztar/devops-001-hello:v003
```
```nginx
kubectl run my-pod8 --image=mysql
```
```nginx
kubectl run my-pod9 --image=postgres
```


```nginx
kubectl get nodes
```
```nginx
kubectl get node
```

```kubernates
kubectl get pods
```
```kubernates
kubectl get pod
```


### Pods

### Deployment

### Service
