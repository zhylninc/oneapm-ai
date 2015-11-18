# Java 版本日志

注意：依据 JDK 的版本，OneAPM Java Agent有两套版本：
1.x版本的 Java Agent 针对 JDK 1.5
3.x版本的 Java Agent 针对 JDK 1.6, 1.7 1.8

OneAPM Java Agent 3.2.0

发布日期：2015/8/28
**新增功能：**
支持中文 appName；
支持根据系统参数重命名事务名称*；
请求参数长度可配置*；
dubbo 分布式支持。
修复问题：
删除以进程号命名的异常信息；
修复 java8 servlet 日志报错；
校准 external 与 external transaction 的数据准确性；
修复 sql 参数在 Windows 出现乱码的问题；
修复小于阀值的 trace 上传问题；
修复 MongoDB 调用者时间占比不显示的问题。
备注：
支持根据系统参数重命名事务名称：
通过设置参数 transaction_parameter_names 区分各参数名，参数之间用逗号分隔，比如：transaction_parameter_names = para1， para2；系统会在抓取到对应参数值后将不同参数对应的事物分类命名与计算。
请求参数长度可配置：
探针默认抓取参数值的最大长度为：256，修改 transaction_tracer.max_user_parameter_size 属性值可以调整这个最大长度值。比如：transaction_tracer.max_user_parameter_size = 300，标示抓取参数值的最大长度为300。

OneAPM Java Agent 3.1.9

发布日期：2015/7/30
下载地址：Java Agent 3.1.9
新增功能：
支持 multipart/form-data 
完善 SQL 参数值的抓取
备注：
关于 multipart/form-data 支持，目前可以抓取文本域参数以及上传文件的大小；整个文件内容的抓取虽然可以实现，但并不建议，因为抓取整个文件会大量消耗系统性能；
关于 SQL 参数值抓取，需要在“应用设置”中将“慢 sql 追踪”模式选为“原始sql” 或配置参数“transaction_tracer.record_sql = raw”。

OneAPM Java Agent 1.1.0

发布日期：2015/6/26
修复问题：
与 Kodo 框架冲突
版本命名问题
增加功能：
JSP 异常抓取

OneAPM Java Agent 3.1.8

发布日期：2015/6/18
修复问题：
新增支持 NoSQL DB 数据抓取。

OneAPM Java Agent 3.1.7

发布日期：2015/4/22
修复问题：
代码混淆。

OneAPM Java Agent 3.1.6

发布日期：2015/4/10
增加功能：
新增控制台在线修改探针配置的功能；
浏览器监控功能：增加对 wildfly、tongweb、bes 等应用服务器的支持；
优化探针配置文件：
文件扩展名从 yml 改为了 properties，减少修改时出错的几率。
新增配置项 appserver_port，用于配置应用的服务端口，此端口会增加到控制台中查看到的应用服务器的命名。
部分用户反馈非主动开启浏览器监控功能的问题，此功能配置项删除，默认值由 true 改为 false。

OneAPM Java Agent 3.1.1

发布日期：2015/3/9
下载链接：Java Agent 3.1.1
增加功能：
增加 WebSphere 支持。
修复问题：
修复浏览器功能配置的问题。

OneAPM Java Agent 3.1.0

Java Agent 3.1.0 支持更多 JDK 和 EJB 版本，特别增设了对 Tuxedo 的支持，以及 MongoDB 的支持。
发布日期：2015/2/2
增加功能：
支持 JDK 1.6/JDK 1.7/JDK 1.8 ；
增加 EJB 2.0，EJB 3.0 框架支持；
增加 Tuxedo 支持；
支持(Tomcat/Weblogic/Bes/Jboss/Jetty/)浏览器数据抓取；
支持 MongoDB 的所有版本；
增加 Redis v2.6.0 版本支持；
增加 Memcache 版本支持（Spymemcache、Xmemcache、Memcache for Java）
基于 Servlet 的事务划分功能。

OneAPM Java Agent 2.0

发布日期：2014/11/17
增加功能：
新增支持 JDK 1.7/JDK 1.8；
增加 EJB 2.0，EJB 3.0 框架支持。
修复问题：
修复了 licence 过期的 Bug，更新 licence 后无需再重启应用；（如果您的监控不可用了，请及时更新探针，目前 OneAPM 还在免费使用中！）
修复在 tomcat 7 获取不到端口问题。

OneAPM Java Agent 1.0

发布日期：2014/10/30
增加功能：
增加 EJB 2.0，EJB 3.0 框架支持。
支持在 xml 文件通配接口或者注解，可以精确抓取到类的方法；
修复问题：
解决浏览器没有数据问题；
解决在 Tomcat 7 获取不到端口问题；
设置 Agent 版本号；（1.0 支持 1.5 和 1.6 版本的 JDK）
把探针端的过期验证解除，转由服务器端进行统一验证。

