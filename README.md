# nginx-varnish-php7-mysql-docker

Varnish - Nginx - Php7 - Mysql - Mongo - Redis - Nodejs - Socket.io - React - Redux - Babel on Docker

### How to install the services with docker

**First should install docker**
* [Docker](https://docs.docker.com/engine/installation/)

To use docker-compose for installing which you want to install service for example:
```
docker-compose up -d varnish nginx
```

### How to use Web-based containers

To put the javascript files in /usr/src/app then edit package.json and run compose then it will be start:
```
docker-compose up -d nodejs
```
