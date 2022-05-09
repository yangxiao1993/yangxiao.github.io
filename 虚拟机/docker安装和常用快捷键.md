# CentOS8 安装docker

1. 安装docker依赖
```
yum install -y https://mirrors.aliyun.com/docker-ce/linux/centos/7/x86_64/edge/Packages/containerd.io-1.2.13-3.2.el7.x86_64.rpm
```
2. 安装docker
```
sudo yum -y install docker-ce docker-ce-cli
```
3. 启动docker
```
systemctl start docker
```
4. 打包
> 首先需要新建一个Dockerfile文件
```
FROM jfactory/java9-slave  -- 打包所需的依赖
MAINTAINER yang     -- 作者
ADD lq_web.jar lq_web.jar  -- 对应的jar包
CMD ["nohup","java","-jar","lq_web.jar","&"]  --  执行的命令
```
> 打包镜像
```
docker build -t my/demo .
```
5. 启动容器
```
docker run -d --name demo -p 8080:8080 my/demo
```
6. 查看日志
```
docker logs -f --tail=500 demo
```

## docker常用命令
```
docker version   -- docker版本

docker ps  -- 查看运行中的容器

docker ps | grep xiaotong -- 根据名称查询运行中的容器

docker ps -a -- 查看所有容器

docker rm [容器id] -- 删除容器

docker image ls -- 查看镜像列表

docker images | grep xiaotong -- 根据名称查询镜像列表

docker image rm [镜像id] -- 删除镜像

docker start [容器id]  启动容器 

docker restart [容器id]  重启容器 

docker stop [容器id]  停止容器 

```