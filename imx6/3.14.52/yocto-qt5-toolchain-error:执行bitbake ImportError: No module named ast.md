编译报错：

```shell
ImportError: No module named ast
```

报错表现：

```shell
* ~/imx6/6d/sdk/bld-fb *
 alex→ $ bitbake -s |grep meta
Traceback (most recent call last):
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/bin/bitbake", line 31, in <module>
    import bb
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/__init__.py", line 77, in <module>
    from bb import fetch2 as fetch
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/fetch2/__init__.py", line 39, in <module>
    from bb import data
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/data.py", line 48, in <module>
    from bb import data_smart
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/data_smart.py", line 35, in <module>
    import bb, bb.codeparser
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/codeparser.py", line 1, in <module>
    import ast
ImportError: No module named ast
/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/event.py:111: RuntimeWarning: Parent module 'bb' not found while handling absolute import
  from bb.msg import BBLogFormatter
Error in atexit._run_exitfuncs:
Traceback (most recent call last):
  File "/opt/fsl-imx-fb/3.14.52-1.1.1/sysroots/x86_64-pokysdk-linux/usr/lib/python2.7/atexit.py", line 24, in _run_exitfuncs
    func(*targs, **kargs)
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/event.py", line 111, in print_ui_queue
    from bb.msg import BBLogFormatter
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/__init__.py", line 77, in <module>
    from bb import fetch2 as fetch
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/fetch2/__init__.py", line 39, in <module>
    from bb import data
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/data.py", line 48, in <module>
    from bb import data_smart
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/data_smart.py", line 35, in <module>
    import bb, bb.codeparser
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/codeparser.py", line 1, in <module>
    import ast
ImportError: No module named ast
Error in sys.exitfunc:
Traceback (most recent call last):
  File "/opt/fsl-imx-fb/3.14.52-1.1.1/sysroots/x86_64-pokysdk-linux/usr/lib/python2.7/atexit.py", line 24, in _run_exitfuncs
    func(*targs, **kargs)
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/event.py", line 111, in print_ui_queue
    from bb.msg import BBLogFormatter
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/__init__.py", line 77, in <module>
    from bb import fetch2 as fetch
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/fetch2/__init__.py", line 39, in <module>
    from bb import data
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/data.py", line 48, in <module>
    from bb import data_smart
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/data_smart.py", line 35, in <module>
    import bb, bb.codeparser
  File "/home/alex/imx6/6d/sdk/sources/poky/bitbake/lib/bb/codeparser.py", line 1, in <module>
    import ast
ImportError: No module named ast
```

解决：

安装python-dev 

参考文章：

https://github.com/lovell/sharp/issues/1087

其中apt-get install python-dev fixed the problem for me.解决问题