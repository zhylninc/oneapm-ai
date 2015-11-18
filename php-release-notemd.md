# PHP版本日志

##OneAPM PHP Agent 2.4.0

发布日期：2015/10/08

**增加功能：**

1. 新增通过 PHP Agent 自动注入 Bi Agent 脚本功能；
+ 新增通过 PHP Agent Bi API 注入 Bi Agent 脚本功能；
+ 新增对 pathinfo 格式 URI 的支持；
+ 新增 PHP 应用和 Java 应用的数据打通，具有调用关系的应用能直接在调用栈中跳转；
+ 新增对 Yii 2.0 的支持，优化对 Yii 1.1 的支持；
+ 新增在调用栈中显示代码所在行号；
+ 增加对 HTTPS 传输的支持；
+ 增加对代理配置的支持；
+ 增加对 FreeBSD 系统的支持。

**优化功能：**
1. 优化安装脚本，在监测到 PHP 环境存在问题时终止安装程序；
+ 优化安装脚本，在无法监测到有效 php.ini 文件时提示用户手动指定绝对路径；
+ 优化 Agent 和 daemon 通信规则，进一步降低资源占用；
+ 优化按子域名拆分聚合的规则，逻辑更加人性化；
+ 优化外部服务时间计算规则，结果更加人性化。
+ 修复问题：
+ 修复在新版本 UI 中，具体外部服务页面中调用者时间占比为空的问题；
+ 修复在新版本 UI 中，拓扑页面的 Web 事务详情中没有外部服务的问题；
+ 修复在新版本 UI 中，错误信息页面自定义参数缺失的问题；
+ 修复在同一台机器部署多个应用时数据合并的问题；
+ 修复在极少数情况下不能通过 kill 命令结束 oneapm-daemon 的问题；
+ 修复在极少数情况下无法启动 oneapm-daemon 的问题；
+ 修复在极少数情况下可能出现的崩溃问题。

**备注：**
1. 本次发布的探针暂不支持 PHP 5.2。




##OneAPM PHP Agent 2.3.12

发布日期：2015/07/14
修复问题：
修复 2.3.11 探针在极少数环境下 daemon 重启问题；
修复 BTM 配置无法更新问题。
增加功能：
支持 business transaction （自定义事务）功能
增加对 fsockopen 接口数据的抓取功能
Agent 的 log 大小限制在 30MB 左右
Daemon 的 log 大小限制在 512MB 左右
Daemon 上传数据使用 Deflate 压缩
OneAPM PHP Agent 2.3.11

发布日期：2015/06/23
修复问题：
1. 修复 PHP Agent 2.3.10 安装脚本卸载命令 purge 不能用的问题。移除 purge 命令，Uninstall 命令直接完全删除。
增加功能：
切换按照网站名显示服务器，默认情况下按照 hostname 命名服务器。
通过设置 oneapm.usesitename=true，切换成按照 $_SERVER['HTTP_HOST'] 的值命名服务器。
Web 事务参数配置功能增加对 POST 参数的支持。
新增 Business Transactions 功能，支持自定义参数拆分 Web 事务。
        1）URI 参数的”等于“匹配模式。
        2）HTTP 参数的”等于“匹配模式。
        3）Header 参数的”等于“匹配模式。
OneAPM PHP Agent 2.3.10

发布日期：2015/06／11
修复问题：
解决单一入口的问题。
增加功能：
php.ini 中新增2个用于配置事务名的解决配置项，分别是 auto_transcation_args 和 auto_transcation_naming。
OneAPM PHP Agent 2.3.9

发布日期：2015/06／2
修复问题：
修复“总览 > web事务”中 Trace 只显示 {main} 的 Bug；
修复 Apdex 值不准确问题。
增加功能：
新增对 NoSQL 的支持(Redis, MongoDB, Memcache, Memcached)；
优化脚本安装流程。
OneAPM PHP Agent 2.3.8

发布日期：2015/05／26
修复问题：
优化 oneapm-daemon 内存占用问题，资源消耗明显下降，性能显著提升；
重启 PHP 应用 oneapm-daemon 伴随启动，无需手动启动 oneapm-daemon。
增加功能：
完善 php.ini 文件中的配置项。
OneAPM PHP Agent 2.3.7

发布日期：2015/04／30
修复问题：
修复 ubuntu 系统，多个 php.ini 没有正确配置的问题。
OneAPM PHP Agent 2.3.6

发布日期：2015/04／27
修复问题：
修复没有 php 扩展目录时，安装失败的问题。
增加功能：
支持自动监控前端浏览器性能；
安装脚本添加升级功能；
在配置选项中，可配置错误报告级别。
OneAPM PHP Agent 2.3.5

发布日期：2015/04／21
修复问题：
大幅提升 PHP Agent 性能；
修复 PHP2.3.1 不支持 amh4.2 和框架报错的问题；
修复出现多服务器的问题。
增加功能：
支持 PHP 5.2；
安装脚本添加升级功能 。
OneAPM PHP Agent 2.2.1

发布日期：2015/3/11
下载链接：PHP Agent 2.2.1
修复问题：
解决各别用户 uri 为空的问题。
增加功能：
新增支持 PostgreSQL 数据库。
OneAPM PHP Agent 2.0.1

发布日期：2015/3/6
修复问题：
解决安装探针后无法启动的 php-fpm 问题。
增加功能：
新增支持PHP 5.6；
新增"应用程序-监控-总览-响应时间图表"中外部事物曲线信息的功能。
OneAPM PHP Agent 1.0.1.47

发布日期：2015/2/13
修复问题：
解决 discuz 框架压测一段时间没有数据问题;
解决配置文件文字提示出入问题;
解决 php-daemon 自动退出问题;
其他小问题的 fix。
增加功能：
支持外部服务功能;
支持 AMH 面板环境;
支持 phpMyAdmin 环境;
安装脚本修改,无需输入安装目录。