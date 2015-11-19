# Java Agent 更新方法

* OneAPM Java Agent 更新，无需卸载 Agent 探针，再重新部署。您只需遵循以下步骤，来完成 Agent 的更新：

* 在安装步骤页面，下载 Java 最新版本 Agent。

* 解压出 OneAPM_java_agent_x.x.x.zip 中的 oneapm.jar 文件。

* 替换掉原有版本的 oneapm.jar 文件，至最新版本。

* 配置文件 oneapm.properties 替换至最新版本
 
* 内容需要按照 properties 中的重新配置一下
重启应用服务器。


* 查看新版本的 Agent 是否可以正常地向 OneAPM 发送数据。
