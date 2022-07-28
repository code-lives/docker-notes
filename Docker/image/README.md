# Alpine
## apt-get install 依赖搜索    https://pkgs.alpinelinux.org
### PHP [镜像案例](https://github.com/code-lives/dockerfile)
### pecl 安装
```
RUN echo '' | pecl install -o -f redis msgpack grpc protobuf grpc protobuf \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable redis msgpack grpc protobuf grpc protobuf 
```
# Jenkins
### 本地搭建 docker-compose.yml
```
version: "3.1"
services:
  nginx:
    restart: always #docker 启动这个容器也跟着启动
    image: jenkins/jenkins:lts-jdk11
    container_name: jenkins #容器的名称
    ports:
      - 8181:8080
      - 50001:50000
    volumes:
      - $PWD/jenkins_home:/var/jenkins_home
      - $PWD/run/docker.sock:/var/run/docker.sock
```
# Rabbitmq
### 本地搭建 docker-compose.yml
```
version: '3.1'
services:
  rabbitmq:
    image: rabbitmq
    restart: always
    container_name: rabbitmq #mysql 容器
    ports:
      - "15672:15672"
      - "5672:5672"

```
# Mysql
### 本地搭建 docker-compose.yml
```
version: '3.1'
services:
  db:
    image: mysql:5.7
    restart: always
    container_name: mysql #mysql 容器
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: 123456
    volumes:
      - $PWD/mysql/db/:/var/lib/mysql/
      - $PWD/mysql/mysqld/:/var/run/mysqld/
      #- $PWD/mysql/mysqld.cnf:/etc/mysql/mysql.conf.d/mysqld.cnf
```
# Redis
### 本地搭建 docker-compose.yml
```
version: '3.1'
services:
  redis:
    image: redis:6.2
    restart: always
    container_name: redis # redis 容器的名称
    ports:
      - "6379:6379"
    volumes:
      - $PWD/redis/data/:/data
      #- $PWD/redis/redis.conf:/usr/local/etc/redis/redis.conf # redis.conf https://redis.io/topics/config
    #command:
      #/bin/bash -c "redis-server /usr/local/etc/redis/redis.conf"

```
