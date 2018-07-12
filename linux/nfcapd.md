#### 选项说明
##### 常用的选项
> 指定监听端口

```
-p portnum
    指定监听的端口，默认值是9995.
    Specifies the port number to listen. Default port is 9995
```
> bind主机

```
-b bindhost
    Specifies the hostname/IPv4/IPv6 address to bind for listening. 
    This can be an IP address or a hostname, resolving to an IP address attached to an interface. 
    Defaults to any available IPv4 interface, if not specified.
-4
    Forces nfcapd to listen on IPv4 addresses only. 
    Can be used together with -b if a hostname has an IPv4 and IPv6 address record.
-6
    Forces nfcapd to listen on IPv6 addresses only. 
    Can be used together with -b if a hostname has an IPv4 and IPv6 address record. Depending on the socket implementation -6 also accepts IPv4 data.
```

##### 不常用的选项



