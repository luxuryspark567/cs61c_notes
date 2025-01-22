---
description: docker
---

# Mac安装docker

## 一、Docker安装

### 1，安装lima：

brew install lima&#x20;

limactl start

[https://github.com/lima-vm/lima.git](https://github.com/lima-vm/lima.git)

1，查看目前运行列表，并包含其分配的名称、SSH、Status、CPU、Memory 等

$ limactl list

2，进入 shell

$ limactl shell docker

3，直接执行 shell 命令 docker ps

$ limactl shell docker docker ps

4，关闭 VM

$ limactl stop docker

5，刪除 VM

$ limactl delete docker

### 2，启动Docker

To run containers with Docker:

<pre data-overflow="wrap"><code>limactl start template://docker
<strong>export DOCKER_HOST=$(limactl list docker --format 'unix:///Users/luxu/.lima/docker//sock/docker.sock')
</strong></code></pre>

### 3，本地直接执行 docker cli 设置

To run `docker` on the host (assumes docker-cli is installed), run the following commands:

{% code overflow="wrap" %}
```
docker context create lima-docker --docker "host=unix:///Users/luxu/.lima/docker/sock/docker.sock"
docker context use lima-docker
docker run hello-world
```
{% endcode %}

## 二、Container安装并运行ubuntu 容器

从ubuntu官网找到最新的ubuntu版本，20250122为24.10版本。

目前 docker 镜像中已经有现成的镜像可以使用，下面安装的是 ubuntu 24.10 版本：

```
$ docker pull ubuntu:24.10
$ docker images 
```

![image](https://catwithtudou-5134.xlog.app/_next/image?url=https%3A%2F%2Fimg.zhengyua.cn%2Fblog%2F202402282342158.png\&w=3840\&q=75)

安装好镜像后，可以创建一个直接创建一个 ubuntu 的容器，或者创建一个映射了Mac本地文件夹的container（方便共享文件）：

```
# Option1，新增本地容器
$ docker run --name ubuntu-container -it ubuntu:24.10 bash

# Option2，新增映射到Mac本地文件夹的container，方便文件共享
docker run -it -v /Users/luxu/Documents/lima_vm:/home/lima_vm ubuntu:24.10
```

此时你就已经能使用 ubuntu 的操作系统来完成需求勒。这里也贴一下可能会用到的常用操作：

```
# 查看当前所有的容器及其状态，比如前面运行的 ubuntu-container
$ docker ps -a 
# 若容器不是运行状态，则需要启动它
$ docker start ubuntu-container
# 进行该容器的终端
$ docker exec -it ubuntu-container bash
```

## 删除container

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## 三、安装 gdb[#](https://catwithtudou-5134.xlog.app/Mac-da-jian-DockerUbuntu-huan-jing-zhi-chi-GDB?locale=zh#user-content-34-%E5%AE%89%E8%A3%85-gdb) <a href="#usercontent34-an-zhuang-gdb" id="usercontent34-an-zhuang-gdb"></a>

进入 ubuntu 容器后，就可以安装 gdb 来调试 c 语言程序了：

```
# 进入容器后更新软件包
$ apt update
# 安装 gdb
$ apt install gcc
$ apt install gdb
$ apt install cgdb
```

## 四、重新启动并且进入container

luxu@Roberts-MacBook \~ % `docker start -a -i modest_colden`

root@4ff78b092733:/#&#x20;
