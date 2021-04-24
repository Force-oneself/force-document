```
启动Zookeeper
    docker run -d --name zookeeper -p 2181:2181 -t wurstmeister/zookeeper

2. 启动Kafka
    docker run  -itd --name kafka \
    -p 9092:9092 \
    -e KAFKA_BROKER_ID=0 \
    -e KAFKA_ZOOKEEPER_CONNECT=127.0.0.1:2181 \
    -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://127.0.0.1:9092 \
    -e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9092 -t wurstmeister/kafka:2.12-2.3.1

3. 搭建Kafka集群
    docker run -d --name kafka1 \
    -p 9093:9093 \
    -e KAFKA_BROKER_ID=1 \
    -e KAFKA_ZOOKEEPER_CONNECT=<宿主机IP>:2181 \
    -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://<宿主机IP>:9093 \
    -e KAFKA_LISTENERS=PLAINTEXT://0.0.0.0:9093 -t wurstmeister/kafka
```