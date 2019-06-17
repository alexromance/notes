报错：没有fetchall选项

解决过程：

grep一下4.1.15文件夹中的do_fetchall选项，

```c++
* ~/nfs_share/IMX_Platform/IMX6D/sdk *
 alex→ $ grep -nr "do_fetchall"
sources/poky/meta/classes/utility-tasks.bbclass:62:do_fetchall[recrdeptask] = "do_fetchall do_fetch"
sources/poky/meta/classes/utility-tasks.bbclass:63:do_fetchall[recideptask] = "do_${BB_DEFAULT_TASK}"
sources/poky/meta/classes/utility-tasks.bbclass:64:do_fetchall() {
sources/poky/meta/conf/documentation.conf:25:do_fetchall[doc] = "Fetches all remote sources required to build a target"
sources/poky/documentation/ref-manual/ref-tasks.xml:558:        <title><filename>do_fetchall</filename></title>
```

打开此文件，发现有此相关的配置，

```c++
* ~/nfs_share/IMX_Platform/IMX6D/sdk *
 alex→ $ tail -10 sources/poky/meta/classes/utility-tasks.bbclass 
do_checkuriall() {
	:
}

addtask fetchall after do_fetch
do_fetchall[recrdeptask] = "do_fetchall do_fetch"
do_fetchall[recideptask] = "do_${BB_DEFAULT_TASK}"
do_fetchall() {
	:
}
```

将此部分配置加入

```c++
{yocto_path}/sources/poky/meta/classes/utility-tasks.bbclass
```

此时，运行bitbake xxxx -c fetchall即可生效。