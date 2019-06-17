编译报错：error: redefinition of ‘struct __locale_struct

报错表现：

```c++
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from /usr/include/libintl.h:103,
|                  from ../git/localedef/include/libintl.h:2,
|                  from glibc/locale/programs/charmap.c:24:
| glibc/locale/xlocale.h:27:16: error: redefinition of 'struct __locale_struct'
|  typedef struct __locale_struct
|                 ^~~~~~~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/ctype.h:237,
|                  from ../git/localedef/include/ctype.h:2,
|                  from glibc/locale/programs/charmap.c:22:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:28:8: note: originally defined here
|  struct __locale_struct
|         ^~~~~~~~~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from /usr/include/libintl.h:103,
|                  from ../git/localedef/include/libintl.h:2,
|                  from glibc/locale/programs/charmap.c:24:
| glibc/locale/xlocale.h:39:4: error: conflicting types for '__locale_t'
|  } *__locale_t;
|     ^~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/ctype.h:237,
|                  from ../git/localedef/include/ctype.h:2,
|                  from glibc/locale/programs/charmap.c:22:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:42:33: note: previous declaration of '__locale_t' was here
|  typedef struct __locale_struct *__locale_t;
|                                  ^~~~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from /usr/include/libintl.h:103,
|                  from ../git/localedef/include/libintl.h:2,
|                  from glibc/locale/programs/charmap.c:24:
| glibc/locale/xlocale.h:42:20: error: conflicting types for 'locale_t'
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from /usr/include/ctype.h:237:0,
|                  from ../git/localedef/include/ctype.h:2,
|                  from glibc/locale/programs/charmap.c:22:
| /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:24:20: note: previous declaration of 'locale_t' was here
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/string.h:152,
|                  from ../git/localedef/include/string.h:1,
|                  from glibc/locale/programs/ld-address.c:25:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:28:8: error: redefinition of 'struct __locale_struct'
|  struct __locale_struct
|         ^~~~~~~~~~~~~~~
| In file included from glibc/locale/langinfo.h:591:0,
|                  from glibc/locale/programs/ld-address.c:24:
| glibc/locale/xlocale.h:27:16: note: originally defined here
|  typedef struct __locale_struct
|                 ^~~~~~~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/string.h:152,
|                  from ../git/localedef/include/string.h:1,
|                  from glibc/locale/programs/ld-address.c:25:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:42:33: error: conflicting types for '__locale_t'
|  typedef struct __locale_struct *__locale_t;
|                                  ^~~~~~~~~~
| In file included from glibc/locale/langinfo.h:591:0,
|                  from glibc/locale/programs/ld-address.c:24:
| glibc/locale/xlocale.h:39:4: note: previous declaration of '__locale_t' was here
|  } *__locale_t;
|     ^~~~~~~~~~
| In file included from /usr/include/string.h:152:0,
|                  from ../git/localedef/include/string.h:1,
|                  from glibc/locale/programs/ld-address.c:25:
| /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:24:20: error: conflicting types for 'locale_t'
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from glibc/locale/langinfo.h:591:0,
|                  from glibc/locale/programs/ld-address.c:24:
| glibc/locale/xlocale.h:42:20: note: previous declaration of 'locale_t' was here
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/stdlib.h:272,
|                  from glibc/locale/programs/charmap-dir.c:26:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:28:8: error: redefinition of 'struct __locale_struct'
|  struct __locale_struct
|         ^~~~~~~~~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from /usr/include/libintl.h:103,
|                  from ../git/localedef/include/libintl.h:2,
|                  from glibc/locale/programs/charmap-dir.c:21:
| glibc/locale/xlocale.h:27:16: note: originally defined here
|  typedef struct __locale_struct
|                 ^~~~~~~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/stdlib.h:272,
|                  from glibc/locale/programs/charmap-dir.c:26:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:42:33: error: conflicting types for '__locale_t'
|  typedef struct __locale_struct *__locale_t;
|                                  ^~~~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from /usr/include/libintl.h:103,
|                  from ../git/localedef/include/libintl.h:2,
|                  from glibc/locale/programs/charmap-dir.c:21:
| glibc/locale/xlocale.h:39:4: note: previous declaration of '__locale_t' was here
|  } *__locale_t;
|     ^~~~~~~~~~
| In file included from /usr/include/stdlib.h:272:0,
|                  from glibc/locale/programs/charmap-dir.c:26:
| /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:24:20: error: conflicting types for 'locale_t'
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from /usr/include/libintl.h:103,
|                  from ../git/localedef/include/libintl.h:2,
|                  from glibc/locale/programs/charmap-dir.c:21:
| glibc/locale/xlocale.h:42:20: note: previous declaration of 'locale_t' was here
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from glibc/locale/programs/localedef.h:24,
|                  from glibc/locale/programs/ld-collate.c:29:
| glibc/locale/xlocale.h:27:16: error: redefinition of 'struct __locale_struct'
|  typedef struct __locale_struct
|                 ^~~~~~~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/stdlib.h:272,
|                  from glibc/locale/programs/ld-collate.c:24:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:28:8: note: originally defined here
|  struct __locale_struct
|         ^~~~~~~~~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from glibc/locale/programs/localedef.h:24,
|                  from glibc/locale/programs/ld-collate.c:29:
| glibc/locale/xlocale.h:39:4: error: conflicting types for '__locale_t'
|  } *__locale_t;
|     ^~~~~~~~~~
| In file included from /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:22:0,
|                  from /usr/include/stdlib.h:272,
|                  from glibc/locale/programs/ld-collate.c:24:
| /usr/include/x86_64-linux-gnu/bits/types/__locale_t.h:42:33: note: previous declaration of '__locale_t' was here
|  typedef struct __locale_struct *__locale_t;
|                                  ^~~~~~~~~~
| In file included from glibc/locale/locale.h:145:0,
|                  from ../git/localedef/include/locale.h:1,
|                  from glibc/locale/programs/localedef.h:24,
|                  from glibc/locale/programs/ld-collate.c:29:
| glibc/locale/xlocale.h:42:20: error: conflicting types for 'locale_t'
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| In file included from /usr/include/stdlib.h:272:0,
|                  from glibc/locale/programs/ld-collate.c:24:
| /usr/include/x86_64-linux-gnu/bits/types/locale_t.h:24:20: note: previous declaration of 'locale_t' was here
|  typedef __locale_t locale_t;
|                     ^~~~~~~~
| glibc/locale/programs/charmap.c: In function 'charmap_read':
| glibc/locale/programs/charmap.c:202:39: warning: passing argument 1 of '__xpg_basename' discards 'const' qualifier from pointer target type [-Wdiscarded-qualifiers]
|      result->code_set_name = basename (filename);
|                                        ^~~~~~~~
| In file included from ../git/localedef/include/string.h:4:0,
|                  from glibc/locale/programs/charmap.c:28:
| /usr/include/libgen.h:34:14: note: expected 'char *' but argument is of type 'const char *'
|  extern char *__xpg_basename (char *__path) __THROW;
|               ^~~~~~~~~~~~~~
| Makefile:66: recipe for target 'charmap-dir.o' failed
| make: *** [charmap-dir.o] Error 1
| make: *** Waiting for unfinished jobs....
| Makefile:66: recipe for target 'ld-address.o' failed
| make: *** [ld-address.o] Error 1
| Makefile:66: recipe for target 'charmap.o' failed
| make: *** [charmap.o] Error 1
| Makefile:66: recipe for target 'ld-collate.o' failed
| make: *** [ld-collate.o] Error 1
| ERROR: oe_runmake failed
| ERROR: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/cross-localedef-native/2.23-r0/temp/log.do_compile.94639)
```

解决：

在{yocto_path}/yocto/fsl-release-bsp/sources/poky/meta/recipes-core/glibc/cross-localedef-native_2.23.bb的patch文件列表中增加0001-Include-locale_t.h-compatibility-header.patch：

```c++
EGLIBCPATCHES = "\
           file://0016-timezone-re-written-tzselect-as-posix-sh.patch \
           file://0017-Remove-bash-dependency-for-nscd-init-script.patch \
           file://0018-eglibc-Cross-building-and-testing-instructions.patch \
           file://0019-eglibc-Help-bootstrap-cross-toolchain.patch \
           file://0020-eglibc-cherry-picked-from.patch \
           file://0021-eglibc-Clear-cache-lines-on-ppc8xx.patch \
           file://0022-eglibc-Resolve-__fpscr_values-on-SH4.patch \
           file://0023-eglibc-Install-PIC-archives.patch \
           file://0025-eglibc-Forward-port-cross-locale-generation-support.patch \
           file://0001-Include-locale_t.h-compatibility-header.patch \
"
```

在{yocto_path}/sources/poky/meta/recipes-core/glibc/glibc路径下新建文件0001-Include-locale_t.h-compatibility-header.patch，文件内容如下：

```c++
From abfeb0cf4e3261a66a7a23abc9aed33c034c850d Mon Sep 17 00:00:00 2001
From: Joshua Watt <Joshua.Watt@garmin.com>
Date: Wed, 6 Dec 2017 13:26:19 -0600
Subject: [PATCH] Include locale_t.h compatibility header

Newer versions of glibc (since 2.26) moved the locale typedefs from
xlocale.h to bits/types/locale_t.h. Create a compatibility header for
these newer versions of glibc

See f0be25b6336db7492e47d2e8e72eb8af53b5506d in glibc

Upstream-Status: Inappropriate
---
 locale/bits/types/locale_t.h | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 locale/bits/types/locale_t.h

diff --git a/locale/bits/types/locale_t.h b/locale/bits/types/locale_t.h
new file mode 100644
index 0000000000..b519a6c5f8
--- /dev/null
+++ b/locale/bits/types/locale_t.h
@@ -0,0 +1 @@
+#include <xlocale.h>
-- 
2.14.3
```

参考文章：

https://blog.csdn.net/weixin_42421766/article/details/82984648