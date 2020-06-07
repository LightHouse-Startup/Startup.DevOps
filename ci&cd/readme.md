## 编译Jenkins镜像
```shell
docker build -f "Jenkins/Dockerfile" --force-rm -t lighthouse/jenkins:1.0 .
```

## 启动Jenkins容器
```shell
docker run --name lighthouse-jenkins \ 
-p 8080:8080 -p 50000:50000 -u root -d \ 
--env JAVA_OPTS="-Xms256m -Xmx512m  -XX:MaxNewSize=256m"  \ 
-v /var/run/docker.sock:/var/run/docker.sock   \ 
-v /usr/bin/docker:/usr/bin/docker  \ 
-v /home/buxiaoxia/software/jenkins:/var/jenkins_home  \
-v /usr/lib64/libltdl.so.7:/usr/lib/x86_64-linux-gnu/libltdl.so.7 \
buxiaoxia/jenkins:1.0
```