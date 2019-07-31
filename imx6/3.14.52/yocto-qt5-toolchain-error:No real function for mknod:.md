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

