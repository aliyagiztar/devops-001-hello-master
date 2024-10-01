
#  DOCKER 

### ============= docker login =============
```
To login to Docker with a username and password:
```
```nginx
docker login   --username aliyagiztar     --password 123456789
```
```nginx
docker login   -u         aliyagiztar     -p        123456789
```

### ============= 🌐 Nginx =============
EXTERNAL_PORT:INTERNAL_PORT
```nginx
docker run     -it     -d     -p 9991:80     --name my-nginx      nginx
```
Access via http://localhost:9991

### ============= 🐘 Postgres =============
```nginx
docker run  --name my-postgres   -p 9999:5432  -e POSTGRES_PASSWORD=123456789  -d  postgres
```

### ============= MySQL =============
```nginx
docker run  --name my-mysql      -p 9990:3306  -e MYSQL_ROOT_PASSWORD=123456789 -d  mysql 
```



### ============= 🔄 Rename a Docker Container  =============
```nginx
docker container rename my-app5 my-app1
```



### ============= 📦 Build Your Project as a Docker Image =============
```nginx
docker build  --build-arg JAR_FILE=target/devops-001-hello-1.0.1.jar   --tag    aliyagiztar/devops-001-hello:v001   .
```
```nginx
docker build  --build-arg JAR_FILE=target/devops-001-hello-1.0.2.jar   --tag    aliyagiztar/devops-001-hello:v002   .
```
```nginx
docker build  --build-arg JAR_FILE=target/devops-001-hello-1.0.2.jar   --tag    aliyagiztar/devops-001-hello:latest   .
```


### ============= Run Your Project as a Docker Container =============
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

### Access via:
```
http://localhost:8081 </br>
http://localhost:8082 </br>
http://localhost:8083 </br>
http://localhost:8084 </br>
http://localhost:8085 </br>
```


============= ⬇️ Pull Images from Docker Hub =============

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



### ============== 🌐 Docker Networking ==============
### List Networks

```nginx
docker network ls
```

### Create a New Network
```nginx
docker network create my-network
```

### Change Network Driver Type
```nginx
docker network create --driver host
```


### Inspect Network and Connected Containers
```nginx
docker network inspect my-network
```


### Connect Containers to a Network
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

### Disconnect Containers from a Network
```nginx
docker network disconnect my-app4
```


### network bilgisi ve onu kullanan containerlar
```nginx
docker network inspect my-network
```

### Remove a Network
```nginx
docker network rm my-network
```


### ============== 📂 Docker Volumes ==============
# List Volumes
```nginx
docker volume ls
```
### Create a New Volume
```nginx
docker volume create my-volume
```
# Remove a Volume
```nginx
docker volume inspect my-volume
```

### Remove a Volume
```nginx
docker volume rm my-volume
```

### Remove Unused Volumes
```nginx
docker volume prune
```

### ============= 🛠 Docker Compose ===================
<img width="1102" alt="hepsicalismiyorsasariolıur" src="https://github.com/user-attachments/assets/c9915352-6d39-4cb0-892b-42c140b2248b">

# Start Services with Docker Compose
```nginx
docker compose -f docker-compose.yml up
```
<img width="2934" alt="mongo-docker-compose" src="https://github.com/user-attachments/assets/41d285a0-61a1-48a6-8c50-bbf812b18e27">

# List Running Containers
```nginx
docker ps
```
```nginx
docker container ls
```

# View Logs for a Specific Service

```nginx
docker-compose logs mongo
```
<img width="2384" alt="mongo-log-checking-compose" src="https://github.com/user-attachments/assets/ef9194fc-bb5f-44d2-91ca-f5e8133fa1b0">

# Stop and Remove Services
```nginx
docker-compose logs -f  mongo
```
<im<img width="558" alt="iki-image-compose" src="https://github.com/user-attachments/assets/f38195b3-f477-4794-8201-1b5314c6a037">
g width="2384" alt="mongo-log-checking-compose" src="https://github.com/user-attachments/assets/cddb4074-dba0-4fb7-99fe-c0479e82ca7c">

<img width="1222" alt="mongo-db-docker" src="https://github.com/user-attachments/assets/ed55e059-74bf-4bfc-bdfb-dc378a12e977">


```nginx
docker compose -f docker-compose.yml down
```

### RabbitMQ
```
version: "3.9"

services:

  rabbitmq:
    image: rabbitmq:3-management
    container_name: rabbitmq-1
    ports:
      - 5672:5672
      - 15672:15672
    environment:
      - "RABBITMQ_DEFAULT_PASS=admin"
      - "RABBITMQ_DEFAULT_USER=admin"
      - "RABBITMQ_DEFAULT_VHOST='vhost'"
    volumes:
      - rabbitmq_data:/var/lib/rabbitmq
volumes:
  rabbitmq_data:
```
<img width="2942" alt="ERAbbit-MQ-Login" src="https://github.com/user-attachments/assets/6db90260-7fe8-4f20-af56-6599254be88c">

### Rabbit MQ Compose
<img width="2285" alt="Rabbit-mq-compose" src="https://github.com/user-attachments/assets/c88e3e83-9870-4e20-abe5-1c1428a957e5">


### ELK
<img width="470" alt="ELK-Stack" src="https://github.com/user-attachments/assets/242f7681-85eb-40af-af7d-1e530e3d07e5">

<img width="1308" alt="logstash-elasticsearch-kibana" src="https://github.com/user-attachments/assets/ddc0f6e8-9fd7-4de3-a787-65a4223f4049">

### ============ Kubernetes ===========

### Run Docker Image as a Container Locally
```nginx
docker run     -it     -d     -p 8085:8080     --name my-app5      aliyagiztar/devops-001-hello:latest
```

### Run Docker Image as a Pod in Kubernetes
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

# Check Kubernetes Nodes and Pods

```nginx
kubectl get nodes
```
```nginx
kubectl get node
```

```nginx
kubectl get pods
```
```nginx
kubectl get pod
```


### Pods

### Deployment

### Service
