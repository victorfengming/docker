# Docker Compose

## 简介

docker

dockerfile build run 手动操作，单个容器

微服务。100个微服务！ 依赖关系

Docker Compose 来轻松高效的管理容器。定义运行多个容器



k8s描述文件

> 官方介绍

定义，运行，多个容器。



![1597803399426](02_docker_DockerCompose%E4%BB%8B%E7%BB%8D.assets/1597803399426.png)

所有的环境都可以使用我们的docker compose

三个步骤：

- DockerFile保证我们的项目在任何地方可以运行
- 
  - services什么是服务
  - docker-compose。yml这个文件怎么写
- 启动项目

![1597803633532](02_docker_DockerCompose%E4%BB%8B%E7%BB%8D.assets/1597803633532.png)

作用： 批量容器编排。

> 我自己理解

Compose 是Docker官方的开源项目。需要安装！这个可不是在docker里面的

`dockerfile`让程序在任何地方运行.web服务.redis,mysql,nginx,...多个容器.

这么多环境要是一个一个启动,太麻烦了,所以Compose应运而生

![1597803833899](02_docker_DockerCompose%E4%BB%8B%E7%BB%8D.assets/1597803833899.png)

docker-compose up 100个服务.

Compose:重要的概念

- 服务services,容器.应用.(web应用,redis,mysql,...)
- 项目project.一组关联的容器.博客.web,mysql、 wp

未来我们的搭建肯定是要用Compose的,不可能用docker跑起来

### docker Swarm

集群方式的部署,4台阿里云服务器,2 4g

