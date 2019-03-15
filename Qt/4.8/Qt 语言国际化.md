**1 找到所有代码中目标翻译的文件，用如下代码改写**
```c++
QObject::tr("低")
```
其中需要注意的是此函数返回的是QString类型，如果接受者是char，清进行相应的转换，比如
**2 生成ts文件**
需要在.pro文件中加入如下
```c++
TRANSLATIONS = AVM_CN.ts \
                AVM_EN.ts# 
```
在命令行中执行如下代码
```shell
lupdate HI3520D.pro -codecfortr utf-8 -ts AVM_EN.ts AVM_CN.ts
```
**需要注意的是必须使用-codecfortr 指定编码格式，否则出现乱码无法进行编辑**
**1 对生成的ts文件使用linguist进行翻译**
直接使用linguist 打开文件进行翻译即可


