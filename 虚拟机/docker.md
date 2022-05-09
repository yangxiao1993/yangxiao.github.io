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
4. 打包服务镜像
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
