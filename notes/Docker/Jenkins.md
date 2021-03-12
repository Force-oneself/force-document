# Jenkins

## 创建挂载文件

``` tex
mkdir /docker/jenkins/home
```

## 修改权限

``` tex
chown -R 1000:1000 /docker/jenkins/
```



## 安装

``` tex
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

