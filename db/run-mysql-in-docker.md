# 在Docker中运行Mysql
* 查看可用的 MySQL 版本
    访问 MySQL 镜像库地址：https://hub.docker.com/_/mysql?tab=tags
    
    `docker search mysql`

* 拉取 MySQL 镜像
    
    `docker pull mysql:latest`

* 查看本地镜像
    `docker images`      

* 运行容器

    `docker run -itd --name mysql-local -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql`
    > MYSQL_ROOT_PASSWORD=123456：设置 MySQL 服务 root 用户的密码

* 安装成功
    
    `docker ps`

* 连接mysql

    - 进入容器`docker exec -it mysql bash`
    - 登录mysql `mysql -u root -p`
        > 登陆成功即可看到mysql版本