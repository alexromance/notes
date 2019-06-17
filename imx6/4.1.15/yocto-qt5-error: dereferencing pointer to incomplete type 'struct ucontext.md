编译报错：error: dereferencing pointer to incomplete type 'struct ucontext'


报错现象：


```c++
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c: In function 'cpu_resume_from_signal':
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:72:37: error: dereferencing pointer to incomplete type 'struct ucontext'
|          sigprocmask(SIG_SETMASK, &uc->uc_sigmask, NULL);
|                                      ^~
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c: In function 'cpu_arm_signal_handler':
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:214:41: error: dereferencing pointer to incomplete type 'struct ucontext'
|  #define PC_sig(context)       ((context)->uc_mcontext.gregs[REG_RIP])
|                                          ^
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:233:10: note: in expansion of macro 'PC_sig'
|      pc = PC_sig(uc);
|           ^~~~~~
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:238:1: warning: control reaches end of non-void function [-Wreturn-type]
|  }
|  ^
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/rules.mak:57: recipe for target 'user-exec.o' failed
| make[1]: *** [user-exec.o] Error 1
| Makefile:184: recipe for target 'subdir-aarch64-linux-user' failed
| make: *** [subdir-aarch64-linux-user] Error 2
| make: *** Waiting for unfinished jobs....
|   CC    arm-linux-user/thunk.o
|   CC    aarch64-softmmu/disas.o
|   CC    arm-softmmu/disas.o
|   CC    arm-linux-user/user-exec.o
|   GEN   aarch64-softmmu/gdbstub-xml.c
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c: In function 'cpu_resume_from_signal':
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:72:37: error: dereferencing pointer to incomplete type 'struct ucontext'
|          sigprocmask(SIG_SETMASK, &uc->uc_sigmask, NULL);
|                                      ^~
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c: In function 'cpu_arm_signal_handler':
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:214:41: error: dereferencing pointer to incomplete type 'struct ucontext'
|  #define PC_sig(context)       ((context)->uc_mcontext.gregs[REG_RIP])
|                                          ^
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:233:10: note: in expansion of macro 'PC_sig'
|      pc = PC_sig(uc);
|           ^~~~~~
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/user-exec.c:238:1: warning: control reaches end of non-void function [-Wreturn-type]
|  }
|  ^
| /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0/rules.mak:57: recipe for target 'user-exec.o' failed
| make[1]: *** [user-exec.o] Error 1
| Makefile:184: recipe for target 'subdir-arm-linux-user' failed
| make: *** [subdir-arm-linux-user] Error 2
```


解决：


This is actually not a GCC issue, but libc6-dev - it received some refactoring of name-spaces. Just replace 'struct ucontext' with 'ucontext_t' and it will compile.
In my current (Debian sid) system I also had to add '--disable-xen' to the build-script and remove compilation of the documentation - which might just be due to some odd local setup, bu then again, those parts are just not essential.

Concerning the alternatives, kAFL is an impressive approach, but I spent a few months on/off to get it to work. Though in Nov they also added some documentation for setup, which would've save me heaps of time. Considering all the custom extensions they did, I am very pessimistic on the long-term usability of kAFL.


```c++
* ~/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0 *
 alex→ $ diff user-exec.c user-exec.c.bak 
61c61
<     ucontext_t *uc = puc;
---
>     struct ucontext *uc = puc;
175c175
<     ucontext_t *uc = puc;
---
>     struct ucontext *uc = puc;
230c230
<     ucontext_t *uc = puc;
---
>     struct ucontext *uc = puc;
* ~/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/qemu-native/2.5.0-r1/qemu-2.5.0 *
```


参考文章：


https://github.com/nccgroup/TriforceAFL/issues/4