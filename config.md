# Deepin Customizations

## 修改窗口圆角大小

1. 控制中心 - 个性化- 圆角窗口

    这个方法只在 Deepin 上适用，并且只有三个值：`0`, `8`, `18`

2. 命令行修改

    ```
    sudo apt install libdtkgui5-bin

    /usr/lib/x86_64-linux-gnu/libdtk-5.2.2/DGui/bin/deepin-gui-settings --set "DTK/WindowRadius" -i 5
    ```

## 标题栏宽度调窄

    ```
    vim ~/.local/share/deepin/themes/deepin/light/titlebar.ini
    vim ~/.local/share/deepin/themes/deepin/dark/titlebar.ini

    [Active]
    height=24

    [Inactive]
    height=24
    ```

## 多任务界面去掉桌面

```
vim .config/kwinrc

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

## Flatpak Mirror

```
sudo flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

## 修改启动关机界面

```
plymouth-set-default-theme -l
plymouth-set-default-theme deepin-hidpi-ssd-logo -R
```

## 双系统时 Windows 慢8小时

在 Debian 系的系统里执行如下命令。

```
timedatectl set-local-rtc 1
```

## 安装新内核

```
sudo echo 'deb http://deb.xanmod.org releases main' > /etc/apt/sources.list.d/xanmod-kernel.list
wget -qO - https://dl.xanmod.org/gpg.key | sudo apt-key add -

sudo apt update
sudo apt install linux-xanmod
```
