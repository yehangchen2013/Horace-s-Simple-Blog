# 定义函数 #

### 定义task函数快速查看任务 ###

```shell
# 定义一个名为task的函数
task() {
  # 将传入的参数存储在变量中
  search_term="$1"
  # 运行ps aux命令并过滤结果
  ps aux | grep "$search_term" | grep -v "grep"
}

# 保存文件后，使更改生效
source ~/.bashrc  # 如果你用的是bash
source ~/.zshrc   # 如果你用的是zsh

```

### 定义pid函数快速查看任务 ###

```shell
# 定义一个名为task的函数
pid() {
  # 将传入的参数存储在变量中
  search_term="$1"
  # 运行ps aux命令并过滤结果
  ps aux | grep "$search_term" | grep -v "grep" | awk '{print $2}'
}

# 保存文件后，使更改生效
source ~/.bashrc  # 如果你用的是bash
source ~/.zshrc   # 如果你用的是zsh

```

### 定义docker_ip函数快速查看ip ###

```shell
function docker_ip() {
    docker inspect --format='{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq) $1
}
```