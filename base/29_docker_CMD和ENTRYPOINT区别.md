
# CMD和ENTRYPOINT区别

https://www.bilibili.com/video/BV1og4y1q7M4?p=29

测试cmd命令

```bash

[root@iz8g9301trfnpxz dockerfile]# cat dockerfile-cmd-test 
FROM centos
CMD ["ls","-a"]

 

```
构建镜像,执行
```bash


[root@iz8g9301trfnpxz /]# ls
bin  boot  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@iz8g9301trfnpxz /]# cd /home/dockerfile/
[root@iz8g9301trfnpxz dockerfile]# ls
mydocker-centos
[root@iz8g9301trfnpxz dockerfile]# vim dockerfile-cmd-test
[root@iz8g9301trfnpxz dockerfile]# docker build -f dockerfile-cmd-test -t cmdtest .
Sending build context to Docker daemon  3.072kB
Step 1/2 : FROM centos
 ---> 831691599b88
Step 2/2 : CMD ["ls","-a"]
 ---> Running in e6dca2412833
Removing intermediate container e6dca2412833
 ---> cef9ed46536a
Successfully built cef9ed46536a
Successfully tagged cmdtest:latest
[root@iz8g9301trfnpxz dockerfile]# 


``` 