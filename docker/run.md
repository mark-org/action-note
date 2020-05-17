
# docker run --help IMAGE ...

* -d --detach Run container in background and print container ID
* -p --publish list Publish a container's port(s) to the host
* --name Assign a name to the container 

# docker tag docker101tutorial {userName}/doccker101tutorial
# docker push {userName}/docker101tutorial

# -i --interactive
Keep STDIN open even if not attached
# -t --tty
Allocate a pseudo-TTY
* tty(终端设备的统称)
* 在UNIX系统中，计算机显示器通常被称为控制台终端（Console）

我们通常在linux下看到的控制台一般是/dev/ttyN，用户可以使用alt+Fn切换控制台，看起来感觉存在多个屏幕。
这种虚拟控制台对应tty1~n，（ssh就是这样，当你通过ssh登录一台服务器以后，就会在/dev/pts/下生成一个控制台设备文件，对应ttyＮ，通常情况下，1<=n<=63）其中 ：
tty0就是/dev/console，/dev/console指向当前虚拟终端。

# Alpine
Alpine Linux是一个完整的操作系统
官方 Alpine 镜像的文档：http://gliderlabs.viewdocs.io/docker-alpine
Docker容器。该容器就是一个Alpine Linux系统，
```
docker pull alpine
docker run -it --name myapline alpine
```
* 以Alpine为基础镜像，创建一个MySQL容器，镜像大小只有36.5MB
* 同样的方式使用Ubuntu系统作为基础镜像，镜像大小有184MB，
~~~

FROM alpine:3.6

RUN apk add --no-cache mysql-client

ENTRYPOINT ["mysql"]

创建一个test/mysqlclient:1.0镜像

docker build -t test/mysqlclient:1.0 .
~~~
Alpine Linux 中的 apk 命令讲解
alpine 提供了非常好用的apk软件包管理工具，

apk add 命令从仓库中安装最新软件包，并自动安装必须的依赖包，也可以从第三方仓库添加软件包。
apk add openssh openntp vim


Alpine Linux 是一个面向安全的轻型的 Linux 发行版。采用了 musl libc 和 busybox 以减小系统的体积和运行时资源消耗。在保持瘦身的同时，
Alpine Linux 还提供了自己的包管理工具 apk，如：apk add、apk update、apk del。


# -v --volume list Bind moutnt a volume

# -e --env list Set enviroment variables

# --netwwork Connect a container to a network

# --ip IPv4 address



