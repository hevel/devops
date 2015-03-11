Docker
=======

安装(默认配置)
----

> **NOTE:**
>
> 内核版本要求:
>
> - **Docker**依赖于lxc，所以内核版本需要在**2.6.32-431**以上.
>
> 需要开启iptable:
>
> - service iptables start
>
> 需要开启数据包转发:
>
> - echo "1" > /proc/sys/net/ipv4/ip_forward
> - sed -i '/net.ipv4.ip_forward/ s/\(.*= \).*/\11/' /etc/sysctl.conf

###安装软件以下3个软件包：

* docker-io-1.0.0-3.el6.x86_64.rpm
* lxc-libs-0.9.0-2.el6.x86_64.rpm
* lxc-0.9.0-2.el6.x86_64.rpm

```sh
#rpm -ivh docker-io-1.0.0-3.el6.x86_64.rpm lxc-libs-0.9.0-2.el6.x86_64.rpm lxc-0.9.0-2.el6.x86_64.rpm
```
Docker 命令行
-------------

> - **docker attach**  : 连接到正在运行容器中
> - **docker build**   : 创建一个新的images
> - **docker commit**  : 保存对容器所做的修改，并保存为新的一个images
> - **docker cp**      : 从容器复制文件到主机
> - **docker diff**    : 列出对images做的修改
> - **docker events**  : 容器事件
> - **docker export**  : 将image打包成tar包
> - **docker history** : 容器内命令历史列表
> - **docker images**  : 列出所有images
> - **docker import**  : 将打包好的images导入主机
> - **docker info**    : 查看主机信息
> - **docker inspect** : 查看容器低层信息，如IP,hostname
> - **docker kill**    : 强制中止容器
> - **docker load**    : 从tar包中导入images到主机
> - **docker login**   : 登录到docker.io
> - **docker logs**    : 查看容器日志信息
> - **docker port**    : 查看容器端口映射
> - **docker ps**      : 查看容器运行情况
> - **docker pull**    : 从docker.io下载images
> - **docker push**    : 上传images到docker.io
> - **docker restart** : 重启正在运行的容器
> - **docker rm**      : 删除已停止的容器
> - **docker rmi**     : 删除本机的images
> - **docker run**     : 创建并运行一个新的容器
> - **docker save**    : 将images所有信息保存到tar包
> - **docker search**  : 在docker.io上搜索images
> - **docker start**   : 启动一个已停止容器
> - **docker stop**    : 停止一个正运行的容器
> - **docker tag**     : 新增或修改images的标签信息
> - **docker top**     : 查看容器内程序运行情况
> - **docker version** : 查看docker版本
> - **docker wait**    : 查看退出容器的退出代码

* [command line] - 更详细请查看docker Command line

常用命令
--------

查看主机images列表

```#docker images```
```
REPOSITORY | TAG     | IMAGE ID     | CREATED     | VIRTUAL SIZE
centos     | centos6 | 0c752394b855 | 3 weeks ago | 124.1 MB
centos     | latest  | 0c752394b855 | 3 weeks ago | 124.1 MB
```


运行一个docker容器

```#docker run -d centos:latest```

运行一个docker容器，并运行/bin/bash

```#docker run -d centos:latest /bin/bash```

运行一个docker容器,映射主机的8080到容器的80端口，并运行apache

```#docker run -d -p 8080:80 centos:latest /usb/sbin/httpd -X```

运行一个docker容器,并自动映射端口（默认从49153开始分配），并运行apache

```#docker run -d -P centos:latest /usb/sbin/httpd -X```

运行一个docker容器，并attach到容器

```#docker run -t -i centos:latest /bin/bash```

运行一个docker容器，限制cpu时间片为1s

```#docker run -d -c 1000 centos:latest```

运行一个docker容器，限制只使用id为0的物理cpu

```#docker run -d --cpuset="0" centos:latest```

运行一个docker容器，限制内存使用为500m(单位为b, k, m or g)

```#docker run -d -m 500m centos:latest```

查看所有当前容器情况

```#docker ps -a```
```
CONTAINER ID | IMAGE              | COMMAND             | CREATED      | STATUS      | PORTS                 | NAMES
26d6952cd066 | salt/master:latest | /opt/init app:start | 44 hours ago | Up 44 hours | 0.0.0.0:49155->22/tcp | salt
```

小细节
------

###export 与save之间的不同

> docker export命令用于持久化容器（不是镜像）
> docker Save命令用于持久化镜像（不是容器）

我们发现导出后的版本会比原来的版本稍微小一些。那是因为导出后，会丢失历史和元数据。执行下面的命令就知道了：

显示镜像的所有层(layer)
```#sudo docker images --tree```

执行命令，显示下面的内容。正你看到的，导出后再导入(exported-imported)的镜像会丢失所有的历史，而保存后再加载（saveed-loaded）的镜像没有丢失历史和层(layer)。这意味着使用导出后再导入的方式，你将无法回滚到之前的层(layer)，同时，使用保存后再加载的方式持久化整个镜像，就可以做到层回滚（可以执行docker tag <LAYER ID> <IMAGE NAME>来回滚之前的层）。


###load与import 之间的不同






参考资料
--------
* [docker中文翻译] - Docker教程中文版本
* [docker官网] - Docker英文文档中心




[command line]:http://docs.docker.com/reference/commandline/cli/
[docker中文翻译]:http://www.widuu.com/docker/index.html
[docker官网]:http://docs.docker.com
