# 终端代理
使用两个环境变量即可，临时生效：
```shell
export http_proxy=http://ip:port
export https_proxy=http://ip:port
```
不建议写死

# Pip
配置文件在~/.config/pip/pip.conf
### 临时
在```pip install```时使用-i参数可以临时换源，示例为清华源，使用其他源自行搜索：

```shell
-i https://pypi.tuna.tsinghua.edu.cn/simple
```

### 永久
```shell
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

### 取消永久
```shell
pip config unset global.index-url
```

### 代理
使用参数--proxy指定代理

# Conda
配置文件为~/.condarc

### 永久
```shell
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge 
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/

# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```

### 取消永久
```shell
conda config --remove-key channels
```

### 设置查看与取消conda代理

```shell
conda config --set proxy_servers.http http://ip:port
conda config --set proxy_servers.https http://ip:port

conda config --get proxy_servers

conda config --remove-key proxy_servers.http
conda config --remove-key proxy_servers.https
```
可以写成脚本：

condaproxy_on:
```shell
#!/bin/bash
if [ $# -eq 1 ];
then
conda config --set proxy_servers.https http://$1:7897
echo -e "\033[32m[√] conda代理已开启\033[0m"
exit
else
echo "usage: conda_proxy_on <your ip>"
fi
```

condaproxy_off:
```shell
#!/bin/bash
conda config --remove-key proxy_servers.https
echo -e "\033[31m[x] conda代理已关闭\033[0m"
```

condaproxy_status:
```shell
#!/bin/bash
conda config --get proxy_servers
```