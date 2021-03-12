# MySQL

## mysql 启动

```java
docker run -it -p 3306:3306 --name mysql \
 -v /docker/mysql/log:/var/log/mysql \
 -v /docker/mysql/data:/var/lib/mysql \
 -v /docker/mysql/conf:/etc/mysql/conf.d \
 -e MYSQL_ROOT_PASSWORD=root \
 -d mysql:5.7.29 /bin/bash
```

## 参数说明

``` te
-p 3306:3306 ： 将容器的3306端口映射到主机的3306端口
-it ：参数交互运行
-v /mydata/mysql/log:/var/log/mysql\ ：将配置文件夹挂载到主机
-v /mydata/mysql/data:/var/lib/mysql\ ：将日志文件夹挂载到主机
-v /mydata/mysql/conf:/etc/mysql\ ：将配置文件夹挂载到主机
-e MYSQl_ROOT_PASSWORD=root\ ：初始化root用户的密码
-d : 使镜像后台运行
/bin/bash : 使启动的镜像停留在后台运行（不添加会启动便迅速Exited）
```

## 在 mydata/mysql/conf/ 创建my.cnf，写入如下配置：

``` tex
[client]
default-character-set=utf8

[mysql]
default-character-set=utf8

[mysqld]
init_connect='SET collation_connection = utf8_general_ci'
init_connect='SET NAMES utf8'
character-set-server=utf8
collation-server=utf8_general_ci
skip-character-set-client-handshake
skip-name-resolve
```

``` tex
docker run -it -p 3306:3306 --name mysql
 -v /dockr/mysql/log:/var/log/mysql 
 -v /docker/mysql/data:/var/lib/mysql 
 -v /docker/mysql/conf:/etc/mysql/conf.d
 -e MYSQL_ROOT_PASSWORD=root
 -d mysql:5.7.29  /bin/bash
 --character-set-server=utf8 
 --collation-server=utf8_general_ci

```



## docker内部登录mysql

``` tex
docker exec -it mysql-images-name /bin/bash
```

