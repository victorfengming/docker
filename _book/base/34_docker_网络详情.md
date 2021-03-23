# docker0网络


## 理解docker0
清空所有环境

```bash

# 测试


[root@iz8g9301trfnpxz home]# docker rmi -f $(docker images -aq)
Untagged: mycentos:0.1



# 获取当前ip地址
[root@iz8g9301trfnpxz home]# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:16:3e:14:13:0a brd ff:ff:ff:ff:ff:ff
    inet 172.24.40.74/18 brd 172.24.63.255 scope global dynamic eth0
       valid_lft 315035939sec preferred_lft 315035939sec
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN 
    link/ether 02:42:4a:5e:af:07 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever



```
三个网络
```bash
# 问题:docker 是如何处理容器网络访问的?
```


```bash

# 测试
[root@iz8g9301trfnpxz home]# docker run -d -P --name tomcat03 tomcat

# 查看容器内地址
[root@iz8g9301trfnpxz home]# docker run -d -P --name tomcat03 tomcat
fc3283ac304d54cfa0f04b5f1904a36e8bc452b99882af575c255206a7308072
[root@iz8g9301trfnpxz home]# docker exec -it tomcat03 ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
72: eth0@if73: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever

# 思考 linux 能不能 ping 通这个容器内部地址
[root@iz8g9301trfnpxz home]# ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.049 ms
64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.050 ms

# linux 能够访问容器内部
```

原理
1. 我们没启动一个docker 容器,docker 就会给docker容器分配一个ip,我们只要安装了docker,就会有一个网卡docker0桥接模式,使用的技术是evth-pair技术!

再次测试ip addr

2. 在一个容器中测试,发现由多了一个网卡
- 我们发现这个容器带来的网卡,都是一对一对儿的
- evth-pair 就是一对的虚拟设备接口,他们都是成对出现的,一段连着协议,一段彼此相连
- 正因为有这个特性,evth-pair 充当一个桥梁,连接各种虚拟网络设备的
- OpenStac,Docker容器之间的连接,OVS的连接,都是使用evth-pair技术


3. 我们来测试下tomcat01和tomcat02是否可以ping通!
```bash
docker exec -it tomcat02 ping 172.18.0.2
# 结论:容器和容器之间是可以互相ping通的
```

绘制一个网络模型图:



