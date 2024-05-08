[TOC]

# IP地址

- 用于和其它计算机进行通讯

- IP地址主要有2个版本，V4版本和V6版本

  - IPv4版本的地址格式是:a.b.c.d，其中abcd表示0~255的数字

  `ifconfig`

- 查看本机的ip地址，若无法使用，可安装：`yum -y install net-tools`

- 127.0.0.1，这个IP地址用于指代本机
- 0.0.0.0，特殊IP地址
  - 可用于指代本机
  - 可以在端口绑定中用来确定绑定关系
  - 在一些IP地址限制中，表示所有IP的意思，如放行规则设置为0.0.0.0，表示允许任意IP访问

# 主机名

- 除了对外联络地址(IP地址)以外，也可以有一个名字，成为主机名

​		`hostname`：查看主机名

​		`hostnamectl set-hostname 主机名`：修改主机名，需root

# 域名解析

- 先查看本机的记录(私人地址本)
  - windows看：`C:\Windows\System32\drivers\etc\hosts`
  - Linux看：`/etc/hosts`
- 再联网去DNS服务器询问

## 配置主机名映射

- 记事本打开`C:\Windows\System32\drivers\etc\hosts`

  ![](E:\E\Typora\notes\photo\Snipaste_2024-05-18_23-47-18.png)

# 在虚拟机里配置固定IP

- 在VMware Workstation中配置IP地址网关和网段(IP地址的范围)

  - 虚拟机编辑选项
  - 虚拟网络编辑器-选择VMnet8
  - 子网IP：`192.168.88.0`
  - 子网掩码：`255.255.255.0`
  - NAT设置-网关IP：`192.168.88.2`

- 在Linux系统中手动修改配置文件，固定IP

  - 使用vim编辑`/etc/sysconfig/network-scripts/ifcfg-ens33`文件，填入如下内容：

    ![](https://happlay-docs.oss-cn-beijing.aliyuncs.com/docs/Snipaste_2024-05-20_16-01-12.png)

  - 执行：`systemctl restart network`重启网卡