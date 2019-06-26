下图为一般方法，对于实体的linux，需要稍微变通一下。

![title](../../.local/static/2019/5/3/1.1561538523723.png)

实体linux配置方法：

```c++
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

