下图为一般方法，对于实体的linux，需要稍微变通一下。

![title](../../.local/static/2019/5/3/1.1561538523723.png)

实体linux配置方法：

```shell
alex@al-1:~$ find /lib/modules/5.0.0-19-generic/ -name "rndis*"
/lib/modules/5.0.0-19-generic/kernel/drivers/net/wireless/rndis_wlan.ko
/lib/modules/5.0.0-19-generic/kernel/drivers/net/usb/rndis_host.ko
alex@al-1:~$  modprobe rndis_host
alex@al-1:~$ lsmod | grep rndis_host
rndis_host             20480  1 rndis_wlan
cdc_ether              20480  1 rndis_host
usbnet                 45056  4 rndis_wlan,cdc_subset,rndis_host,cdc_ether
alex@al-1:~$ 
```

实测每次开机网卡名字都可能变化，所以使用如下方式：

```shell
alex@al-1:~$ ifconfig -a
enp0s20f0u1c2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.7.5  netmask 255.255.255.0  broadcast 192.168.7.255
        ether be:b0:f9:7a:a3:23  txqueuelen 1000  (以太网)
        RX packets 84  bytes 11614 (11.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 395  bytes 82541 (82.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.82  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::cad:a468:758f:8f93  prefixlen 64  scopeid 0x20<link>
        ether 8c:ec:4b:58:c6:d8  txqueuelen 1000  (以太网)
        RX packets 607371  bytes 743763070 (743.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 617876  bytes 485904645 (485.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (本地环回)
        RX packets 20494  bytes 80224928 (80.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20494  bytes 80224928 (80.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9c:30:5b:ad:f0:bb  txqueuelen 1000  (以太网)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

注意复制好网卡的名字，然后运行：

```shell
ifconfig enp0s20f0u1c2 192.168.7.5 up
```

此时，观察

