
# 容器之间互通
* 新建两个容器
```
docker run -d --name box1 busybox /bin/sh -c "while true;do sleep 3600;done"
docker run -d --name box2 busybox /bin/sh -c "while true;do sleep 3600;done"
```
进入box1 ping box2
```
docker exec -it ac1aa7242949 /bin/sh
ping 172.17.0.3
```
表明新建的两个容器之间是可以互通的，他们之间通过bridge docker0进行通信，docker0为他们分别组了一对

# 通过 User-defined networks（推荐）
docker network来创建一个桥接网络，在docker run的时候将容器指定到新创建的桥接网络中，这样同一桥接网络中的容器就可以通过互相访问。
```
docker network create test-network
docker run -it --network test-network --network-alias mysql  -e MYSQL_ROOT_PASSWORD=123 mysql:5.7
docker run -it --network test-network --network-alias centos  centos /bin/bash

chrome 172.19.0.2

