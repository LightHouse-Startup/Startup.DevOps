# 在Centos7上安装java环境

## 1、检查系统Jdk安装情况
* 查看是否安装了Java
    
    `java -version`

* 查看内置JDK

    `rpm -qa | grep jdk`

* 卸载内置jdk
    
    `yum remove xxx` 
    > xxx为上条命令的jdk包名

## 2、下载
* [jdk地址](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
    
    使用wget命令下载，地址需要登录Oracle网站才能拿到，并且有时效性，过期得重新登录获取。
    
* wget下载jdk
    ```shell
    wget -c https://download.oracle.com/otn/java/jdk/8u251-b08/3d5a2bb8f8d4428b be94aed7ec7ae784/jdk-8u251-linux-x64.tar.gz?AuthParam=1591708888_2659b7785b51e713b6816f7c41419307 -O jdk-8u251-linux-x64.tar.gz
    ```
    >-c表示断点续传 -O重命名（O为大写） 

* 检查安装包大小是否正常
    `ls -lht`

    ps:这里建议下载到`/usr/local/src`目录

## 3、安装
* 创建安装目录

    `mkdir /usr/local/java/`
* 解压至安装目录

    `tar -zxvf jdk-8u251-linux-x64.tar.gz -C /usr/local/java/`

## 4、配置环境变量
* 配置JAVA_HOME，PATH

    编辑文件`vim /etc/profile`，在最后追加
    ```shell
    # java env config
    export JAVA_HOME=/usr/local/java/jdk1.8.0_251
    export JRE_HOME=${JAVA_HOME}/jre
    export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
    export PATH=${JAVA_HOME}/bin:$PATH
    ```
* 使配置生效
    `source /etc/profile`

* 添加软链接
    `ln -s /usr/local/java/jjdk1.8.0_251/bin/java /usr/bin/java`        
* 验证
    `java -version`

## 来源
* [CentOS7安装Java8](https://blog.csdn.net/small_love/article/details/77394721)
* [CentOS 7 安装 JAVA环境（JDK 1.8）](https://www.cnblogs.com/stulzq/p/9286878.html)
