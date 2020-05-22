# linux 应用相关问题
包括操作系统的报错,软件在安装过程中出现错误等

## 1. Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

在安装apt install xubuntu-desktop 时报错
```
 * Reloading system message bus config...                                                                                                                                                                          
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "reload" failed.
dpkg: error processing package blueman (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 blueman
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
解决方案：
启动dbus
```
/etc/init.d/dbus start
```
成功解决问题

## 2. sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
无意中将sudo的权限修改了，导致执行sudo时报错
```bash
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set

```
使用su root命令时会报以下错误：

```
su:Authentication failure
```

问题原因：sudo的用户属组要属于uid 0，即root用户


解决方案：
由于我使用的是虚拟机virtualbox，需要通过使用虚拟机加载recovry 模式，网上有人说 按住esc键，有的说按住shift键，但是对我来说都不管用，就当我要放弃准备重装系统的时候发现，启动界面右下角提示
按F12 选择启动项，抱着试试的态度，进去发现从镜像文件中启动，在选择 硬盘启动，还真的进入到了recovery模式。
接下来的操作就简单多了

在终端中输入
```
chown root:root bin/sudo

chmod 4755 bin/sudo

```

## 3.Error setgid: Operation not permitted
问题：普通用户在执行su 命令是 报错
```
setgid: Operation not permitted

```

解决方案：

执行命令
```
chmod a+s /bin/su

```