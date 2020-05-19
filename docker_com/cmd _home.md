
# images存储在哪
Docker的镜像以及一些数据都是在/var/lib/docker目录下，

docker cp ./a.txt containerId:/deng/
docker commit -a deng -m commit001 test01 REP:V

docker run -it -v /home/my_docker/v:/deng -name cName 27487 sh

