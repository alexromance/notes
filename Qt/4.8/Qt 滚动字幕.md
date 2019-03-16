qt字幕滚动是用来处理大量英文的显示和按钮来服务的，一共分为 步
**1 构造一个QString**
构造一个QString用来给qlabel或者qpushbutton来设置text。需要注意的是，qlabel默认居左显示，qpushbutton默认居中显示，需要根据目标显示效果分别对两者进行align的重新设置，此处button需要居左显示，故代码如下：
```c++
    qpushbutton_dialog_auto_test_head_left->setStyleSheet("QPushButton{text-align : left;}");
    qpushbutton_dialog_auto_test_head_left->setMaximumWidth(275);
    qpushbutton_dialog_auto_test_head_left->setMinimumWidth(275);
```
**2 构造一个QTimer**
构造一个QTimer用来定时给控件的文本进行刷新，定时器超时时间设置为200-300ms之间，此处重点说明超时槽函数
```c++
    static int pos = 0;
    if(pos > m_str_head.length())
        pos = 0;
    qpushbutton_dialog_auto_test_head_left->setText(m_str_head.mid(pos) + m_str_head.left(pos));
    pos++;
```
**需要注意的是mid和left函数的先后位置不可颠倒，必须如上设置，否则没有滚动效果**
**3 **

