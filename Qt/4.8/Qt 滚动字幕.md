qt字幕滚动是用来处理大量英文的显示和按钮来服务的，一共分为 步
**1 构造一个QString**
构造一个QString用来给qlabel或者qpushbutton来设置text。需要注意的是，qlabel默认居左显示，qpushbutton默认居中显示，需要根据目标显示效果分别对两者进行align的重新设置，此处button需要居左显示，故代码如下：
```c++
    qpushbutton_dialog_auto_test_head_left->setStyleSheet("QPushButton{text-align : left;}");
    qpushbutton_dialog_auto_test_head_left->setMaximumWidth(275);
    qpushbutton_dialog_auto_test_head_left->setMinimumWidth(275);
```
**2 **
