# nanopi 开发WiringPi时 报错 “undefined rference to erypt pow shm_open”

## 基于nanopiNEO4（RK3399），使用gcc编译 WiringPi相关代码时出现报错

执行命令：
```bash
$ gcc -wall -o test test.c -lwiringPi -lpthread 
```
报错：
```bash
/lib.libwiringPi.so :undefined reference to 'crypt'
/lib.libwiringPi.so :undefined reference to 'pow'
/lib.libwiringPi.so :undefined reference to 'shm_open'
collect2:error : ld returned 1 exit status
```
![error](/images/wringpi_error/1.png)

## 错误原因
缺少以上3个库，解决方法为：在shell中输入
```bash
$ man crypt
```
![crypt](/images/wringpi_error/2.png)

## 最终命令
```bash
$ gcc -wall -o test test.c -lwiringPi -lpthread -lcrypt -lm -lrt 
```

