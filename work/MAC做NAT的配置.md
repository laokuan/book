#MAC做NAT的配置

1. ####使能转发

    ```
    sudo sysctl -w net.inet.ip.forwarding=1
    ```
2. ####配置nat规则
    需要创建一个新的文件，包含在/etc/pf.conf目录下，例如：
    ```
    more /etc/pf.conf
    
    #
    # com.apple anchor point
    #
    scrub-anchor "com.apple/*"
    nat-anchor "com.apple/*"
    nat-anchor "wangning-nat"
    rdr-anchor "com.apple/*"
    dummynet-anchor "com.apple/*"
    anchor "com.apple/*"
    load anchor "wangning-nat" from "/etc/pf.anchors/wangning-nat"
    load anchor "com.apple" from "/etc/pf.anchors/com.apple"
    ```
    
    上面的wang-nat规则是新加的：
    1. 需要用nat-anchor定义一个规则;
    2. 在后面用load anchor 引用这个规则
    
3. ####具体的规则定义

    具体规则定义如下，保存在/etc/pf.anchors/wangning-nat文件中了。
    ```
    more wangning-nat 
    nat on en0 from en5:network to any -> en0 
    ```
    其中：en0是无线接口，en5是有线接口，标识：从en5来的报文做nat，采用en0的接口地址。
    > 开始配置错误了：把第一个en0配置成en5了，导致不通。
    
4. ####启动pfctrl

    需要手工重新启动pfctl:
    > 命令是：sudo pfctl -evf /etc/pf.conf
    
    ```
    sudo pfctl -evf /etc/pf.conf  
    Password:
    pfctl: Use of -f option, could result in flushing of rules
    present in the main ruleset added by the system at startup.
    See /etc/pf.conf for further details.
    
    No ALTQ support in kernel
    ALTQ related functions disabled
    scrub-anchor "/*" all fragment reassemble
    nat-anchor "/*" all
    nat-anchor "wangning-nat" all
    rdr-anchor "/*" all
    anchor "/*" all
    dummynet-anchor "/*" all
    
    Loading anchor wangning-nat from /etc/pf.anchors/wangning-nat
    nat on en0 inet from 172.16.1.0/24 to any -> 192.168.0.105
    
    Loading anchor com.apple from /etc/pf.anchors/com.apple
    anchor "/*" all
    anchor "/*" all
    pfctl: pf already enabled
    ```
    
    禁止pfctl的命令：sudo pfctl -d
    >注：每次无线接口en0的ip地址变化，需要重新启动一次pfctl，从提示上看pfctl是获取的接口ip地址作为nat之后的源地址，但是不会感知到接口地址的变化。    