# 在Docker中运行Redis
* 搜索镜像

    `docker search redis`

* 下载官方镜像

    `docker pull redis`

* 启动redis

    `docker run -dt -p 6379:6379 --restart=always --name myredis redis`    
    > --restart=always：该容器会跟随docker进程重启
* 连接redis

    `docker exec -it redis-test /bin/bash`

    ps：

    关于Redis集群搭建后续再记录

参考：
* [Docker 安装 Redis](https://www.runoob.com/docker/docker-install-redis.html)
* [Docker redis 集群搭建](https://www.runoob.com/docker/docker-redis-cluster.html)