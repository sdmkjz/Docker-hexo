# 基于Docker容器的HEXO博客

### 介绍

hexo是一个基于Node.js 快速、简洁且高效的博客框架。

Hexo 支持 GitHub Flavored Markdown 的所有功能，甚至可以整合 Octopress 的大多数插件

同时支持部署到Github Pages等平台

本镜像启动即用，部署简单，同时支持amd64/arm64架构

### 入门

创建一个新的博客容器，-p为后台运行(可选)--name=为容器名，可自行指定，使用 -v target:/app 指定您的博客位置,-p为端口映射-p 4000:4000前端口可自行更改：

```shell
docker run -p --name=hexo \
-v /blog:/app \
-p 4000:4000 \
mkjz/hexo:silm
```



```shell
docker run -p --name=hexo \
-v /blog:/app \
-p 4000:4000 \
mkjz/hexo:latest
```

**注：**

**1.silm镜像为精简版本，镜像内除hexo-cli外 没有额外安装任何软件包以及npm插件 若有diy需求 请自行访问容器使用指令安装(若为arm64架构，请在tag后指定-arm64版本 例:mkjz/hexo:silm-arm64 )**

**2.latest镜像为全量版本，包含git,hexo-permalink-pinyin,hexo-wordcount常用插件，目前只支持amd64架构**



### 访问Hexo

```shell
访问hexo博客界面 http://<ip_address>:4000  此端口可在启动命令-p中自定义
```

### 访问容器

如果您希望执行进一步的配置，即安装自定义主题与安装npm包，可以通过如下指令。访问容器 

```shell
docker exec -it hexo /bin/sh
```
## 说明

修改配置文件或添加主题后，需重启容器，网站将自动重构

```shell
docker restart 容器名
```

查看日志

```shell
docker logs 容器名
```









