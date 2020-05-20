
# images存储在哪
Docker的镜像以及一些数据都是在/var/lib/docker目录下，

docker cp ./a.txt containerId:/deng/
docker commit -a deng -m commit001 test01 REP:V

docker run -it -v /home/my_docker/v:/deng -name cName 27487 sh

# 查看版本 cat /etc/issue
错误：cat /proc/version 或 uname -a ，这样查到的是宿主机的系统。

docker run --name my-custom-nginx-container -v /host/path/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx

Running nginx in read-only mode
```
$ docker run -d -p 80:80 --read-only -v $(pwd)/nginx-cache:/var/cache/nginx -v $(pwd)/nginx-pid:/var/run nginx
```

# 为什么使用Docker Compose File
按照docker官方的建议，每一个容器只启动一个进程，这样便于管理和解耦。
docker提供了Docker Compose File，可以使用docker-compose.yaml文件，按照特定的语法语句编写指令，
管理多个镜像的部署和端口等操作，实现真证的快速部署。
在不同服务器上部署时，只需要一个docker-compose.yaml文件，便能完成应用的部署操作。

docker-compose.yaml
```
version: "3.6"
services:
  flask-web:
    build: .
    ports:
        - "5000:9999"
    container_name: flask-web
  redis:
    image: redis
    container_name: redis
```

