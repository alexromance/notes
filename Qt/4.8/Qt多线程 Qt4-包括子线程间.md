多说无益，直接上代码

# 1 普通的信号槽
**主线程和子线程**
```c++
#ifndef THREAD_FUSE_H
#define THREAD_FUSE_H

#include <QObject>
class thread_fuse : public QObject
{
    Q_OBJECT
public:
    explicit thread_fuse(HI_U32 src_width, HI_U32 src_height, HI_U32 des_width, HI_U32 des_height, QObject *parent = nullptr);
    ~thread_fuse() override;
signals:

public slots:
    void  thread_fuse_run();
    void    on_timer_out();  //注意槽函数需要进行实现


```


**子线程和子线程**
# 2 Q_INVOKABLE与invokeMethod

# 3 事件驱动




**4 注意不可以有while等耗时操作，可以使用qtimer方式进行驱动**