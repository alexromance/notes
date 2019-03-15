***1 生成ts文件***
*需要在.pro文件中加入如下*
```c++
TRANSLATIONS = AVM_CN.ts \
                AVM_EN.ts
```
*在命令行中执行如下代码*
```shell
lupdate HI3520D.pro -codecfortr utf-8 -ts AVM_EN.ts AVM_CN.ts
```
**需要注意的是必须使用-codecfortr 指定编码格式，否则出现乱码无法进行编辑**
***2 对生成的ts文件使用linguist进行翻译***
*直接使用linguist *

