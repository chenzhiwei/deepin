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
    height=40

    [Inactive]
    height=40
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
sudo apt -y install flatpak

sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

sudo flatpak remote-modify --no-follow-redirect --url=https://mirror.sjtu.edu.cn/flathub flathub

# restart system

flatpak install com.github.unrud.VideoDownloader org.gtk.Gtk3theme.deepin org.gtk.Gtk3theme.deepin-dark \
    org.mozilla.firefox org.supertuxproject.SuperTux org.telegram.desktop us.zoom.Zoom
```

`--no-follow-redirect` 表示将此 URL 持久化下来，否则这个 URL 会在更新后被重置回默认值。低版本没有这个参数，需要手动添加`url-is-set=true`到文件`/var/lib/flatpak/repo/config`。

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
