# 压缩相关问题

## 1. 如何修复“tar：Exiting with failure status due to previous errors”
在使用tar 解压压缩包时出现报错 
```
tar: Exiting with failure status due to previous errors
```
解决方案：不具备读写权限,修改文件权限或者在解压命令前加上 “sudo”

## 2.解压一般文件 
#### tar 为linux系统中比较常用的命令，它的一般用法为：

```bash
tar [参数] [文件内容]
```

####  一般的参数

* 必选参数：

        -A 新增压缩文件到已存在的压缩

        -B 设置区块大小

        -c 建立新的压缩文件

        -d 记录文件的差别

        -r 添加文件到已经压缩的文件

        -u 添加改变了和现有的文件到已经存在的压缩文件

        -x 从压缩的文件中提取文件

        -t 显示压缩文件的内容

        -z 支持gzip解压文件

        -j 支持bzip2解压文件

        -Z 支持compress解压文件

        -v 显示操作过程

        -l 文件系统边界设置

        -k 保留原有文件不覆盖

        -m 保留文件不被覆盖

        -W 确认压缩文件的正确性


* 可选参数如下：

        -b 设置区块数目

        -C 切换到指定目录

        -f 指定压缩文件

        --help 显示帮助信息

        --version 显示版本信息

#### 一般用法

* 解压缩：

```tar xvf FileName.tar```

* 压缩  ：

```tar cvf FileName.tar DirName```


## 3. 其他常用解压/压缩命令

1. gz

    解压1：

     ```gunzip FileName.gz```

    解压2：

    ```gzip -d FileName.gz```

    压缩：

    ```gzip FileName```

2. tar.gz 和 tgz

    解压：

    ```tar zxvf FileName.tar.gz```

    压缩：

    ```tar zcvf FileName.tar.gz DirName```

3. bz2

    解压1：

    ```bzip2 -d FileName.bz2```

    解压2：

    ```bunzip2 FileName.bz2```

    压缩： 

    ```bzip2 -z FileName```

4. tar.bz2

    解压：

    ```tar jxvf FileName.tar.bz2```

    压缩：

    ```tar jcvf FileName.tar.bz2 DirName```


5. bz

    解压1：

    ```bzip2 -d FileName.bz```

    解压2：

    ```bunzip2 FileName.bz```


6. tar.bz

    解压：

    ```tar jxvf FileName.tar.bz```

7. Z

    解压：

    ```uncompress FileName.Z```

    压缩：

    ```compress FileName```


8. tar.Z

    解压：

    ```tar Zxvf FileName.tar.Z```

    压缩：

    ```tar Zcvf FileName.tar.Z DirName```


9. zip

    解压：

    ```unzip FileName.zip```

    压缩：

    ```zip FileName.zip DirName```

10. rar

    解压：

    ```rar x FileName.rar```

    压缩：

    ```rar a FileName.rar DirName ```

11. 7z
    解压：
    
    ```7z x manager.7z -r -o /home/xx```
     *   x 代表解压缩文件，并且是按原始目录解压（还有个参数 e 也是解压缩文件，但其会将所有文件都解压到根下，而不是自己原有的文件夹下）
     *   manager.7z 是压缩文件.这里大家要换成自己的。如果不在当前目录下要带上完整的目录
     *   -r 表示递归所有的子文件夹
     *   -o 是指定解压到的目录，这里大家要注意-o后是没有空格的直接接目录
  
    
    压缩：
    ```7z a -t7z -r manager.7z /home/manager/*```
    
     * a 代表添加文件／文件夹到压缩包
     * -t 是指定压缩类型 一般我们定为7z
     * -r 表示递归所有的子文件夹，manager.7z 是压缩好后的压缩包名，/home/manager/* 是要压缩的目录，＊是表示该目录下所有的文件。
   

## 4. 制作根文件系统rootfs压缩包 rootfs
``` 
tar cjvf rootfs.tar.bz2 .
```

