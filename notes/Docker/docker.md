## Spring Cloud

### Nacos

``` shell
docker run --name nacos -itd -p 8848:8848 \
--privileged=true \
--restart=always \
-e JVM_XMS=512m -e JVM_XMX=512m -e MODE=standalone \
-v /Users/jeikerxiao/nacos:/home/nacos/logs  \
nacos/nacos-server:1.3.1 \
```

## ELK

### Elasticsearch

``` shell
mkdir -p /docker/elasticsearch/config
mkdir -p /docker/elasticsearch/data

echo "http.host: 0.0.0.0" >>/docker/elasticsearch/config/elasticsearch.yml

chmod -R 777 /docker/elasticsearch/

docker run -it -d --name es -p 9200:9200 -p 9300:9300 -e ES_JAVA_OPTS="-Xms512m -Xmx512m" -v /docker/elasticsearch/plugins:/usr/share/elasticsearch/plugins -v /docker/elasticsearch/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml -v /docker/elasticsearch/data:/usr/share/elasticsearch/data -e "discovery.type=single-node" elasticsearch:7.4.2
```

### Kibana

``` shell
docker run -it --name kibana -e ELASTICSEARCH_HOSTS=http://120.76.175.67:9200 -p 5601:5601 \
-d kibana:7.4.2
```

### Logstash

1. 启动logstash

``` shell
docker run -d --name=logstash logstash:7.4.2
```

2. 复制文件

``` shell
docker run -d --name=logstash logstash:7.4.2
mkdir -p /docker/logstash/config/conf.d
docker cp logstash:/usr/share/logstash/config /docker/logstash
docker cp logstash:/usr/share/logstash/data /docker/logstash
docker cp logstash:/usr/share/logstash/pipeline /docker/logstash
chmod 777 -R /docker/logstash
```

3. 新建文件syslog.conf，用来收集/var/log/messages

```shell
vi /docker/logstash/config/conf.d/syslog.conf
```

​	内容如下：

```json
input {
  file {
    #标签
    type => "systemlog-localhost"
    #采集点
    path => "/var/log/messages"
    #开始收集点
    start_position => "beginning"
    #扫描间隔时间，默认是1s，建议5s
    stat_interval => "5"
  }
}

output {
  elasticsearch {
    hosts => ["192.168.31.190:9200"]
    index => "logstash-system-localhost-%{+YYYY.MM.dd}"
 }
}
```

4. 重新启动logstash

```shell
docker rm -f logstash
docker run -it -d --log-driver json-file --log-opt max-size=100m --log-opt max-file=2 -p 5044:5044 --name logstash -v /docker/logstash/logstash.yml:/usr/share/logstash/config/logstash.yml -v /docker/logstash/conf.d/:/usr/share/logstash/conf.d/ logstash:7.4.2
```

## Jenkins

``` shell
mkdir /docker/jenkins/home
# 修改权限
chown -R 1000:1000 /docker/jenkins/
docker run \
  -u root \
  --name jenkins \
  --rm \
  -itd \
  -p 8080:8080 \
  -p 50000:50000 \
  -v /docker/jenkins/home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins:2.60.1
```

## Kafka

``` shell
# 启动Zookeeper
docker run -d --name zookeeper -p 2181:2181 -it zookeeper:3.4.14
# 启动Kafka
docker run  -itd --name kafka \
-p 9092:9092 \
-e KAFKA_BROKER_ID=0 \
-e KAFKA_ZOOKEEPER_CONNECT=127.0.0.1:2181 \
-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://127.0.0.1:9092 \
-e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9092 -t wurstmeister/kafka:2.12-2.3.1

# 搭建Kafka集群
docker run -d --name kafka1 \
-p 9093:9093 \
-e KAFKA_BROKER_ID=1 \
-e KAFKA_ZOOKEEPER_CONNECT=<宿主机IP>:2181 \
-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://<宿主机IP>:9093\
-e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9093 -t wurstmeister/kafka:2.12-2.3.1
```

## Redis

``` shell
mkdir -p /docker/redis/conf
touch /docker/redis/conf/redis.conf
docker run -it -p 6379:6379 --name redis 
-v /docker/redis/data:/data \
-v /docker/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis:5.0.6 redis-server /etc/redis/redis.conf
```

## MySQL

1. mysql 启动

```shell
docker run -it -p 3306:3306 --name mysql \
 -v /docker/mysql/log:/var/log/mysql \
 -v /docker/mysql/data:/var/lib/mysql \
 -v /docker/mysql/conf:/etc/mysql/conf.d \
 -e MYSQL_ROOT_PASSWORD=root \
 -d mysql:5.7.29 /bin/bash
```

2. 参数说明

``` shell
-p 3306:3306 ： 将容器的3306端口映射到主机的3306端口
-it ：参数交互运行
-v /mydata/mysql/log:/var/log/mysql\ ：将配置文件夹挂载到主机
-v /mydata/mysql/data:/var/lib/mysql\ ：将日志文件夹挂载到主机
-v /mydata/mysql/conf:/etc/mysql\ ：将配置文件夹挂载到主机
-e MYSQl_ROOT_PASSWORD=root\ ：初始化root用户的密码
-d : 使镜像后台运行
/bin/bash : 使启动的镜像停留在后台运行（不添加会启动便迅速Exited）
```

3. 在 docker/mysql/conf/ 创建my.cnf，写入如下配置：

``` properties
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

``` shell
docker run -it -p 3306:3306 --name mysql
 -v /dockr/mysql/log:/var/log/mysql 
 -v /docker/mysql/data:/var/lib/mysql 
 -v /docker/mysql/conf:/etc/mysql/conf.d
 -e MYSQL_ROOT_PASSWORD=root
 -d mysql:5.7.29  /bin/bash
 --character-set-server=utf8 
 --collation-server=utf8_general_ci

```

