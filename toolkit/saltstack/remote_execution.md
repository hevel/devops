# 远程命令执行

**远程命令执行**是 saltstack 的两大核心功能之一也是日常使用得最多的功能。借助这一功能，我们可以轻松的实现在成百上千台主机上添加用户、修改用户密码等操作。

通过在 master 端试用 salt 这个命令行接口向 minion 端发送操作令，salt用法如下：
```
salt <target> <module.func> [arg]
        |           |          |
    目标minion      |        模块方法接受的参数
                要调用的模块方法

#示例
salt 8ed6ee48370d test.echo "What can I do for u? master"
salt '*' test.echo "hello, saltstack"
```

在更多的情况下我们需要对某些特定的 minion 进行操作，所以 SaltStack 提供了多种过滤 minion 的方法：
- 指定 minion-id

```
salt localhost test.ping
salt 3e4f5d6g test.ping
```

- 默认匹配规则：shell 风格的 glob 表达式（基于通配符的匹配规则）

```
salt '*' test.ping
salt '*.example.net' test.ping
salt 'web?.example.net' test.ping
salt 'minion[1-9]' test.ping
salt 'web[1,8]' test.ping
salt 'db[!0-9]' test.ping
```
更多通配符用法请参考：

[Wildcards](http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm)

[Shell 通配符](http://man.chinaunix.net/linux/mandrake/101/zh_cn/Command-Line.html/glob-regex.html)

- -E   PCRE 正则表达式

```
salt -E web\d+\.(dev|qa|prod)\.com test.ping
salt -E minion-[23][0-9] test.ping
```
更多正则表达式用法请参考：

[正则表达式语法](https://msdn.microsoft.com/zh-cn/library/ae5bf541%28v=vs.90%29.aspx)

[Regular Expressions Cheat Sheet by DaveChild
](http://www.cheatography.com/davechild/cheat-sheets/regular-expressions/)

- -L   List 列表模式

```
salt -L 'minion1,minion2,minion3' test.ping
```

- -R   SECO range #应该很少能用上

```
salt --range %test:CLUSTER test.ping
```
要使用 Range 需要先配置 Range Server，具体请参考：
[SECO Range](http://docs.saltstack.com/en/latest/topics/targeting/range.html)

- -S   Subnet 子网(CIDR 表示法)或IP

```
salt -S 192.168.1.0/24 test.ping
salt -S 172.16.13.100 test.ping
```
[IP CIDR互转工具](http://www.ipaddressguide.com/cidr)

- -N   Nodegroup 分组模式，需要在/etc/salt/master里配置nodegroups参数。

```
nodegroups:
    group1: 'L@foo.domain.com,bar.domain.com,baz.domain.com and bl*.domain.com'
    group2: 'G@os:Debian and foo.domain.com'

salt -N group1 test.ping
```

- -G   Grains glob(基于 Grains 的匹配) #**Grains** 即 minion 启动时加载的关于主机的部分信息，如 OS 名称、Python 版本、内存大小等。

```
salt -G 'os:Ubuntu' test.ping
salt -G 'cpuarch:x86_64' grains.items
salt '*' grains.ls #列出所有可用的 Grains 的键
salt '*' grains.items #列出所以 Grains 的键和值
salt '*' grains.item pythonversion # 根据 Grains 的键查看值
```

可以在 /etc/salt/minion 或者 /etc/salt/grains 里配置自定义 Grains。

```
grains:
  fake_key:
    - fake_value1
    - fake_value2
```

- -I   Pillar glob（通配符结合 Pillar）# **Pillar**即存储在 master 上的提供给 minion 使用的数据。默认情况下 master 的配置信息会被加载到 pillar 中。pillar 数据默认保存在/srv/pillar目录下，详细用法此处略过，可参考官方教程：[Pillar Walkthrough](http://docs.saltstack.com/en/latest/topics/tutorials/pillar.html)

```
salt -I 'master:daemon:False' test.ping
salt -I 'foo:bar:baz*' test.ping
```
- -C   复合模式，组合上面几种匹配模式，可用 or, and, not连接不同规则。

| 前缀字母 | 匹配类型 | 示例 |
| -- | -- | -- |
| G |  Grains glob（Grains结合通配符）| G@os:Ubuntu |
| E | PCRE 正则表达式 | E@web\d+\.(foo)\.loc |
| P | Grains PCRE（Grains 结合正则表达式）| P@os:RedHat |
| L | List（列表）| L@minion1,minion2,minion3 |
| I | Pillar glob（Pillar结合通配符）| I@key:value |
| S | Subnet/IP address（子网或 IP）| S@192.168.1.0/24 or S@192.168.1.100 |
| R | Range cluster（Range 集群） | R@%foo.bar |


##Saltstack 执行模块
Saltstack 内置了大量的执行模块可供调用，模块列表详见：[Full list of builtin execution modules](http://docs.saltstack.com/en/latest/ref/modules/all/)。

**部分模块使用示例：**
```
#帮助
salt '*' sys.list_modules  //列出所有内建功能模块
salt '*' sys.list_functions //列出所有功能函数
salt '*' sys.doc //列出所有文档
salt '*' sys.doc user.info//查看某个功能模块的说明文档

#Grains数据管理
salt '*' grains.ls //列出所有可用的grains的名字
salt '*' grains.item os //显示操作系统类型
salt '*' grains.items //显示所有grains

#包管理 dpkg、yumpkg、aptpkg、freebsdpkg 别名 pkg
salt '*' pkg.install apache //安装
salt '*' pkg.install pkgs="['apache','nginx']" //安装多个包
salt '*' pkg.upgrade ruby //升级
salt '*' pkg.list_pkgs //查看已经安装的包

#磁盘信息
salt '*' disk.percent //各磁盘分区使用量（百分比）
salt '*' disk.percent /var //指定磁盘分区使用量

#查看系统状态信息
salt '*' status.cpuinfo //查看 CPU 详细信息
salt '*' status.diskusage //各磁盘分区使用量（字节）
salt '*' status.meminfo //查看内存信息
salt '*' status.uptime //查看系统运行时长

#系统管理
salt '*' system.halt //关机
salt '*' system.reboot //重启
salt '*' system.shutdown //关机
salt '*' system.shutdown at_time='now' //指定时间关机

#用户管理 useradd 别名 user
salt '*' user.add test //添加用户
salt '*' user.delete name remove=True force=True //删除
salt '*' user.info root //查看用户信息
salt '*' user.rename name new_name //修改用户名
salt '*' user.list_users //查看所以用户
salt '*' user.getent //查看所有用户的信息

#网络
salt '*' network.connect archlinux.org 80 //测试连通性
salt '*' network.connect archlinux.org 80 timeout=3
salt '*' network.connect archlinux.org 80 timeout=3 family=ipv4
salt '*' network.get_hostname //获取主机名
salt '*' network.interfaces //查看所以网络端口
salt '*' network.hw_addr eth0 //获取指定网络端口的 MAC 地址
salt '*' network.ip_addrs //查看IP
salt '*' network.ip_addrs eth0 //查看指定网络端口的 IP
salt '*' network.netstat //查看端口状态
salt '*' network.ping archlinux.org //ping 指定域名或 IP
```












