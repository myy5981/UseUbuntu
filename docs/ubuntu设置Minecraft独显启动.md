ubuntu上运行Minecraft java版默认不会使用独显启动

在安装nvidia驱动后，使用以下命令，可以使用独显启动：
```shell
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia minecraft-launcher
```

但是很麻烦

可以写到shell脚本中，并在启动器中配置启动路径为该脚本：

在PATH路径中新建prime_run文件（我习惯在主目录中新建ubin文件夹存放自己写的一些常用的脚本、程序），写入以下内容：
```shell
#!/bin/sh
export __NV_PRIME_RENDER_OFFLOAD=1
export __GLX_VENDOR_LIBRARY_NAME=nvidia
export __VK_LAYER_NV_optimus=NVIDIA_only
exec "$@"
```

```$@```表示后跟的所有参数，如此，使用prime_run命令在原本的命令前可以使用独显启动任意程序，就像sudo可以以root权限启动程序一样。

推荐在~/.minecraft中新建launch.sh文件，写入如下内容：

```shell
#!/bin/bash
/home/myy/ubin/prime-run /home/myy/.minecraft/runtime/java-runtime-delta/linux/java-runtime-delta/bin/java "$@"
```

在Minecraft启动器的配置中，设置【JAVA可执行文件路径】为该launch.sh文件即可使用独显享受我的世界。