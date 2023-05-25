## Docker是什么
Docker 是一个开源的应用容器引擎，其中包括镜像、容器、仓库等功能，目的就是通过对应用组件的封装、分发、部署、运行等生命周期的管理，使用户的产品（可以是 web 应用或者数据库应用）及其环境能够做到“一次封装，到处运行”。再通俗点说，我们使用Docker，只需要配置一次Docker容器上面的应用，就可以跨平台，跨服务器，实现应用程序跨平台间的无缝衔接，Docker实际上就相当于一个封闭的沙盒或者是集装箱，它可以把不同的应用全都放在它的集装箱里面，并且以后有需要的时候，可以直接把集装箱搬到其他平台或者服务器上，同时相比于容器的封装隔离，容器编排也更有价值。
## 隔离与限制
容器里运行的进程实际上运行在宿主机的操作系统上，但Docker通过Linux命名空间和cgroups机制实现了
Docker 容器通过 Linux 内核的 Namespace 技术实现了文件系统、进程、设备以及网络的隔离，然后再通过 Cgroups 对 CPU、 内存等资源进行限制，最终实现了容器的沙箱机制。但其本质上仍然是运行在宿主机上的一个进程，它们共用宿主机的内核，如果你要在 Windows 宿主机上运行 Linux 容器，或者在低版本的 Linux 宿主机上运行高版本的 Linux 容器，都是行不通的。
## 镜像分层
> Docker镜像基于联合文件系统（Union FS）技术，实现镜像分层和写时拷贝。

Docker镜像由多层构成。不同镜像可以包含完全相同的层，位于这些镜像都是基于另一个镜像之上构建的，不同的镜像都能使用相同的父镜像作为他们的基础镜像，这提升了镜像在网络上的分发效率，同时也减少了镜像的存储空间。当基于相同基础层的镜像被构建成两个容器时，它们就能够读相同的文件。但是如果其中一个容器写入某些文件，另外一个是无法看见文件变更的。因此即使它们共享文件，仍然彼此隔离。这是因为容器镜像层是只读的。容器运行时，一个新的可写层在镜像层之上被创建。容器修改位于底层的一个文件时，此文件的一个拷贝在顶层被创建，进程写的是此拷贝。
## 基础命令
### 镜像仓库
登录
```
docker login -u username -p password server 
```
登出
```
docker logout 
```
查看镜像列表
```
docker images
```
删除镜像
```
docker rmi <image_id>
```
拉取镜像
```
docker pull <repository>/<image_name>:tag
```
推送镜像
```
docker push <repository>/<image_name>:tag
```
更新镜像
```
docker commit -m 'commit desc' -a 'author' <container_id> <repository>/<image_name>:tag
```
构建镜像
```
docker build -t <repository>/<image_name>:tag .
```
设置镜像标签
```
docker tag imageId <repository>/<image_name>:tag
```
### 容器
查看容器列表
``` 
docker ps
# -a 查看所有容器
# -s 查看容器大小
# -q 仅查看容器Id
# -l 查看最后一个容器
```
删除容器
```
docker rm <container_id>
```
查看容器详细信息
```
docker inspect <container_id>
```
查看容器日志
```
docker logs <container_id>
# 容器日志在主机中的路径
# /var/lib/docker/containers/<container_id>/<container_id>-json.log
```
运行容器
```
docker run -d --name containerName <repository>/<image_name>:tag
# -P : 容器内部端口随机映射到主机的端口
# -p : 容器内部端口绑定到指定的主机端口
# -v : 将容器内部数据卷映射到主机数据卷
```
重启容器
```
docker restart <container_id>
```
关闭容器
```
docker stop <container_id>
```
进入容器
```
docker exec -it <container_id> /bin/bash
```
导出容器
```
docker export <container_id> res.tar
```
导入容器
```
cat docker/res.tar | docker import - test/ubuntu:v1
```

