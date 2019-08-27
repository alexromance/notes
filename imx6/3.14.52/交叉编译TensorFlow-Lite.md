1 首先安装交叉编译工具链

2 查看此版本通用的编译选项，此处对于imx来说是查看source的environment文件。

```shell

* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ vim /opt/fsl-imx-fb/3.14.52-1.1.1/environment-setup-cortexa9hf-vfp-neon-poky-linux-gnueabi 
```

文件中的此行是重点

```shell

export PYTHONHOME=/opt/fsl-imx-fb/3.14.52-1.1.1/sysroots/x86_64-pokysdk-linux/usr
export CC="arm-poky-linux-gnueabi-gcc  -march=armv7-a -mfloat-abi=hard -mfpu=neon -mtune=cortex-a9 --sysroot=$SDKTARGETSYSROOT"
export CXX="arm-poky-linux-gnueabi-g++  -march=armv7-a -mfloat-abi=hard -mfpu=neon -mtune=cortex-a9 --sysroot=$SDKTARGETSYSROOT"
```

由此处得知我们需要更改的特殊编译选项。

3 复制树梅派的配置文件，修改如下：

```shell
* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ cp build_rpi_lib.sh build_imx_lib.sh 

* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ diff build_rpi_lib.sh build_imx_lib.sh 
23c23
< make -j 4 TARGET=rpi -C "${TENSORFLOW_DIR}" -f tensorflow/lite/tools/make/Makefile
---
> make -j 4 TARGET=imx -C "${TENSORFLOW_DIR}" -f tensorflow/lite/tools/make/Makefile
* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ 
```

4 复制树梅派的

