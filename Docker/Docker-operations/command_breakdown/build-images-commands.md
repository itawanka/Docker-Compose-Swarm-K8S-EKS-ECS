# Flow-2: Create a new Docker Image, Run as Container and Push to Docker Hub

## Pre-requisite Step
- Create your Docker hub account. 
- https://hub.docker.com/
- **Important Note**: In the below listed commands wherever you see **awanmbandi** you can replace with your own docker hub account id. 


## Step-1: Run the base Nginx container
- Access the URL http://localhost
```
docker run --name PERSONAL_CONTAINER_NAME -p HOST_PORT:CONTAINER_PORT -d IMAGE_NAME
docker run --name mynginxdefault -p 80:80 -d nginx
docker ps
docker stop mynginxdefault
```

```bash
Explanation:
-d: Runs the container in detached mode (in the background).
-p 8080:80: Maps port 8080 on your host to port 80 in the container.
--name my-nginx: Names the container my-nginx.
nginx: The official Nginx Docker image.
```

## Step-2: Create Dockerfile and copy our customized index.html
- **Dockerfile**
```
FROM nginx
COPY index.html /usr/share/nginx/html
```

## Step-3: Build Docker Image & run it
```
docker build -t awanmbandi/mynginx_image1:v1 .
docker run --name mynginx1 -p 80:80 -d awanmbandi/mynginx_image1:v1

Replace your docker hub account Id
docker build -t <your-docker-hub-id>/image-name:v1 .
docker run --name mynginx1 -p 80:80 -d <your-docker-hub-id>/mynginx_image1:v1
```

## Step-4: Tag & push the Docker image to docker hub
```
docker images
docker tag awanmbandi/mynginx_image1:v1 awanmbandi/mynginx_image1:v1-release
docker push awanmbandi/mynginx_image1:v1-release

Replace your docker hub account Id
docker tag <your-docker-hub-id>/mynginx_image1:v1 <your-docker-hub-id>/mynginx_image1:v1-release
docker push <your-docker-hub-id>/mynginx_image1:v1-release
```
## Step-5: Verify the same on docker hub
- Login to docker hub and verify the image we have pushed
- Url: https://hub.docker.com/repositories



SonarQube Scanner
Snyk
Multibranch Scan Webhook Trigger
Eclipse Temurin installer
Pipeline: Stage View
Docker
Docker Commons
Docker Pipeline
docker-build-step
Docker API
Kubernetes
Kubernetes CLI
Kubernetes Credentials
Kubernetes Client API
Kubernetes Credentials Provider
Kubernetes :: Pipeline :: DevOps Steps
Slack Notification
ssh-agent
BlueOcean
Build Timestamp