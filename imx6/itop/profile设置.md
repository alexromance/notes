```shell
# Ash profile
# vim: syntax=sh

# No core files by default
ulimit -S -c 0 > /dev/null 2>&1
USER="`id -un`"
LOGNAME=$USER
PS1='\e[36m\h@\e[33m\u:\e[34m\e[1m\w\e[0m# '

PATH=$PATH
HOSTNAME=`/bin/hostname`
export USER LOGNAME PS1 PATH

EVENT_TS=$(cat /proc/bus/input/devices | grep -E 'TSC2007|ft5x0x_ts' -A4 | tail -1 | awk '{print $NF}')
EVENT_IR=$(cat /proc/bus/input/devices | grep -E 'hs0038' -A3 | tail -1 | awk '{print $NF}')

export TSLIB_ROOT=/usr/local/tslib
export TSLIB_TSDEVICE=/dev/input/$EVENT_TS
export TSLIB_CONFFILE=$TSLIB_ROOT/etc/ts.conf
export TSLIB_PLUGINDIR=$TSLIB_ROOT/lib/ts
export TSLIB_CALIBFILE=/etc/pointercal
export TSLIB_CONSOLEDEVICE=none
export TSLIB_FBDEVICE=/dev/fb0


export QT_ROOT=/opt/qt-5.7.0
export PATH=$QT_ROOT/bin:$PATH
export QT_QPA_FONTDIR=$QT_ROOT/lib/fonts
export QT_QPA_PLATFORM_PLUGIN_PATH=$QT_ROOT/plugins
export QT_QPA_PLATFORM=linuxfb:tty=/dev/fb0
#export QML2_IMPORT_PATH=$QT_ROOT/qml
#export QT_QPA_PLATFORM=eglfs
#export QT_QPA_EGLFS_FB=/dev/fb0
#export QT_EGLFS_IMX6_NO_FB_MULTI_BUFFER=2
###########################export QT_QPA_EVDEV_TOUCHSCREEN_PARAMETERS=/dev/input/$EVENT_TS
export QT_QPA_EVDEV_KEYBOARD_PARAMETERS=/dev/input/$EVENT_IR
export QT_DEBUG_PLUGINS=1
export QT_QPA_FB_TSLIB=1
#export QT_QPA_EGLFS_TSLIB=1
#export QT_QPA_EGLFS_WIDTH=480
#export QT_QPA_EGLFS_HEIGHT=272
############################open egls debuglog
#export QT_QPA_EGLFS_DEBUG=1

export OPENGL_ROOT=/usr/local/OpenGLlib

#export OPENCV_ROOT=/usr/local/OpenCV

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$TSLIB_ROOT/lib:$QT_ROOT/lib:/lib:$OPENGL_ROOT/lib:#$OPENCV_ROOT/lib
```

