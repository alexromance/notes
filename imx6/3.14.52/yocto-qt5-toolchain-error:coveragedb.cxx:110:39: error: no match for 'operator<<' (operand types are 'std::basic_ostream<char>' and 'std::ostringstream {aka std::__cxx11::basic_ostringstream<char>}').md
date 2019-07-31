编译报错：

```shell
coveragedb.cxx:110:39: error: no match for 'operator<<' (operand types are 'std::basic_ostream<char>' and 'std::ostringstream {aka std::__cxx11::basic_ostringstream<char>}')
```

报错表现：

```shell
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/coveragedb.cxx: In function 'bool has_table(sqlite3*, const char*)':
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/coveragedb.cxx:110:39: error: no match for 'operator<<' (operand types are 'std::basic_ostream<char>' and 'std::ostringstream {aka std::__cxx11::basic_ostringstream<char>}')
|      cerr << _("Error in statement: ") << command << " [" << errmsg << "]."
|      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/coveragedb.cxx:110:39: note: candidate: operator<<(int, int) <built-in>
| /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/coveragedb.cxx:110:39: note:   no known conversion for argument 2 from 'std::ostringstream {aka std::__cxx11::basic_ostringstream<char>}' to 'int'
| In file included from /usr/include/c++/7/iostream:39:0,
|                  from /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/parse.h:16,
|                  from /home/alex/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git/coveragedb.cxx:9:
| /usr/include/c++/7/ostream:108:7: note: candidate: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ostream_type& (*)(std::basic_ostream<_CharT, _Traits>::__ostream_type&)) [with _CharT = char; _Traits = std::char_traits<char>; std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
|        operator<<(__ostream_type& (*__pf)(__ostream_type&))
|        ^~~~~~~~
| /usr/include/c++/7/ostream:108:7: note:   no known conversion for argument 1 from 'std::ostringstream {aka std::__cxx11::basic_ostringstream<char>}' to 'std::basic_ostream<char>::__ostream_type& (*)(std::basic_ostream<char>::__ostream_type&) {aka std::basic_ostream<char>& (*)(std::basic_ostream<char>&)}'
| /usr/include/c++/7/ostream:117:7: note: candidate: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>::__ios_type& (*)(std::basic_ostream<_CharT, _Traits>::__ios_type&)) [with _CharT = char; _Traits = std::char_traits<char>; std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>; std::basic_ostream<_CharT, _Traits>::__ios_type = std::basic_ios<char>]
|        operator<<(__ios_type& (*__pf)(__ios_type&))
|        ^~~~~~~~
| /usr/include/c++/7/ostream:117:7: note:   no known conversion for argument 1 from 'std::ostringstream {aka std::__cxx11::basic_ostringstream<char>}' to 'std::basic_ostream<char>::__ios_type& (*)(std::basic_ostream<char>::__ios_type&) {aka std::basic_ios<char>& (*)(std::basic_ios<char>&)}'
| /usr/include/c++/7/ostream:127:7: note: candidate: std::basic_ostream<_CharT, _Traits>::__ostream_type& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char; _Traits = std::char_traits<char>; std::basic_ostream<_CharT, _Traits>::__ostream_type = std::basic_ostream<char>]
|        operator<<(ios_base& (*__pf) (ios_base&))
|        ^~~~~~~~
```

解决：

command 替换成 command.str()

```shell
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git *
 alex→ $ diff coveragedb.cxx coveragedb.cxx.bak
110c110
<     cerr << _("Error in statement: ") << command.str() << " [" << errmsg << "]."
---
>     cerr << _("Error in statement: ") << command << " [" << errmsg << "]."
133c133
<     cerr << _("Error in statement: ") << command.str() << " [" << errmsg << "]."
---
>     cerr << _("Error in statement: ") << command << " [" << errmsg << "]."
* ~/imx6/6d/sdk/bld-fb/tmp/work/x86_64-linux/systemtap-native/2.7+gitAUTOINC+bf16266782-r0/git *
 alex→ $ 
```

参考文章：

https://lists.fedoraproject.org/pipermail/devel/2015-February/208406.html