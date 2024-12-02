官网下载qqmusic后，点击开始图标闪退。

解决此问题需在```/usr/share/applications/qqmusic.desktop```中修改Exec项，删去%U并添加--no-sandbox

```ini
Exec=/opt/qqmusic/qqmusic --no-sandbox
```
