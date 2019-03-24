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
函数的第一个和第三个函数分别代表发送信号和接受信号并相应槽函数的对象，其实connet函数还有第五个参数
1、Qt::AutoConnection： 默认值，使用这个值则连接类型会在信号发送时决定。如果接收者和发送者在同一个线程，则自动使用Qt::DirectConnection类型。如果接收者和发送者不在一个线程，则自动使用Qt::QueuedConnection类型。

2、Qt::DirectConnection：槽函数会在信号发送的时候直接被调用，槽函数运行于信号发送者所在线程。效果看上去就像是直接在信号发送位置调用了槽函数。这个在多线程环境下比较危险，可能会造成奔溃。

3、Qt::QueuedConnection：槽函数在控制回到接收者所在线程的事件循环时被调用，槽函数运行于信号接收者所在线程。发送信号之后，槽函数不会立刻被调用，等到接收者的当前函数执行完，进入事件循环之后，槽函数才会被调用。多线程环境下一般用这个。

4、Qt::BlockingQueuedConnection：槽函数的调用时机与Qt::QueuedConnection一致，不过发送完信号后发送者所在线程会阻塞，直到槽函数运行完。接收者和发送者绝对不能在一个线程，否则程序会死锁。在多线程间需要同步的场合可能需要这个。

5、Qt::UniqueConnection：这个flag可以通过按位或（|）与以上四个结合在一起使用。当这个flag设置时，当某个信号和槽已经连接时，再进行重复的连接就会失败。也就是避免了重复连接。

不管是使用那种方式，要想在子线程里面触发的信号的槽函数在子线程执行，信号槽连接必须使用DirectConnection 方式；
![title](../../.local/static/2019/2/0/20180525165537440.1553403428453.png)

**子线程和子线程**
此处子线程和子线程我主要说明两种，一种是两个子线程都在主线程中进行
# 2 Q_INVOKABLE与invokeMethod

# 3 事件驱动




**4 注意不可以有while等耗时操作，可以使用qtimer方式进行驱动**