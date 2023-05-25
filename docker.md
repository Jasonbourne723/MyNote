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
docker rmi imageId
```
拉取镜像
```
docker pull repository/imagename:tag
```
推送镜像
```
docker push repository/imagename:tag
```
更新镜像
```
docker commit -m 'commit desc' -a 'author' containerId repository/imagename:tag
```
构建镜像
```
docker build -t repository/imagename:tag .
```
设置镜像标签
```
docker tag imageId repository/image:tag
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
docker rm containerId
```
查看容器详细信息
```
docker inspect containerId
```
查看容器日志
```
docker logs containerId
```
运行容器
```
docker run -d --name containerName repository/imageName:tag
# -P : 是容器内部端口随机映射到主机的端口
# -p : 是容器内部端口绑定到指定的主机端口
```
