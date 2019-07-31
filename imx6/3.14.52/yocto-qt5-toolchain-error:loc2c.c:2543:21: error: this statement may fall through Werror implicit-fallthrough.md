编译报错：

```shell
/loc2c.c:2543:21: error: this statement may fall through [-Werror=implicit-fallthrough=]
```

报错表现：

```shell
7+gitAUTOINC+bf16266782-r0/git/'`cache.cxx
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/loc2c.c: In function 'c_emit_location':
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/loc2c.c:2543:21: error: this statement may fall through [-Werror=implicit-fallthrough=]
|   l->address.declare = "addr";
|   ~~~~~~~~~~~~~~~~~~~^~~~~~~~
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/loc2c.c:2544:7: note: here
|        case loc_fragment:
|        ^~~~
| cc1: all warnings being treated as errors
| Makefile:1039: recipe for target 'stap-loc2c.o' failed
| make[2]: *** [stap-loc2c.o] Error 1
| make[2]: *** Waiting for unfinished jobs....
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/tapsets.cxx: In member function 'void dwarf_query::parse_function_spec(const string&)':
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/tapsets.cxx:1202:11: error: this 'if' clause does not guard... [-Werror=misleading-indentation]
|            if (lineno_type != WILDCARD)
|            ^~
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/tapsets.cxx:1236:13: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the 'if'
|              if (has_nearest && lineno_type != ABSOLUTE
|              ^~
| cc1plus: all warnings being treated as errors
| Makefile:1179: recipe for target 'stap-tapsets.o' failed
| make[2]: *** [stap-tapsets.o] Error 1
| make[2]: Leaving directory '/home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/build'
| Makefile:1860: recipe for target 'all-recursive' failed
| make[1]: *** [all-recursive] Error 1
| make[1]: Leaving directory '/home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/build'
| Makefile:667: recipe for target 'all' failed
| make: *** [all] Error 2
| ERROR: oe_runmake failed
| WARNING: exit code 1 from a shell command.
| ERROR: Function failed: do_compile (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/temp/log.do_compile.3191)
ERROR: Task 3982 (virtual:native:/home/alex/imx6/6d/sdk/sources/poky/meta/recipes-kernel/systemtap/systemtap_git.bb, do_compile) failed with exit code '1'
```

解决：

先删掉此次出错的binuntils包的stamp文件中的doconfigure 和do complie ，然后去掉-Werror选项

```shell
find . -iname "makefile*" | xargs sed -i "s/-Werror//g"
```

