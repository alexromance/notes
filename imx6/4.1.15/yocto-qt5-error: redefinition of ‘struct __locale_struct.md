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

