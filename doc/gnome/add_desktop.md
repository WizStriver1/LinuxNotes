# 添加程序到gnome搜索菜单中的步骤
1. 首先在/usr/share/applications/路径下创建一个扩展名为desktop的配置文件，然后编辑它，以firefox为例：
```
vim /usr/share/applications/firefox.desktop
```
输入以下内容
```
[Desktop Entry]

Name=firefox

Exec=/usr/local/firefox/firefox

Icon=/usr/local/firefox/chrome/default/default128.png

Terminal=false

Type=Application

Categories=Application;Development;
```

ok啦，这样就能在gnome菜单中直接搜索firefox了
