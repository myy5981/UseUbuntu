Miniconda下载后不能补全，激活环境时需要输入activate全部字母，可以下载自动补全插件启用Tab补全功能：

在base环境（或不启动任何环境，其实也是base环境）下
```shell
conda install -c conda-forge conda-bash-completion
```

如果你在安装conda时没有设置启动终端时自动启动conda base环境，即```auto_activate_base: false```，你还需要在~/.bashrc文件（或其他用于终端配置的文件）中加入：

```shell
CONDA_ROOT=~/anaconda3   # <- set to your Anaconda/Miniconda installation directory
if [[ -r $CONDA_ROOT/etc/profile.d/bash_completion.sh ]]; then
    source $CONDA_ROOT/etc/profile.d/bash_completion.sh
else
    echo "WARNING: could not find conda-bash-completion setup script"
fi
```
