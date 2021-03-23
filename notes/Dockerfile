FROM openjdk:8-jre #基于哪个镜像进行构建
WORKERDIR /app #定义进入容器时默认位置，接下来后序操作工作位置
ADD demo-0.0.1.SNAPSHOT.jar app.jar #将上线文中名字为演示-xxjar复制到工作目录同时修改其名称为app.jar
EXPOSE 8080 #让当前容器保露哪个端口因为项目使用端口是8081
ENTRTPOINT ["java", "-jar"] #启动应用固定命令
CMD ["app.jar"] #执行jar名称
