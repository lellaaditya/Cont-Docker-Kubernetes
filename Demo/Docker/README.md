# Docker

Containerize an application Hello-world Python


Build the Image

docker build -t hello-world-py .

![alt text](image-3.png)

To Check the Image

docker images

![alt text](image.png)

Run the Image to make container

docker run -d -p 8080:8080 hello-world-py

![alt text](image-1.png)

To check the container is running

docker ps

![alt text](image-2.png)

Access the Application

![alt text](image-4.png)


# CI Pipeline(Azure Pipelines)

Build -> Push

https://github.com/lellaaditya/Cont-Docker-Kubernetes/blob/main/Demo/Docker/Dockerfile

https://github.com/lellaaditya/Cont-Docker-Kubernetes/blob/main/Demo/Kubernetes/azure-pipeline.yaml

![alt text](image-5.png)


Push Image to ACR

<img width="892" height="736" alt="image" src="https://github.com/user-attachments/assets/26996a9f-46f3-450d-9a65-bdbfab64fd03" />
