编译报错：help2man: can't get `--help' info from automake-1.15

报错表现：


```c++
ERROR: automake-native-1.15-r0 do_compile: oe_runmake failed
ERROR: automake-native-1.15-r0 do_compile: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/automake-native/1.15-r0/temp/log.do_compile.50814)
ERROR: Logfile of failure stored in: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/automake-native/1.15-r0/temp/log.do_compile.50814
Log data follows:
| DEBUG: Executing shell function do_compile
| NOTE: make -j 4
| : && /bin/mkdir -p doc && { PATH='/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/automake-native/1.15-r0/build/t/wrap:'$PATH && export PATH; } && /usr/bin/perl ../automake-1.15/doc/help2man --output=doc/automake-1.15.1 automake-1.15
| help2man: can't get `--help' info from automake-1.15
| Try `--no-discard-stderr' if option outputs to stderr
| Makefile:3687: recipe for target 'doc/automake-1.15.1' failed
| make: *** [doc/automake-1.15.1] Error 255
| ERROR: oe_runmake failed
| WARNING: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/automake-native/1.15-r0/temp/run.do_compile.50814:1 exit 1 from 'exit 1'
| ERROR: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/automake-native/1.15-r0/temp/log.do_compile.50814)
ERROR: Task 571 (virtual:native:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/meta/recipes-devtools/automake/automake_1.15.bb, do_compile) failed with exit code '1'
NOTE: Tasks Summary: Attempted 100 tasks of which 95 didn't need to be rerun and 1 failed.
```

解决：


修改makefile源代码：
```c++

```