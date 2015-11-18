# 内网服务器如何部署OneAPM

* 使用场景：

 nginx 有外网 IP，可以访问外网，tomcat 不能上网，nginx 反向代理到 tomcat进行客户正常的业务运行，我们想为tomcat安装探针将数据发送到 oneapm 时，就需要在有外网 IP 的 nginx 上配置 squid 做代理，探针收集内网 tomcat 的性能数据后，通过 nginx 的 squid 将数据传送给 oneapm server。
* 以 Linux 为例，简易配置 squid 的配置步骤如下：

  1.Yum 安装
  ```
  yum -y install squid
  ```
  2.初始化 squid ，生成 cache 目录
  ```
  squid -z
  ```
  3.配置 squid
  ```
  vi /etc/squid.conf
  ```
  4.添加acl访问规则：
  ```
  acl 名称 src 客户内网网段/掩码
  ```
  例：
  ```
  acl oneapm src 192.168.0.0/24
  ```
* 设置允许访问权限
  ```
  http_access allow oneapm
  ```
  1.启动squid
  ```
  service squid start
  ```
  2.编辑 oneapm.properties 或者 oneapm.yml
  ```
  proxy_host squid的主机地址
  proxy_port 3128
  ```
  3.启动oneapm探针
  
  #####**注意:**
安装 squid 记得配置安全规则，3128端口不要暴露在外网，仅提供内网访问即可。其它安全方法也可以为 squid 配置用户名密码认证，配置认证后，你还需要为 oneapm.properties 或者 oneapm.yml 添加 proxy 的用户与密码。

* 其它 squid 版本下载：http://www.squid-cache.org/Versions/

