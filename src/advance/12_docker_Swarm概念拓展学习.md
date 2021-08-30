
# 概念总结
#### swarm

集群的管理编号.docker可以初始化一个swarm集群,其他节点可以加入.(管理,工作者)

#### Node

就是一个docker节点.多个节点就组成了一个网络集群(管理,工作者)

#### Service

任务,可以在管理节点或者工作节点来运行,核心! 用户访问! 

#### Task

容器内的命令,细节任务! 

![1597885039727](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885039727.png)



一个大的服务里面有4个副本,每个副本就是一个小的task

![1597885095828](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885095828.png)



![1597885112268](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885112268.png)

命令 -> 管理 -> api -> 调度 -> 工作节点 (创建Task容器未出创建!)

在k8s的官网

![1597885289414](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885289414.png)

![1597885298060](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885298060.png)

![1597885343185](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885343185.png)

![1597885656917](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885656917.png)

拓展: 网络模式 : "PublishMode":"ingress"

Swarm:

![1597885708313](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597885708313.png)



Overlay:

ingress: 特殊的Overlay网络! 负载均衡的功能! IPVS VIP!

虽然docker 在4台机器上,实际上网络是同一个! ingress 网络,是一个特殊的Overlay网络

![1597886043666](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597886043666.png)



网络变成了一个整体

![1597886091760](12_docker_Swarm%E6%A6%82%E5%BF%B5%E6%8B%93%E5%B1%95%E5%AD%A6%E4%B9%A0.assets/1597886091760.png)

