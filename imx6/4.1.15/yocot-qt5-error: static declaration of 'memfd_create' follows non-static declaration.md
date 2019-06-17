编译报错：error: static declaration of 'memfd_create' follows non-static declaration


报错表现：


```c++
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/util/memfd.c:43:12: error: static declaration of 'memfd_create' follows non-static declaration
|  static int memfd_create(const char *name, unsigned int flags)
|             ^~~~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/mman-linux.h:115:0,
|                  from /usr/include/x86_64-linux-gnu/bits/mman.h:45,
|                  from /usr/include/x86_64-linux-gnu/sys/mman.h:41,
|                  from /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/include/qemu/osdep.h:142,
|                  from /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/util/memfd.c:28:
| /usr/include/x86_64-linux-gnu/bits/mman-shared.h:46:5: note: previous declaration of 'memfd_create' was here
|  int memfd_create (const char *__name, unsigned int __flags) __THROW;
|      ^~~~~~~~~~~~
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/rules.mak:57: recipe for target 'util/memfd.o' failed
| make: *** [util/memfd.o] Error 1
| make: *** Waiting for unfinished jobs....
| ERROR: oe_runmake failed
| ERROR: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/temp/log.do_compile.42067)
ERROR: Task 981 (virtual:native:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/meta/recipes-devtools/qemu/qemu_2.5.0.bb, do_compile) failed with exit code '1'
WARNING: libxslt-native-1.1.28-r0 do_fetch: Failed to fetch URL ftp://xmlsoft.org/libxslt/libxslt-1.1.28.tar.gz, attempting MIRRORS if available
```


解决：


将 
```c{yocto_path}/build-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/util/memfd.c
```
文件中memfd_create函数名重命名为tmp_memfd_create