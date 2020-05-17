
# Docker Volume

# Docker的数据持久化主要有两种方式：
* bind mount
* volume

** > 要么存在于host的某个指定目录中(bind mount)，要么使用docker自己管理的volume
（/var/lib/docker/volumes下）

# bind mount早期
windows和linxu的目录结构不一样
Dockerfile不能出现bind mount,这样的Dockerfile是不可移植的

# 使用volume
docker下所有的volume都在host机器上的指定目录下/var/lib/docker/volumes
```
docker run -it -v my-volume:/mydata alpine sh
```







