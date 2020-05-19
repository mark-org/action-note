systemctl 方式
# 停止 sudo systemctl stop docker
# 重启 sudo systemctl restart docker
# 守护进程重启 sudo systemctl daemon-reload


https://hub.docker.com/_/mysql


```
$ docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=root -d mysql

>>>>>1
FROM alpine:3.7
RUN apk add --no-cache mysql-client
ENTRYPOINT ["mysql"]

>>>>>2
docker build -t myalpine:0.1 .

>>>>>3
docker run -it --name myalpine myalpine:0.1 -h 服务端IP -uroot -p密码

193.112.136.240 3306 root @Dengppx123456

docker run -it --name mymysql mymysql -h 193.112.136.240 -uroot -p@Dengppx123456

```



使用镜像
```
FROM alpine:3.8
RUN echo http://mirrors.ustc.edu.cn/alpine/v3.8/main > /etc/apk/repositories
RUN echo http://mirrors.ustc.edu.cn/alpine/v3.8/community >> /etc/apk/repositories
RUN apk update && apk upgrade
RUN apk add mysql-client
ENTRYPOINT ["mysql"]

```

MySQL 备份专用镜像

```
FROM myalpine:0.1
RUN mkdir data
ENV mysql_user root
ENV mysql_pass 123
ENV mysql_host 服务端IP
ENV mysql_db test
ENTRYPOINT mysqldump -h$mysql_host -u$mysql_user -p$mysql_pass $mysql_db > /data/$mysql_db.sql
```

# 启动状态为Exited(0)容器
docker ps -a
docker start <CONTAINER ID>
docker rm <CONTAINER ID>
>>>>>>>>
docker run -d -p 8000:8000 openresty/openresty:lastest
docker run -p 8000:8000 -v /data:/data -d openresty/openresty:lastest
docker run -it nginx:lastest /bin/bash (交互模式启动,并在容器内执行/bin/bash命令)


# CMD ENTRYPOINT
* CMD给出的是一个容器的默认的可执行体。也就是容器启动以后，默认的执行的命令。重点就是这个“默认”。
* 它主要作用是默认的容器启动执行命令
### The CMD instruction has three forms:
* CMD ["executable","param1","param2"] (exec form, this is the preferred form)
* CMD ["param1","param2"] (as default parameters to ENTRYPOINT)
* CMD command param1 param2 (shell form)  默认是在/bin/sh -c下执行
```
FROM centos
CMD echo "hello cmd!"
=> docker run 7db28...
hello cmd!

CMD ["/bin/bash", "-c", "echo 'hello cmd!'"] 全路径
如果有多个，最后一个生效

docker run 76f echo glgl
glgl
```

# ENTRYPOINT
* An ENTRYPOINT allows you to configure a container that will run as an executable.
```
ENTRYPOINT has two forms:
ENTRYPOINT ["executable", "param1", "param2"] (exec form, preferred)

docker run -it --name mymysql10 mymysql ...
```




# docker inspect IMAGE_NAME 


# 通过docker history查看镜像构建过程（即dockerfile）






# 进入Docker容器比较常见的几种做法如下：
使用docker attach
使用SSH
使用nsenter
使用exec

sudo docker attach 44fc0f0582d9 
sudo docker exec -it 775c7c9ee1e1 /bin/bash


# attach和exec
Docker attach可以attach到一个已经运行的容器的stdin，然后进行命令执行的动作。
但是需要注意的是，如果从这个stdin中exit，会导致容器的停止。


使用-it时，则和我们平常操作console界面类似。而且也不会像attach方式因为退出，导致整个容器退出。
这种方式可以替代ssh或者nsenter、nsinit方式，在容器内进行操作。



* attach 直接进入容器 启动命令 的终端，不会启动新的进程。
* exec 则是在容器中打开新的终端，并且可以启动新的进程。
* 如果想直接在终端中查看启动命令的输出，用 attach；其他情况使用 exec。




















































