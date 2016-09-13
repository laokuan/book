# 网络操作

本文以Centos7.0的操作为准，准CentOS7.0上，网络相关的改动比CentOS6有较大的变化。

### 修改网卡的名字

CentOS7.0的网卡命名规则和6.0版本有较大的变化。默认情况下CentOS7.0是以Bios中的名字作为网卡的命名标准，

```
[root@centos ~]# service network restart
Restarting network (via systemctl):  Job for network.service failed. See 'systemctl status network.service' and 'journalctl -xn' for details.
[FAILED]

[root@centos ~]# systemctl status network
network.service - LSB: Bring up/down networking
   Loaded: loaded (/etc/rc.d/init.d/network)
   Active: failed (Result: exit-code) since Fri 2016-09-09 16:53:09 EDT; 13s ago
  Process: 7947 ExecStart=/etc/rc.d/init.d/network start (code=exited, status=1/FAILURE)

Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos network[7947]: RTNETLINK answers: File exists
Sep 09 16:53:09 centos systemd[1]: network.service: control process exited, code=exited status=1
Sep 09 16:53:09 centos systemd[1]: Failed to start LSB: Bring up/down networking.
Sep 09 16:53:09 centos systemd[1]: Unit network.service entered failed state.
```

错误修复的方式，需要在ifcfg－eth0中加入HWADDR配置：
```
[root@centos network-scripts]# more ifcfg-eth0
TYPE=Ethernet
BOOTPROTO=dhcp
DEFROUTE=yes
PEERDNS=yes
PEERROUTES=yes
IPV4_FAILURE_FATAL=no
UUID=e8351680-25a8-4cb3-b953-e132123f2e69
NAME=eth0
HWADDR="00:0c:29:28:3c:71"
ONBOOT=yes
```

