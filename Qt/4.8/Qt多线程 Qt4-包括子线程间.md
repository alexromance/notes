多说无益，直接上代码

# 1 普通的信号槽
**主线程和子线程**
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
#ifndef THREAD_COMPLEX_TASK_H
#define THREAD_COMPLEX_TASK_H

#include <QObject>
#include <QFileInfoList>
#include <QTimer>

#include <sys/vfs.h>

#include <hi_type.h>


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
}

//
#ifndef WIDGET_AVM_H
#define WIDGET_AVM_H
#include <QWidget>
class widget_avm : public QWidget
{
    Q_OBJECT
public:
    explicit widget_avm(int width, int height, QWidget *parent = nullptr);


private:
    static const HI_U32 src_width               = 1280;
    static const HI_U32 src_height              = 720;
    static const HI_U32 des_width               = 320;
    static const HI_U32 des_height              = 480;

#if !QT_WINDOW_FLAG_OPEN
    QPushButton *qbutton;
#endif
    QPushButton *qpush_button_zoom;

    QLabel      *qlabel_times;
    QLabel      *qlabel_video;
    QImage      *qimage_photo_video_blank;
    QImage      *qimage_photo_video_normal;
    QImage      *qimage_back_track_blank;
    QImage      *qimage_back_track_normal;
    QImage      *qimage_back_line_left;
    QImage      *qimage_back_line_right;
    QImage      *qimage_four_view;

    QImage      *qimage_f;
    QImage      *qimage_b;
    QImage      *qimage_l;
    QImage      *qimage_r;
    QLabel      *qlabel_logo;
    QLabel      *qlabel_back_track;
    QLabel      *qlabel_camera_status;
    QLabel      *qlabel_speed;
    QLabel      *qlabel_back_line_left;
    QLabel      *qlabel_back_line_right;
    QLabel      *qlabel_four_view;


    QProgressBar*qprogress_play;

    QPointer<dialog_engineer>       dialog_engineer_slot    = nullptr;

    QTime       time;
    QString     flag_rect;

    QString     usb_status;

    int         flag_video;
    const char widget_speed_sub[4][6] = {
            "-1X",
            "-2X",
            "-3X",
            "-4X",
    };
    const char widget_speed_add[4][6] = {
            "1X",
            "2X",
            "3X",
            "4X",
    };
    const char widget_speed_pause[2][4] = {
            "1X",
            "PA",
    };

    const char qpush_button_status[2][8] = {
            "缩放",
            "平移",
    };

    int         index_sub;
    int         index_add;
    int         index_pause;

    bool        b_wake_up;
    int         init();
    void        keyPressEvent(QKeyEvent *event) override;
    HI_S32      widget_avm_check_venc();
    void        widget_avm_key_function();
    void        widget_avm_show_four_view();
    void        widget_avm_qtimer_init();
    void        widget_avm_background_init();
    void        widget_avm_set_window_init();
    void        widget_avm_bar();
    void        widget_avm_speed_add();
signals:
    void    sinnal_start_fuse_thread();
    void    signal_call_show();


public slots:
    void        on_change_time_function();
    void        on_recvs_usb();
    void        on_usb_flash_list();
```


**子线程和子线程**
# 2 Q_INVOKABLE与invokeMethod

# 3 事件驱动




**4 注意不可以有while等耗时操作，可以使用qtimer方式进行驱动**