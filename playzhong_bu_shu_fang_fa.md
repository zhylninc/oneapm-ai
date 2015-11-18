# play中部署方法
* Play 2.2+ production 模式安装方法

 注意：play 启动命令不支持 -javaagent 选项。
 
 使用解压命令：
 ```
 play clean dist && unzip target/universal/*.zip
 ```
 在启动 Play 框架的应用程序时添加 -J-javaagent 选项。例如：
 ```
 cd UNZIPPEDFOLDER;
 ```
 ```
 ./bin/SCRIPTNAME -J-javaagent:path/to/oneapm.jar
 ```
 Play 2 production 模式安装方法
 
 注意：play 启动命令不支持 -javaagent 选项。
 
 注意：play 启动命令不支持 -javaagent 选项。
 
 ```
 play clean dist && unzip dist/*.zip
 ```
 在启动 play 框架的应用程序时添加 -javaagent 选项。例如：
 
 ```
 cd UNZIPPEDFOLDER;
 ```
 ```
 chmod a+x start;
 ```
 ```
 ./start -javaagent:path/to/oneapm.jar
 ```