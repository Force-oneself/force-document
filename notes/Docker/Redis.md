# Redis

## 下载

``` java
docker pull redis:version
```

## 启动  

``` te
1. mkdir -p /docker/redis/conf
2. touch /docker/redis/conf/redis.conf
3. docker run -it -p 6379:6379 --name redis -v /docker/redis/data:/data \
-v /docker/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis:5.0.6 redis-server /etc/redis/redis.conf
```

## Redis使用redis-cli命令

``` tex
docker exec -it redis redis-cli
```
