# Jetty 安装方法


* Jetty 7及以上版本 安装方法

 在jetty.sh的脚本中，See if JETTY_PORT is defined 的模块下加入
```
JAVA_OPTIONS+=("-javaagent:/full/path/to/oneapm.jar")
```
* Jetty 6及以下版本 安装方法

 Jetty 启动脚本 (jetty.sh)可以使用 JAVA_OPTIONS 环境变量配置：
* 

 ```
export JAVA_OPTIONS="${JAVA_OPTIONS}
  -javaagent:/full/path/to/oneapm.jar"
 ```
 ***
 #####注意：/full/path/to/oneapm.jar为oneapm绝对路径

