```language
QString path = "F12345.mp4";
path.toStdString().data();
path.toUtf8().data();
```
**使用此方法可以从qstring转换为const char\*即可**
**使用第二行的方法qstring转化为char\* 即可**

  
