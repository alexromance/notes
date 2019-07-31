编译报错：

No real function for mknod:

报错表现：

```shell
| NOTE: Executing license_create_manifest ...
| DEBUG: Executing shell function license_create_manifest
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| ls: cannot access '/home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/imx6dlsabresd/pkgdata/runtime-reverse/No': No such file or directory
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| No real function for mknod: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknod
| No real function for mknodat: /home/alex/imx6/6d/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/../lib/pseudo/lib64/libpseudo.so: undefined symbol: mknodat
| readlink: missing operand
| Try 'readlink --help' for more information.
```

参考：

打入gcc6的一个patch

```shell
* ~/imx6/6d/sdk *
 alex→ $ find . -name "pseudo_wrappers.c" | xargs grep -nr "pseudo_diag"
./bld-fb/tmp/work/x86_64-linux/pseudo-native/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:123:			pseudo_diag("No real function for %s: %s\n", func->name, e);
./bld-fb/tmp/work/x86_64-linux/pseudo-native/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:211:	pseudo_diag("pseudo: ENOSYS for '%s'.\n", func ? func : "<nil>");
./bld-fb/tmp/work/x86_64-linux/pseudo-native/1.6.4-r0/pseudo-1.6.4/ports/linux/xattr/pseudo_wrappers.c:65:		pseudo_diag("Fatal: ACL support no available for header version %d.\n",
./bld-fb/tmp/work/x86_64-linux/pseudo-native/1.6.4-r0/pseudo-1.6.4/ports/darwin/pseudo_wrappers.c:87:		pseudo_diag("Fatal: ACL support no available for header version %d.\n",
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/package/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:123:			pseudo_diag("No real function for %s: %s\n", func->name, e);
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/package/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:211:	pseudo_diag("pseudo: ENOSYS for '%s'.\n", func ? func : "<nil>");
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/package/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/ports/linux/xattr/pseudo_wrappers.c:65:		pseudo_diag("Fatal: ACL support no available for header version %d.\n",
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:123:			pseudo_diag("No real function for %s: %s\n", func->name, e);
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:211:	pseudo_diag("pseudo: ENOSYS for '%s'.\n", func ? func : "<nil>");
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/ports/linux/xattr/pseudo_wrappers.c:65:		pseudo_diag("Fatal: ACL support no available for header version %d.\n",
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/ports/darwin/pseudo_wrappers.c:87:		pseudo_diag("Fatal: ACL support no available for header version %d.\n",
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/packages-split/nativesdk-pseudo-dbg/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:123:			pseudo_diag("No real function for %s: %s\n", func->name, e);
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/packages-split/nativesdk-pseudo-dbg/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/pseudo_wrappers.c:211:	pseudo_diag("pseudo: ENOSYS for '%s'.\n", func ? func : "<nil>");
./bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/packages-split/nativesdk-pseudo-dbg/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4/ports/linux/xattr/pseudo_wrappers.c:65:	pseudo_diag("Fatal: ACL support no available for header version %d.\n",
* ~/imx6/6d/sdk *

 alex→ $ diff pseudo_wrappers.c pseudo_wrappers.c.bak
122c122
< 		/*if (e != NULL) {
---
> 		if (e != NULL) {
124c124
< 		}*/
---
> 		}
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/pseudo-native/1.6.4-r0/pseudo-1.6.4 *
 alex→ $ 

* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/package/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4 *
 alex→ $ diff pseudo_wrappers.c pseudo_wrappers.c.bak
122c122
< 		/*if (e != NULL) {
---
> 		if (e != NULL) {
124c124
< 		}*/
---
> 		}
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-pseudo/1.6.4-r0/package/usr/src/debug/nativesdk-pseudo/1.6.4-r0/pseudo-1.6.4 *
 alex→ $ 
```

**注意并没有解决！**

