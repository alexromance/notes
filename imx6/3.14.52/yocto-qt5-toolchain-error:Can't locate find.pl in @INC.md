报错表现：

```shell
ERROR: Function failed: do_configure (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2d-r0/temp/log.do_configure.15995)
ERROR: Logfile of failure stored in: /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2d-r0/temp/log.do_configure.15995
Log data follows:
| DEBUG: Executing python function sysroot_cleansstate
| DEBUG: Python function sysroot_cleansstate finished
| DEBUG: Executing shell function do_configure
| Can't locate find.pl in @INC (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at perlpath.pl line 7.
| WARNING: exit code 2 from a shell command.
| ERROR: Function failed: do_configure (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2d-r0/temp/log.do_configure.15995)
```

解决：

在/etc/perl 中写入find.pl文件即可

