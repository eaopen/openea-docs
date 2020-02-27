

## docker环境
如已有docker环境则跳过此部分。

新安装docker环境，推荐操作系统为centos7。

### 使用 yum 安装

Centos7 或 Centos 8 均可。

Docker 要求 CentOS 系统的内核版本高于 3.10 ，查看本页面的前提条件来验证你的CentOS 版本是否支持 Docker 。

通过 uname -r 命令查看你当前的内核版本

[root@runoob ~]# uname -r


### 安装 Docker

默认采用 Docker CE 社区免费版，安装文档参见

https://docs.docker.com/install/linux/docker-ce/centos/

* 删除旧的docker

yum remove docker docker-common docker-selinux docker-engine

* 安装相关依赖

yum install -y yum-utils device-mapper-persistent-data  lvm2

* 查看Docker版本

yum list docker-ce --showduplicates | sort -r

* 安装Docker

yum install docker-ce docker-ce-cli containerd.io

centos8 安装docker报错，需要先安装containerd.io

从网站 https://download.docker.com/linux/centos/7/x86_64/stable/Packages/ 找到最新版本进行安装
```
dnf install https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.6-3.3.el7.x86_64.rpm
```

* 启动Docker,并设置为开机自启

systemctl start docker
systemctl enable docker


## 安装docker-compose

### 安装python

yum install python3
pip3 -V

### 安装docker-compose

pip3 install docker-compose


## 国内优化

### 国内软件源

添加软件源信息
```
## 官方软件源
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
## 国内镜像  
sudo yum-config-manager \ 
    --add-repo \ 
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

### 镜像加速

鉴于国内网络问题，后续拉取 Docker 镜像十分缓慢，需要配置加速器来解决，网易的镜像地址：http://hub-mirror.c.163.com。

新版的 Docker 使用 /etc/docker/daemon.json（Linux） 或者 %programdata%\docker\config\daemon.json（Windows） 来配置 Daemon。

请在该配置文件中加入（没有该文件的话，请先建一个）：
```
{
  "registry-mirrors": ["http://hub-mirror.c.163.com"]
}
```
