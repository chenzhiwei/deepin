# Deepin Customizations

## 修改窗口圆角大小

1. 控制中心 - 个性化- 圆角窗口

    这个方法只在 Deepin 上适用，并且只有三个值：`0`, `8`, `18`

2. 命令行修改

    ```
    sudo apt install libdtkgui5-bin

    /usr/lib/x86_64-linux-gnu/libdtk-5.2.2/DGui/bin/deepin-gui-settings --set "DTK/WindowRadius" -i 5
    ```

## 多任务界面去掉桌面

```
vim .config/kwin/kwinrc

[TabBox]
ShowDesktopMode=0
```

## 隐藏系统托盘的蓝牙图标

```
gsettings list-recursively

gsettings set com.deepin.dde.daemon bluetooth false
```

## Deepin Terminal

将切换标签（Tab）的快捷键换成`Alt + [1-9]`。

## 安装新内核

```
sudo echo 'deb http://deb.xanmod.org releases main' > /etc/apt/sources.list.d/xanmod-kernel.list
wget -qO - https://dl.xanmod.org/gpg.key | sudo apt-key add -

sudo apt update
sudo apt install linux-xanmod
```
