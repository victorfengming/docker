### 体会

弹性,负载,扩缩容

以后告别 docker run!

如果你还是用docker run  那你docker 还是玩具状态

dokcer-compose up! 启动一个项目.单机!

集群: swarm `docker service`

容器 => 服务! 

redis! = 3份! 容器!

集群: 高可用, web-> redis(3台,不同的机器上!)



![1597819728670](11_docker_Swarm%E9%9B%86%E7%BE%A4%E5%BC%B9%E6%80%A7%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1.assets/1597819728670.png)



容器 => 服务 => 副本!

redis服务 => 10个副本 ! (同时开启10个redis容器)

![1597819852922](11_docker_Swarm%E9%9B%86%E7%BE%A4%E5%BC%B9%E6%80%A7%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1.assets/1597819852922.png)

体验: 创建服务,动态扩展服务,动态



![1597819950319](11_docker_Swarm%E9%9B%86%E7%BE%A4%E5%BC%B9%E6%80%A7%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1.assets/1597819950319.png)



灰度发布:金丝雀发布!

停止

淘宝! 不可能有404

就是说升级不影响发布

![1597820116318](11_docker_Swarm%E9%9B%86%E7%BE%A4%E5%BC%B9%E6%80%A7%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1.assets/1597820116318.png)

```cmd
docker run # 容器启动 ! 不具有扩缩容器
docker service # 服务! 具有扩缩容器,滚动更新!
```

查看服务

![1597820201431](11_docker_Swarm%E9%9B%86%E7%BE%A4%E5%BC%B9%E6%80%A7%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1.assets/1597820201431.png)

动态扩缩容

![1597820731457](11_docker_Swarm%E9%9B%86%E7%BE%A4%E5%BC%B9%E6%80%A7%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1.assets/1597820731457.png)

服务,集群中任意的节点都可以访问.服务可以有多个副本动态扩缩容实现高可用!

---

弹性,扩缩容 十分重要

10台服务器 比如 aliyun 10000台服务器 , 卖给别人 ! 虚拟化! 

服务的高可用,任何的企业

delete the password

 https://www.bilibili.com/video/BV1kv411q7Qc?p=11 

移除!

docker swarm 其实并不难

只要会搭建集群,会启动服务,动态管理容器就可以了!



