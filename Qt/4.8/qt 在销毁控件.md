` QObject *sends = QObject::sender();`
` qDebug()<< sends <<"this is dialog_auto_test";`
` sends->deleteLater();`
` sends = nullptr;`
**通过此方法，可以把object的发送者直接删除，目前效果显示为**