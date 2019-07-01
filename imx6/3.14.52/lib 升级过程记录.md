**方式1：** 手动替换各种链接库

操作1：误删libc.so.6

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



**结果1：** 各种报错


