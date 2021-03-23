
# DockerFile

dockerfile是用来构建docker镜像的文件! 命令参数脚本

构建步骤:
1. 编写一个dockerfile 文件

2. docker build 构建成为一个镜像

3. docker run 运行镜像

4. docker push 发布镜像(dockerHub,阿里云镜像仓库!)

查看一下官网上面再怎么做的


很多官方镜像都是基础包,很多功能都没有
ping clear 这种命令需要自己安装 centos里面不是基础包,我们需要自己来搭建自己的镜像

官方既然可以制作镜像,那我们也可以

## docker file 介绍
## docker file 构建过程
很多指令:

基础知识:

1. 每个保留关键字都是必须是大写字母
2. 执行从上到下顺序执行

3. # 表示注释

4. 每个指令都会创建提交一个新的镜像层,并提交!

dockerfile是面向开发的,我们以后要发布项目,做镜像,就需要编写dockerfile文件,这个文件十分简单!

docker镜像逐渐成为企业交付标准,必须要掌握

Dockerfile: 构建文件,定义了一切步骤,源代码

DockerImages:通过dockerfile 构建生成的镜像,最终发布和运行的产品,原来是jar war

docker容器: 容器就是镜像运行起来提供服务器.


