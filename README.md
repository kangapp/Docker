# Docker

## Docker安装

### Docker for Centos

- 安装 [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- 安装 [Vagrant](https://www.vagrantup.com/downloads.html)  
新建目录--> vagrant init centos/7(生成vagrant file) --> vagrant up（下载并打开虚拟机）--> vagrant ssh(进入虚拟环境)  
[Vagrant库](https://app.vagrantup.com/boxes/search)  
- 其他命令:  
     vagrant status  
     vagrant destroy

- 安装[Docker](https://docs.docker.com/v17.12/install/linux/docker-ce/centos/#install-docker-ce-1)  

## Docker 架构和底层技术

> Docker提供了一个开发，打包，运行app的平台

### Docker Engine

- 后台进程（dockerd）
- REST API Server
- CLI接口 （docker）

### Docker Image

sudo gpasswd -a vagrant docker（加入docker组）

> - 文件和meta data的集合
> - 分层的，并且每一层都可以添加改变删除文件，成为一个新的image
> - 不同的image可以共享相同的layer
> - image本身是只读的

#### Image的获取

- Build form Dockerfile

> docker build -t name:tag .

- Pull form Registry

> docker pull [image](https://hub.docker.com/)

### Container

> - 通过Image创建
> - 在Image layer之上建立一个container layer（可读写）
> - Image负责app的存储和分发，Container负责运行app

#### Container命令

- docker commit [image name] [new image]  
把修改过的container创建image
- docker inspect [container id]
获取container详细信息

### Docker File

```bash
#制作base image
FROM scratch
FROM centos
#RUN 会生成新的分层
RUN yum update && yum install -y vim
#WORKDIR 指定当前目录
#ADD 添加本地文件到工作目录并解压
#COPY 添加本地文件到工作目录
#ENV 设置常量
```

> RUN:执行命令并创建新的Image Layer  
> CMD:设置容器启动后默认执行的命令和参数  
> ENTRYPOINT:设置容器启动时运行的命令

### 容器的操作

```bash
docker exec -it [container id] /bin/bash
docker exec -it [container id] python
```

### Docker 持久化

#### 基于本地文件系统的Volume

> 可以在执行Docker create或Docker run时，通过-v参数将主句的目录作为容器的数据卷。  

##### Volume的类型

- 受管理的data Volume，由docker后台自动创建。  
Doclerfile: VOLUME /var/lib/mysql  
docker run -v mysql:/var/lib/mysql
- 绑定挂载的Volume，具体挂载位置可以由用户指定。
docker run -v [本地目录]:[容器目录]

#### 基于plugin和Volume
