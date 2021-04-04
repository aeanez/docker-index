# How to deploy your own Git server with Gitea

#### 1- Create your docker-compose.yml file


```
version: "3"

networks:
  gitea:
    external: false

services:
  server:
    image: gitea/gitea:1.13.6
    container_name: gitea
    environment:
      - USER_UID=1000
      - USER_GID=1000
    restart: always
    networks:
      - gitea
    volumes:
      - ./gitea:/data
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
      - "3000:3000"
      - "222:22"
```

#### 2- Deploy your service

```
# docker-compose up
```

#### Optional: Setting your own MySQL or MariaDB database
```
version: "3"

networks:
  gitea:
    external: false

services:
  server:
    image: gitea/gitea:1.13.6
    container_name: gitea
    environment:
      - USER_UID=1000
      - USER_GID=1000
      - DB_TYPE=mysql   #Add the database type
      - DB_HOST=db:3306 #Add the database server port
      - DB_NAME=gitea   #Add the database name
      - DB_USER=gitea   #Add the database user
      - DB_PASSWD=gitea #Add the database password
    restart: always
    networks:
      - gitea
    volumes:
      - ./gitea:/data
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
     ports:
       - "3000:3000"
       - "222:22"
    depends_on: # If your servide depends on another one
      - db      # you must set it here

  #Add the database server configuration
  db:
    image: mysql:5.7
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=gitea
      - MYSQL_USER=gitea
      - MYSQL_PASSWORD=gitea
      - MYSQL_DATABASE=gitea
    networks:
      - gitea
    volumes:
      - ./mysql:/var/lib/mysql
```

You can also have a different mysql server running already. If so, you can ommit 'depends_on' on the server: config and all the 'db:' config.