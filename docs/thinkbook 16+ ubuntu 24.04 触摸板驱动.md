thinkbook 16+ 2024 安装ubuntu 24.04.1后触摸板无效，经检查为驱动缺失，以下为解决方案：

```shell
sudo apt update
sudo apt upgrade
reboot #确保内核更新到最新
git clone "https://github.com/ty2/goodix-gt7868q-linux-driver.git"
cd goodix-gt7868q-linux-driver
make #这里会将内核写入Makefile文件中参与编译，所以上面说要更新内核
sudo cp goodix-gt7868q.ko /lib/modules/[your kernel name]/kernel/drivers/
sudo mkdir /etc/libinput
sudo cp local-overrides.quirks /etc/libinput/local-overrides.quirks
sudo depmod
sudo modprobe goodix-gt7868q # 测试是否能够使用
sudo echo "goodix-gt7868q"|sudo tee /etc/modules-load.d/goodix-gt7868q.conf
reboot
# 查看加载的驱动
lsmod | grep goodix-gt7868q
#每次内核大更新需要重新配置
```

随着内核的更新，可能不再需要驱动
