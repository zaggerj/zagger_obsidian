---
created: 2023-11-15T20:46
updated: 2023-11-15T20:46
---
# docker

## 基础知识

### YAML 入门教程

- [地址](https://www.runoob.com/w3cnote/yaml-intro.html)

### cat /proc/version

### ls

### exit

### 学习总线

- 即使再小的帆也能远航，只要学不死，就往死里学！
- dock概述

	- 为什么出现？

- 历史：vm比较重，还要模拟硬件

	- docker历史
	- docke的网站

		- 官网：https://www.docker.com/
		- 文档地址：https://docs.docker.com/
		- 仓库地址：https://hub.docker.com/
		- 百度百科：https://baike.baidu.com/item/Docker/13344470?fr=aladdin

- 比较Docker和虚拟机技术的不同：

	- 创通虚拟机，虚拟出一条硬件，运行一个完整的操作系统，然后在这个系统上安装和运行软件
	- 容器内的应用直接运行在宿主机的内容，容器是没有自己的内核的，也没有虚拟我们的硬件的，所以就轻便了
	- 每个容器间是互相隔离的，每个容器内都有一个属于自己的文件系统，互不影响

- DevOps（开发、运维）
- docker的组成，像redis一样，redis client 访问redis server，docker起起来之后，也一样，docker run pull build命令，真正运行在，docker服务上的，有一个docker的守护进程（Docker daemon）运行时，需要通过镜像运行，镜像就好比java类，运行起来时，会返回很多对象（容器）。镜像来自远程仓库。

	- 镜像（image）

		- docker镜像就好比是一个模板，可以通过这个模板来创建容器服务，tomcat镜像 =》run =》tomcat01容器（提供服务器），通过这个镜像可以创建多个容器（最终服务运行或者项目运行就是在容器中的）。

	- 容器（container）

		- docker利用容器技术，独立运行一个或者一组应用，通过镜像来创建的。启动，停止，删除，基本命令！

			- 目前可以把容器理解为一个简易的linux系统，项目就放在其中

	- 仓库（repository）

		- 仓库就是存放镜像的地方
		- 仓库分为公有仓库和私有仓库！
		- Docker Hub（默认是国外的）
		- 阿里云。。。都有容器服务（配置镜像加速！）

- 安装docker

### 介绍

- Docker是什么

	- 出现的原因

	  虚拟机占用资源特别大 启动慢
	  
	  传统的交换模式：只给程序，不给环境
	  
	  1、开发和运维之间的鸿沟
	  2、减少运维的工作量
	  
	  
	  
	- 设计理念

	  解决了什么问题：
	  运行环境和配置的问题，方便持续集成，有助于整体发布
	  
- 能干什么

	- 企业级

		- 美团
		- 京东

	- 开发和运维

	  对开发和运维比较简单
	  
- 获取

	- www.docker.com

	  英文官网
	  
	  文档地址：
	  https://docs.docker.com/get-started/
	  
	- www.docker-cn.com

	  中文网站，解决英文网站访问慢的问题
	  
- 仓库

	- hub.docker.com

	  docker 仓库地址
	  国内访问速度比较慢，可以使用Ali云加速
	  
	  加速方式
	  1、请求时制定镜像地址
	  docker pull registry.docker-cn.com/library/ubuntu:16.04
	  
	  2、启动docker守护进程时，添加--registry-mirror参数
	  
	  3、修改配置文件/etc/docker/daemon.json
	  {
	    "registry-mirrors": ["https://registry.docker-cn.com"]
	  }
	  
- docker介绍

	- Docker 是服务器----客户端架构。命令行运行docker命令的时候，需要本机有 Docker 服务。如果这项服务没有启动，可以用下面的命令启动（官方文档）。
# service 命令的用法
$ sudo service docker start
# systemctl 命令的用法
$ sudo systemctl start docker
	- Docker 把应用程序及其依赖，打包在 image 文件里面。只有通过这个文件，才能生成 Docker 容器
	- docker run -i -t ubuntu /bin/bash

		- 可以看出容器中包含了基本的进程，网络设备，文件系统，跟传统中的虚拟机有着非常相似的现象

	- 容器
	- Linux容器技术vs虚拟机
	- 什么是docker
	- docker目标

		- 提供简单轻量级的建模方式
		- 职责的逻辑分离
		- 快速高效的开发生命周期
		- 鼓励使用面向服务的架构

	- docker的使用场景

		- 1.使用docker容器开发、测试、部署服务
		- 2.创建隔离的运行环境
		- 3.搭建测试环境
		- 4.构建多用户的平台即服务（PaaS）基础设施
		- 5.提供软件即服务（SaaS）应用程序
		- 6.高性能、超大规模的宿主机部署

	- docker的基本组成

		- 1.Docker Client 客户端

			- C/S架构
			- 本地/远程
			- 客户端和守护进程

		- 2.Docker Daemon守护进程
		- 3.Docker Image镜像

			- 容器的基石

				- 只读层

			- 层叠的只读文件系统
			- 最底端是一个引导文件系统 bootfs
			- 联合加载（union mount）

		- 4.Docker Container容器

			- 通过镜像启动

				- 镜像是打包和启动阶段

			- 启动和执行阶段

				- 容器的阶段

					- 读写层

			- 写时复制（copy on write）

		- 5.Docker Registry仓库
		- 图示

### 【特点】

- 启动速度快
- 更轻量

### 【docker内部组件】

- Namespace  

	-  命名空间，提供一种对进程隔离的一种机制，例如进程，网络、挂载等资源

- ControlGroups  

	- 资源控制组的作用就是控制计算机资源的，与namespace不同CGroups 主要做的是硬件资源的隔离。

- Union File System  

	- 联合文件系统，支持将不同位置的目录挂载到同一个虚拟文件系统，形成一种分层的模型

### 【docker的核心组成】

- 镜像

	- 是什么

		- UnionFS(联合文件系统)
		- 镜像加载原理
		- 分层镜像
		- 为什么采用这种设计

	- docker commit 镜像提交

		- docker commit -m="" -a="作者" 容器id 目标镜像名称:[标签名]

		  docker commit --help
		  
		  docker commit -m="create image from current container" -a="panshen" 3a90f19f1669 "tomcat2:2.0"
		  
		  用已经存在的容器做一个新的镜像
	- 镜像是一个特殊的文件系统，可以理解为一个只读包，甚至可以理解为类与实例中的类。每个镜像可能有多个镜像组成。它是一种层级结构，每次对镜像的修改，docker都会铸造成一个镜像层。

- 容器

	- 容器可以理解为类与实例中的实例，镜像是死的是不可变的。而容器却是一个活的空间。每次启动容器都是通过镜像启动一个新的容器。

- 仓库

	- 远端中的镜像仓库，例如npm仓库

### 【docker安装】

- 参考官方文档

  安装社区版本就行
  
  centos 安装地址
  https://docs.docker.com/install/linux/docker-ce/centos/#os-requirements
  
- 配置仓库地址
- 两个系列：

	- 社区版（ce）
	- 企业版（ee）

		- 收费，提供额外服务

- centos安装

	- sudo yum install yum-utils device-mapper-persistent-data lvm2 
sudo yum-config-manager --add-repo    https://download.docker.com/linux/centos/docker-ce.repo 
sudo yum install docker-ce

### 【docker的运行过程】

- docker的运行过程可以简单的理解为，从远端仓库中拉取合适的镜像到本地-->通过镜像创建容器-->启动容器
- 【图示】

### 架构

https://www.cnblogs.com/CloudMan6/p/6763789.html

client

docker服务器 （docker 守护进程）

docker镜像

docker容器 镜像运行的实例

仓库 存放镜像的仓库，包含共有和私有

运行过程
当client 执行命令docker run nginx时，client发送socket消息给docker守护进程，

docker守护进程先在本地看下有没有这个镜像存在，如果不存在就去远程仓库下载，然后保存到本地；

然后通过 container run命令把这个镜像做成一个容器然后运行起来


### 组成

- 镜像
- 容器
- 仓库

### 数据卷

- 是什么
- 能干什么
- 数据卷
- 数据容器卷

	- 是什么
	- 能干什么

		- 日志系统存储（典型场景）

	- 使用

		- docker run -it --name n1 --volumes-from n0 centos

- 【背景】

	- 因为容器内部的文件系统是随着容器内部的生命周期所创建和移出的，并且容器隔离，我们很难从外部获得或者操作容器内部文件中的数据。

- 【3种挂载方式】

	- Bind Mount

		- bind mount相对于volumn唯一的区别就是将容器内的目录映射到宿主机中的任意一个位置。
		- docker run -d -v /mnt:/mnt -name logs centos 
		- 唯一区别的就是，volume对应的是文件名(nginx-html)，而bindMount则是一个相对路径(/mnt)

	- Volume

		- volumes是docker管理宿主机文件系统的一部分，在/var/lib/docker/volumes目录下，当你创建一个数据卷时，会默认放在volumes目录
		- 创建命令

			- docker volume create nginx-html

				- 

			- docker volume ls查看

		- 通过docker vlolume inspect nginx-html来查看具体信息

			- 

		- 我们来创建一个新的nginx容器来和数据卷进行挂载

			- docker run -d --name nginx -v nginx-html:/usr/share/nginx/html nginx


		- 挂载成功后我们进入宿主机中

			- cd /var/lib/docker/volumes/nginx-html/_data

		- 你会发现宿主机中的nginx-html目录中多了两个文件

			- 

		- 同时我们进入到容器内部

			- docker exec -it 7454e37763d0 bash
			- cd /usr/share/nginx/html

		- 

	- Tmpfs mount

		- Tmpfs Mount是临时挂载到系统内存中，存储不是永久的，会随着容器的停止而消失。适用于不需要持久保存的数据。挂载时需要用--tmpfs来指定。
		- docker run -d --name webapp --tmpfs /webapp/cache webapp:latest

### 网络

- 【背景】

	- 一个完整的项目可能存在很多容器：nodejs，mysql，redis，webapp等
	- 他们之间彼此之间可能存在通信问题
	- 比如node容器如何连接mysql，为此docker提供了网络驱动

- 可以通过 docker network ls 来查看网络驱动
- 如果想看网络驱动的具体信息和对应的容器，使用 docker network inspect [网络驱动]

	- docker network inspect bridge

- 单机

	- Bridge Network

		- 会在主机上创建一个虚拟网桥，此主机上启动的Docker容器会连接到这个虚拟网桥上。
		- 如图所示，bridge的ip地址都是以172.17开头显示的。不指定网络默认为bridge模式。

			- 

	- Host Network

		- 通过--net host来使用host模式，host模式是宿主机公用一个network，使用宿主机的IP和端口。
		- 创建一个新的nginx3的容器，通过--net host来指定网络驱动
		- docker run -d --name nginx3 --network host nginx
		- 启动完毕，进入到host详情，会发现多出了一个容器，并且没有ip地址，如图下

			- 

	- None Network

		- 不为Docker容器进行任何网络配置。通过 --net none

- 多机

	- Overlay Network

- 创建自定义网络

	- docker network create -d bridge mynetwork
	- 执行查看  d ocker network ls

		- 

- 容器之间的link

	- 通常由于容器之前隔离，两个容器之间的网络是无法进行通信的，通常我们需要通过link来建立容器之间的连接。
	- docker run -d --name nodeapp --link mysql node
	- 或者说两个容器同时加入自定义的网络中也是可行的
	- docker run -d --name mysql --network mynetwork mysql
	- docker run -d --name nodeapp --network mynetwork node 

## 命令

### 帮助命令

- docker version
- docker info
- docker --help

### docker search 镜像名

starts 类似github上的stars

official 是否官方
- 查看远端库的镜像，跟npm search类似

	- 出现的列表表头是

### docker pull

- 拉取镜像
- docker pull centos

	- 不指定tag时，默认拉取最新的tag

### docker images

- 查看镜像
- 参数

	- -a 列出所有镜像
	- -q 只显示镜像ID
	- --digests：显示摘要信息
	- --no-trunc：不截断输出，显示完整的镜像ID

### docker create 

- 创建容器
- 如果说镜像是个类，那么我们需要创建一个实例来让我们操作。

	- docker create centos
	- 如果当你本地没有centos的镜像时候，会默认从远端仓库中的拉取对应的版本。我们还可以通过--name来指定容器的别名。

### docker ps 

- 查看容器
- 通过docker ps可以查看当前所有正在运行的容器，但是由于上方容器没有运行，在执行操作时，需要在后面加一个-a参数。代表所有容器。

	- docker ps -a

### docker start  stop  reset（启动/停止/重启容器）

- docker stop
- 通过 docker create创建的容器，是处于 Created 状态的，其内部的应用程序还没有启动，所以我们需要通过docker start命令来启动它。

	- docker start 8c784b9b2118
	- 通过docker start + 容器id 来启动容器，如果给容器配置了别名，也可以通过别名来启动容器。启动容器后通过docker ps。
	- 执行 docker ps 发现空空如也
	- 执行 docker ps -a，发现容器处于Exited状态
	- 这是因为如果容器内部没有进程正在运行，那么容器在 start 之后会停止。如果存在进程的容器，例如nginx，mysql，你在启动后就会变成up状态。

### docker run

- -v 宿主机目录:容器目录

	- -v, --volume=[]， 给容器挂载存储卷，挂载到容器的某个目录

- --rm 停止后清空

	- --rm=false， 指定容器停止后自动删除容器(不支持以docker run -d启动的容器)

- -d detached运行容器
- -p端口号，映射
- -e，docker run -e传递环境变量
- 【常用选项说明】

	- -d, --detach=false， 指定容器运行于前台还是后台，默认为false

		- 后台运行容器，并返回容器ID

	- -i, --interactive=false， 打开STDIN，用于控制台交互

		- 以交互模式运行容器，通常与 -t 同时使用；

	- -t, --tty=false， 分配tty设备，该可以支持终端登录，默认为false

		- 为容器重新分配一个伪输入终端，通常与 -i 同时使用

	- -u, --user=""， 指定容器的用户
	- -a, --attach=[]， 登录容器（必须是以docker run -d启动的容器）
	- -w, --workdir=""， 指定容器的工作目录
	- -c, --cpu-shares=0， 设置容器CPU权重，在CPU共享场景使用
	- -e, --env=[]， 指定环境变量，容器中可以使用该环境变量
	- -m, --memory=""， 指定容器的内存上限
	- -P, --publish-all=false， 指定容器暴露的端口
	- -p, --publish=[]， 指定容器暴露的端口

		- 端口映射，格式为： 主机(宿主)端口:容器端口

	- -h, --hostname=""， 指定容器的主机名
	- -v, --volume=[]， 给容器挂载存储卷，挂载到容器的某个目录

		- 绑定数据卷

	- --volumes-from=[]， 给容器挂载其他容器上的卷，挂载到容器的某个目录
	- --cap-add=[]， 添加权限，权限清单详见：http://linux.die.net/man/7/capabilities
	- --cap-drop=[]， 删除权限，权限清单详见：http://linux.die.net/man/7/capabilities
	- --cidfile=""， 运行容器后，在指定文件中写入容器PID值，一种典型的监控系统用法
	- --cpuset=""， 设置容器可以使用哪些CPU，此参数可以用来容器独占CPU
	- --device=[]， 添加主机设备给容器，相当于设备直通
	- --dns=[]， 指定容器的dns服务器
	- --dns-search=[]， 指定容器的dns搜索域名，写入到容器的/etc/resolv.conf文件
	- --entrypoint=""， 覆盖image的入口点
	- --env-file=[]， 指定环境变量文件，文件格式为每行一个环境变量
	- --expose=[]， 指定容器暴露的端口，即修改镜像的暴露端口
	- --link=[]， 指定容器间的关联，使用其他容器的IP、env等信息
	- --lxc-conf=[]， 指定容器的配置文件，只有在指定--exec-driver=lxc时使用
	- --name=""， 指定容器名字，后续可以通过名字进行容器管理，links特性需要使用名字
	- --net="bridge"， 容器网络设置:

		- 指定容器的网络连接类型
		- bridge 使用docker daemon指定的网桥
		- host //容器使用主机的网络
		- container:NAME_or_ID >//使用其他容器的网路，共享IP和PORT等网络资源
		- none 容器使用自己的网络（类似--net=bridge），但是不进行配置

	- --privileged=false， 指定容器是否为特权容器，特权容器拥有所有的capabilities
	- --restart="no"， 指定容器停止后的重启策略:
	- no：容器退出时不重启
	- on-failure：容器故障退出（返回值非零）时重启
	- always：容器退出时总是重启
	- --rm=false， 指定容器停止后自动删除容器(不支持以docker run -d启动的容器)
	- --sig-proxy=true， 设置由代理接受并处理信号，但是SIGCHLD、SIGSTOP和SIGKILL不能被代理

- [【示例】](https://www.cnblogs.com/ycg-blog/p/12666119.html)

	- 运行一个在后台执行的容器，同时，还能用控制台管理：docker run -i -t -d ubuntu:latest
	- 运行一个带命令在后台不断执行的容器，不直接展示容器内部信息：docker run -d ubuntu:latest ping www.docker.com
	- 运行一个在后台不断执行的容器，同时带有命令，程序被终止后还能重启继续跑，还能用控制台管理，docker run -d --restart=always ubuntu:latest ping www.docker.com
	- 为容器指定一个名字，docker run -d --name=ubuntu_server ubuntu:latest
	- 容器暴露80端口，并指定宿主机80端口与其通信(: 之前是宿主机端口，之后是容器需暴露的端口)，docker run -d --name=ubuntu_server -p 80:80 ubuntu:latest
	- 指定容器内目录与宿主机目录共享(: 之前是宿主机文件夹，之后是容器需共享的文件夹)，docker run -d --name=ubuntu_server -v /etc/www:/var/www ubuntu:latest
	- docker run -d --rm --name webres -p 27017:27017 -v $PWD/db/.data/configdb:/data/configdb -v $PWD/db/.data/db:/data/db -e MONGO_INITDB_ROOT_USERNAME=webres -e MONGO_INITDB_ROOT_PASSWORD=123456 mongo:4

- 【示例】

	- docker run ubuntu:15.10 /bin/echo "hello world"
	- docker run -i -t ubuntu:15.10 /bin/bash
	- docker run -d ubuntu:15.10 /bin/sh -c "while true; do echo hello world; sleep 1; done"

		- 使用-p 将您的机器的端口4000映射到集装箱发布的端口80

			- docker run -p 4000:80 friendlyhello

		- -d

			- detached

				- docker run -d -p 4000:80 friendlyhello

	- docker run -p 80:80 -v nginx-html:/usr/share/nginx/html -d --name nginx nginx:latest

		- 使用镜像 nginx:latest，以后台模式启动一个容器,将容器的 80 端口映射到主机的 80 端口,将容器的/usr/share/nginx/html目录映射到主机目录下的docker中的nginx-html数据卷中。并取名为nginx。 可以看到容器的状态变成了up。
		- 每个docker容器和我们宿主机之间存在隔离关系，假设有一个nginx服务，内部容器监听的端口号是80，这时候如何将外面访问宿主机80端口号的时候，能够访问到nginx服务呢
		- 所以我们需要作出映射通过-p将宿主机上的80端口和nginx端口进行映射。
		- -v将宿主机中的目录挂载到容器的目录中，便于以后数据的备份和防止容器删除后数据的丢失。

### docker exec   (在运行的容器中执行命令)

- 很多时候，我们需要的操作并不仅仅是按照镜像所给出的命令启动容器而已，我们还会希望进一步了解容器或者操作容器，这时候最佳的方式就是让我们进入到容器内部
- docker exec -it ngnix bash
- 你会发现命令行前缀变成了一串容器的hash，说明你已经成功进入了容器内部。这里我是以bash方式进入了，当然你也可以以其他的交互方式进入。-it命令和上方的docker run中的参数一样，在run中代表着创建一个新的容器并启动进入容器内部

### docker rmi 删除镜像

- 删除容器或者镜像

	- docker rmi 镜像id
	- docker rmi 容器id
	- 需要注意的是，如果容器正在运行中，需要先将容器停止后方能删除。

- 删除单个 docker rmi&nbsp;镜像id/镜像名称
- 删除多个镜像 docker rmi id1 id2
- 删除全部镜像 docker rmi ${docker images -qa}

  docker rmi `docker images -qa`
  
  $() ($+小括号)子shell命令
### docker inspect (获取容器/镜像的元数据)

- docker inspect [容器id/镜像id]
- 通过上述命令可以获取容器或者镜像的相关信息
- 包含端口号映射情况，数据卷挂载情况，网络情况等，反正只要想看容器或者镜像的具体信息时候，敲这个命令准没错

### docker save load （导出镜像/导入镜像）

- 将容器导出成一个tar文件-o指定为指定文件中

	- docker save -o nginx.tar [镜像id]

- 导入镜像

	- docker load -i nginx.tar

### docker export import (导出容器/导入容器)

- 将容器导出成一个tar文件

	- docker export -o nginx.tar [容器id]

- 导入容器

	- 这里需要注意的是，使用docker import并非直接将容器导入，而是将容器运行时的内容以镜像的形式导入。所以导入的结果其实是一个镜像，而不是容器。

		- docker import nginx.tar

### docker cp

- 用于容器与主机之间的数据拷贝
- 【语法】

	- docker cp [OPTIONS] container:src_path dest_path
docker cp [OPTIONS] dest_path container:src_path 


- 【例子】

	- docker cp b80f4b3ad86a:/root/Neptune/docs ~/
	- 将b80f4b3ad86adocker中的docs文件夹复制到宿主机的home目录下
	- 在主机目录下创建一个abc.txt文件

		- touch abc.txt
		- 将目录下的abc.txt文件移到容器中的/data目录下
		- docker cp ./abc.txt a175b4a2fd94:/data
		- 进入容器内部

			- docker exec -it a175b4a2fd94 bash

		- 会发现/data目录下存在了abc.txt文件，反之，容器内容的文件或者目录也可以复制到主机内，只要将两者调换顺序即可。

			- docker cp  a175b4a2fd94:/data /data/

### docker logs

- 获取容器的日志

### 其他不常用的命令

- 

### docker 运行命令

- 新建并运行

	- docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

		- OPTIONS --name为容器指定新名称
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; -d 后台运行
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; -i交换方式运行
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; -t伪终端
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; -p端口映射
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; -P随机端口映射


		  docker ps status列中包含up，标识服务已经起来了
		  
		  
		  
- 列出所有运行的容器

	- docker ps [options]

		- -a :所有正在运行和运行过的
-l: 显示最近创建的容器
-n:显示最近创建的n个容器
-q:只显示容器id

- 退出容器

	- exit / ctrl + d：退出并停止容器

	  待验证
	- ctrl+p+q:退出不停止容器

- 启动容器

	- docker start 容器id/名称

	  启动已经退出的容器
	  
- 重启容器

	- docker restart 容器id/名称

- 停止容器

	- docker stop&nbsp;容器id/名称

- 强制停止所有容器

	- docker kill 容器id/名称

- 删除容器

	- docker rm 容器id/名称

- 删除所有容器

	- docker rm -f $(docker ps -aq)
docker ps -a -q | xargs docker rm

- 以后台方式运行容器

	- docker run -d 容器

	  不占用当前终端
	  
	  比如tomcat容器，有后台方式运行就不占用当前控制台
	  
	  
- 进入正在运行的容器，并以前台方式运行

	- docker exec -it 容器id/名称 bashshell 产生新的进程

	  -t 伪终端
	  docker exec -it c600f5bdd5b0 /bin/bash
	  
	  docker exec -it c600f5bdd5b0 bash
	  
	- docker attach 容器id/名称 进入容器不产生新的进程
	- -it：exec -i:  --interactive(相互作用的)       Keep STDIN open even if not attached(即使没有连接，也要保持STDIN打开)
       exec -t:   --tty                          Allocate a pseudo-TTY(分配一个 冒充的终端设备)

- 容器 <->拷贝文件<->主机

	- docker copy 容器id/名称:容器中路径 主机路径
docker copy&nbsp;主机路径 容器id/名称:容器中路径&nbsp;

	  docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-
	  
	  docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH
	  
## Dockerfile介绍

### 是什么

构建Docker镜像的构建文件
### 执行流程

### 关键字

- FROM

	- 基础镜像，当前镜像是基于那个镜像

- MAINTAINER

	- 镜像维护者的姓名和邮箱地址

- RUN

	- 镜像构建时需要运行的命令

- WORKDIR

	- 容器创建后，默认在那个目录

- EXPOSE

	- 当前容器对外暴露的接口

- ENV

	- 用来构建镜像时设置环境变量

- ADD

	- 将宿主机目录下的文件copy到镜像且ADD命令会自动解压压缩包

	  ADD 不能加压zip包
- COPY

	- 拷贝数据

- VOLUME

	- 容器数据卷，用来保存和持久化

- CMD

	- 指定容器启动时需要运行的命令
	- 多条CMD命令，只有最后一条生效
	- CMD命令会被docker run之后的参数替换

- ENTRYPOINT

	- 指定容器启动过程中需要运行的命令
	- 把docker run命令的参数追加到后面

- ONBUILD

## docker compose

### 【背景】

- 往往一个完整的项目可能很多容器组成，为每个容器挂载网络，指定数据卷会变非常的麻烦，幸好，docker-compose为我们解决了这儿问题

### 【Compose 简介】

- 是用于定义和运行多容器 Docker 应用程序的工具。

### 【Compose 安装】

- Linux

	-  sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
	- sudo chmod +x /usr/local/bin/docker-compose
	- sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
	- docker-compose --version

### 【示例】

- nginx容器配置文件

	- 

- 关键字含义

	- 

- 通过docker-compose up -d 启动容器 如果有重名的容器记得先删除

	- 

### 【常见命令】

- docker-compose ps

	- 列出所有运行容器

		- 

- logs：查看服务日志输出

	- docker-compose logs

- port：打印绑定的公共端口，下面命令可以输出 eureka 服务 8761 端口所绑定的公共端口

	- docker-compose port eureka 8761

- build：构建或者重新构建服务

	- docker-compose build

- start：启动指定服务已存在的容器

	- docker-compose start eureka

- stop：停止已运行的服务的容器

	- docker-compose stop eureka

- rm：删除指定服务的容器

	- docker-compose rm eureka

- up：构建、启动容器

	- docker-compose up

- kill：通过发送 SIGKILL 信号来停止指定服务的容器

	- docker-compose kill eureka

- pull：下载服务镜像
- scale：设置指定服务运气容器的个数，以 service=num 形式指定

	- docker-compose scale user=3 movie=3

- run：在一个服务上执行一个命令

	- docker-compose run web bash

### 【docker-compose.yml 属性】

- version：指定 docker-compose.yml 文件的写法格式
- services：多个容器集合
- build：配置构建时，Compose 会利用它自动构建镜像，该值可以是一个路径，也可以是一个对象，用于指定 Dockerfile 参数

	- build: ./dir
---------------
build:
    context: ./dir
    dockerfile: Dockerfile
    args:
        buildno: 1

- command：覆盖容器启动后默认执行的命令

	- command: bundle exec thin -p 3000
----------------------------------
command: [bundle,exec,thin,-p,3000]

- dns：配置 dns 服务器，可以是一个值或列表

	- dns: 8.8.8.8
------------
dns:
    - 8.8.8.8
    - 9.9.9.9

- dns_search：配置 DNS 搜索域，可以是一个值或列表

	- dns_search: example.com
------------------------
dns_search:
    - dc1.example.com
    - dc2.example.com

- environment：环境变量配置，可以用数组或字典两种方式

	- environment:
    RACK_ENV: development
    SHOW: 'ture'
-------------------------
environment:
    - RACK_ENV=development
    - SHOW=ture

- env_file：从文件中获取环境变量，可以指定一个文件路径或路径列表，其优先级低于 environment 指定的环境变量

	- env_file: .env
---------------
env_file:
    - ./common.env

- expose：暴露端口，只将端口暴露给连接的服务，而不暴露给主机

	- expose:
    - "3000"
    - "8000"

- image：指定服务所使用的镜像

	- image: java

- network_mode：设置网络模式

	- network_mode: "bridge"
network_mode: "host"
network_mode: "none"
network_mode: "service:[service name]"
network_mode: "container:[container name/id]"

- ports：对外暴露的端口定义，和 expose 对应

	- ports:   # 暴露端口信息  - "宿主机端口:容器暴露端口"
- "8763:8763"
- "8763:8763"

- links：将指定容器连接到当前连接，可以设置别名，避免ip方式导致的容器重启动态改变的无法连接情况

	- links:    # 指定服务名称:别名 
    - docker-compose-eureka-server:compose-eureka

- volumes：卷挂载路径

	- volumes:
  - /lib
  - /var

- logs：日志输出信息

	- --no-color          单色输出，不显示其他颜.
-f, --follow        跟踪日志输出，就是可以实时查看日志
-t, --timestamps    显示时间戳
--tail              从日志的结尾显示，--tail=200

### 【Docker  Compose 其他】

- 更新容器

	- 当服务的配置发生更改时，可使用 docker-compose up 命令更新配置
	- 此时，Compose 会删除旧容器并创建新容器，新容器会以不同的 IP 地址加入网络，名称保持不变，任何指向旧容起的连接都会被关闭，重新找到新容器并连接上去

- links

	- 服务之间可以使用服务名称相互访问，links 允许定义一个别名，从而使用该别名访问其它服务
	- version: '2'
services:
    web:
        build: .
        links:
            - "db:database"
    db:
        image: postgres
	- 这样 Web 服务就可以使用 db 或 database 作为 hostname 访问 db 服务了

## docker文章集合

### [使用Docker构建统一的前端开发环境](https://blog.csdn.net/M2l0ZgSsVc7r69eFdTj/article/details/80650053)

## ubuntu arm64版本 fd安装

### apt-get install cargo

git clone https://github.com/sharkdp/fd

# Build
cd fd
cargo build

# Run unit tests and integration tests
cargo test

# Install
cargo install --path .

vim ~/.zshrc 

# add env
PATH=/root/.cargo/bin:$PATH




