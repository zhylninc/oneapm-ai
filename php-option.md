# PHP

OneAPM PHP Agent 从 oneapm.cfg 和 php.ini 两个配置文件中获取配置信息。您可以在本文中了解各个参数的意义，以及对应的配置方式。

你可以在这些位置找到该配置文件：
+ oneapm.cfg 的位置：/etc/oneapm/oneapm.cfg
+ php.ini 的位置: 自定义路径


##oneapm.cfg

|配置名称|默认值|生效方式|参数类型|参数说明|
|:-------------|:-------------|:-----|:---|:---|
|logfile|var/log/oneapm/oneapm-daemon.log|重启 daemon|String|log 文件所在路径|
|loglevel|off|重启 daemon|String|deamon 程序的日志输出级别，可选值 (error、warning、info、debug、verbosedebug)。|
|collector_host|tpm.oneapm.com|重启 daemon|String|指定 OneAPM daemon 与 OneAPM server 的通信地址。|
|port|http:80,ssl:443|重启 daemon|String|指定 OneAPM daemon 与 OneAPM server 的通信端口。|
|ssl_connect|0|重启 daemon|Number|是否开启 ssl 协议传输。默认值0，设置为1开启。|
|proxy|null|重启 daemon|String|代理参数，有效格式为：user:password@host[:port]或者 host[:port]|

>修改 oneapm.cfg 文件后，需要重启 oneapm-daemon 进程后才能生效。
重启命令：/etc/init.d/oneapm-daemon-service restart


##php.ini 配置文件
|配置名称|默认值|生效方式|参数类型|参数说明|
|:-------------|:-------------|:-----|:---|:---|
|oneapm.appname|PHP Application|1、停止daemon。2、重启应用服务器。|String|可以根据自身需要对应用程序进行命名。|
|oneapm.key|无|重启应用服务器|String|请输入 OneAPM PHP Agent 安装步骤中第一步生成的授权编号。License 默认为空，填写正确的License才能正常上传数据。|
|oneapm.record_sql|obfuscated|重启应用服务器|String|该参数控制抓取的 sql 字段信息。可将其设置为 raw，抓取完整的 sql 信息；也可以设置为 off，不抓取 sql 信息；设置为 obfuscated 抓取的是混淆模式的 sql，sql 中重要的数据信息不显示。|
|oneapm.transaction_threshold|0.5|重启应用服务器|Number|判断是否记录分析慢事务的阀值。超过这个值 Agent 开始记录分析慢事务的详细信息（trace）。单位：秒。|
|oneapm.explain_threshold |0.5|重启应用服务器|Number|判断是否记录分析慢 SQL 的阀值。超过这个值 Agent 开始记录分析慢 SQL 的详细信息。单位：秒。|
|oneapm.errorlevel|ERROR|重启应用服务器|String|配置错误信息中记录的 PHP 错误级别，可选项(NOTICE, WARNING, ERROR, CLOSE)。|
|oneapm.loglevel|ERROR|重启应用服务器|String|探针的日志输出级别。可选值(ERROR, WARN, INFO, TRACE, DEBUG )。|
|oneapm.auto_transaction_get|空|重启应用服务器|String|设置用 get 参数传递的事务名称，比如 URL 为 http://url/index.php?s=/home/index/index.html ，如果设置此配置项的值为"s"，则 Web 事务名就会变成 WebTransaction/Uri/home/index/index.html，而不是默认的 WebTransaction/Uri/home/index/index.html。|
|oneapm.auto_transaction_post|空|重启应用服务器|String|设置用 post 参数传递事务名称，例如 URL 为 http：//url/index.PHP，post 表单参数 name=admin， password=zabbix，设置 oneapm.auto_transaction_post = name，事务名称就更改为：WebTransaction/Uri/admin，默认事务名称是：WebTransaction/Uri/index.php|
|oneapm.auto_transaction_naming|true|	重启应用服务器|	String|	是否抓取单一入口框架。默认抓取。|
|oneapm.usesitename|false|重启应用服务器|String|按照网站名区分应用。|
|oneapm.http_capture_params|true|重启应用服务器|String|是否抓取Http参数。可选值(false)。|
|oneapm.is_pathinfo|false|重启应用服务器|String|是否启用 pathinfo 模式，如果开启，PHP 探针抓取的事务展示模式是：http：//www.xxx.com/index.PHP/key1/key2/key3，如果不开启，PHP 探针抓取的事务展示模式是：http：//www.xxx.com/index.php|
|oneapm.num_pathinfo|0|重启应用服务器|Number|抓取的 pathinfo 展示个数，只有在 oneapm.is_pathinfo 设置为 true 时有效，设置 oneapm.num_pathinfo=0，抓取的 http：//www.xxx.com/index.PHP/key1/key2/key3 后面参数个数不限，例如设置为1，抓取的 web 事务展示为：http：//www.xxx.com/index.PHP/key1|
|oneapm.browser_monitoring|false|重启应用服务器|String|是否开启自动注入 Bi Agent 脚本。默认值 false，设置为 true 开启。|
|oneapm.browser_monitoring.is_js_text|false|重启应用服务器|String|切换 Bi Agent 脚本注入方式，url 注入加载链接；text 注入脚本内容。默认值 false；可选值 url，text。|
|oneapm.browser_monitoring.request.ip| all|重启应用服务器|String| 在开启插码功能下，对指定ip进行插码。对用户IP过滤（即浏览器端IP），默认值是all，表示对所有用户IP插码。如果只允许对特定IP请求进行插码，则配置用户IP即可，多个IP之间用英文逗号进行分割，例如：只对10.0.0.1和10.0.0.2用户进行插码，则配置为：browser_monitoring.request.ip = 10.0.0.1,10.0.0.2|
|oneapm.browser_monitoring.request.url|all|重启应用服务器|String| 在开启插码功能下，对指定url进行插码。对请求的url进行过滤，默认值是all，表示对所有url插码。如果对特定请求进行插码，配置其url即可，多个URL之前用英文逗号分隔。例如; 对 http://www.example.com/index.php请求进行插码，则配置为：browser_monitoring.request.url = http://www.example.com/index.php|
|oneapm.browser_monitoring.request.param|all|重启应用服务器|String| 在开启插码功能下，对指定请求参数进行插码。对请求的参数进行过滤，默认是all，表示对所有参数插码。参数配置格式是： 参数名:参数值 ，多个参数用英文逗号分隔开。对参数顺序没有要求，满足POST、GET请求，一般结合browser_monitoring.request.url进行使用。例如1：只对http://www.example.com/index.php?service=login&name=bob进行插码，则配置如下：browser_monitoring.request.url =  http://www.example.com/index.php|
|browser_monitoring.request.param| service:login,name:bob|重启应用服务器|String|例如2：http://www.example.com/forum.php?mod=forumdisplay&fid=2&page=1|
|browser_monitoring.request.param | page:1,mod:forumdisplay,fid:2 |重启应用服务器|String|顺序不同，可以插码|
|browser_monitoring.request.param | mod:forumdisplay,fid:2|重启应用服务器|String| 配置参数少于实际参数，可以插码
|browser_monitoring.request.param | mod:forumdisplay,fid:2,page:1,uid:6|重启应用服务器|String| 配置参数多于实际参数，被过滤，不能插码|







>备注：以下参数的优先级顺序为（按从高到低排列）
+ btm
+ oneapm.usesitename
+ oneapm.auto_transaction_naming
+ oneapm.auto_transaction_get
+ oneapm.auto_transaction_post
+ oneapm.is_pathinfo
+ default

>修改 php.ini 文件后，需要重启 PHP 服务器(例如 Apache、PHP-FPM)才能生效。
