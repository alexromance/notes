编译报错：

```shell
ERROR: Function failed: license_create_manifest
```

报错表现：

```shell
| Try 'basename --help' for more information.
| WARNING: exit code 1 from a shell command.
| DEBUG: Python function do_rootfs finished
| ERROR: Function failed: license_create_manifest (log file is located at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/imx6dlsabresd-poky-linux-gnueabi/fsl-image-qt5/1.0-r0/temp/log.do_rootfs.2871)
```

参考：

change dash to bash

**注意并未解决！**

参考文章：

http://e2e.ti.com/support/legacy_forums/embedded/linux/f/354/t/577042