编译报错： error: conflicting types for 'copy_file_range

报错表现：

```c++
ERROR: e2fsprogs-native-1.42.99+1.43+gitAUTOINC+0f26747167-r0 do_compile: oe_runmake failed
ERROR: e2fsprogs-native-1.42.99+1.43+gitAUTOINC+0f26747167-r0 do_compile: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/temp/log.do_compile.111805)
ERROR: Logfile of failure stored in: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/temp/log.do_compile.111805
Log data follows:
| DEBUG: Executing shell function do_compile
| NOTE: make -j 2
| cd ./util ; make subst
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/util'
| echo "/* fake dirpaths.h for config.h */" > dirpaths.h
| gcc  -c -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -DHAVE_CONFIG_H ../../git/util/subst.c -o subst.o
| gcc  -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 -o subst subst.o
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/util'
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[1]: 'util/subst.conf' is up to date.
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[1]: 'lib/config.h' is up to date.
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| ./util/subst -f ./util/subst.conf ../git/lib/dirpaths.h.in lib/dirpaths.h
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| cd .; CONFIG_FILES=./lib/ext2fs/ext2_types.h ./config.status
| config.status: creating ./lib/ext2fs/ext2_types.h
| config.status: creating lib/config.h
| config.status: lib/config.h is unchanged
| config.status: executing po-directories commands
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| ../../util/subst -f ../../util/subst.conf ../../../git/lib/et/compile_et.sh.in compile_et
| /bin/chmod +x compile_et
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| ../../util/subst -f ../../util/subst.conf ../../../git/lib/ext2fs/ext2_err.et.in ext2_err.et
| ../et/compile_et --build-tree ext2_err.et
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| make libs
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'util/subst.conf' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'lib/config.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'lib/dirpaths.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'lib/ext2fs/ext2_types.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[2]: 'compile_et' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| make[2]: 'ext2_err.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| making all in lib/et
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make -s real-subdirs
| make[3]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[3]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| touch subdirs
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/et/error_message.c -o error_message.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/et/et_name.c -o et_name.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/et_name.o -c ../../../git/lib/et/et_name.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/et/init_et.c -o init_et.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/error_message.o -c ../../../git/lib/et/error_message.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/init_et.o -c ../../../git/lib/et/init_et.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/et/com_err.c -o com_err.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/et/com_right.c -o com_right.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/com_err.o -c ../../../git/lib/et/com_err.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/com_right.o -c ../../../git/lib/et/com_right.c
| (cd elfshared; gcc  --shared -o libcom_err.so.2.1 \
| 	-L../../../lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 \
| 	-Wl,-soname,libcom_err.so.2 error_message.o et_name.o init_et.o com_err.o com_right.o -lpthread)
| (if test -r libcom_err.a; then /bin/rm -f libcom_err.a.bak && /bin/mv libcom_err.a libcom_err.a.bak; fi)
| /bin/mv elfshared/libcom_err.so.2.1 .
| ar rc libcom_err.a error_message.o et_name.o init_et.o com_err.o com_right.o
| /bin/rm -f ../libcom_err.so.2.1 ../libcom_err.so ../libcom_err.so.2
| (cd ..; /bin/ln  \
| 	`echo lib/et | sed -e 's;lib/;;'`/libcom_err.so.2.1 libcom_err.so.2.1)
| /bin/rm -f ../libcom_err.a
| (cd ..; /bin/ln  \
| 	`echo lib/et | sed -e 's;lib/;;'`/libcom_err.a libcom_err.a)
| (cd ..; /bin/ln  libcom_err.so.2.1 libcom_err.so)
| (cd ..; /bin/ln  libcom_err.so.2.1 libcom_err.so.2)
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| making all in lib/ss
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ss'
| make -s real-subdirs
| ../../util/subst -f ../../util/subst.conf ../../../git/lib/ss/mk_cmds.sh.in mk_cmds
| /bin/chmod +x mk_cmds
| make[3]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ss'
| ../et/compile_et --build-tree ../../../git/lib/ss/ss_err.et
| make[3]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ss'
| touch subdirs
| DIR=../../../git/lib/ss _SS_DIR_OVERRIDE=. ./mk_cmds ../../../git/lib/ss/std_rqs.ct
| ../et/compile_et --build-tree ../../../git/lib/ss/ss_err.et
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ss_err.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/ss_err.o -c ss_err.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c std_rqs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/invocation.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/std_rqs.o -c std_rqs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/help.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/invocation.o -c ../../../git/lib/ss/invocation.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/help.o -c ../../../git/lib/ss/help.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/execute_cmd.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/execute_cmd.o -c ../../../git/lib/ss/execute_cmd.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/listen.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/listen.o -c ../../../git/lib/ss/listen.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/parse.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/parse.o -c ../../../git/lib/ss/parse.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/error.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/error.o -c ../../../git/lib/ss/error.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/prompt.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/request_tbl.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/prompt.o -c ../../../git/lib/ss/prompt.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/request_tbl.o -c ../../../git/lib/ss/request_tbl.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/list_rqs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/pager.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/list_rqs.o -c ../../../git/lib/ss/list_rqs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/pager.o -c ../../../git/lib/ss/pager.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/requests.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/data.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/data.o -c ../../../git/lib/ss/data.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/requests.o -c ../../../git/lib/ss/requests.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ss/get_readline.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -DSHARED_ELF_LIB -fPIC -o elfshared/get_readline.o -c ../../../git/lib/ss/get_readline.c
| (if test -r libss.a; then /bin/rm -f libss.a.bak && /bin/mv libss.a libss.a.bak; fi)
| (cd elfshared; gcc  --shared -o libss.so.2.0 \
| 	-L../../../lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 \
| 	-Wl,-soname,libss.so.2 ss_err.o std_rqs.o invocation.o help.o execute_cmd.o listen.o parse.o error.o prompt.o request_tbl.o list_rqs.o pager.o requests.o data.o get_readline.o -lcom_err -ldl)
| ar rc libss.a ss_err.o std_rqs.o invocation.o help.o execute_cmd.o listen.o parse.o error.o prompt.o request_tbl.o list_rqs.o pager.o requests.o data.o get_readline.o
| /bin/rm -f ../libss.a
| /bin/mv elfshared/libss.so.2.0 .
| (cd ..; /bin/ln  \
| 	`echo lib/ss | sed -e 's;lib/;;'`/libss.a libss.a)
| /bin/rm -f ../libss.so.2.0 ../libss.so ../libss.so.2
| (cd ..; /bin/ln  \
| 	`echo lib/ss | sed -e 's;lib/;;'`/libss.so.2.0 libss.so.2.0)
| (cd ..; /bin/ln  libss.so.2.0 libss.so)
| (cd ..; /bin/ln  libss.so.2.0 libss.so.2)
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ss'
| making all in lib/e2p
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/e2p'
| make -s real-subdirs
| make[3]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/e2p'
| make[3]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/e2p'
| touch subdirs
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/fgetflags.c -o fgetflags.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/feature.c -o feature.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/fgetflags.o -c ../../../git/lib/e2p/fgetflags.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/fsetflags.c -o fsetflags.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/fsetflags.o -c ../../../git/lib/e2p/fsetflags.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/fgetversion.c -o fgetversion.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/feature.o -c ../../../git/lib/e2p/feature.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/fgetversion.o -c ../../../git/lib/e2p/fgetversion.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/fsetversion.c -o fsetversion.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/getflags.c -o getflags.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/getflags.o -c ../../../git/lib/e2p/getflags.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/fsetversion.o -c ../../../git/lib/e2p/fsetversion.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/getversion.c -o getversion.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/hashstr.c -o hashstr.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/getversion.o -c ../../../git/lib/e2p/getversion.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/iod.c -o iod.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/hashstr.o -c ../../../git/lib/e2p/hashstr.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/iod.o -c ../../../git/lib/e2p/iod.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/ls.c -o ls.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/mntopts.c -o mntopts.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/mntopts.o -c ../../../git/lib/e2p/mntopts.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ls.o -c ../../../git/lib/e2p/ls.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/parse_num.c -o parse_num.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/parse_num.o -c ../../../git/lib/e2p/parse_num.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/pe.c -o pe.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/pf.c -o pf.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/pe.o -c ../../../git/lib/e2p/pe.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/pf.o -c ../../../git/lib/e2p/pf.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/ps.c -o ps.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ps.o -c ../../../git/lib/e2p/ps.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/setflags.c -o setflags.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/setflags.o -c ../../../git/lib/e2p/setflags.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/setversion.c -o setversion.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/uuid.c -o uuid.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/setversion.o -c ../../../git/lib/e2p/setversion.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/uuid.o -c ../../../git/lib/e2p/uuid.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/ostype.c -o ostype.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/percent.c -o percent.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ostype.o -c ../../../git/lib/e2p/ostype.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/percent.o -c ../../../git/lib/e2p/percent.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/e2p/crypto_mode.c -o crypto_mode.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/crypto_mode.o -c ../../../git/lib/e2p/crypto_mode.c
| (cd elfshared; gcc  --shared -o libe2p.so.2.3 \
| 	-L../../../lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 \
| 	-Wl,-soname,libe2p.so.2 feature.o fgetflags.o fsetflags.o fgetversion.o fsetversion.o getflags.o getversion.o hashstr.o iod.o ls.o mntopts.o parse_num.o pe.o pf.o ps.o setflags.o setversion.o uuid.o ostype.o percent.o crypto_mode.o )
| (if test -r libe2p.a; then /bin/rm -f libe2p.a.bak && /bin/mv libe2p.a libe2p.a.bak; fi)
| ar rc libe2p.a feature.o fgetflags.o fsetflags.o fgetversion.o fsetversion.o getflags.o getversion.o hashstr.o iod.o ls.o mntopts.o parse_num.o pe.o pf.o ps.o setflags.o setversion.o uuid.o ostype.o percent.o crypto_mode.o
| /bin/rm -f ../libe2p.a
| (cd ..; /bin/ln  \
| 	`echo lib/e2p | sed -e 's;lib/;;'`/libe2p.a libe2p.a)
| /bin/mv elfshared/libe2p.so.2.3 .
| /bin/rm -f ../libe2p.so.2.3 ../libe2p.so ../libe2p.so.2
| (cd ..; /bin/ln  \
| 	`echo lib/e2p | sed -e 's;lib/;;'`/libe2p.so.2.3 libe2p.so.2.3)
| (cd ..; /bin/ln  libe2p.so.2.3 libe2p.so)
| (cd ..; /bin/ln  libe2p.so.2.3 libe2p.so.2)
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/e2p'
| making all in lib/support
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/support'
| make -s real-subdirs
| touch subdirs
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/plausible.c -o plausible.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/mkquota.c -o mkquota.o
| ../../lib/et/compile_et --build-tree ../../../git/lib/support/prof_err.et
| ../../lib/et/compile_et --build-tree ../../../git/lib/support/prof_err.et
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/quotaio.c -o quotaio.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/quotaio_v2.c -o quotaio_v2.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/quotaio_tree.c -o quotaio_tree.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/dict.c -o dict.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/profile.c -o profile.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/support/profile_helpers.c -o profile_helpers.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c prof_err.c -o prof_err.o
| (if test -r libsupport.a; then /bin/rm -f libsupport.a.bak && /bin/mv libsupport.a libsupport.a.bak; fi)
| ar rc libsupport.a mkquota.o plausible.o profile.o profile_helpers.o prof_err.o quotaio.o quotaio_v2.o quotaio_tree.o dict.o
| /bin/rm -f ../libsupport.a
| (cd ..; /bin/ln  \
| 	`echo lib/support | sed -e 's;lib/;;'`/libsupport.a libsupport.a)
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/support'
| making all in lib/ext2fs
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| make -s real-subdirs
| gcc  -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -DHAVE_CONFIG_H -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 -o gen_crc32ctable \
| 	../../../git/lib/ext2fs/gen_crc32ctable.c
| make[3]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| make[3]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| touch subdirs
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/bb_compat.c -o bb_compat.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/inode_io.c -o inode_io.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/bb_compat.o -c ../../../git/lib/ext2fs/bb_compat.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/inode_io.o -c ../../../git/lib/ext2fs/inode_io.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/write_bb_file.c -o write_bb_file.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/write_bb_file.o -c ../../../git/lib/ext2fs/write_bb_file.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/dupfs.c -o dupfs.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/imager.c -o imager.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/dupfs.o -c ../../../git/lib/ext2fs/dupfs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/imager.o -c ../../../git/lib/ext2fs/imager.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/test_io.c -o test_io.o
| In file included from ../../../git/lib/ext2fs/ext2_fs.h:19:0,
|                  from ../../../git/lib/ext2fs/test_io.c:35:
| ../../lib/ext2fs/ext2_types.h:184:0: warning: "__bitwise" redefined
|  #define __bitwise
| 
| In file included from /usr/include/linux/prctl.h:5:0,
|                  from /usr/include/x86_64-linux-gnu/sys/prctl.h:22,
|                  from ../../../git/lib/ext2fs/test_io.c:27:
| /usr/include/linux/types.h:22:0: note: this is the location of the previous definition
|  #define __bitwise __bitwise__
| 
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ext2_err.c -o ext2_err.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ext2_err.o -c ext2_err.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/alloc.c -o alloc.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/test_io.o -c ../../../git/lib/ext2fs/test_io.c
| In file included from ../../../git/lib/ext2fs/ext2_fs.h:19:0,
|                  from ../../../git/lib/ext2fs/test_io.c:35:
| ../../lib/ext2fs/ext2_types.h:184:0: warning: "__bitwise" redefined
|  #define __bitwise
| 
| In file included from /usr/include/linux/prctl.h:5:0,
|                  from /usr/include/x86_64-linux-gnu/sys/prctl.h:22,
|                  from ../../../git/lib/ext2fs/test_io.c:27:
| /usr/include/linux/types.h:22:0: note: this is the location of the previous definition
|  #define __bitwise __bitwise__
| 
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/alloc.o -c ../../../git/lib/ext2fs/alloc.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/alloc_sb.c -o alloc_sb.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/alloc_sb.o -c ../../../git/lib/ext2fs/alloc_sb.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/alloc_stats.c -o alloc_stats.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/alloc_tables.c -o alloc_tables.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/alloc_stats.o -c ../../../git/lib/ext2fs/alloc_stats.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/atexit.c -o atexit.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/alloc_tables.o -c ../../../git/lib/ext2fs/alloc_tables.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/atexit.o -c ../../../git/lib/ext2fs/atexit.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/badblocks.c -o badblocks.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/bb_inode.c -o bb_inode.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/badblocks.o -c ../../../git/lib/ext2fs/badblocks.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/bb_inode.o -c ../../../git/lib/ext2fs/bb_inode.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/bitmaps.c -o bitmaps.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/bitops.c -o bitops.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/bitmaps.o -c ../../../git/lib/ext2fs/bitmaps.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/bitops.o -c ../../../git/lib/ext2fs/bitops.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/blkmap64_rb.c -o blkmap64_rb.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/blkmap64_ba.c -o blkmap64_ba.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/blkmap64_ba.o -c ../../../git/lib/ext2fs/blkmap64_ba.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/blkmap64_rb.o -c ../../../git/lib/ext2fs/blkmap64_rb.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/blknum.c -o blknum.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/block.c -o block.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/blknum.o -c ../../../git/lib/ext2fs/blknum.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/block.o -c ../../../git/lib/ext2fs/block.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/bmap.c -o bmap.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/check_desc.c -o check_desc.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/bmap.o -c ../../../git/lib/ext2fs/bmap.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/check_desc.o -c ../../../git/lib/ext2fs/check_desc.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/closefs.c -o closefs.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/crc16.c -o crc16.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/crc16.o -c ../../../git/lib/ext2fs/crc16.c
| ./gen_crc32ctable > crc32c_table.h
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/closefs.o -c ../../../git/lib/ext2fs/closefs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/csum.c -o csum.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/dblist.c -o dblist.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/csum.o -c ../../../git/lib/ext2fs/csum.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/dblist.o -c ../../../git/lib/ext2fs/dblist.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/dblist_dir.c -o dblist_dir.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/dirblock.c -o dirblock.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/dblist_dir.o -c ../../../git/lib/ext2fs/dblist_dir.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/dirblock.o -c ../../../git/lib/ext2fs/dirblock.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/dirhash.c -o dirhash.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/dir_iterate.c -o dir_iterate.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/dirhash.o -c ../../../git/lib/ext2fs/dirhash.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/dir_iterate.o -c ../../../git/lib/ext2fs/dir_iterate.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/expanddir.c -o expanddir.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/ext_attr.c -o ext_attr.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/expanddir.o -c ../../../git/lib/ext2fs/expanddir.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/extent.c -o extent.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ext_attr.o -c ../../../git/lib/ext2fs/ext_attr.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/extent.o -c ../../../git/lib/ext2fs/extent.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/fallocate.c -o fallocate.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/fileio.c -o fileio.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/fileio.o -c ../../../git/lib/ext2fs/fileio.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/fallocate.o -c ../../../git/lib/ext2fs/fallocate.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/finddev.c -o finddev.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/flushb.c -o flushb.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/finddev.o -c ../../../git/lib/ext2fs/finddev.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/flushb.o -c ../../../git/lib/ext2fs/flushb.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/freefs.c -o freefs.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/gen_bitmap.c -o gen_bitmap.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/freefs.o -c ../../../git/lib/ext2fs/freefs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/gen_bitmap64.c -o gen_bitmap64.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/gen_bitmap.o -c ../../../git/lib/ext2fs/gen_bitmap.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/gen_bitmap64.o -c ../../../git/lib/ext2fs/gen_bitmap64.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/get_num_dirs.c -o get_num_dirs.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/get_pathname.c -o get_pathname.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/get_num_dirs.o -c ../../../git/lib/ext2fs/get_num_dirs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/getsize.c -o getsize.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/get_pathname.o -c ../../../git/lib/ext2fs/get_pathname.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/getsize.o -c ../../../git/lib/ext2fs/getsize.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/getsectsize.c -o getsectsize.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/i_block.c -o i_block.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/getsectsize.o -c ../../../git/lib/ext2fs/getsectsize.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/i_block.o -c ../../../git/lib/ext2fs/i_block.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/icount.c -o icount.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/ind_block.c -o ind_block.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ind_block.o -c ../../../git/lib/ext2fs/ind_block.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/icount.o -c ../../../git/lib/ext2fs/icount.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/initialize.c -o initialize.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/inline.c -o inline.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/initialize.o -c ../../../git/lib/ext2fs/initialize.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/inline.o -c ../../../git/lib/ext2fs/inline.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/inline_data.c -o inline_data.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/inode.c -o inode.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/inline_data.o -c ../../../git/lib/ext2fs/inline_data.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/io_manager.c -o io_manager.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/inode.o -c ../../../git/lib/ext2fs/inode.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/io_manager.o -c ../../../git/lib/ext2fs/io_manager.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/ismounted.c -o ismounted.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/link.c -o link.o
| In file included from ../../../git/lib/ext2fs/ext2_fs.h:19:0,
|                  from ../../../git/lib/ext2fs/ismounted.c:42:
| ../../lib/ext2fs/ext2_types.h:184:0: warning: "__bitwise" redefined
|  #define __bitwise
| 
| In file included from /usr/include/linux/loop.h:29:0,
|                  from ../../../git/lib/ext2fs/ismounted.c:25:
| /usr/include/linux/types.h:22:0: note: this is the location of the previous definition
|  #define __bitwise __bitwise__
| 
| ../../../git/lib/ext2fs/ismounted.c: In function 'check_loop_mounted':
| ../../../git/lib/ext2fs/ismounted.c:58:13: warning: In the GNU C Library, "major" is defined
|  by <sys/sysmacros.h>. For historical compatibility, it is
|  currently defined by <sys/types.h> as well, but we plan to
|  remove this soon. To use "major", include <sys/sysmacros.h>
|  directly. If you did not intend to use a system-defined macro
|  "major", you should undefine it after including <sys/types.h>.
|   if (major(mnt_rdev) == LOOP_MAJOR) {
|              ^~~~~~~~~~~~~~~~~~~~~~~~~
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/link.o -c ../../../git/lib/ext2fs/link.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/llseek.c -o llseek.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/llseek.o -c ../../../git/lib/ext2fs/llseek.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/ismounted.o -c ../../../git/lib/ext2fs/ismounted.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/lookup.c -o lookup.o
| In file included from ../../../git/lib/ext2fs/ext2_fs.h:19:0,
|                  from ../../../git/lib/ext2fs/ismounted.c:42:
| ../../lib/ext2fs/ext2_types.h:184:0: warning: "__bitwise" redefined
|  #define __bitwise
| 
| In file included from /usr/include/linux/loop.h:29:0,
|                  from ../../../git/lib/ext2fs/ismounted.c:25:
| /usr/include/linux/types.h:22:0: note: this is the location of the previous definition
|  #define __bitwise __bitwise__
| 
| ../../../git/lib/ext2fs/ismounted.c: In function 'check_loop_mounted':
| ../../../git/lib/ext2fs/ismounted.c:58:13: warning: In the GNU C Library, "major" is defined
|  by <sys/sysmacros.h>. For historical compatibility, it is
|  currently defined by <sys/types.h> as well, but we plan to
|  remove this soon. To use "major", include <sys/sysmacros.h>
|  directly. If you did not intend to use a system-defined macro
|  "major", you should undefine it after including <sys/types.h>.
|   if (major(mnt_rdev) == LOOP_MAJOR) {
|              ^~~~~~~~~~~~~~~~~~~~~~~~~
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/lookup.o -c ../../../git/lib/ext2fs/lookup.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/mkdir.c -o mkdir.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/mkjournal.c -o mkjournal.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/mkdir.o -c ../../../git/lib/ext2fs/mkdir.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/mkjournal.o -c ../../../git/lib/ext2fs/mkjournal.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/mmp.c -o mmp.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/mmp.o -c ../../../git/lib/ext2fs/mmp.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/namei.c -o namei.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/namei.o -c ../../../git/lib/ext2fs/namei.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/native.c -o native.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/native.o -c ../../../git/lib/ext2fs/native.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/newdir.c -o newdir.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/openfs.c -o openfs.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/newdir.o -c ../../../git/lib/ext2fs/newdir.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/progress.c -o progress.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/openfs.o -c ../../../git/lib/ext2fs/openfs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/progress.o -c ../../../git/lib/ext2fs/progress.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/punch.c -o punch.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/qcow2.c -o qcow2.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/punch.o -c ../../../git/lib/ext2fs/punch.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/qcow2.o -c ../../../git/lib/ext2fs/qcow2.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/read_bb.c -o read_bb.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/read_bb_file.c -o read_bb_file.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/read_bb.o -c ../../../git/lib/ext2fs/read_bb.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/read_bb_file.o -c ../../../git/lib/ext2fs/read_bb_file.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/res_gdt.c -o res_gdt.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/rw_bitmaps.c -o rw_bitmaps.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/res_gdt.o -c ../../../git/lib/ext2fs/res_gdt.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/sha512.c -o sha512.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/rw_bitmaps.o -c ../../../git/lib/ext2fs/rw_bitmaps.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/sha512.o -c ../../../git/lib/ext2fs/sha512.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/swapfs.c -o swapfs.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/swapfs.o -c ../../../git/lib/ext2fs/swapfs.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/symlink.c -o symlink.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/tdb.c -o tdb.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/symlink.o -c ../../../git/lib/ext2fs/symlink.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/undo_io.c -o undo_io.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/undo_io.o -c ../../../git/lib/ext2fs/undo_io.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/unix_io.c -o unix_io.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/tdb.o -c ../../../git/lib/ext2fs/tdb.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/unix_io.o -c ../../../git/lib/ext2fs/unix_io.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/unlink.c -o unlink.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/unlink.o -c ../../../git/lib/ext2fs/unlink.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/valid_blk.c -o valid_blk.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/valid_blk.o -c ../../../git/lib/ext2fs/valid_blk.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/version.c -o version.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/rbtree.c -o rbtree.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/version.o -c ../../../git/lib/ext2fs/version.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -c ../../../git/lib/ext2fs/crc32c.c -o crc32c.o
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/rbtree.o -c ../../../git/lib/ext2fs/rbtree.c
| gcc  -I. -I../../lib -I../../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  -fPIC -o elfshared/crc32c.o -c ../../../git/lib/ext2fs/crc32c.c
| (if test -r libext2fs.a; then /bin/rm -f libext2fs.a.bak && /bin/mv libext2fs.a libext2fs.a.bak; fi)
| ar rc libext2fs.a bb_compat.o inode_io.o write_bb_file.o dupfs.o imager.o test_io.o ext2_err.o alloc.o alloc_sb.o alloc_stats.o alloc_tables.o atexit.o badblocks.o bb_inode.o bitmaps.o bitops.o blkmap64_ba.o blkmap64_rb.o blknum.o block.o bmap.o check_desc.o closefs.o crc16.o crc32c.o csum.o dblist.o dblist_dir.o dirblock.o dirhash.o dir_iterate.o expanddir.o ext_attr.o extent.o fallocate.o fileio.o finddev.o flushb.o freefs.o gen_bitmap.o gen_bitmap64.o get_num_dirs.o get_pathname.o getsize.o getsectsize.o i_block.o icount.o ind_block.o initialize.o inline.o inline_data.o inode.o io_manager.o ismounted.o link.o llseek.o lookup.o mkdir.o mkjournal.o mmp.o namei.o native.o newdir.o openfs.o progress.o punch.o qcow2.o read_bb.o read_bb_file.o res_gdt.o rw_bitmaps.o sha512.o swapfs.o symlink.o tdb.o undo_io.o unix_io.o unlink.o valid_blk.o version.o rbtree.o
| (cd elfshared; gcc  --shared -o libext2fs.so.2.4 \
| 	-L../../../lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 \
| 	-Wl,-soname,libext2fs.so.2 bb_compat.o inode_io.o write_bb_file.o dupfs.o imager.o test_io.o ext2_err.o alloc.o alloc_sb.o alloc_stats.o alloc_tables.o atexit.o badblocks.o bb_inode.o bitmaps.o bitops.o blkmap64_ba.o blkmap64_rb.o blknum.o block.o bmap.o check_desc.o closefs.o crc16.o crc32c.o csum.o dblist.o dblist_dir.o dirblock.o dirhash.o dir_iterate.o expanddir.o ext_attr.o extent.o fallocate.o fileio.o finddev.o flushb.o freefs.o gen_bitmap.o gen_bitmap64.o get_num_dirs.o get_pathname.o getsize.o getsectsize.o i_block.o icount.o ind_block.o initialize.o inline.o inline_data.o inode.o io_manager.o ismounted.o link.o llseek.o lookup.o mkdir.o mkjournal.o mmp.o namei.o native.o newdir.o openfs.o progress.o punch.o qcow2.o read_bb.o read_bb_file.o res_gdt.o rw_bitmaps.o sha512.o swapfs.o symlink.o tdb.o undo_io.o unix_io.o unlink.o valid_blk.o version.o rbtree.o -lcom_err)
| /bin/rm -f ../libext2fs.a
| (cd ..; /bin/ln  \
| 	`echo lib/ext2fs | sed -e 's;lib/;;'`/libext2fs.a libext2fs.a)
| /bin/mv elfshared/libext2fs.so.2.4 .
| /bin/rm -f ../libext2fs.so.2.4 ../libext2fs.so ../libext2fs.so.2
| (cd ..; /bin/ln  \
| 	`echo lib/ext2fs | sed -e 's;lib/;;'`/libext2fs.so.2.4 libext2fs.so.2.4)
| (cd ..; /bin/ln  libext2fs.so.2.4 libext2fs.so)
| (cd ..; /bin/ln  libext2fs.so.2.4 libext2fs.so.2)
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| making all in intl
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/intl'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/intl'
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make progs
| make[1]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'util/subst.conf' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'lib/config.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'lib/dirpaths.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: 'lib/ext2fs/ext2_types.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[2]: 'compile_et' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| make[2]: 'ext2_err.h' is up to date.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| making all in lib/et
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/et'
| making all in lib/ss
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ss'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ss'
| making all in lib/e2p
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/e2p'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/e2p'
| making all in lib/support
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/support'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/support'
| making all in lib/ext2fs
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/lib/ext2fs'
| making all in intl
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/intl'
| make[2]: Nothing to be done for 'all'.
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/intl'
| making all in e2fsck
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/e2fsck'
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/e2fsck.c -o e2fsck.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/unix.c -o unix.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/super.c -o super.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/pass1.c -o pass1.o
| ../../git/e2fsck/unix.c: In function 'main':
| ../../git/e2fsck/unix.c:312:47: warning: '%s' directive output may be truncated writing up to 255 bytes into a region of size 58 [-Wformat-truncation=]
|     snprintf(fname, 80, "/proc/acpi/ac_adapter/%s/state",
|                                                ^~
| In file included from /usr/include/stdio.h:862:0,
|                  from ../../git/e2fsck/unix.c:15:
| /usr/include/x86_64-linux-gnu/bits/stdio2.h:64:10: note: '__builtin___snprintf_chk' output between 29 and 284 bytes into a destination of size 80
|    return __builtin___snprintf_chk (__s, __n, __USE_FORTIFY_LEVEL - 1,
|           ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
|         __bos (__s), __fmt, __va_arg_pack ());
|         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/pass1b.c -o pass1b.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/pass2.c -o pass2.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/pass3.c -o pass3.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/pass4.c -o pass4.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/pass5.c -o pass5.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/journal.c -o journal.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/badblocks.c -o badblocks.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/util.c -o util.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/dirinfo.c -o dirinfo.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/dx_dirinfo.c -o dx_dirinfo.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/ehandler.c -o ehandler.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/problem.c -o problem.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/message.c -o message.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/quota.c -o quota.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/recovery.c -o recovery.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/region.c -o region.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/revoke.c -o revoke.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/ea_refcount.c -o ea_refcount.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/rehash.c -o rehash.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/logfile.c -o logfile.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/sigcatcher.c -o sigcatcher.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/readahead.c -o readahead.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H  ../../git/e2fsck/extents.c -o extents.o
| ../util/subst -t -f ../util/subst.conf ../../git/e2fsck/e2fsck.8.in e2fsck.8
| ../util/subst -t -f ../util/subst.conf ../../git/e2fsck/e2fsck.conf.5.in e2fsck.conf.5
| gcc  -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath-link,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -Wl,-rpath,/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/lib -Wl,-O1 -Wl,-rpath-link,../lib -rdynamic -o e2fsck unix.o e2fsck.o super.o pass1.o pass1b.o pass2.o pass3.o pass4.o pass5.o journal.o badblocks.o util.o dirinfo.o dx_dirinfo.o ehandler.o problem.o message.o quota.o recovery.o region.o revoke.o ea_refcount.o rehash.o logfile.o sigcatcher.o  readahead.o extents.o ../lib/libsupport.a ../lib/libext2fs.so ../lib/libcom_err.so  -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -lblkid  -L/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/lib -luuid   ../lib/libe2p.so -ldl -lblkid
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/e2fsck'
| making all in debugfs
| make[2]: Entering directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/debugfs'
| _SS_DIR_OVERRIDE=../lib/ss ../lib/ss/mk_cmds ../../git/debugfs/debug_cmds.ct
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/debugfs.c -o debugfs.o
| ../../git/debugfs/debugfs.c: In function 'do_mknod':
| ../../git/debugfs/debugfs.c:1731:13: warning: In the GNU C Library, "makedev" is defined
|  by <sys/sysmacros.h>. For historical compatibility, it is
|  currently defined by <sys/types.h> as well, but we plan to
|  remove this soon. To use "makedev", include <sys/sysmacros.h>
|  directly. If you did not intend to use a system-defined macro
|  "makedev", you should undefine it after including <sys/types.h>.
|   st.st_rdev = makedev(major, minor);
|              ^~~~~~~~~~~~~~~~~~~~~~~~
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/util.c -o util.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/ncheck.c -o ncheck.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/icheck.c -o icheck.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/ls.c -o ls.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/lsdel.c -o lsdel.o
| ../../git/debugfs/ls.c: In function 'print_filename':
| ../../git/debugfs/ls.c:60:8: warning: '<encrypted (' directive output truncated writing 12 bytes into a region of size 1 [-Wformat-truncation=]
|       "<encrypted (%d)>", len);
|        ~^~~~~~~~~~~
| ../../git/debugfs/ls.c:60:6: note: directive argument in the range [0, 255]
|       "<encrypted (%d)>", len);
|       ^~~~~~~~~~~~~~~~~~
| In file included from /usr/include/stdio.h:862:0,
|                  from ../../git/debugfs/ls.c:9:
| /usr/include/x86_64-linux-gnu/bits/stdio2.h:64:10: note: '__builtin___snprintf_chk' output between 16 and 18 bytes into a destination of size 1
|    return __builtin___snprintf_chk (__s, __n, __USE_FORTIFY_LEVEL - 1,
|           ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
|         __bos (__s), __fmt, __va_arg_pack ());
|         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/dump.c -o dump.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/set_fields.c -o set_fields.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/logdump.c -o logdump.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/htree.c -o htree.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/unused.c -o unused.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS -I../../git/debugfs ../../git/debugfs/../misc/e2freefrag.c -o e2freefrag.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/filefrag.c -o filefrag.o
| _SS_DIR_OVERRIDE=../lib/ss ../lib/ss/mk_cmds ../../git/debugfs/extent_cmds.ct
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/extent_inode.c -o extent_inode.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/zap.c -o zap.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS -I../../git/debugfs \
| 	 ../../git/debugfs/../misc/create_inode.c -o create_inode.o
| gcc  -c -I. -I../lib -I../../git/lib -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -isystem/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/include -O2 -pipe -DHAVE_CONFIG_H -I../../git/debugfs/../e2fsck -DDEBUGFS ../../git/debugfs/quota.c -o quota.o
| ../../git/debugfs/../misc/create_inode.c: In function 'do_mknod_internal':
| ../../git/debugfs/../misc/create_inode.c:290:13: warning: In the GNU C Library, "major" is defined
|  by <sys/sysmacros.h>. For historical compatibility, it is
|  currently defined by <sys/types.h> as well, but we plan to
|  remove this soon. To use "major", include <sys/sysmacros.h>
|  directly. If you did not intend to use a system-defined macro
|  "major", you should undefine it after including <sys/types.h>.
|    devmajor = major(st->st_rdev);
|              ^~~~~~~~~~~~~~~~~~~~
| ../../git/debugfs/../misc/create_inode.c:291:13: warning: In the GNU C Library, "minor" is defined
|  by <sys/sysmacros.h>. For historical compatibility, it is
|  currently defined by <sys/types.h> as well, but we plan to
|  remove this soon. To use "minor", include <sys/sysmacros.h>
|  directly. If you did not intend to use a system-defined macro
|  "minor", you should undefine it after including <sys/types.h>.
|    devminor = minor(st->st_rdev);
|              ^~~~~~~~~~~~~~~~~~~~
| ../../git/debugfs/../misc/create_inode.c: At top level:
| ../../git/debugfs/../misc/create_inode.c:395:18: error: conflicting types for 'copy_file_range'
|  static errcode_t copy_file_range(ext2_filsys fs, int fd, ext2_file_t e2_file,
|                   ^~~~~~~~~~~~~~~
| In file included from ../../git/debugfs/../misc/create_inode.c:19:0:
| /usr/include/unistd.h:1110:9: note: previous declaration of 'copy_file_range' was here
|  ssize_t copy_file_range (int __infd, __off64_t *__pinoff,
|          ^~~~~~~~~~~~~~~
| Makefile:412: recipe for target 'create_inode.o' failed
| make[2]: *** [create_inode.o] Error 1
| make[2]: *** Waiting for unfinished jobs....
| make[2]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build/debugfs'
| Makefile:398: recipe for target 'all-progs-recursive' failed
| make[1]: *** [all-progs-recursive] Error 1
| make[1]: Leaving directory '/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/build'
| Makefile:334: recipe for target 'all' failed
| make: *** [all] Error 2
| ERROR: oe_runmake failed
| ERROR: Function failed: do_compile (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/e2fsprogs-native/1.42.99+1.43+gitAUTOINC+0f26747167-r0/temp/log.do_compile.111805)
ERROR: Task 173 (virtual:native:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/meta/recipes-devtools/e2fsprogs/e2fsprogs_git.bb, do_compile) failed with exit code '1'
NOTE: Tasks Summary: Attempted 4081 tasks of which 3495 didn't need to be rerun and 1 failed.
Waiting for 0 running tasks to finish:
```

解决：

