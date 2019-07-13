此问题在本次编译过程中出现了两次，原因均是由于perl版本比较高。

编译报错：

Unescaped left brace in regex is illegal here in regex;

报错表现：

第一处：

```shell
ERROR: Function failed: do_configure (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/log.do_configure.20436)
ERROR: Logfile of failure stored in: /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/log.do_configure.20436
Log data follows:
| DEBUG: Executing python function sysroot_cleansstate
| DEBUG: Python function sysroot_cleansstate finished
| DEBUG: Executing shell function autotools_preconfigure
| DEBUG: Shell function autotools_preconfigure finished
| DEBUG: Executing python function autotools_copy_aclocals
| DEBUG: SITE files ['endian-little', 'common-linux', 'common-glibc', 'bit-64', 'x86_64-linux', 'common']
| DEBUG: Python function autotools_copy_aclocals finished
| DEBUG: Executing shell function do_configure
| Unescaped left brace in regex is illegal here in regex; marked by <-- HERE in m/\${ <-- HERE ([^ \t=:+{}]+)}/ at /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/automake line 3936.
| Unescaped left brace in regex is illegal here in regex; marked by <-- HERE in m/\${ <-- HERE ([^ \t=:+{}]+)}/ at /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/automake line 3936.
| WARNING: exit code 255 from a shell command.
| ERROR: Function failed: do_configure (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/log.do_configure.20436)
```

第二处：

```shell
| Unescaped left brace in regex is illegal here in regex; marked by <-- HERE in m/^\@strong{ <-- HERE (.*)}$/ at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.2.0-r1/qemu-2.2.0/scripts/texi2pod.pl line 320.
| Makefile:476: recipe for target 'qemu-img.1' failed
| make: *** [qemu-img.1] Error 255
| make: *** Waiting for unfinished jobs....
| ERROR: oe_runmake failed
| WARNING: exit code 1 from a shell command.
| ERROR: Function failed: do_compile (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.2.0-r1/temp/log.do_compile.1219)
```

解决：

```shell
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.2.0-r1/qemu-2.2.0/scripts *
 alex→ $ diff texi2pod.pl texi2pod.pl.bak
320c320
< 	    $column =~ s/^\@strong[{](.*)}$/$1/;
---
> 	    $column =~ s/^\@strong{(.*)}$/$1/;
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.2.0-r1/qemu-2.2.0/scripts *
 alex→ $ 
```

总的来说，都是把不支持的用法 **{**  用  **[{]**  进行一下修改

参考文章：

https://www.cnblogs.com/zengjfgit/p/9178523.html