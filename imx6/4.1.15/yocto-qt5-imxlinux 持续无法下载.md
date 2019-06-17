imxlinux 由于是git库，下载过慢导致持续无法下载

解决：

运行 bitbake fsl-image-qt5 -c fetchall -vDD

捕捉到log如下：

```c++
DEBUG: linux-imx-4.1.15-r0 do_fetch: Running export DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/1000/bus"; export SSH_AGENT_PID="2860"; export SSH_AUTH_SOCK="/run/user/1000/keyring/ssh"; export PATH="/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/scripts:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/arm-poky-linux-gnueabi:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/imx6dlsabresd/usr/bin/crossscripts:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/sbin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/sbin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/bin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/scripts:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/bitbake/bin:/opt/imx6/arm-4.9-2016.02/bin:/opt/imx6/arm-2014.05/bin:/opt/hisi-linux/x86-arm/arm-hisiv300-linux/target/bin:/usr/local/Trolltech/Qt-4.8.7/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"; export HOME="/home/alex"; /usr/bin/env wget -t 2 -T 30 -nv --passive-ftp --no-check-certificate -P /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/downloads/ 'http://downloads.yoctoproject.org/mirror/sources/git2_git.freescale.com.imx.linux-imx.git.tar.gz'
DEBUG: linux-imx-4.1.15-r0 do_fetch: Mirror fetch failure for url http://downloads.yoctoproject.org/mirror/sources/git2_git.freescale.com.imx.linux-imx.git.tar.gz (original url: git://git.freescale.com/imx/linux-imx.git;protocol=git;branch=imx_4.1.15_2.0.0_ga)
DEBUG: linux-imx-4.1.15-r0 do_fetch: Fetcher failure: Fetch command failed with exit code 8, output:
http://downloads.yoctoproject.org/mirror/sources/git2_git.freescale.com.imx.linux-imx.git.tar.gz:
2019-06-13 12:05:33 ERROR 404: Not Found.

DEBUG: linux-imx-4.1.15-r0 do_fetch: Trying Upstream
DEBUG: linux-imx-4.1.15-r0 do_fetch: Fetcher accessed the network with the command git -c core.fsyncobjectfiles=0 clone --bare --mirror git://git.freescale.com/imx/linux-imx.git /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/downloads//git2/git.freescale.com.imx.linux-imx.git
DEBUG: linux-imx-4.1.15-r0 do_fetch: Running export DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/1000/bus"; export SSH_AGENT_PID="2860"; export SSH_AUTH_SOCK="/run/user/1000/keyring/ssh"; export PATH="/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/scripts:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin/arm-poky-linux-gnueabi:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/imx6dlsabresd/usr/bin/crossscripts:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/sbin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/sbin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/bin:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/scripts:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/bitbake/bin:/opt/imx6/arm-4.9-2016.02/bin:/opt/imx6/arm-2014.05/bin:/opt/hisi-linux/x86-arm/arm-hisiv300-linux/target/bin:/usr/local/Trolltech/Qt-4.8.7/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"; 
export HOME="/home/alex"; 
git -c core.fsyncobjectfiles=0 clone --bare --mirror git://git.freescale.com/imx/linux-imx.git /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/downloads//git2/git.freescale.com.imx.linux-imx.git
```

注意最后一行，给出了当前克隆路径以及目标文件位置和名字等信息。
使用如下命令进行则

参考文章：

https://blog.csdn.net/hesunwen/article/details/89026776