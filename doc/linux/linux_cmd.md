# Linux常用命令的使用方法

## 复制文件或目录 cp

### 一般用法：
> cp [options] source dest
>
> cp [options] source... directory
### 参数说明：

- -a：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpR参数组合。
- -d：复制时保留链接。这里所说的链接相当于Windows系统中的快捷方式。
- -f：覆盖已经存在的目标文件而不给出提示。
- -i：与-f选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答"y"时目标文件将被覆盖。
- -p：除复制文件的内容外，还把修改时间和访问权限也复制到新文件中。
- -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
- -l：不复制文件，只是生成链接文件。

## 创建文件夹 mkdir
### 一般用法：
> mkdir [-p] dirName
>
> -p 确保目录名称存在，不存在的就建一个。

### 示例：
创建test目录
> mkdir test

在目录test下创建host目录

>mkdir -p /test/host

## ubuntu查看文件和文件夹大小
> ll -h
### 查看当前目录大小：

> du -h --max-depth=0
## 查看系统相关信息 
### 查看系统信息

```bash
$uname -a               # 查看内核/操作系统/CPU信息
$head -n 1 /etc/issue   # 查看操作系统版本 
$cat /proc/cpuinfo      # 查看CPU信息
$hostname               # 查看计算机名 
$lspci -tv              # 列出所有PCI设备
$lsusb -tv              # 列出所有USB设备 
$lsmod                  # 列出加载的内核模块
$env                    # 查看环境变量

```
### 查看资源

```bash
$free -m                # 查看内存使用量和交换区使用量 
$df -h                  # 查看各分区使用情况 
$du -sh <目录名>        # 查看指定目录的大小 
$grep MemTotal /proc/meminfo   # 查看内存总量
$grep MemFree /proc/meminfo    # 查看空闲内存量
$uptime                 # 查看系统运行时间、用户数、负载 
$cat /proc/loadavg      # 查看系统负载

```
### 磁盘和分区

```bash
$mount | column -t      # 查看挂接的分区状态 
$fdisk -l               # 查看所有分区 
$swapon -s              # 查看所有交换分区
$hdparm -i /dev/hda     # 查看磁盘参数(仅适用于IDE设备) 
$dmesg | grep IDE       # 查看启动时IDE设备检测状况

```
### 网络

```bash
$ifconfig               # 查看所有网络接口的属性
$iptables -L            # 查看防火墙设置 
$route -n               # 查看路由表 
$netstat -lntp          # 查看所有监听端口 
$netstat -antp          # 查看所有已经建立的连接
$netstat -s             # 查看网络统计信息
```
### 进程

```bash
$ps -ef                 # 查看所有进程 
$top                    # 实时显示进程状态
```
### 用户

```bash
$w                      # 查看活动用户 
$id <用户名>            # 查看指定用户信息 
$last                   # 查看用户登录日志 
$cut -d: -f1 /etc/passwd   # 查看系统所有用户 
$cut -d: -f1 /etc/group    # 查看系统所有组 
$crontab -l             # 查看当前用户的计划任务
```
### 服务

```bash
$chkconfig --list       # 列出所有系统服务 
$chkconfig --list | grep on    # 列出所有启动的系统服务
```
### 程序

```bash
$rpm -qa                # 查看所有安装的软件包
```

### 查看主板的序列号

```bash
$dmidecode | grep -i ’serial number’
```

### 用硬件检测程序kuduz探测新硬件
```bash
$service kudzu start ( or restart)
```

### 查看CPU信息
```bash
$cat /proc/cpuinfo [dmesg | grep -i 'cpu'][dmidecode -t processor]
```

### 查看内存信息
```bash
$cat /proc/meminfo [free -m][vmstat]
```

### 查看板卡信息
```bash
$cat /proc/pci
```

### 查看显卡/声卡信息
```bash
$lspci |grep -i ‘VGA’[dmesg | grep -i 'VGA']
```

### 查看网卡信息
```bash
$dmesg | grep -i ‘eth’[cat /etc/sysconfig/hwconf | grep -i eth][lspci | grep -i 'eth']
```

### 查看PCI信息
```bash
$lspci (相比cat /proc/pci更直观）
```
### 查看USB设备
```bash
$cat /proc/bus/usb/devices
```
### 查看键盘和鼠标
```bash
$cat /proc/bus/input/devices
```
### 查看系统硬盘信息和使用情况
```bash
$fdisk & disk – l & df
```
### 查看各设备的中断请求(IRQ)
```bash
$cat /proc/interrupts
```

### 查看系统体系结构
```bash
$uname -a
```
### 查看及启动系统的32位或64位内核模式
```bash
$isalist –v [isainfo –v][isainfo –b]
```
### dmidecode查看硬件信息，包括bios、cpu、内存等信息
* 测定当前的显示器刷新频率
```bash
$dmidecod /usr/sbin/ffbconfig –rev \?
```

* 查看系统配置
```bash
$dmidecod /usr/platform/sun4u/sbin/prtdiag –v
```

### 查看当前系统中已经应用的补丁
```bash
$showrev –p
```
### 显示当前的运行级别
```bash
$who –rH
```

### 查看当前的bind版本信息
```bash
$nslookup –class=chaos –q=txt version.bind
```

### 查看硬件信息
```bash
$dmesg | more 
```
### 显示外设信息, 如usb，网卡等信息
```bash
$lspci 
```

### /proc 中文件中包含系统特定信息：
```bash
$Cpuinfo        #主机CPU信息
$Dma            #主机DMA通道信息
$Filesyst#ems   #文件系统信息
$Interrup#ts    #主机中断信息
$Ioprots        #主机I/O端口号信息
$Meninfo        #主机内存信息
$Version    #Linux内存版本信息
```


## apt-get & dpkg 相关命令


### 更新软件包列表
```bash
$apt-get update
```
### 安装一个新软件包（参见下文的aptitude） 
```bash
$apt-get install packagename
```
### 卸载一个已安装的软件包（保留配置文件） 
```bash
$apt-get remove packagename
```
### 卸载一个已安装的软件包（删除配置文件） 

```bash
$apt-get --purge remove packagename
```
### 强制卸载软件包
```bash
$dpkg --force-all --purge packagename 
```
### 清除已经删掉的软件 
```bash
$apt-get autoclean
``` 
### 清除软件备份 
```bash
$apt-get clean
```
### 更新所有已安装的软件包 
```bash
$apt-get upgrade
```
### 将系统升级到新版本 
```bash
$apt-get dist-upgrade
```
### 在软件包列表中搜索字符串 
```bash
$apt-cache search string
```
### 列出所有与模式相匹配的软件包
```bash
$dpkg -l package-name-pattern
```
### 显示软件包信息
```bash
$apt-cache showpkg pkgs
```
### 打印可用软件包列表 
```bash
$apt-cache dumpavail
```
### 显示软件包记录，类似于dpkg –print-avail 
```bash
$apt-cache show pkgs
```
### 打印软件包列表中所有软件包的名称。
```bash
$apt-cache pkgnames
```
### 这个文件属于哪个已安装软件包
```bash
$dpkg -S file
```
### 列出软件包中的所有文件
```bash
$dpkg -L package
```
## 查看Ubuntu 版本
### 方法1
在终端中执行下列指令
```bash
$cat /etc/issue
```
### 方法2
```bash
$sudo lsb_release -a
```