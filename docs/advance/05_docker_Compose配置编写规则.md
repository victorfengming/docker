### yaml规则
docker-compose.yaml核心

https://docs.docker.com/compose/compose-file/#compose-file-structure-and-examples

```
# 3层

version: " # 版本
services: # 服务
	服务1:web
		# 服务配置
		images
		build
		network
		......
	服务2:redis
		...
	服务3:redis
		...
		
# 其他配置
volumes:
networks:
configs:

		
```



![1597807527782](05_docker_Compose%E9%85%8D%E7%BD%AE%E7%BC%96%E5%86%99%E8%A7%84%E5%88%99.assets/1597807527782.png)