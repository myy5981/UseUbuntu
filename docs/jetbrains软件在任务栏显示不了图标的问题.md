在.desktop文件中，加入：

```ini
StartupWMClass=jetbrains-pycharm
```

该字段为关键，其他程序可以此类推。

如何查找这个字段的值：

按 Alt + F2 启动“运行一个命令”对话框。当对话框打开时，输入lg并按Enter键，点击【Windows】可查看。对于具有Xorg会话的非GNOME桌面，请打开终端并运行```xprop WM_CLASS```命令。鼠标光标将变成十字准线，然后只需单击应用程序窗口就会在终端输出中输出其类名。
