# How to deploy your own Jenkins with Docker

#### 1- Execute this command on your CLI

```
docker run --name myjenkins -p 8080:8080 -p 50000:50000 -v ./jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```