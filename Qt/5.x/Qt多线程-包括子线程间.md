**首先声明的是Qt5可以兼容Qt4中描述的各种方式，只是比较麻烦罢了，所以此处主要介绍两种**

**4 全局观察者方式**

参考https://blog.csdn.net/q862343646/article/details/79947005，
其中已经实验只有QT5可是，其中的原因是在QT5中signal是可以使用public进行修饰的，但是QT4中只能是protected，所以编译过程中会报错，提示
```c++
/home/alex/nfs_share/work/qt/globalObserver/globalObserver.cpp:59: error: 'notify' is a protected member of 'obesrverApater'
            emit (*iter)->obesrverApater->notify();
                                          ^

```

**5 将信号作为槽函数**

此方式也是比较取巧，但是还是此方法的重载只有在QT5中才有实现，QT4中由于源码的问题，此种重载不能实现，没有任何反应
```c++


```
