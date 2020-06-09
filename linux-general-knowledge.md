* 重命名文件

    `mv old-file-name new-file-name`

* 删除文件（夹）
    
    `rm -r -f file(directory)`    

* SSH连接Linux超时自动断开
    ```shell
    cd /etc/ssh

    # 查看sshd_config中关于客户端活动状态的配置
    grep ClientAlive sshd_config

    # 默认配置如下
    # ----------------------------
    #ClientAliveInterval 0
    #ClientAliveCountMax 3
    # ----------------------------
    # ClientAliveInterval指定了服务器端向客户端请求消息的时间间隔, 默认是0, 不发送。设置60表示每分钟发送一次, 然后客户端响应, 这样就保持长连接了。
    # ClientAliveCountMax表示服务器发出请求后客户端没有响应的次数达到一定值, 就自动断开。正常情况下, 客户端不会不响应，使用默认值3即可。

    # 备份原配置文件
    cp sshd_config sshd_config.bak

    # 启用客户端活动检查，每60秒检查一次，3次不活动断开连接
    sed -i "s/#ClientAliveInterval 0/ClientAliveInterval 60/g" sshd_config
    sed -i "s/#ClientAliveCountMax 3/ClientAliveCountMax 3/g" sshd_config

    # 确认修改
    grep ClientAlive sshd_config

    # 比较配置文件差异
    diff sshd_config sshd_config.bak

    # 重新加载ssd配置，让配置生效
    service sshd reload
    ```
    来源于：[如何解决SSH连接Linux超时自动断开？](https://www.cnblogs.com/enjoycode/p/5022607.html)