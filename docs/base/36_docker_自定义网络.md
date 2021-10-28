# docker0自定义网络



查看所有的网络
```bash
[root@iz8g9301trfnpxz home]# docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
68c30b64280c        bridge              bridge              local
e5373821382b        host                host                local
bc64d000f692        none                null                local

```
网络模式


|网络模式|解释|
|---|---|
|bridge|桥接docker(默认,自己创建也是bridge模式)|
|none|不配置网络|
|host|和宿主机共享网络|
|container|容器网络连通!(用的少!局限很大)|


测试
```bash
# 我们直接启动的命令 --net bridge ,而这个就是我们的docker0
[root@iz8g9301trfnpxz home]# docker run -d -P --name tomcat01 tomcat
[root@iz8g9301trfnpxz home]# docker run -d -P --name tomcat01 --net bridge tomcat
120ae6154cb8a090d7bf43c5b25620fa6913afd1eae5426ec6dc3fb95de1e4b2

# docker0 特点: 默认,域名不能访问,--link可以打通连接!

# 我们可以自定义一个网络! 
# --driver bridge
# --subnet 192.168.0.0/16   192.168.0.2
# --gateway 192.168.0.1 
[root@iz8g9301trfnpxz home]# docker network create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 mynet
8a651bded67f27601cc17590df67043bad863e8b9e3b8b3f9b636bf8ebbb30f8

[root@iz8g9301trfnpxz home]# docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
68c30b64280c        bridge              bridge              local
e5373821382b        host                host                local
8a651bded67f        mynet               bridge              local
bc64d000f692        none                null                local

```

查看一下

```bash

[root@iz8g9301trfnpxz home]# docker network inspect mynet
[
    {
        "Name": "mynet",
        "Id": "8a651bded67f27601cc17590df67043bad863e8b9e3b8b3f9b636bf8ebbb30f8",
        "Created": "2020-08-03T09:57:58.644192346+08:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "192.168.0.0/16",
                    "Gateway": "192.168.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]
[root@iz8g9301trfnpxz home]# 



```