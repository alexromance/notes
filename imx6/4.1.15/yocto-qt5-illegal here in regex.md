编译报错：illegal here in regex; marked by <-- HERE in m/\${ <-- HERE ([^ \t=:+{}]+)}

报错表现：

```c++
NOTE: Preparing RunQueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
ERROR: libtool-native-2.4.6-r0 do_configure: Function failed: do_configure (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/log.do_configure.56269)
ERROR: Logfile of failure stored in: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/log.do_configure.56269
Log data follows:
| DEBUG: Executing python function sysroot_cleansstate
| DEBUG: Python function sysroot_cleansstate finished
| DEBUG: Executing shell function autotools_preconfigure
| DEBUG: Shell function autotools_preconfigure finished
| DEBUG: Executing python function autotools_copy_aclocals
| DEBUG: SITE files ['endian-little', 'common-linux', 'common-glibc', 'bit-64', 'x86_64-linux', 'common']
| DEBUG: Python function autotools_copy_aclocals finished
| DEBUG: Executing shell function do_configure
| Unescaped left brace in regex is illegal here in regex; marked by <-- HERE in m/\${ <-- HERE ([^ \t=:+{}]+)}/ at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/automake line 3939.
| Unescaped left brace in regex is illegal here in regex; marked by <-- HERE in m/\${ <-- HERE ([^ \t=:+{}]+)}/ at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/automake line 3939.
| WARNING: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/run.do_configure.56269:1 exit 255 from 'automake --version'
| ERROR: Function failed: do_configure (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/libtool-native/2.4.6-r0/temp/log.do_configure.56269)
ERROR: Task 579 (/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/meta/recipes-devtools/libtool/libtool-native_2.4.6.bb, do_configure) failed with exit code '1'
WARNING: pigz-native-2.3.3-r0 do_fetch: Failed to fetch URL http://zlib.net/pigz/pigz-2.3.3.tar.gz, attempting MIRRORS if available
```

解决：



参考文章：

https://www.cnblogs.com/zengjfgit/p/9178523.html