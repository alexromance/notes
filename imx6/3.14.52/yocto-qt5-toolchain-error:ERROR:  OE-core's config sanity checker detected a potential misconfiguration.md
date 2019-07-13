刚开始运行bitbake就出现了问题

编译报错：

ERROR:  OE-core's config sanity checker detected a potential misconfiguration.

报错表现：


```shell
* ~/imx6/6d/sdk/bld-fb *
 alex→ $ bitbake -s | grep meta
ERROR:  OE-core's config sanity checker detected a potential misconfiguration.
    Either fix the cause of this error or at your own risk disable the checker (see sanity.conf).
    Following is the list of potential problems / advisories:

    libsdl-native is set to be ASSUME_PROVIDED but sdl-config can't be found in PATH. Please either install it, or configure qemu not to require sdl.
* ~/imx6/6d/sdk/bld-fb *
 alex→ $ 
```

解决：

无脑安装libsdl

```shell
sudo apt install libsdl-image1.2-dev
```




