# Docker中安装redis

1.拉取镜像：docker pull redis:latest
2.运行 redis 容器：（在运行容器之前先向下看2020.8.13更新那一块关于redis的更新）

     可以不设置密码：docker run -itd --name myredis -p 6379:6379 redis
     也可以设置密码：docker run -d --name myredis -p 6379:6379 redis --requirepass "password"

  其中myredis是容器名称,"mypassword"为要设置的密码

3.再次进入redis容器进行交互：docker exec -it myredis /bin/bash

Auth '12345678'


# Docker中的RabbitMQ安装

1. 拉取最新镜像：docker pull rabbitmq:management（加上management以便启动启动 RabbitMQ 后可以打开管理界面）

2. 创建rabbitmq容器 ：

     # 方式一：默认guest 用户，密码也是 guest
    docker run -d --hostname my-rabbit --name rabbit -p 15672:15672 -p 5672:5672 rabbitmq:management
     # 方式二：设置用户名root，密码123123
    docker run -d --hostname my-rabbit --name rabbit -e RABBITMQ_DEFAULT_USER=root -e RABBITMQ_DEFAULT_PASS=123123 -p 15672:15672 -p 5672:5672 rabbitmq:management

3. 访问管理界面
访问管理界面的地址就是 http://宿主机IP:15672


# Docker中的MonogoDB安装

docker pull mongo:latest
docker run -id --name=cas_mongo -p 27017:27017 mongo

使用dockerfile文件创建一个docker镜像 -t 设置tag  最后的.表示当前目录
docker build -f DockerFile  -t zkuidocker:v1 .



# Docker中的Mysql安装

不加latest,自动默认latest,安装mysql'最新版本
docker pull mysql


docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=12345678 -d mysql:latest

GRANT ALL ON *.* TO 'root'@'172.17.0.1';
grant all privileges on *.* to root@'%' identified by '1234578' with grant option;

# Docker中的HBASE

docker search hbase
docker pull harisekhon/hbase
docker run -d -p 2181:2181 -p 8080:8080 -p 8085:8085 -p 9090:9090 -p 9095:9095 -p 16000:16000 -p 16010:16010 -p 16201:16201 -p 16301:16301  -p 16030:16030 -p 16020:16020 --name hbase001 harisekhon/hbase

localhost:16010


# Docker 中的 pinpoint
# 克隆官方提供的docker git
git clone https://github.com/naver/pinpoint-docker.git
cd pinpoint-docker
# 1.7.3版本需要将 pinpoint-docker/docker-compose.yml的第17行和第18行修改为绝对路径，否则会启动报错（docker 17.03版本测试）
# 如需修改相关组件的ip和端口，请修改pinpoint-Docker/.env文件
docker-compose pull && docker-compose up -d
# 启动完成后访问网页 http://localhost:8081/#/submit 将pinpoint-docker/pinpoint-flink/build/pinpoint-flink-job-{pinpoint-version}.jar 文件手动upload到flik组件中，上传的版本需要和pinpoint保持一致
# 访问：http://localhost:8079/ 即可浏览pinpoint页面
# 官方说明：https://github.com/naver/pinpoint-docker
