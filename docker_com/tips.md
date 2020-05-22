
# docker run --rm 
* Automatically remove the container when it exits
* Docker容器退出时，默认容器内部的文件系统仍然被保留，以方便调试并保留用户数据
* 对于foreground容器，由于其只是在开发调试过程中短期运行，其用户数据并无保留的必要，
设置--rm，这样在容器退出时能够自动清理容器内部的文件系统。
--rm选项不能与-d同时使用。
--rm选项也会清理容器的匿名data volumnes,等价于在容器退出后，执行docker rm -v

# Detached(-d)
* 当运行在容器的根进程退出时，以detached模式启动的容器也退出。
* 以detached模式运行的容器当它停止时无法自动删除，因此-rm选项和-d选项不能一起使用。
* 不要传递一个service x start命令在detached的容器。
>> * docker run -d -p 80:80 my_image service nginx start 
	(根进程service nginx start启动后立即返回，导致detached容器按照设计停止)
* $ docker run -d -p 80:80 my_image nginx -g 'daemon off;'

nginx镜像里不加，因在docker-compose.yml里有
```
docker history nginx:latest
CMD ["nginx" "-g" daemon...

```
# 要对一个detached容器输入/输出，使用网络连接和共享数据卷
要重新附着一个detached容器，使用docker attach命令
1.关闭docker:/etc/init.d/docker stop
2.sudo su切换到root身份，cd /var/lib/docker/containers/容器id/，进入对应容器目录
3.vi hostconfig.json，修改如下，将容器目录/import绑定到主机/data目录: "Binds": ["/data:/import"],
4.vi config.v2.json,修改如下，添加MountPoints: ....
5.启动docker:/etc/init.d/docker start
6.最后docker ecec -it 容器id /bin/bash进入ls -l /就可以看见import目录



 