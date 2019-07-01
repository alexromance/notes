**方式1：** 手动替换各种链接库

操作1：误删libc.so.6软链接

现象：

```shell
root@imx6dlsabresd:/lib# rm libc.so.6 
root@imx6dlsabresd:/lib# ln -s libc-2.21.so libc.so.6
ln: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
```

解决：

```shell
LD_PRELOAD=/lib/libc-2.27.so ln -s /lib/libc-2.27.so /lib/libc.so.6
```

参考文章：

https://www.linuxidc.com/Linux/2017-02/140994.htm

操作2：误删 ld-linux-armhf.so.3软链接

现象：

```shell
root@imx6dlsabresd:/mnt/imx6d# mv a.out aa.out
-sh: /bin/mv: No such file or directory
root@imx6dlsabresd:/mnt/imx6d# vi /etc/profile 
-sh: /bin/vi: No such file or directory
root@imx6dlsabresd:/mnt/imx6d# tar
-sh: /bin/tar: No such file or directory
root@imx6dlsabresd:/mnt/imx6d# scp
-sh: /usr/bin/scp: No such file or directory
```

各种命令都是No such file or directory

解决：

```shell
/lib/ld-2.21.so --library-path /lib/ /bin/ln -s /lib/ld-2.21.so /lib/ld-linux-armhf.so.3
```

参考文章：

http://www.xuyanlinux.com/archives/142

操作3：拷贝libm.so.6软链接后程序报错

```shell
root@imx6dlsabresd:/lib# find . -name "*2.27*"
./librt-2.27.so
./libresolv-2.27.so
./ld-2.27.so
./libm-2.27.so
./libanl-2.27.so
./libnss_dns-2.27.so
./libnss_compat-2.27.so
./libc-2.27.so
./libdl-2.27.so
./libBrokenLocale-2.27.so
./libnss_files-2.27.so
./libnsl-2.27.so
./libpthread-2.27.so
./libutil-2.27.so
./libcrypt-2.27.so
```

先在板子上查找出一直的2.27高版本的lib，然后从pc上一个一个对应着高版本的进行拷贝。

pc:

```shell
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp ld-linux-armhf.so.3 ~/nfs_share/all_test/imx6d/
a.out           opengles2_test  test_lib/       test_usr_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp ld-linux-armhf.so.3 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp librt.so.1 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libresolv.so.2 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libm.so.6 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libanl
libanl-2.27.so  libanl.so.1     
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libanl
libanl-2.27.so  libanl.so.1     
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libanl.so.1 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libnss_dns
libnss_dns-2.27.so  libnss_dns.so.2     
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libnss_dns.so.2 ~/nfs_share/all_test/imx6d/test_
test_lib/     test_usr_lib/ 
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libnss_dns.so.2 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libnss_compat.so.2 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libnss_compat.so.2 ~/nfs_share/all_test/imx6d/test_lib/
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi/lib *
 alex→ $ cp libpthread.so.0 ~/nfs_share/all_test/imx6d/test_lib/
```

板子：

```shell
root@imx6dlsabresd:/mnt/imx6d/test_lib# cp ld-linux-armhf.so.3 /lib
root@imx6dlsabresd:/mnt/imx6d/test_lib# cp librt.so.1 /lib/
root@imx6dlsabresd:/mnt/imx6d/test_lib# cp libresolv.so.2 /lib
root@imx6dlsabresd:/mnt/imx6d/test_lib# cp libm.so.6 /lib
root@imx6dlsabresd:/mnt/imx6d/test_lib# cp libanl.so.1 /lib
cp: relocation error: /lib/libm.so.6: symbol __strtod_nan version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
```

现象：

```shell
root@imx6dlsabresd:/mnt/imx6d/test_lib# cp libanl.so.1 /lib
cp: relocation error: /lib/libm.so.6: symbol __strtod_nan version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
```

解决：

LD_PRELOAD=/lib/libc-2.27.so ln -sf /lib/libc-2.27.so /lib/libc.so.6

参考文章：

https://blog.51cto.com/zhaoyong/194327

**结果1：** 各种报错，感觉无法进行下去了。

**方式2：**直接打包编译好的


