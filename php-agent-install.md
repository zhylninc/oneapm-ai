# PHP
1、获取授权编号

    注册用户进来之后会自动分配一个license key。
    
2、下载探针
    
    

    1>手动下载
    2>命令下载
    
3、安装探针

    解压Agent安装包
    tar -xzf OneAPM_php_Agent_latest.tar.gz
    
    定位至「安装包所在路径」
    cd oneapm-php5-linux-install-script
    
    执行安装脚本
    sudo ./oneapm-install install  --license=your license key
    
    等待安装脚本执行。若出现以下信息，则安装成功。
    OneAPM is now installed on your system. Congratulations!
    
4. 重启
    
    重启 Apache 或 php-fpm。

    然后，稍等片刻，等待 OneAPM 接收 Agent 发送的数据。
    
    