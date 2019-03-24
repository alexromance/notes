多说无益，直接上代码

# 1 普通的信号槽
**主线程和子线程**
```c++
#ifndef THREAD_COMPLEX_TASK_H
#define THREAD_COMPLEX_TASK_H

#include <QObject>

class thread_complex_task : public QObject
{
    Q_OBJECT
public:
    explicit thread_complex_task(QObject *parent = nullptr);
    ~thread_complex_task() override;

private:
    QTimer          *m_task_timer;
    QString         flag_rect;
    QFileInfoList   fileList_disk;
    const char*     pdisk = "/nfsroot";
    long long       freespace = 0;
    struct statfs   disk_statfs;
    long long       totalspace = 0;
    int             flag_my_task;
    int             flag_sleep;
    int             flag_heart_beat;

    HI_U32          res_l;
    HI_U32          res_r;
    HI_U32          res_b;
    HI_S32          s32Ret;

    void            cleanup_disk();
    void            udisk_check();
    void            sleep_vout_vsd();
    void            flash_led(bool my_led);
    void            acc_check();
    int             venc_check_for_off_screen();
    void            heart_beat_operatings();
    void            sleep_operatings();
    void            usb_operatings();

signals:
    void            signal_change_time();
    void            signal_usb_status();
    void            signal_usb_flash_list();

public slots:
    void            on_change_timer_disk();
```


**子线程和子线程**
# 2 Q_INVOKABLE与invokeMethod

# 3 事件驱动




**4 注意不可以有while等耗时操作，可以使用qtimer方式进行驱动**