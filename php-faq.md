# PHP

##注意事项 
 1. 之所以要知道你的PHP bin 目录，是因为你的PHP命令行程序在此目录。我们要通过 PHP命令行获取你的PHP版本；是否为线程安全；php.ini的路径以及PHP扩展的安装路径。获取这些信息后我们的安装脚本才能将对应的程序放置在相应的目录，修改php.ini来加入我们程序。

 2. PHP-Agent 分为两个部分：
  一个是PHP扩展，负责收集数据，并发送给 oneapm-daemon
  一个是oneapm-daemon 负责将数据缓存一段时间发送给我们的SaaS端服务器

 3. 我们的产品不能与其他同类型的产品同时安装（如 Xdebug， New Relic等）

 4. 需要Root权限

 5. 需要关闭SELinux， 没有关闭的话我们的 PHP扩展无法与 oneapm-daemon进行通信

##可能遇到问题
 1. 后台没有数据
请检查php.ini文件中的oneapm.key=”license”是否正确
请检查是否能够ping通我们的服务器 tpm.oneapm.com
请检查进程中是否启动了oneapm-daemon [ps –ef|grep oneapm-daemon]
请检查phpinfo中是否有 OneAPM的信息
重启一次 oneapm-daemon 与 PHP
请检查你的环境是否在我们的支持列表中
如果仍然没有数据请修改配置文件，开启日志 debug模式（可以打印详细的日志）
1）.  php.ini 中 oneapm.loglevel=debug
2）.  /etc/oneapm/oneapm.cfg 中 loglevel=debug
将产生的日志发送给我们，可以更快的解决你的问题

 2. 如果在监控的应用程序中看不到相关的trace和慢sql信息，可能是你的网站和数据库检索速度很快。因此可以修改相应的配置信息对trace和慢sql产生的时间进行修改。
在php.ini配置文件最下方添加：oneapm.stack_trace_threshold=500（默认值是500ms，可以安装自己网站的参数进行修改，此参数时间单位是：毫秒）
修改完毕，请重启PHP服务器(Apache、PHP-FPM等)和oneapm-daemon

 3. 崩溃
也有可能你安装了一些特殊的插件，会导致我们crash。如果发现请立即联系我们。我们会尽快解决该问题

 4. 在使用过程中，可能遇到重启oneapm-daemon进程的情况
停止oneapm-daemon进程的命令：service oneapm-daemon-service stop
启动oneapm-daemon进程的命令：service oneapm-daemon-service start
重启oneapm-daemon进程的命令：service oneapm-daemon-service restart

 5. PHP探针在安装过程中，如果机器中没有/tmp文件夹会自动生成，卸载PHP探针会将/var/log/oneapm压缩成tar包放在/tmp文件夹下，因此PHP探针安装成功后，请不要随便删除文件夹/tmp，否则卸载探针时会报错。
 
 6. 目前由于server端进行了重构，当静态修改php.ini中的配置时，请重新命名后在重启oneapm-daemon和Apache/PHP-FPM，否则配置文件不生效。