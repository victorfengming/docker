
# Compose安装
1.下载

![1597804111053](03_docker_Compose%E5%AE%89%E8%A3%85.assets/1597804111053.png)

上面那个可能会很慢

用这个要快一点儿

```cmd
curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.5/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
```

试一下

```cmd
[root@iz8g9301trfnpxz ~]# curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.5/docker-compose-`uname -s` - `uname -m` > /usr/local/bin/docker-compose
curl: option -: is unknown
curl: try 'curl --help' or 'curl --manual' for more information
[root@iz8g9301trfnpxz ~]# curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.5/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   423  100   423    0     0    502      0 --:--:-- --:--:-- --:--:--   501
100 16.7M  100 16.7M    0     0  8412k      0  0:00:02  0:00:02 --:--:-- 24.3M
[root@iz8g9301trfnpxz ~]# cd /usr/local/bin/
[root@iz8g9301trfnpxz bin]# ls
docker-compose  jemalloc-config  jemalloc.sh  jeprof  libmcrypt-config  luajit  luajit-2.0.4  mcrypt  mdecrypt
[root@iz8g9301trfnpxz bin]# 

```

安装成功

```cmd
[root@iz8g9301trfnpxz bin]# sudo chmod +x docker-compose 
[root@iz8g9301trfnpxz bin]# docker-compose 
Define and run multi-container applications with Docker.


[root@iz8g9301trfnpxz bin]# docker-compose -version
docker-compose version 1.25.5, build 8a1c60f6

```



