docker run --name nacos -itd -p 8848:8848 \
--privileged=true \
--restart=always \
-e JVM_XMS=512m -e JVM_XMX=512m -e MODE=standalone \
-v /Users/jeikerxiao/nacos:/home/nacos/logs  \
nacos/nacos-server:1.3.1 \