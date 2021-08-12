## 账号

``` tex
# VPN
何永泉：wx_heyongquan hyq@123！heyongquan heyq@123
王天然：wangtianran wtr456852!@#

# processon
地址：https://www.processon.com/
账号：lin.hu@winkeytech.com
密码：2025@YYTech
# 微信开发平台
账号：lin.hu@winkeytech.com
密码：kO5oJ6cZ
```

## 华侨城B系统

### Prod

#### Rancher

``` tex
http://10.251.24.2:18001
admin fQ7%xS6#fT2$tY6&qZ9%pI9$
```

#### XxlJob

``` tex
http://10.251.24.2/xxl-job-admin
admin uK6@oB5!jE0#iC9!sQ
```

#### Nacos

``` tex
http://10.251.24.2:8848/nacos
nacos nacos
```

#### MySQL

``` te
10.251.24.7
hqc_scrm_rw hXpVgDThrp!
```

#### RabbitMQ

``` tex
连接地址：10.251.24.22:5672
WebUI地址：http://10.251.24.22:15672
admin KPa2=@ujXE
```

#### Redis

``` te
10.251.24.6:6379
ngKoaR#U8Kx
```

#### Elasticsearch

``` te
10.251.24.194:9200
10.251.24.36:9200
10.251.24.155:9200
admin BpWs%3uG*k
```

#### ELB

``` te
10.251.24.8
公网IP：124.71.43.51
```

#### OBS

``` te
Endpoint：obs.cn-south-1.myhuaweicloud.com
访问域名：obs-crmprod.obs.cn-south-1.myhuaweicloud.com
```

#### 服务器

``` tex
app1 10.251.24.2
app2 10.251.24.3
app3 10.251.24.4
resource 10.251.24.5 
```



***

### Test

#### Rancher

``` tex
http://10.252.24.2:18001
admin bN2!rM5^gG3!jF6$rY2&fN8!
```

#### XxlJob

``` tex
http://10.252.24.2/xxl-job-admin
admin uK6@oB5!jE0#iC9!sQ
```

#### Nacos

``` tex
http://10.252.24.2:8848/nacos
nacos pX0@mL8!hN1@yM6@
```

#### MySQL

``` te
10.252.24.6 3306
hqc_scrm_rw X2znT%MatKaA
```

#### Redis

``` te
10.252.24.5:6379
e4F-5qnuCv
```

#### RabbitMQ

``` te
连接地址：10.252.24.199:5672
WebUI界面：http://10.252.24.199:15672
admin xmtX-YGpP7
```

#### Elasticsearch

``` tex
10.252.24.22:9200
admin R2NbrK%frNV
```

#### 服务器

``` tex
10.252.24.2
```

#### OBS

``` tex
Endpoint：obs.cn-south-1.myhuaweicloud.com
访问域名：obs-crmuat.obs.cn-south-1.myhuaweicloud.com
```



***

### Dev





微信获取三方IP

``` shell
# 获取access_token
curl -X GET https://api.weixin.qq.com/cgi-bin/token?grant_type=client_credential&appid=wx7cb86c849afd48dc&secret=f2ee76854a2c2f92b7eaec96f2201631
# 获取ip
https://api.weixin.qq.com/cgi-bin/get_api_domain_ip?access_token=

"101.226.212.27","112.60.0.226","112.60.0.235","116.128.163.147","117.184.242.111","121.51.130.115","121.51.166.37","121.51.90.217","180.97.7.108","182.254.88.157","183.3.234.152","183.57.48.62","203.205.239.82","203.205.239.94","36.152.5.109","58.246.220.31","58.251.80.204","58.251.82.216","103.223.56.48"
```



华云盾下拉数据集成

``` shell
# 下拉登录
curl -X POST -d 'method=login&request={"systemCode": "CRM","integrationKey" : "P@ssw0rd","force" : true,"timestamp" : 1555578726000}' http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json > login.txt

# 全量下拉同步
curl -X POST -d 'method=syncTask&request={"tokenId": "b6f652c7-c477-4d0d-b9d4-fee7a8ccea19","timestamp" : 1555578726000}' http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json > syncTask.txt
# 全量下拉同步完成

# 增量下拉同步
curl -X POST -d 'method=pullTask&request={"tokenId": "7231c22e-bb43-4514-be27-bcaa976ed86f","timestamp" : 1555578726000}' http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json > pullTask.txt

# 增量下拉同步完成
curl -X POST -d 'method=pullFinish&request={"tokenId": "7ab03c19-86df-433c-bbe8-5411e674e8b8","taskId": "20210416114954075-CEB4-F661A0B65","success" : true,"timestamp": 1558422043686,"guid" : "zhaoliyuan"}' http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json > pullFinish.txt
# 注销
curl -X POST -d 'method=logout&request={"tokenId" : "b6f55716-3fe1-4e42-836e-564198914915","timestamp" : 1515339070}' http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json

```

``` http
# 下拉登录
http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json?method=login&request={"systemCode": "CRM","integrationKey" : "P@ssw0rd","force" : true,"timestamp" : 1555578726000}
# 增量下拉同步
http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json?method=pullTask&request={"tokenId": "b6f55716-3fe1-4e42-836e-564198914915","timestamp" : 1555578726000}
# 增量下拉同步完成 
http://idtest.chinaoct.com:18080/oct_bim-server/integration/api.json?method=pullFinish&request={"tokenId": "b6f55716-3fe1-4e42-836e-564198914915","taskId": "20210407145451551-83C0-D7CDCC8BD","success" : true,"guid" : "yiaili","timestamp": 1558422043686,"objectCode":"CRMACCOUNT","objectType":"TARGET_ACCOUNT","id":"20210407145451524-650F-00667CE44"}
```



curl -X POST -d 'tenantType=0&code=index&roleAlias=admin' http://ip/doubletenant/initrole/

\### 时间同步

\```sh
\# 设置时区
vi /etc/profile
\# 添加
export TZ="Asia/Shanghai"
\# 更新环境变量
source /etc/profile

\# 安装ntp
yum install -y ntp

\# 需要安装时间同步，不然集群会有问题
vi /etc/ntp.conf
\# 增加阿里云时间同步
server ntp.aliyun.com

\# 启动ntpd
systemctl restart ntpd

\# 设置开机启动
systemctl enable ntpd
\```

\###

