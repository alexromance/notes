编译报错：error: this statement may fall through [-Werror=implicit-fallthrough=]

报错表现：

```c++
_64-linux/usr/include -O2 -pipe -fstack-protector-all -D_FORTIFY_SOURCE=2 -c -o stap-loc2c.o `test -f 'loc2c.c' || echo '../git/'`loc2c.c
| ../git/loc2c.c: In function 'c_emit_location':
| ../git/loc2c.c:2563:21: error: this statement may fall through [-Werror=implicit-fallthrough=]
|   l->address.declare = "addr";
|   ~~~~~~~~~~~~~~~~~~~^~~~~~~~
| ../git/loc2c.c:2564:7: note: here
|        case loc_fragment:
|        ^~~~
| cc1: all warnings being treated as errors
| Makefile:1043: recipe for target 'stap-loc2c.o' failed
| make[2]: *** [stap-loc2c.o] Error 1
| make[2]: *** Waiting for unfinished jobs....
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/build'
| Makefile:1878: recipe for target 'all-recursive' failed
| make[1]: *** [all-recursive] Error 1
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/build'
| Makefile:670: recipe for target 'all' failed
| make: *** [all] Error 2
| WARNING: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/temp/run.do_compile.48233:1 exit 1 from 'exit 1'
| ERROR: oe_runmake failed
| ERROR: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/temp/log.do_compile.48233)
ERROR: Task 4935 (virtual:native:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/meta/recipes-kernel/systemtap/systemtap_git.bb, do_compile) failed with exit code '1'
```

解决：

```c++
* ~/nfs_share/IMX_Platform/IMX6D/sdk *
 alex→ $ find . -name "loc2c.c"
./bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/git/loc2c.c
./bld-fb/tmp/work/cortexa9hf-neon-poky-linux-gnueabi/systemtap/2.9-r0/git/loc2c.c
* ~/nfs_share/IMX_Platform/IMX6D/sdk *
 alex→ $ 
* ~/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/git *
 alex→ $ diff loc2c.c loc2c.c.bak 
2564d2563
<         __attribute__((fallthrough)); //  <- this is added
* ~/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.9-r0/git *
```

参考文章：

https://github.com/ethereum/solidity/issues/2420