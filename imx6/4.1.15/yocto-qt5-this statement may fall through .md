编译报错：this statement may fall through [-Werror=implicit-fallthrough=]


报错表现：

```c++
| ../../elfutils-0.164/libdwfl/dwfl_report_elf.c: In function '__libdwfl_elf_address_range':
| ../../elfutils-0.164/libdwfl/dwfl_report_elf.c:172:19: error: this statement may fall through [-Werror=implicit-fallthrough=]
|        add_p_vaddr = true;
|                    ^
| ../../elfutils-0.164/libdwfl/dwfl_report_elf.c:174:5: note: here
|      case ET_DYN:
|      ^~~~
| gcc  -D_GNU_SOURCE -DHAVE_CONFIG_H -DLOCALEDIR='"/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/share/locale"' -I. -I../../elfutils-0.164/libdwfl -I..  -I. -I../../elfutils-0.164/libdwfl -I../../elfutils-0.164/lib -I.. -I../../elfutils-0.164/libdwfl -I../../elfutils-0.164/libdwfl/../libelf -I../../elfutils-0.164/libdwfl/../libebl -I../../elfutils-0.164/libdwfl/../libdw -I../../elfutils-0.164/libdwfl/../libdwelf -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -std=gnu99 -Wall -Wshadow -Wformat=2 -Wold-style-definition -Wstrict-prototypes -Werror -Wunused -Wextra -Wstack-usage=262144  -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -c -o dwfl_module_report_build_id.o ../../elfutils-0.164/libdwfl/dwfl_module_report_build_id.c
| cc1: all warnings being treated as errors
| Makefile:576: recipe for target 'dwfl_report_elf.o' failed
| make[2]: *** [dwfl_report_elf.o] Error 1
| make[2]: *** Waiting for unfinished jobs....
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/elfutils-native/0.164-r0/build/libdwfl'
| Makefile:473: recipe for target 'all-recursive' failed
| make[1]: *** [all-recursive] Error 1
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/elfutils-native/0.164-r0/build'
| Makefile:389: recipe for target 'all' failed
| make: *** [all] Error 2
| ERROR: oe_runmake failed
| ERROR: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/elfutils-native/0.164-r0/temp/log.do_compile.28917)
```

解决：

```c++
grep _no_Werror\) * -r | cut -d":" -f1 | xargs sed -i "s/[$](if [$]([$]([*F]*)_no_Werror),,-Werror)//"
grep _no_Werror\) * -r | cut -d":" -f1 | xargs sed -i "s/[$]([$]([*F]*)_no_Werror),,-Werror) [$](if//"
```


参考文章：


https://www.cnblogs.com/zengjfgit/p/9181721.html