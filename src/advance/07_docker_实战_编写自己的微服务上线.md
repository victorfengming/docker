
# 微服务上线
实战

1. 编写项目微服务
2. dockerfile构建镜像
3. docker-compose.yaml编排项目
4. 丢到服务器 docker-compose up

小结:

未来项目只要有docker-compose文件.按照这个规则,启动编排容器

公司: docker-compose.直接启动

网上开源项目:docker-compose一键搞定

假设项目要重新部署打包

```
docker-compose up --build # 重新构建
```

总结:

**工程,服务,容器,**

项目compose:三层

- 工程Project

- 服务 服务

- 容器 运行实例 ! docker k8s 容器 pods kuber controler apply -f"xxxx.yaml"

  

docker compose 搞定

