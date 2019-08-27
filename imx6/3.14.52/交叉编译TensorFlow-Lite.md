1 首先安装交叉编译工具链并下载源码

```shell


2 安装所需的软件包

```shell

* ~/google/tensorflow *
 alex→ $ ./tensorflow/lite/tools/make/download_dependencies.sh
```

3 查看此版本通用的编译选项，此处对于imx来说是查看source的environment文件。

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

4 复制树梅派的配置文件，修改如下：

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

5 复制树梅派的编译配置文件，修改如下：

```shell

* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ cp targets/rpi_makefile.inc targets/imx_makefile.inc 



* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ diff targets/rpi_makefile.inc targets/imx_makefile.inc 
1,2c1,2
< # Settings for Raspberry Pi.
< ifeq ($(TARGET),rpi)
---
> # Settings for imx.
> ifeq ($(TARGET),imx)
6c6
<   TARGET_TOOLCHAIN_PREFIX := arm-linux-gnueabihf-
---
>   TARGET_TOOLCHAIN_PREFIX := arm-poky-linux-gnueabi-
10,14c10,14
< 			-march=armv7-a \
<       -mfpu=neon-vfpv4 \
<       -funsafe-math-optimizations \
<       -ftree-vectorize \
<       -fPIC
---
>       -march=armv7-a \
>       -mfloat-abi=hard \
>       -mfpu=neon \
>       -mtune=cortex-a9 \
>       --sysroot=/opt/fsl-imx-fb/3.14.52-1.1.1/sysroots/cortexa9hf-vfp-neon-poky-linux-gnueabi
18,21c18,21
<       -mfpu=neon-vfpv4 \
<       -funsafe-math-optimizations \
<       -ftree-vectorize \
<       -fPIC
---
>       -mfloat-abi=hard \
>       -mfpu=neon \
>       -mtune=cortex-a9 \
>       --sysroot=/opt/fsl-imx-fb/3.14.52-1.1.1/sysroots/cortexa9hf-vfp-neon-poky-linux-gnueabi
58,59c58,59
<     -ldl
< 
---
>     -ldl \
>     -lrt
* ~/google/tensorflow/tensorflow/lite/tools/make *
 alex→ $ 
```

6 开始编译。

```shell

* ~/google/tensorflow *
 alex→ $ ./tensorflow/lite/tools/make/build_imx_lib.sh 
```

**参考文章：**

https://tensorflow.google.cn/lite/guide/build_rpi?hl=en

