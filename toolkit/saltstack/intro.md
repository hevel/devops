# 简介及安装

##简介
SaltStack 是一个批量化的主机管理工具,借助 SaltStack 可以轻松管理成百上千的主机。类似的工具还有 Puppet、 Chef、 Ansible 等。总体来说Saltstack 比 Puppet、Chef 更加简单易用，比 Ansible 更加快速功能更加强大。

关于这几工具的详细比较请参考以下文章：

[A Taste of Salt: Like Puppet, But Less Frustrating](http://blog.smartbear.com/devops/a-taste-of-salt-like-puppet-except-it-doesnt-suck/)

[Community Metrics: Comparing Ansible, Chef, Puppet and Salt](http://redmonk.com/sogrady/2013/12/06/configuration-management-2013/)

[Configuration Management: Which should I choose: Chef, Puppet, Ansible, Saltstack, Docker, or something else?](http://www.quora.com/Configuration-Management/Which-should-I-choose-Chef-Puppet-Ansible-Saltstack-Docker-or-something-else)

[Salt vs. Chef](http://www.scriptrock.com/articles/salt-vs-chef)

[Moving away from Puppet: SaltStack or Ansible?](http://ryandlane.com/blog/2014/08/04/moving-away-from-puppet-saltstack-or-ansible/)

[Ansible and Salt: A detailed comparison](https://missingm.co/2013/06/ansible-and-salt-a-detailed-comparison/)

[Salt vs. Ansible](http://jensrantil.github.io/salt-vs-ansible.html)

SaltStack 采用 python 开发，C/S 结构，master(=server) 端和 minion(=client) 端通信基于 ZeroMQ，

**SaltStack主要特性：**
- 简单，安装配置都非常简单
- 并行
- 快速可靠，采用 ZeroMQ 消息队列，消息序列化采用 msgpack（比 json 和 protocol buffer 更轻量）并采用 AES 算法加密。
- 提供 Python API和 REST API
- 功能强大，内置大量功能模块
- 社区活跃

**SaltStack 的核心功能可以分为两块：**
- 配置管理
- 分布式远程命令执行。


###SaltStack CLI（命令行交互接口）
- salt，在 master 端对 minion 端执行操作
- salt-api，管理 REST API
- salt-call，用以在 minion 端执行模块功能
- salt-cloud，云端虚拟机管理
- salt-cp，从 master 端复制文件到 minion 端
- salt-key，管理master 端公钥
- salt-master，管理 minion 端
- salt-minion，接受来自 master 端的命令
- salt-run，执行 salt runner 命令
- salt-ssh，通过 ssh 控制 minion
- salt-syndic，特殊的 minion 负责转发 master 命令给其他 minion


##安装

SaltStack minion 端支持大多数 Linux/Unix 发行版 以及 Windows， master 端只能运行在 Linux/Unix 环境下。目前（2015-03-06）Saltstack的稳定版本是2014.7.0，代号 Helium。

###运行环境依赖：
- Python（介于2.6和3.0之间的版本（含2.6））及以下类库：
    - msgpack-python
    - YAML
    - Jinja2
    - MarkupSafe
    - apache-libcloud
    - Requests
- ZeroMQ（默认）或者 RAET
    - ZeroMQ 依赖于：
        - ZeroMQ  3.2.0及以上版本
        - pyzmq 2.2.0及以上版本
        - PyCrypto
        - M2Crypto
    - RAET 依赖于：
        - RAET
        - libnacl
        - ioflo

###Ubuntu 下安装
```
sudo add-apt-repository ppa:saltstack/salt #添加 PPA 仓库
sudo apt-get update #更新包管理数据库

#以下包按需安装
sudo apt-get install salt-master
sudo apt-get install salt-minion
sudo apt-get install salt-syndic

sudo apt-get install salt-cloud
sudo apt-get install salt-cp
sudo apt-get install salt-ssh
sudo apt-get install salt-api(2014.7.0版已将其合并到 master，不用单独安装)

service salt-master start #启动 salt-master 服务

```

###RedHat/CentOS/ Scientific Linux / Amazon Linux / Oracle Linux 下安装
```
#安装配置epel源
rpm -Uvh install http://mirrors.zju.edu.cn/epel/6/i386/epel-release-5-4.noarch.rpm #RedHat5
rpm -Uvh install http://mirrors.zju.edu.cn/epel/6/i386/epel-release-6-8.noarch.rpm #RedHat6
rpm -Uvh install http://mirrors.zju.edu.cn/epel/7/x86_64/e/epel-release-7-5.noarch.rpm #RedHat7

yum install salt-master -y
yum install salt-minion -y

service salt-master start #手动启动 salt-master 服务
chkconfig salt-master on #开机启动 salt-master 服务
service salt-minion start #手动启动 salt-master 服务
chkconfig salt-minion on #开机启动 salt-minion 服务
```

**除了用各 Linux/Unix 发行版的包管理器安装外还可以用 pip 安装（推荐）**
```
pip install salt
```

其他Linux 发行版安装请参考官方文档：
[http://docs.saltstack.com/en/latest/topics/installation/](http://docs.saltstack.com/en/latest/topics/installation/)

##配置
master端如有启用防火墙需要放通4505（消息发布）和4506（消息接收）两个TCP端口。

SaltStack 配置文件默认路径位/etc/salt，master 端配置文件为/etc/salt/master，minion 端配置文件为/etc/salt/minion。**修改配置文件后需要重启对应服务使所做修改生效。**

master 配置文件说明：[http://docs.saltstack.com/en/latest/ref/configuration/master.html](http://docs.saltstack.com/en/latest/ref/configuration/master.html)

minion 配置文件说明：[http://docs.saltstack.com/en/latest/ref/configuration/minion.html](http://docs.saltstack.com/en/latest/ref/configuration/minion.html)

master 端采用默认配置即可运行，minion 端需要修改指定 master 端域名或 ip。
```
# Set the location of the salt master server, if the master server cannot be
# resolved, then the minion will fail to start.
master: salt
```
默认指向域名为 salt 的主机，我将 master 和 minion 均安装在本机所以设置为
```
master: localhost
或者
master: 127.0.0.1
```
请根据实际情况设置master的域名或ip。**修改配置文件后记得重启对应服务。
**
##使用
配置完成后在 master 端执行
```
salt-key -a localhost #接受指定minion的公钥
salt-key -A #接受所有公钥

salt-call key.finger --local //minion端执行，显示pubkey
salt-key  -f  your-minion-id //master端验证指定minion的pubkey
```
如果在 master 配置文件里设置了 **auto_accept: True** 则不需要手动认证。

其他常用命令
```
salt-key -L #查看所有公钥
salt-key -l un #查看未认证（unaccepted）公钥
salt-key -l acc #查看已经通过认证（accepted）的公钥
salt-key -D #删除所以公钥
salt-key -h #查看帮助文档
```
完成认证后，执行如下命令，验证 master 端和 minion 端的联通性：
```
salt '*' test.ping # * 表示对所有 minion
```
正常情况下应该得到如下的输出：
```
3bb6e8e2bd4d:
    True
2a82568ff187:
    True
8ed6ee48370d:
    True
```
True 表示连通，False 表示无法连通。

也可以通过如下命令查看 minion 端和 master 端的连通性：
```
salt-run manage.status #列出所有的 minion
salt-run manage.up #列出连通的 minion
salt-run manage.down # 列出无法连通的 minion
salt-run manage.versions # 查看连通的 minion 的版本号
salt-run -d #查看 salt-run 更多模块用法
salt-run -h #查看 salt-run 帮助文档
```

安装配置完成，下一节将介绍一些 SaltStack 常用的命令和常用的执行模块。







