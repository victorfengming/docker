# Swarm

工作模式

Docker Engine1.12 introduce Swarm mode that enables you to create a cluster of one or more Docker 

![1597817496587](09_docker_Swarm%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA.assets/1597817496587.png)

If you haven't already ,read through the swarm mode overview and key concepts.

# 搭建集群

![1597818025202](09_docker_Swarm%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA.assets/1597818025202.png)

![1597818036576](09_docker_Swarm%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA.assets/1597818036576.png)

![1597818207034](09_docker_Swarm%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA.assets/1597818207034.png)



私网,公网

![1597818346437](09_docker_Swarm%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA.assets/1597818346437.png)

初始化节点`docker swarm init`

docker swarm join 加入一个节点!

```
# 获取令牌
docker swarm join-token manager
docker swarm join-token worker
```

![1597818452674](09_docker_Swarm%E9%9B%86%E7%BE%A4%E6%90%AD%E5%BB%BA.assets/1597818452674.png)

把后面的节点搭建进去

100台服务器

1. 生成主节点

2. 加入(管理者,worker)

   目标:双主双从!