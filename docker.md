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
# -P : 是容器内部端口随机映射到主机的端口
# -p : 是容器内部端口绑定到指定的主机端口
# -v : 
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
docker loda
```

