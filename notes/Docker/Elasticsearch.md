# Elasticsearch

## 下载镜像

``` tex
docker pull elasticsearch:7.4.2
docker pull kibana:7.4.2
```

## 创建实例

``` tex
mkdir -p /docker/elasticsearch/config
mkdir -p /docker/elasticsearch/data

echo "http.host: 0.0.0.0" >>/docker/elasticsearch/config/elasticsearch.yml

chmod -R 777 /docker/elasticsearch/

docker run -it -d --name es -p 9200:9200 -p 9300:9300 -e ES_JAVA_OPTS="-Xms512m -Xmx512m" -v /docker/elasticsearch/plugins:/usr/share/elasticsearch/plugins -v /docker/elasticsearch/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml -v /docker/elasticsearch/data:/usr/share/elasticsearch/data -e "discovery.type=single-node" elasticsearch:7.4.2
```

## Kibana

``` tex
docker run -it --name kibana -e ELASTICSEARCH_HOSTS=http://120.76.175.67:9200 -p 5601:5601 \
-d kibana:7.4.2
```

## Logstash

#### 启动logstash

``` tex
docker run -d --name=logstash logstash:7.4.2
```

#### 复制文件

``` tex
docker run -d --name=logstash logstash:7.4.2
mkdir -p /docker/logstash/config/conf.d
docker cp logstash:/usr/share/logstash/config /docker/logstash
docker cp logstash:/usr/share/logstash/data /docker/logstash
docker cp logstash:/usr/share/logstash/pipeline /docker/logstash
chmod 777 -R /docker/logstash
```

新建文件syslog.conf，用来收集/var/log/messages

```tex
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

重新启动logstash

```tex
docker rm -f logstash

docker run -it -d \
  --name=logstash \
  -v /docker/logstash:/usr/share/logstash \
  -v /docker/logstash/log/messages:/var/log/messages \
  logstash:7.4.2
```



``` tex
docker run -it -d --log-driver json-file --log-opt max-size=100m --log-opt max-file=2 -p 5044:5044 --name logstash -v /docker/logstash/logstash.yml:/usr/share/logstash/config/logstash.yml -v /docker/logstash/conf.d/:/usr/share/logstash/conf.d/ logstash:7.4.2
```
