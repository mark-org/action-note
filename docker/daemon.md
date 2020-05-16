#  "registry-mirrors": ["https://hub-mirror.c.163.com"],

# Linux上配置文件的默认位置是 /etc/docker/daemon.json。
该--config-file标志可用于指定非默认位置。
重启后才生效
```
systemctl restart docker.service


{
//配置仓库镜像地址
"registry-mirrors": ["https://kzflb.mirror.aliyuncs.com"],
//默认http私有仓库不能访问，设置后才可以
"insecure-registries": ["http://192.168.2.196"],
//开启docker-API远程访问
"hosts": ["tcp://0.0.0.0:2375","unix:///var/run/docker.sock"]
}

```
registry-mirrors: it replaces the daemon registry mirrors with a new set of registry mirrors.
If some existing registry mirrors in daemon’s configuration are not in newly reloaded registry mirrors,
these existing ones will be removed from daemon’s config.

