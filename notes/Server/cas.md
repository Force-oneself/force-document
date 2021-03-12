### 利用tomcat服务器配置https双向认证

#### 1.为服务器生成证书

进入%JAVA_HOME%/bin目录，使用如下命令：

```
keytool -genkey -v -alias tomcat -keyalg RSA -keystore E:\Development\Document\certificate\tomcat.keystore -validity 36500
```

"E:\Development\Document\certificate":证书文件的保存路径；

"-validity -36500":证书的有效期时间，默认90天；

"tomcat"：自定义证书名称。

在命令行填写必要参数：

A.输入keystore密码：此处需要输入大于6个字符的字符串；

B.“您的名字与姓氏是什么？”，必须是部署主机的域名或者IP（本地使用localhost）；

C.

D.输入<tomcat>的主密码，此项较为重要，会在tomcat配置文件中使用，建议输入与keystore的密码一致，输入回车进入证书的生成目录。

#### 2.为客户端生成证书

为浏览器生成证书，以便让服务器来验证它。为了能将证书顺利导入至IE或者Firefox。证书格式应该是PKCS12，因此，使用如下命令生成：

```
keytool -genkey -v -alias mykey -keyalg RSA -storetype PKCS12 -keystore E:\Development\Document\certificate\mykey.p12
```

"mykey":为自定义；

“E:\Development\Document\certificate\mykey.p12”:证书存放位置；

双击mykey.p12文件，即可将证书导入至浏览器（客户端）。

#### 3.让服务器信任客户端证书

由于是双向SSL认证，服务器必须要信任客户端证书。因此，必须把客户端证书添加为服务器的信任认证，由于不能直接将PKCS12格式的证书库导入，必须先把客户端证书导入为一个单独的CER文件，使用如下命令：

```
keytool -export -alias mykey -keystore E:\Development\Document\certificate\mykey.p12 -storetype PKCS12 -storepass 你设置的密码 -rfc -file E:\Development\Document\certificate\mykey.cer
```

#### 4.导入到服务器的证书库

```
keytool -import -v -file E:\Development\Document\certificate\mykey.cer -keystore E:\Development\Document\certificate\tomcat.keystore
```

通过list命令查看服务器的证书库，可以看到两个证书，一个是服务器证书一个是客户端证书：

```
keytool -list -keystore E:\Development\Document\certificate\tomcat.keystore(tomcat为你设置服务器的证书名)
```

#### 5.让客户端信任服务器证书

```
keytool -keystore E:\Development\Document\certificate\tomcat.keystore -export -alias tomcat -file E:\Development\Document\certificate\tomcat.cer(tomcat为你设置服务器的证书名)
```

到导出目录双击tomcat.cer文件，按照提示安装证书，将证书填入到“收信人的根证书颁发机构”。

#### 6.配置Tomcat服务器

打开Tomcat根目录下的conf/server.xml文件，找到Connector port=“8443”配置段，修改如下：

```xml
<Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol"
           SSLEnabled="true" maxThreads="150" scheme="https"
		   secure="true" clientAuth="true" sslProtocol="TLS"
		   keystoreFile="E:\Development\Document\certificate\tomcat.keystore"
		   keystorePass="he970801"
		   truststoreFile="E:\Development\Document\certificate\tomcat.keystore"
		   truststorePass="he970801">
</Connector>
```

属性说明：

clientAuth：设置是否双向验证，默认为false；

keystoreFile：服务器证书路径；

keystorePass：服务证书密码；

truststoreFile：用来验证客户端证书的根证书，此例中就是服务器证书；

truststorePass：根证书密码。

#### 7.测试