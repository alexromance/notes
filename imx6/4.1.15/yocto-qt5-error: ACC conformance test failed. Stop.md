编译报错：error: ACC conformance test failed. Stop.

报错表现：

```c++
| checking whether your compiler passes the ACC conformance test... FAILED
| configure:
| configure: Your compiler failed the ACC conformance test - for details see
| configure: `config.log'. Please check that log file and consider sending
| configure: a patch or bug-report to <lzop-bugs@oberhumer.com>.
| configure: Thanks for your support.
| configure:
| configure: error: ACC conformance test failed. Stop.
| NOTE: The following config.log files may provide further information.
| NOTE: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/lzop-native/1.03-r0/build/config.log
| ERROR: configure failed
| ERROR: Function failed: do_configure (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/lzop-native/1.03-r0/temp/log.do_configure.67700)
```

解决：

