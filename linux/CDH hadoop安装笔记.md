#创建了一个CentOS的VM基础模板

该模板的改动：

禁用了CentOS 7的网卡命名规则，改成了eth0这样的规则

把yum源改成163的

在VMware中创建一个独立的网络

eth0设置成固定IP地址分配
注意：NAT的地址分配

关闭了selinux

关闭了防火墙组件

以上可以作为CentOS 7的一个标准模板，源于CentOS 7的最小化安装。


