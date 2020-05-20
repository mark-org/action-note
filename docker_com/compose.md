

# Compose使用的三个步骤
* 使用Dockerfile定义应用程序的环境
* 使用docker-compose.yml定义构成应用程序的服务，这样它们可以在隔离环境中一起运行
* 最后，执行docker-compose up命令来启动并运行整个应用程序

# Compose安装
1. https://github.com/docker/compose/releases
2. curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-Linux-x86_64" -o /usr/local/bin/docker-compose
3. chmod +x /usr/local/bin/docker-compose
4. ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
5. docker-compose --version

