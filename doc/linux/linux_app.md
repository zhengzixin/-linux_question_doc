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
解决办法：
启动dbus
```
/etc/init.d/dbus start
```
成功解决问题
