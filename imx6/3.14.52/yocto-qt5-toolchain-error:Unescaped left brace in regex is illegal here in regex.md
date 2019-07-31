编译报错：

```shell
Unescaped left brace in regex is illegal here in regex
```

报错表现：

```shell
|   GEN   config-all-devices.mak
|   CC    tests/qemu-iotests/socket_scm_helper.o
|   GEN   qemu-options.texi
|   GEN   qemu-monitor.texi
|   GEN   qemu-img-cmds.texi
|   GEN   qemu-tech.html
|   GEN   qemu-img.1
| Unescaped left brace in regex is illegal here in regex; marked by <-- HERE in m/^\@strong{ <-- HERE (.*)}$/ at /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-qemu/2.2.0-r1/qemu-2.2.0/scripts/texi2pod.pl line 320.
```

解决：

还是老样子，替换一下旧的写法即可

```shell
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-qemu/2.2.0-r1/qemu-2.2.0/scripts *
 alex→ $ diff texi2pod.pl texi2pod.pl.bak
320c320
< 	    $column =~ s/^\@strong[{](.*)}$/$1/;
---
> 	    $column =~ s/^\@strong{(.*)}$/$1/;
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-nativesdk-pokysdk-linux/nativesdk-qemu/2.2.0-r1/qemu-2.2.0/scripts *
 alex→ $ 
```