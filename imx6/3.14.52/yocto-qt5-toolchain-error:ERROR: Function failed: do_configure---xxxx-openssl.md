报错表现：

```shell
ERROR: Function failed: do_configure (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2d-r0/temp/log.do_configure.1346)
ERROR: Logfile of failure stored in: /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2d-r0/temp/log.do_configure.1346
Log data follows:
| DEBUG: Executing python function sysroot_cleansstate
| DEBUG: Python function sysroot_cleansstate finished
| DEBUG: Executing shell function do_configure
| ERROR: Function failed: do_configure (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2d-r0/temp/log.do_configure.1346)
```

解决：

无脑安装openssl1.0

```shell
sudo apt install openssl1.0
```
