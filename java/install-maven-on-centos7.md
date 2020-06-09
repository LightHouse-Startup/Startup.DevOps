# 在Centos7上安装Maven
[Java安装](install-java-jdk-on-centos7)

## 下载

* maven 3.x 下载地址: https://maven.apache.org/download.cgi
    
    `wget -c https://mirror.bit.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz`

## 安装

* 解压安装包
    
    `tar -zxvf apache-maven-3.6.3-bin.tar.gz`

* 移动到安装目录

    `mv apache-maven-3.6.1 /usr/local/apache-maven-3.6.1`

## 配置环境变量
* 添加MAVEN_HOME

   编辑文件`vim /etc/profile`，在最后追加

    ```shell
    # java env config
    export JAVA_HOME=/usr/local/java/jdk1.8.0_251
    export JRE_HOME=${JAVA_HOME}/jre
    export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib

    # maven env config
    export MAVEN_HOME=/usr/local/apache-maven-3.6.3
    export PATH=$PATH:${JAVA_HOME}/bin:${MAVEN_HOME}/bin
    ```
* 使配置生效
    `source /etc/profile`
* 验证
    `mvn -version`
    
## 来源
* [centos 7 配置 maven 3.x](https://blog.csdn.net/zhaosongbin/article/details/89963415)