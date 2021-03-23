# docker0容器互联

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



