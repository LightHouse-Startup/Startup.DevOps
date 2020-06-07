# 使用Portainer管理Docker镜像&容器
Portainer可用于可视化管理Docker镜像和容器，包括：下载上传镜像，创建、启动、停止、移除容器等。

* 搜索镜像源

    `docker search portainer`

* 下载官方镜像

    `docker pull portainer/portainer`

* 启动portainer
    
    `docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock --restart=always --name portainer portainer/portainer`
    >- 这里一定要使用`-v`进行挂载，登入portainer后配置连接local/remote docker进程时会检查

* portainer功能展示
    - dashboard
    ![dashboard](images/{7EA9BB5E-1C62-42F9-92FB-427819E24696}_20200604112657.jpg)

    - pull image
    ![pull image](images/{4394B1D1-D30B-4591-BA13-A5B97B5EB857}_20200604112346.jpg)

    - run container
    ![run container](images/{A23887B4-964C-4963-B294-450ED60157C9}_20200604112958.jpg)

    - manage container
    ![manage container](images/{DD659F5A-ECE2-4C73-8265-479CFA7A5C2D}_20200604112835.jpg)

    
    ps:
    
    以上只是管理本地docker的设置，管理remote的后续用到再记录。

## 参考
* [docker：轻量级图形页面管理工具Portainer](http://www.secflag.com/archives/413.html)