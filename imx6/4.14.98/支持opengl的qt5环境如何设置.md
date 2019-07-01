直接上配置：

```shell
######################################
                                                                           
#export QT_ROOT=/usr/local/qt5                                         
export QT_ROOT=/lib           
export QT_QPA_FONTDIR=$QT_ROOT/lib/fonts        
export QT_QPA_PLATFORM_PLUGIN_PATH=$QT_ROOT/qt5/plugins                   
export QT_QPA_PLATFORM=linuxfb:fb=/dev/fb0                        
export QML2_IMPORT_PATH=$QT_ROOT/qt5/qml 
export QT_QPA_PLATFORM=eglfs            
export QT_EGLFS_IMX6_NO_FB_MULTI_BUFFER=2
export QT_DEBUG_PLUGINS=1                
LD_LIBRARY_PATH="/lib:/usr/lib:"             
LD_LIBRARY_PATH=$QT_ROOT/lib:$LD_LIBRARY_PATH
                                             
#####################################                             
export PATH PS1 OPIEDIR QPEDIR QTDIR EDITOR TERM
                                                
umask 022
```

参考文章：

https://www.jianshu.com/p/9cc782436ece