```language
const char common_str_config::update_host_time[13] = "主机日期";
```
**每个汉字占3个字节，还有一个换行 \n占一个字节，所以是 4 × 3 + 1 = 13**
```language
const char common_str_config::update_decoder[24] = "/nfsroot/update_decoder"
```
**每个字母所占的字节数等于总共输出来的长度，所以是输出来的长度 24**
