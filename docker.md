## 容器

## 隔离与限制
Docker 容器通过 Linux 内核的 Namespace 技术实现了文件系统、进程、设备以及网络的隔离，然后再通过 Cgroups 对 CPU、 内存等资源进行限制，最终实现了容器的沙箱机制。但其本质上仍然是运行在宿主机上的一个进程，它们共用宿主机的内核，所以如果你想在windows上运行linuxrong
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

