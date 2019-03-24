多说无益，直接上代码

# 1 普通的信号槽

```c++
//thread_fuxe.h
#ifndef THREAD_FUSE_H
#define THREAD_FUSE_H
#include <QObject>  //注意一定要包含QObject并且作为基类进行继承
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
}

//thread_complex.h
#ifndef THREAD_COMPLEX_TASK_H
#define THREAD_COMPLEX_TASK_H
#include <QObject>

class thread_complex_task : public QObject
{
    Q_OBJECT
public:
    explicit thread_complex_task(QObject *parent = nullptr);
    ~thread_complex_task() override;

signals:
    void            signal_change_time();
    void            signal_usb_status();
    void            signal_usb_flash_list();

public slots:
    void            on_change_timer_disk();
}

//widget_avm.h
#ifndef WIDGET_AVM_H
#define WIDGET_AVM_H
#include <QWidget>
class widget_avm : public QWidget
{
    Q_OBJECT
public:
    explicit widget_avm(int width, int height, QWidget *parent = nullptr);

signals:
    void    sinnal_start_fuse_thread();
    void    signal_call_show();

public slots:
    void        on_change_time_function();
    void        on_recvs_usb();
    void        on_usb_flash_list();
```

代码已经写完，现在开始正餐

**主线程和子线程之间**
```c++
auto tasks          = new thread_complex_task;
connect(tasks, SIGNAL(signal_change_time()),   this, SLOT(on_change_time_function()));
connect(tasks, SIGNAL(signal_usb_status()),    this, SLOT(on_recvs_usb()));
connect(tasks, SIGNAL(signal_usb_flash_list()),this, SLOT(on_usb_flash_list()));

```
函数的第一个和第三个函数分别代表发送信号和接受信号并相应槽函数


**子线程和子线程**
# 2 Q_INVOKABLE与invokeMethod

# 3 事件驱动




**4 注意不可以有while等耗时操作，可以使用qtimer方式进行驱动**