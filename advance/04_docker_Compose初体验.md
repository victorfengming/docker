# Compose初体验

体验

地址:  https://docs.docker.com/compose/gettingstarted/ 

**看一看官方怎么说**

---

# Get started with Docker Compose

*Estimated reading time: 10 minutes*

On this page you build a simple Python web application running on Docker Compose. The application uses the Flask framework and maintains a hit counter in Redis. While the sample uses Python, the concepts demonstrated here should be understandable even if you’re not familiar with it.

这里面用到了python中的flask框架

python应用,计数器

---

一顿操作开始

---

1. 创建文件夹

```cmd
[root@iz8g9301trfnpxz home]# mkdir composetest
[root@iz8g9301trfnpxz home]# cd composetest/
[root@iz8g9301trfnpxz composetest]# ll
total 0
[root@iz8g9301trfnpxz composetest]# vim app.py
[root@iz8g9301trfnpxz composetest]# vim requirements.txt
[root@iz8g9301trfnpxz composetest]# vim Dockerfile
```

创建app.py文件内容

```python
import time

import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)


def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)


@app.route('/')
def hello():
    count = get_hit_count()
    return 'Hello World! I have been seen {} times.\n'.format(count)
```

创建requirements.txt内容

```
flask
redis
```

创建dockerfile

```cmd
FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP app.py
ENV FLASK_RUN_HOST 0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
EXPOSE 5000
COPY . .
CMD ["flask", "run"]

```

定义服务

## Step 3: Define services in a Compose file

Create a file called `docker-compose.yml` in your project directory and paste the following:

```
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: "redis:alpine"
```

执行

## Step 4: Build and run your app with Compose

1. From your project directory, start up your application by running `docker-compose up`.

## 总结

1. 应用 app.py
2. Dockerfile应用打包为镜像
3. Docker-compose yaml文件(定义整个服务,需要的环境.web, redis) 完整的上线服务!
4. 启动compose项目(docker-compose up)

## 流程

1. 创建网络
2. 执行Docker-compose.yml文件
3. 启动服务

docker-compose yaml

Creating composetest_web_1 ... done

Creating composetest_redis_1 ... done

1. 文件名 composetest

2. 服务

   1. ```
      version: '3'
      services:
        web:
          build: .
          ports:
            - "5000:5000"
        redis:
          image: "redis:alpine"
      ```

   



---

compose up 后,会自动帮我们安装docker需要的镜像

比如python

![1597806456881](04_docker_Compose%E5%88%9D%E4%BD%93%E9%AA%8C.assets/1597806456881.png)

mysql:3306

10个容器实例:mysql 10, ip(项目中的内容都在同一个网络下面.域名访问)

![1597806579451](04_docker_Compose%E5%88%9D%E4%BD%93%E9%AA%8C.assets/1597806579451.png)

如果在同一个网络下,我们可以直接通过域名访问.

![1597806827606](04_docker_Compose%E5%88%9D%E4%BD%93%E9%AA%8C.assets/1597806827606.png)

可以一键启动,服务,都是可以的

### docker小结
1. Docker镜像.run-> 容器
2. DockerFile构建镜像 (服务打包)
3. docker-compose启动项目(编排,多个微服务/环境)
4. docker网络
5. 