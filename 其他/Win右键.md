1,

打开注册表（win+r）输入 regedit

2,

展开

```
HKEY_CLASSES_ROOT\DesktopBackground\Shell
```

3,

点击【shell】后在右侧窗口鼠标右击选择【新建】选择【项】


将新建的项重命名为【关机】


点击【关机】后双击右侧窗口中的【默认】，在数值数据处输入【关机】点击【确定】


鼠标右击左侧【关机】选择【新建】选择【项】

将新建的项命名为

```
command
```

4,

点击【command】后双击右侧窗口中的【默认】，在数值数据处输入 Shutdown -s -f -t 00 点击【确定】

```
关机 Shutdown -s -f -t 00
注销 Shutdown -l
重启 Shutdown -r -f -t 00
锁屏 Rundll32 User32.dll,LockWorkStation
```

