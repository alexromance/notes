```language
    QObject *sends = QObject::sender();
    qDebug()<< sends <<"this is dialog_auto_test";
    sends->deleteLater();
    sends = nullptr;

```
**通过此方法，可以把object的发送者直接删除，目前效果显示为槽函数触发后删除掉当前的项目**

![title](../../.local/static/2019/2/0/sender.1553398960707.gif)
