# How to deploy your own MariaDB/MySQL server with Docker

#### 1- Execute this command on your CLI


```
# docker run -p 127.0.0.1:3306:3306  --name MyDockerServerName -e MYSQL_ROOT_PASSWORD=ChangeThisPassword -d mariadb:5.7
```

You will be allowed to access to that server with the root user and the password that you set.


It is also posible to change the incomming port e.g 9999
```
# docker run -p 127.0.0.1:9999:3306 --name MyServerWithOtherPort -e MYSQL_ROOT_PASSWORD=ChangeThisPassword -d mariadb:5.7
```