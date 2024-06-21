
首先，我们需要了解Overlay2是一种在Docker中用于实现镜像分层的存储驱动程序。但随着我们不断地使用Docker创建、启动和停止容器，Overlay2可能会存储大量的临时文件，从而占用大量的磁盘空间。因此，需要清理这些临时文件以释放磁盘空间。以下是具体的步骤：
## 1. 停止所有正在运行的容器

使用下面的命令来停止所有正在运行的Docker容器：
```sh
docker stop $(docker ps -aq)
```
注：上述命令中的“-aq”选项表示列出所有容器ID，不管它们是否在运行中。
## 2. 删除所有未使用的Docker镜像

使用下面的命令来删除所有未使用的Docker镜像：
```sh
docker image prune -a
```
注：上述命令中的“-a”选项表示删除所有未被使用的镜像，包括Docker文件系统中的dangling镜像。（Docker文件系统指的是镜像和容器共享的文件系统）
## 3. 删除所有未使用的Docker卷

使用下面的命令来删除所有未使用的Docker卷：
```sh
docker volume prune
```
## 4. 删除所有未使用的Docker网络

使用下面的命令来删除所有未使用的Docker网络：
```sh
docker network prune
```
## 5. 清理Overlay2存储驱动的临时文件

使用下面的命令来清理Overlay2存储驱动的临时文件：
```sh
docker system prune --all --force --volumes
```

### 示例1：清理单个节点

假设我们正在使用“docker_host1”主机上的Docker，并需要清理Overlay2占用的磁盘空间。使用SSH连接到“docker_host1”主机，并执行以下命令：
```
ssh user@docker_host1
docker stop $(docker ps -aq)
docker image prune -a
docker volume prune
docker network prune
docker system prune --all --force --volumes
```
这将停止所有正在运行的容器，并清理所有未使用的镜像、卷和网络，并清理Overlay2存储驱动的临时文件。

### 示例2：清理Docker Swarm集群

假设我们正在使用Docker Swarm集群，并且需要清理Overlay2占用的磁盘空间。使用SSH连接到Swarm管理节点，并执行以下命令：

```sh
ssh user@swarm_manager1
docker node ls
```

这将列出所有加入了Swarm集群的节点。选择一个节点并使用SSH连接进去，然后执行上述删除命令。重复这个过程，直到所有节点都被清理完毕。

注：在Swarm集群中需要逐个节点进行清理，否则可能会导致数据丢失或Docker服务无法正常工作。