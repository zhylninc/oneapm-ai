# 如何对指定 jar 包进行监控

* 在 jar 的启动命令中执行如下命令，即可完成对指定 jar 的监控：

 ```
 java -javaagent: oneapm.jar -jar *.jar
 ```
 **注意：**
* -javaagent: 后面跟 oneapm.jar 的绝对路径
* jar 后面跟要监控的 jar 的路径
* 这种方式同时支持，使用 spring boot 内嵌 Web 容器，并将整个应用打包成 jar 包的监控

---


