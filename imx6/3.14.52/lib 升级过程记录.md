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

先在板子上查找出需要移植的2.27高版本的lib，然后从pc上一个一个对应着高版本的进行拷贝。

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

**方式2：**直接打包编译好的高版本lib进行替换

操作1：

先把pc上的编译好的高版本lib进行打包。

```shell
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi *
 alex→ $ tar -czvf /home/alex/nfs_share/all_test/imx6d/lib.tar.gz lib/
lib/
lib/libnss_mdns_minimal.so.2
lib/libext2fs.so.2.4
lib/libncursesw.so.5
lib/librt-2.27.so
lib/depmod.d/
lib/depmod.d/search.conf
lib/libblkid.so.1
lib/libattr.so.1
lib/libudev.so
lib/libnss_hesiod-2.27.so
lib/libdl.so.2
lib/libsmartcols.so.1
lib/libnss_compat.so.2
lib/libext2fs.so.2
lib/libnss_mdns6.so.2
lib/libcidn-2.27.so
lib/libnsl.so.1
lib/librt.so.1
lib/libz.so.1
lib/libss.so.2
lib/libudev.so.1
lib/libm.so.6
lib/libnss_db-2.27.so
lib/libnss_nisplus.so.2
lib/libmount.so.1.1.0
lib/.debug/
lib/.debug/libnss_mdns_minimal.so.2
lib/.debug/libext2fs.so.2.4
lib/.debug/librt-2.27.so
lib/.debug/libnss_systemd.so.2
lib/.debug/libnss_hesiod-2.27.so
lib/.debug/libnss_mdns6.so.2
lib/.debug/libcidn-2.27.so
lib/.debug/libnss_db-2.27.so
...
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.dep
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.softdep
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/extra/
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/extra/galcore.ko
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.alias
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.symbols
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.symbols.bin
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.dep.bin
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.order
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.alias.bin
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.builtin.bin
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.builtin
lib/modules/4.14.98-imx_4.14.98_2.0.0_ga+g5d6cbeafb80c/modules.devname
* /opt/fsl-imx-fb/4.14-sumo/sysroots/cortexa9hf-neon-poky-linux-gnueabi *
 alex→ $ 
```

然后在板子上进行直接解压替换：

```shell
root@imx6dlsabresd:/# tar -xzvf lib.tar.gz  
lib/
lib/libanl.so.1
lib/libm.so.6
lib/libcrypt-2.21.so
lib/libutil.so.1
lib/libpthread.so.0
lib/libnsl-2.21.so
lib/libpthread-2.21.so
lib/librt-2.21.so
lib/libblkid.so.1.1.0
lib/libnss_dns-2.21.so
...
lib/libtinfo.so.5
lib/ld-linux-armhf.so.3
lib/ld-2.21.so
lib/libc-2.21.so
lib/librt.so.1
lib/libuuid.so.1
lib/libanl-2.21.so
lib/libdl.so.2
lib/libBrokenLocale-2.21.so
lib/libtinfo.so.5.9
lib/libnss_compat-2.21.so
lib/libBrokenLocale.so.1
lib/libutil-2.21.so
lib/libblkid.so.1
lib/libnsl.so.1
lib/libresolv-2.21.so
lib/libdl-2.21.so
lib/libcrypt.so.1
```

**结果2：**完美运行



