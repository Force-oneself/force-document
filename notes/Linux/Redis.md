# Redis

## 安装

``` shell
# 安装依赖
yum -y install gcc gcc-c++ kernel-devel
# 解压源码
tar -xzf redis-xxxx.tar.gz
cd redis-xxxx
# 编译
make
# 安装
make PREFIX=/usr/local/redis install
mkdir /usr/local/redis/etc/
cp redis.conf /usr/local/redis/etc/
cd /usr/local/redis/bin/
cp redis-benchmark redis-cli redis-server /usr/bin/
```

