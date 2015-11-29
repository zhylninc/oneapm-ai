# Java 参数配置说明－备份


* OneAPM Java Agent 从 oneapm.properites  配置文件中获取配置信息。您可以在本文中了解各个参数的意义，以及对应的配置方式。

## License_key


* 默认值:这里请输入第二步生成的 License Key

* 生效方式: 重启应用服务器

* 参数类型: String 

* 可选参数: OneAPM 提供的 License Key

* 参数说明:<br>1.请填写 OneAPM 安装步骤提供 License Key;<br>2.配置正确的 License Key 后，OneAPM Agent 将与 OneAPM server 通信，使得 OneAPM Agent 正常工作;


## agent_enabled

 * 默认值: true 

 * 生效方式: 重启应用服务器
 
 * 参数类型: Boolean
 
 * 可选参数:  true 和 false
  
 * 参数说明: 设置为 true 将启用 OneAPM Agent，设置为 false 将停用 OneAPM Agent;


## enable_auto_app_naming

 * 默认值:  false
 
 * 生效方式: 重启应用服务器 

 * 参数类型: Boolean 

 * 可选参数: true 和 false
 
 * 参数说明: <br> 1.当中间件部署多个应用程序时，OneAPM Agent 将自动区分每个应用程序的名称，将业务数据存放相关应用程序;<br>2.设置为 false 后 OneAPM Agent 将不再自动区分应用程序，所有的数据会统一记录<br>在 app_name 参数指定应用程序中。
 

## app_name

 * 默认值:  MyApplication 

 * 生效方式:  重启应用服务器
 
 * 参数类型 : String
  
*  参数说明:app_name只支持英文命名。指定初始化应用程序名称，当中间件部署多个应用时，<br>OneAPM Agent 将所有应用程序数据统一记录到初始化应用程序中，设置enable_auto_app_naming 为 true，OneAPM Agent将数据自动分散到相关应用程序中; 


## enable_auto_transaction_naming

 * 默认值 : true 

 * 生效方式:  重启应用服务器
 
 * 参数类型 : Boolean 

 * 可选参数 : true 和 false
 
 * 参数说明 :<br> 1.设置为 true，启用基于 component-based 事务命名;<br>2.设置为 false 将按照事务请求的 URI 进行命名; 


## log_level

 * 默认值 : off

 * 生效方式 : 立即生效
 
 * 参数类型:  String
 
 * 可选参数:  off / severe / waring / info / fine / finer / finest 

 * 参数说明:<br>  1.设置非 off 值将记录 OneAPM Agent 的工作日志;<br>2.当您需要进行故障分析时，参数级别决定日志的细度; 


## 日志输出级别

* off: 无日志[off]


* severe: 严重[severe]

* waring :正常[severe + warning]

* info :正常[severe + warning + info]

* fine: 精度[severe + warning + info + fine]

* finer: 细度[severe + warning + info + fine + finer]

* finest: 最好[severe + warning + info + fine + finer + finest]



## audit_mode


 * 默认值:  false 

 * 生效方式:  立即生效
 
 * 参数类型:  Boolean 

 * 可选参数:  true / false 

 * 参数说明 : 设置为 true 将以普通文本形式记录 OneAPM Agent 与 OneAPM server 的通信数据，并将数据记录在日志中。 


## log_file_count

默认值  1 
| 生效方式 | 重启应用服务器 |
| 参数类型 | Integer |
| 参数说明 | 限制 OneAPM Agent 日志生成的数量，仅当 log_level 参数处于非 off 值时生效。<br>超过这个数量时，日志将覆盖使用。 |

## log_limit_in_kbytes

| 默认值 | 0 |
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Integer  |
| 参数说明 | 以 KB 为单位，限制 OneAPM Agent 日志的大小。当参数设置为 0 时，<br>则不限制日志大小。|

## log_file_name

| 默认值 | oneapm.log |
| -- | -- |
| 生效方式 | 重启应用服务器 |
| 参数类型 | String |
| 参数说明 | 指定 OneAPM Agent 日志输出的名称。 |

## log_file_path

| 默认值 | oneapm.jar 同级目录 |
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | String |
| 参数说明 | 指定 OneAPM Agent 日志位置，仅当 log_level 参数处于非 off 值时生效。|

## SSL

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean|
| 可选参数 | true / false|
| 参数说明 | 1.设置为 true，指定OneAPM Agent 使用 HTTPS 与 OneAPM server 加密通信;<br>2.设置为 false 则采用 HTTP 方式通信;|

## host

| 默认值 | tpm.oneapm.com|
| -- | -- |
| 生效方式 | 重启应用服务器 |
| 参数类型 | 网络地址 |
| 可选参数 | IP 地址 / 域名 |
| 参数说明 | 指定 OneAPM Agent 与 OneAPM server 的通信地址; |

## port

| 默认值 | 443 |
| -- | -- |
| 生效方式 | 重启应用服务器 |
| 参数类型 | Integer |
| 参数说明 | 指定 OneAPM Agent 与 OneAPM server 的通信端口。|

## proxy_host

| 生效方式 | 重启应用服务器|
| -- | -- |
| 参数类型 | String |
| 可选参数 | IP 地址 / 域名 |
| 参数说明 | OneAPM Agent 使用代理与 OneAPM server 通信时配置指定代理的主机地址。|

## proxy_port

| 生效方式 | 重启应用服务器|
| -- | -- |
|参数类型 | String |
| 可选参数 | IP 地址 / 域名 |
| 参数说明 | OneAPM Agent 使用代理与 OneAPM server 通信时配置指定代理的主机端口。 |

## proxy_user

| 生效方式 | 重启应用服务器|
| -- | -- |
|参数类型 | String |
| 可选参数 | IP 地址 / 域名 |
| 参数说明 | OneAPM Agent 使用代理与 OneAPM server 通信时需要指定代理的用户名。|

## proxy_password

| 生效方式 | 重启应用服务器|
| -- | -- |
| 参数类型 | String |
| 可选参数 | IP 地址 / 域名 |
| 参数说明 | OneAPM Agent 使用代理与 OneAPM server 通信时需要指定代理的密码。|

## capture_params

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false|
| 参数说明 | 1.设置为 true，OneAPM Agent 将捕捉事务 URL 的 HTTP 参数;<br>2.设置为 false 将忽略事务 URL 的 HTTP 参数;|

## ignored_params

| 默认值 | credit_card, ssn, password|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 |String|
| 参数说明 |过滤业务 HTTP 请求参数，多个参数以英文格式的逗号分隔。|

## apdex_t

| 默认值 | 0.5|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Float |
| 可选参数 | Integer / Float |
| 参数说明 | 以国际通用的 apdex 算法标记事务执行状态，参数以 0.5 为例，<br>事务执行时间 0 &ndash; 0.5 秒为优，事务执行时间 0.5 &ndash; 2 秒为可容忍，<br>事务执行时间 2 秒以上为不可容忍;|

## transaction_tracer

* 功能说明：深度捕捉缓慢事务，每分钟将数据发送至 OneAPM server，包括事务中包含的 SQL 语句信息。


## enabled

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | ture / false |
| 参数说明 | 慢Web事务。参数为 transaction_tracer 的子参数，用于控制是否启用 transaction_tracer 功能;|
## transaction_threshold

| 默认值 | apdex_f|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | String (Float) |
| 参数说明 | 当事务执行时间超过该值时，事务将生成 Trace。该参数以秒为单位可以设置整数或浮点数。 |
| 注意 | 慢Web事务。参数为 apdex_f 时，OneAPM 将使用 apdex_t 的4倍参数值;|
## record_sql

| 默认值 |obfuscated|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | String |
| 可选参数 | off / raw / obfuscated |
| 参数说明 | 当启用 transaction_tracer 功能时，该参数标记 SQL 记录的模式，off 为不记录 <br>SQL，raw 为不进行处理并记录原始的 SQL 语句，obfuscated 为经过处理的<br>SQL 语句，加密显示语句的 String 串或数字参数;|
## obfuscated_sql_fields

| 生效方式 | 重启应用服务器|
| -- | -- |
| 参数类型 | String |
| 可选参数 | credit_card, ssn, password 等其他 SQL 指定字段 |
| 参数说明 |默认不启用。仅当 record_sql 为 raw 时，不记录 SQL语句的指定的字段，多个<br>字段使用逗号分隔。 |
## log_sql

| 默认值 | off|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false |
| 参数说明 | OneAPM Agent 使用代理与 OneAPM server 通信时配置指定代理的主机地址。|
## stack_trace_threshold

| 默认值 | 0.5|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Integer |
| 参数说明 | 慢SQL调用。参数以秒为单位，当 SQL 响应时间超过该值时，事务将生成 SQL 语句<br> Trace，解析运行时间较长的 SQL;|
## explain_enabled

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Bloolen |
| 可选参数 | true / false |
| 参数说明 | 设置为 true，将在 SQL 语句的Trace 中生成缓慢 SQL 语句的执行计划，仅支持MySQL<br> 和 PostgreSQL;|
## explain_threshold

| 默认值 | 0.5|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Integer |
| 参数说明 | 当 explain_enabled 为 true 时，OneAPM Agent 捕捉 SQL 执行时间超过该值的 SQL<br> 并生成执行计划;|
## top_n

| 默认值 | 20|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Integer |
| 参数说明 | 该参数表示事务URL 产生的 trace 数量，URL 产生超过参数限制的 trace 将会被丢弃。<br>当参数设置为 0 时，始终显示 URL 最慢的 trace;|

## error_collector

* 功能说明:捕捉业务使用过程中抛出的异常信息.

## enabled

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false |
| 参数说明 | 参数为 error_collector 的子参数，用于控制是否启用 error_collector 功能;|
## ignore_errors

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | String|
| 参数说明 | 当启用 error_collector 功能后，该参数用于忽略指定业务代码中类引发的错误信息。<br>多个类名称以逗号分隔;|
## ignore_status_codes

| 默认值 | 404|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | 数字 |
| 可选参数 | 错误代码 |
| 参数说明 | 当启用 error_collector 功能后，该参数用于忽略指定业务 HTTP 的错误代码，多个代码<br>以逗号分隔，例如 404，505;|
## cross_application_tracer

* 功能说明
跨越应用程序记录外部调用次数与响应时间。


## enabled

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false |
| 参数说明 | 参数为 cross_application_tracer 的子参数，用于控制是否启用外部调用功能;|
## thread_profiler
* 功能说明： 详细追踪事务的信息。包括CPU时间分布，堆栈中代码执行的情况，每个方法的执行时间和调用次数，线程锁的情况。 



## enabled 

|默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false |
| 参数说明 | 参数为 thread_profiler 的子参数，用于控制是否启用线程的性能剖析功能;|

## 配置浏览器监控
* 参数说明：启用真实用户体验，OneAPM Agent 能够记录用户浏览器下载和加载应用系统的时间。



## auto_instrument


| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false |
| 参数说明 | 设置为 true，OneAPM Agent 自动在 JSP 中插入 API 指令，注入 JavaScript 语句进行监控;|
## enabled

| 默认值 | true|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | Boolean |
| 可选参数 | true / false |
| 参数说明 | 参数为 browser_monitoring 的子参数，用于控制是否启用监控前端功能;|
|注意|该网络地址应该设置为所有浏览器客户端可以访问的地址;|
## beacon_port

| 默认值 | 443|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | TCP 端口 |
| 参数说明 | 指定 OneAPM Agent 与 OneAPM server 的通信端口;|

## beacon_apdex_t

| 默认值 | 7.0|
| -- | -- |
| 生效方式 | 重启应用服务器|
| 参数类型 | 数字 |
| 参数说明 | 设置trace阀值，当客户端浏览器页面加载时间超过这个阀值时，将会产生trace记录;|





