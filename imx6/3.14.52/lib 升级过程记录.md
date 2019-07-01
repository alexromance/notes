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



**结果1：** 各种报错


