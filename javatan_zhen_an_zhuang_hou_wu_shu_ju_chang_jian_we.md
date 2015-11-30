# Java 探针安装后无数据常见问题


## **常见问题：**

** 问题 1 :windows下的Tomcat 容器参考官方部署步骤部署oneapm,提示成功了，但是还是看不到数据，是什么原因啊？**

* 回答:首先查看有没有／OneAPM／logs目录，如果不存在，就是oneapm就是没有部署成功，首先查看 tomcat bin/catalina.bat 脚本中 JAVA_OPTS="-Xmx1024m -Xms512m"中的设置，然后
   设置为JAVA_OPTS="-Xmx1024m -Xms512m －javaagent:/path/to/oneapm.jar" 然后重启tomcat,可以解决你的问题。注意：-javaagent:后面跟安装oneapm.jar的绝对路径；


**问题 2 ：tomcat下部署oneapm并重启后，／OneAPM/logs目录也可以看到，但是还是看不到数据，是什么原因啊？**

* 回答：遇到这种情况，排查方法如下：

 1.排查网络是否跟oneapm正常打通，执行命令 telnet tpm.oneapm.com 443 或者 ping tpm.oneapm.com，如果不通请检查网络环境，并修复，确认可以跟oneapm打通；

 2.排查服务器的时间是否为北京时间东八区的时间，如果不是请更新下服务器的时间跟北京东八区的时间保持一致；
 
 3.打开并检查／OneAPM/oneapm.properties文件配置，设置 ssl = true；host = tpm.oneapm.com；port = 443；
 
 4.检查 tomcat 根目录下是否有temp目录，如果没有请手动创建temp目录；例如：
 ```
 ➜  apache-tomcat-8.0.28  ls -l
total 14896
-rw-r--r--@  1 qinheng  staff    58068 Oct  7 19:26 LICENSE
-rw-r--r--@  1 qinheng  staff     1489 Oct  7 19:26 NOTICE
drwxr-xr-x@  8 qinheng  staff      272 Nov 26 23:13 OneAPM
-rw-r--r--@  1 qinheng  staff  7530606 Nov 27 09:56 OneAPM.zip
-rw-r--r--@  1 qinheng  staff     6913 Oct  7 19:26 RELEASE-NOTES
-rw-r--r--@  1 qinheng  staff    16682 Oct  7 19:26 RUNNING.txt
drwxr-xr-x@ 26 qinheng  staff      884 Nov 26 23:26 bin
drwxr-xr-x@ 11 qinheng  staff      374 Nov 26 23:28 conf
drwxr-xr-x@ 26 qinheng  staff      884 Nov 26 23:20 lib
drwxr-xr-x@ 13 qinheng  staff      442 Nov 27 10:02 logs
drwxr-xr-x@  9 qinheng  staff      306 Nov 27 21:50 temp
drwxr-xr-x@ 10 qinheng  staff      340 Nov 27 21:50 webapps
drwxr-xr-x@  3 qinheng  staff      102 Nov 26 23:28 work
➜  apache-tomcat-8.0.28
```
注意：Tomcat根目录下必须要有temp目录；


**问题 3 ：Java开发的 jar包程序 应该如何使用oneapm进行监控？**

* 回答：jar包应用根据jar的启动命令加入启动参数 －javaagent:/full/path/to/oneapm.jar ,
例如：
1.通过 执行命令 java -jar test.jar 启动jar程序，想使用oneapm来监控jar程序，正确的执行命令是 java －javaagent:/full/path/to/oneapm.jar -jar test.jar

 2.通过脚本启动jar 程序，脚本模版如下：
```
source /etc/profile 
cd 'dirname $0'
cmd="java -Xms512m -Xmx2048m -XX:PermSize=256m -jar test.jar"
exec ${cmd} 
echo "execute test.jar finish......"
```
正确引入 oneapm.jar 方式 脚本应修改为：
```
cmd="java -Xms512m -Xmx2048m -XX:PermSize=256m －javaagent:/full/path/to/oneapm.jar -XX:PermSize=256m -XX:MaxPermSize=256m -jar test.jar" 
```
注意：－javaagent:后面跟安装oneapm.jar的绝对路径；

**问题 4 ：可以看到/OneAPM/logs/目录，网络和时间都是正确的，还是没有数据，是什么原因啊？**

* 回答：检查／OneAPM的权限，保证／OneAPM／目录及目录下的文件有执行的权限，再重启启动tomcat；
例如：

 ```
➜  apache-tomcat-8.0.28  ls -l OneAPM
total 11864
drwxrwxrwx@ 42 qinheng  staff     1428 Aug 27 02:50 extensions
drwxr-xr-x@ 25 qinheng  staff      850 Aug 27 10:51 lib
drwxr-xr-x   3 qinheng  staff      102 Nov 26 23:13 logs
-rw-r--r--@  1 qinheng  staff  6057639 Aug 27 10:51 oneapm.jar
-rw-r--r--@  1 qinheng  staff    13679 Nov 26 23:10 oneapm.properties
➜  apache-tomcat-8.0.28
```


**问题 5 :Centos下的Tomcat 容器参考官方部署步骤部署oneapm,提示" Install successful"表示成功了，但是还是看不到数据，是什么原因啊？**

* 回答：执行 ps aux |grep oneapm 命令，查看oneapm进程是否存在,如果没有，检查tomcat 容器，是否在启动脚本里配置过 VM参数，例如：JAVA_OPTS="-Xmx1024m -Xms512m " ，如果有应修改为 JAVA_OPTS="-Xmx1024m -Xms512m －javaagent:/path/to/oneapm.jar" ；注意：-javaagent:后面跟安装oneapm.jar的绝对路径；


**问题 6 ：在／OneAPM 目录下执行 java -jar oneapm.jar 后 报错如下：”com.blueware.monitor ERROR: init charset error, using default encoding in Strings utf-8“，是什么原因啊？**

* 回答：oneapm默认使用的utf-8跟你的tomcat的默认编码格式不一致导致的错误，这个错误可以忽略，不影响oneapm的使用；


**问题 7 ：成功部署oneapm后，重启应用服务器后报错"Error bootstrapping oneapm agent:java.lang.RuntimeException: java.io.IOException: No such file or directory",是什么原应啊？**

* 回答：这个错误是因为，tomcat 目录缺少 temp目录，手动创建temp目录，再重启tomcat就不再会有这个报错；


**问题 8 ：错误信息”中没有 Sample Stack Trace;**

* 回答：当错误被快速重复抛出，基于性能的考虑，Java 编译器可能会优化掉 Sample stack trace 。若要禁用该优化，您可以在 JVM 参数中加上：
-XX:-OmitStackTraceInFastThrow;


**问题 9 ：重启应用服务器后抛出 Error opening zip file: oneapm.jar ；**

* 回答：原因：Agent jar 包的访问路径在 -javaagent JVM 选项中是完全限定的。如果没有正确地指定路径，该错误会在应用程序服务器启动时抛出，并且 JVM 也会退出运行。
解决办法：指定到 -javaagent 选项中 oneapm.jar 文件的完整路径。例如，如果 oneapm.jar 文件是在 Tomcat 主目录 /home/tomcat 中的 OneAPM 目录下，该选项应该以如下方式指定：-javaagent:/home/tomcat/oneapm/oneapm.jar 注意：-javaagent:后面跟oneapm.jar安装的绝对路径;


**问题 10 ：部署 Java 探针至 Tomcat，重启 Tomcat 后，日志报错，报错信息如下：“blueware 1 ERROR: license_key is expired in the config, not starting BlueWare Agent”**

* 回答：原因：License 许可过期。
解决方法：1.重新登陆 OneAPM 生成 License Key；2.将 License Key 复制并写入到探针的 oneapm.properites 文件中；3.重启 Tomcat；

