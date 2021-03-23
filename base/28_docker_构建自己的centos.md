
# 实战测试

实战测试

创建自己的centos

```shell script
# 编写dockerfile配置文件
[root@iz8g9301trfnpxz ~]# cd /home
[root@iz8g9301trfnpxz home]# mkdir dockerfile
[root@iz8g9301trfnpxz home]# ls
admin  ceshi  dockerfile  docker-test-volume  kuangshen.java  mysql  test.java
[root@iz8g9301trfnpxz home]# cd dockerfile/
[root@iz8g9301trfnpxz dockerfile]# ls
[root@iz8g9301trfnpxz dockerfile]# vim mydocker-centos
[root@iz8g9301trfnpxz dockerfile]# cat mydocker-centos 
FROM centos
MAINTAINER victor<510510280@qq.com>

ENV MYPATH /urs/local
WORKDIR $MYPATH

RUN yum -y install vim
RUN yum -y install net-tools

EXPOSE 80

CMD echo $MYPATH
CMD echo "-------------------end------------------"
CMD /bin/bash


# 通过这个文件构建镜像
```

通过build命令进行构建
# 命令 docker build -f dockerfile 文件路径 -t 镜像名
```shell script
[root@iz8g9301trfnpxz dockerfile]# docker build -f mydocker-centos -t mycentos:0.1 .
Sending build context to Docker daemon  2.048kB
Step 1/10 : FROM centos
 ---> 831691599b88
Step 2/10 : MAINTAINER victor<510510280@qq.com>
 ---> Running in 5485ccbf2672
Removing intermediate container 5485ccbf2672
 ---> 131330e2008d
Step 3/10 : ENV MYPATH /urs/local
 ---> Running in 7ddbc3982cdc
Removing intermediate container 7ddbc3982cdc
 ---> d8afdf73ae5e
Step 4/10 : WORKDIR $MYPATH
 ---> Running in ee1bb41513bc
Removing intermediate container ee1bb41513bc
 ---> 77b75be518d6
Step 5/10 : RUN yum -y install vim
 ---> Running in 4d801fad886d
CentOS-8 - AppStream                            409 kB/s | 5.8 MB     00:14    
CentOS-8 - Base                                 2.5 MB/s | 2.2 MB     00:00    
CentOS-8 - Extras                               941  B/s | 7.0 kB     00:07    
Dependencies resolved.
================================================================================
 Package             Arch        Version                   Repository      Size
================================================================================
Installing:
 vim-enhanced        x86_64      2:8.0.1763-13.el8         AppStream      1.4 M
Installing dependencies:
 gpm-libs            x86_64      1.20.7-15.el8             AppStream       39 k
 vim-common          x86_64      2:8.0.1763-13.el8         AppStream      6.3 M
 vim-filesystem      noarch      2:8.0.1763-13.el8         AppStream       48 k
 which               x86_64      2.21-12.el8               BaseOS          49 k

Transaction Summary
================================================================================
Install  5 Packages

Total download size: 7.8 M
Installed size: 31 M
Downloading Packages:
(1/5): gpm-libs-1.20.7-15.el8.x86_64.rpm        219 kB/s |  39 kB     00:00    
(2/5): vim-filesystem-8.0.1763-13.el8.noarch.rp 434 kB/s |  48 kB     00:00    
(3/5): which-2.21-12.el8.x86_64.rpm             2.5 MB/s |  49 kB     00:00    
(4/5): vim-enhanced-8.0.1763-13.el8.x86_64.rpm  813 kB/s | 1.4 MB     00:01    
(5/5): vim-common-8.0.1763-13.el8.x86_64.rpm    839 kB/s | 6.3 MB     00:07    
--------------------------------------------------------------------------------
Total                                           805 kB/s | 7.8 MB     00:09     
warning: /var/cache/dnf/AppStream-02e86d1c976ab532/packages/gpm-libs-1.20.7-15.el8.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID 8483c65d: NOKEY
CentOS-8 - AppStream                            862 kB/s | 1.6 kB     00:00    
Importing GPG key 0x8483C65D:
 Userid     : "CentOS (CentOS Official Signing Key) <security@centos.org>"
 Fingerprint: 99DB 70FA E1D7 CE22 7FB6 4882 05B5 55B3 8483 C65D
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : which-2.21-12.el8.x86_64                               1/5 
  Installing       : vim-filesystem-2:8.0.1763-13.el8.noarch                2/5 
  Installing       : vim-common-2:8.0.1763-13.el8.x86_64                    3/5 
  Installing       : gpm-libs-1.20.7-15.el8.x86_64                          4/5 
  Running scriptlet: gpm-libs-1.20.7-15.el8.x86_64                          4/5 
  Installing       : vim-enhanced-2:8.0.1763-13.el8.x86_64                  5/5 
  Running scriptlet: vim-enhanced-2:8.0.1763-13.el8.x86_64                  5/5 
  Running scriptlet: vim-common-2:8.0.1763-13.el8.x86_64                    5/5 
  Verifying        : gpm-libs-1.20.7-15.el8.x86_64                          1/5 
  Verifying        : vim-common-2:8.0.1763-13.el8.x86_64                    2/5 
  Verifying        : vim-enhanced-2:8.0.1763-13.el8.x86_64                  3/5 
  Verifying        : vim-filesystem-2:8.0.1763-13.el8.noarch                4/5 
  Verifying        : which-2.21-12.el8.x86_64                               5/5 

Installed:
  gpm-libs-1.20.7-15.el8.x86_64         vim-common-2:8.0.1763-13.el8.x86_64    
  vim-enhanced-2:8.0.1763-13.el8.x86_64 vim-filesystem-2:8.0.1763-13.el8.noarch
  which-2.21-12.el8.x86_64             

Complete!
Removing intermediate container 4d801fad886d
 ---> 9458be1e73c5
Step 6/10 : RUN yum -y install net-tools
 ---> Running in c764b7488e52
Last metadata expiration check: 0:00:17 ago on Fri Jul 31 06:20:50 2020.
Dependencies resolved.
================================================================================
 Package         Architecture Version                        Repository    Size
================================================================================
Installing:
 net-tools       x86_64       2.0-0.51.20160912git.el8       BaseOS       323 k

Transaction Summary
================================================================================
Install  1 Package

Total download size: 323 k
Installed size: 1.0 M
Downloading Packages:
net-tools-2.0-0.51.20160912git.el8.x86_64.rpm   3.4 MB/s | 323 kB     00:00    
--------------------------------------------------------------------------------
Total                                           208 kB/s | 323 kB     00:01     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : net-tools-2.0-0.51.20160912git.el8.x86_64              1/1 
  Running scriptlet: net-tools-2.0-0.51.20160912git.el8.x86_64              1/1 
  Verifying        : net-tools-2.0-0.51.20160912git.el8.x86_64              1/1 

Installed:
  net-tools-2.0-0.51.20160912git.el8.x86_64                                     

Complete!
Removing intermediate container c764b7488e52
 ---> 7e388732db7d
Step 7/10 : EXPOSE 80
 ---> Running in 3805ab7a1061
Removing intermediate container 3805ab7a1061
 ---> de64af90d6a6
Step 8/10 : CMD echo $MYPATH
 ---> Running in 30d1c0c9ba45
Removing intermediate container 30d1c0c9ba45
 ---> 0dcdb63da784
Step 9/10 : CMD echo "-------------------end------------------"
 ---> Running in 5ea7cbe4f0c7
Removing intermediate container 5ea7cbe4f0c7
 ---> 146bc756b80a
Step 10/10 : CMD /bin/bash
 ---> Running in 537d8346e6be
Removing intermediate container 537d8346e6be
 ---> 3f4f73543aa2
Successfully built 3f4f73543aa2
Successfully tagged mycentos:0.1
[root@iz8g9301trfnpxz dockerfile]# 

```
现在我们使用就可以用了
```shell script
[root@iz8g9301trfnpxz dockerfile]# docker images
REPOSITORY            TAG                 IMAGE ID            CREATED              SIZE
mycentos              0.1                 3f4f73543aa2        About a minute ago   287MB
kuangshen/centos      1.0                 5c7e025fc4ff        4 hours ago          215MB
tomcat02              1.0                 b17b415625d5        6 hours ago          657MB
tomcat                latest              9a9ad4f631f8        2 days ago           647MB
portainer/portainer   latest              62771b0b9b09        8 days ago           79.1MB
mysql                 5.7                 8679ced16d20        8 days ago           448MB
nginx                 latest              8cf1bfb43ff5        9 days ago           132MB
redis                 latest              50541622f4f1        9 days ago           104MB
centos                latest              831691599b88        6 weeks ago          215MB
elasticsearch         7.6.2               f29a1ee41030        4 months ago         791MB
elasticsearch         latest              5acf0e8da90b        22 months ago        486MB
[root@iz8g9301trfnpxz dockerfile]# docker run -it mycentos:0.1
[root@88886ca9deb0 local]# pwd
/urs/local
[root@88886ca9deb0 local]# 

```
对比之前原生的,centos

我们增加的镜像

我们可以列出咱们的本地镜像的变更历史


