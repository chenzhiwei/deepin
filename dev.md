# 编译开发相关

## 在容器里编译软件

我喜欢让机器保持干净，而深度系统里编译一个它自己的软件需要下载一堆 QT5 的相关库，而这些库平时我根本不用，所以为了让系统不臃肿，我选择在容器里编译。

```
podman run --it --name=deepin debian:10.8 bash

apt update
apt -y install vim ca-certificates gnupg
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 425956BB3E31DF51

vim /etc/apt/sources.list

    deb [by-hash=force] https://community-packages.deepin.com/deepin/ apricot main contrib non-free

apt update
apt -y install git

git clone https://github.com/linuxdeepin/deepin-terminal
cd deepin-terminal
apt build-dep .
mkdir build && cd build
cmake ..
make
```
