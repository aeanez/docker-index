# How to deploy your own MariaDB/MySQL server with Docker

#### 1- Execute this command on your CLI


```
# docker run -p 127.0.0.1:3306:3306  --name MyDockerServerName -e MYSQL_ROOT_PASSWORD=ChangeThisPassword -d mariadb:5.7
```