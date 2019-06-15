编译报错： Can't locate find.pl in @INC

报错表现：


```c++
ERROR: openssl-native-1.0.2h-r0 do_configure: Function failed: do_configure (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2h-r0/temp/log.do_configure.35252)
ERROR: Logfile of failure stored in: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2h-r0/temp/log.do_configure.35252
Log data follows:
| DEBUG: Executing python function sysroot_cleansstate
| DEBUG: Python function sysroot_cleansstate finished
| DEBUG: Executing shell function do_configure
| Can't locate find.pl in @INC (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at perlpath.pl line 7.
| WARNING: /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2h-r0/temp/run.do_configure.35252:1 exit 2 from 'perl perlpath.pl /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/sysroots/x86_64-linux/usr/bin'
| ERROR: Function failed: do_configure (log file is located at /home/alex/nfs_share/IMX_Platform/IMX6D/sdk/bld-fb/tmp/work/x86_64-linux/openssl-native/1.0.2h-r0/temp/log.do_configure.35252)
ERROR: Task 765 (virtual:native:/home/alex/nfs_share/IMX_Platform/IMX6D/sdk/sources/poky/meta/recipes-connectivity/openssl/openssl_1.0.2h.bb, do_configure) failed with exit code '1'
NOTE: Tasks Summary: Attempted 299 tasks of which 118 didn't need to be rerun and 1 failed.
Waiting for 0 running tasks to finish:
```

解决：


在/etc/perl中添加缺失的文件


文件如下：


```c++
 # This library is deprecated and unmaintained. It is included for
        # compatibility with Perl 4 scripts which may use it, but it will be
        # removed in a future version of Perl. Please use the File::Find module
        # instead.
        
        # Usage:
        #    require "find.pl";
        #
        #    &find('/foo','/bar');
        #
        #    sub wanted { ... }
        #        where wanted does whatever you want.  $dir contains the
        #        current directory name, and $_ the current filename within
        #        that directory.  $name contains "$dir/$_".  You are cd'ed
        #        to $dir when the function is called.  The function may
        #        set $prune to prune the tree.
        #
        # For example,
        #
        #   find / -name .nfs\* -mtime +7 -exec rm -f {} \; -o -fstype nfs -prune
        #
        # corresponds to this
        #
        #    sub wanted {
        #        /^\.nfs.*$/ &&
        #        (($dev,$ino,$mode,$nlink,$uid,$gid) = lstat($_)) &&
        #        int(-M _) > 7 &&
        #        unlink($_)
        #        ||
        #        ($nlink || (($dev,$ino,$mode,$nlink,$uid,$gid) = lstat($_))) &&
        #        $dev < 0 &&
        #        ($prune = 1);
        #    }
        #
        # Set the variable $dont_use_nlink if you're using AFS, since AFS cheats.
        
        use File::Find ();
        
        *name        = *File::Find::name;
        *prune        = *File::Find::prune;
        *dir        = *File::Find::dir;
        *topdir        = *File::Find::topdir;
        *topdev        = *File::Find::topdev;
        *topino        = *File::Find::topino;
        *topmode    = *File::Find::topmode;
        *topnlink    = *File::Find::topnlink;
        
        sub find {
            &File::Find::find(\&wanted, @_);
        }
        
        1;
```

参考文章：


https://www.cnblogs.com/zengjfgit/p/9181330.html