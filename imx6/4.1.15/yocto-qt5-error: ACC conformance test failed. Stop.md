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

将{yocto_path}/sources/poky/meta/recipes-support/lzop/lzop/x32_abi_miniacc_h.patch文件内容替换成下面内容：

```c++
Fix get of FLAGS register in x32 ABI,

x32 ABI requires to have 64-bit variable to store FLAGS register
instead of size_t that is 32-bit variable, this fix operand
type mismatch when try to pop previous pushf value.

Upstream-Status: Submitted

Signed-off-by: An铆bal Lim贸n <anibal.limon@linux.intel.com>

Index: lzop-1.03/src/miniacc.h
===================================================================
--- lzop-1.03.orig/src/miniacc.h
+++ lzop-1.03/src/miniacc.h
@@ -754,6 +754,9 @@
 #elif defined(__amd64__) || defined(__x86_64__) || defined(_M_AMD64)
 #  define ACC_ARCH_AMD64            1
 #  define ACC_INFO_ARCH             "amd64"
+#  if defined(__ILP32__)
+#    define ACC_ARCH_AMD64_X32      1
+#  endif
 #elif defined(__thumb__) || (defined(_M_ARM) && defined(_M_THUMB))
 #  define ACC_ARCH_ARM              1
 #  define ACC_ARCH_ARM_THUMB        1
@@ -4469,12 +4469,12 @@
 #if defined(__MSDOS__) && defined(__TURBOC__) && (__TURBOC__ < 0x0150)
 #elif 1 && (ACC_CC_SUNPROC) && !defined(ACCCHK_CFG_PEDANTIC)
 #else
-    ACCCHK_ASSERT((1   << (8*SIZEOF_INT-1)) < 0)
+    ACCCHK_ASSERT((int)(1u   << (8*SIZEOF_INT-1)) < 0)
 #endif
     ACCCHK_ASSERT((1u  << (8*SIZEOF_INT-1)) > 0)
 #if 1 && (ACC_CC_SUNPROC) && !defined(ACCCHK_CFG_PEDANTIC)
 #else
-    ACCCHK_ASSERT((1l  << (8*SIZEOF_LONG-1)) < 0)
+    ACCCHK_ASSERT((long)(1ul  << (8*SIZEOF_LONG-1)) < 0)
 #endif
     ACCCHK_ASSERT((1ul << (8*SIZEOF_LONG-1)) > 0)
 #if defined(acc_int16e_t)
@@ -4703,7 +4703,7 @@
 #elif 1 && (ACC_CC_LCC || ACC_CC_LCCWIN32) && !defined(ACCCHK_CFG_PEDANTIC)
 #elif 1 && (ACC_CC_SUNPROC) && !defined(ACCCHK_CFG_PEDANTIC)
 #elif !(ACC_BROKEN_INTEGRAL_PROMOTION) && (SIZEOF_INT > 1)
-    ACCCHK_ASSERT( (((unsigned char)128) << (int)(8*sizeof(int)-8)) < 0)
+    ACCCHK_ASSERT( (int)((unsigned int)((unsigned char)128) << (int)(8*sizeof(int)-8)) < 0)
 #endif
 #if (ACC_CC_BORLANDC && (__BORLANDC__ >= 0x0530) && (__BORLANDC__ < 0x0560))
 # pragma option pop
@@ -6787,7 +6790,11 @@ ACCLIB_PUBLIC_NOINLINE(void, acc_debug_n
 ACCLIB_PUBLIC_NOINLINE(int, acc_debug_align_check_query) (void)
 {
 #if (ACC_ARCH_AMD64 || ACC_ARCH_I386) && (ACC_ASM_SYNTAX_GNUC)
+#  if defined(ACC_ARCH_AMD64_X32)
+    unsigned long long r;
+#  else
     size_t r;
+#  endif
     __asm__ __volatile__("pushf\n pop %0\n" : "=a" (r) : : __ACC_ASM_CLOBBER);
     return (int)(r >> 18) & 1;
 #elif (ACC_ARCH_I386) && (ACC_ASM_SYNTAX_MSC)
```
参考文章：

https://blog.csdn.net/weixin_42421766/article/details/82983170