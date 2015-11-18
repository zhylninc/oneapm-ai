# Weblogic中部署方法


* Linux & Mac

 修改 startWebLogic.sh或startWebLogic.bat，添加内容如下：
```
export JAVA_OPTIONS="$JAVA_OPTIONS -javaagent:/path/to/oneapm.jar"
```
* Windows

 修改 startWebLogic.sh 或 startWebLogic.bat，添加内容如下：
* 

 ```
set JAVA_OPTIONS=%JAVA_OPTIONS% -javaagent:"C:\path\to\oneapm.jar"
 ```
 ***
 #####注意：/full/path/to/oneapm.jar为oneapm绝对路径