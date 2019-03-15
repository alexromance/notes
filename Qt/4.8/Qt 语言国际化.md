**1 tr()函数改写代码**
找到所有代码中目标翻译的文件，用如下代码改写
```c++
QObject::tr("低")
```
其中需要注意的是此函数返回的是QString类型，如果接受者是char，清进行相应的转换，参考QString转换为char
**2 lupdate生成ts文件**
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
**3 linguist进行翻译**
对生成的ts文件使用linguist进行翻译，直接使用linguist 打开文件进行翻译即可。或者可以直接用vim打开文件，用类似xml的格式进行改写
**4 lrelease发布翻译**
```shell
 lrelease AVM_EN.ts -qm AVM_EN.qm
```
**5 main函数改写**
将上一步生成的qm文件拷贝到指定位置，然后在main文件中改写代码
```c++
    QApplication app(argc, argv);
    QTranslator tsor;
    tsor.load("AVM_EN.qm");
//    tsor.load("AVM_CN.qm");
    app.installTranslator(&tsor);
```
注意代码中第三行的路径是与指定的位置相关，每次重新生成qm文件后都需要重新编译pro工程





